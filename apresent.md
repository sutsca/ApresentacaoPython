---
theme: default
slideNumber: true
transition: slide
---

# Calculadora de TMB: Explicação do Código

---

## Função `calcular_tmb`


def calcular_tmb(peso, altura, idade, sexo):
    if sexo == "masculino":
        tmb = 66 + (13.7 * peso) + (5 * altura) - (6.8 * idade)
    elif sexo == "feminino":
        tmb = 665 + (9.6 * peso) + (1.8 * altura) - (4.7 * idade)
    else:
        tmb = None
        print("Sexo não reconhecido.")
    return tmb


A função calcular_tmb calcula a Taxa de Metabolismo Basal (TMB) usando a equação de Harris-Benedict.

---
 ## Função `calcular_macronutrientes`

 def calcular_macronutrientes(peso):
    prot = 2 * peso 
    carb = 3 * peso
    gord = 0.5 * peso
    return prot, carb, gord

A função calcular_macronutrientes calcula a quantidade de proteína, carboidratos e gorduras em gramas com base no peso do usuário.
---

## Função `calcular_gasto_calorico`

def calcular_gasto_calorico(exercicio, peso, tempo):
    if exercicio == 1:
        return 3.5 * peso * tempo
    elif exercicio == 2:
        return 6 * peso * tempo
    elif exercicio == 3:
        print("Saindo do programa!")
        sys.exit()
    else:
        print("Exercício não reconhecido.")
        return None

A função calcular_gasto_calorico calcula o gasto calórico com base no tipo de exercício, peso do usuário e tempo de prática.


---

## Função `main`

def main():
    # Captura de dados do usuário
    peso = float(input("Digite seu peso (em kg): "))
    altura = float(input("Digite sua altura (em centimetros): "))
    idade = float(input("Digite sua idade: "))
    sexo = input("Digite seu sexo (masculino/feminino): ").lower()

    # Cálculo da TMB
    tmb = calcular_tmb(peso, altura, idade, sexo)

    if tmb is not None:
        # Exibição da TMB
        print(f"Sua taxa de metabolismo basal é {tmb:.2f} calorias.")

        # Cálculo de macronutrientes
        prot, carb, gord = calcular_macronutrientes(peso)
        print(f"Para atender suas necessidades diárias, consuma {prot:.2f}g de proteína, {carb:.2f}g de carboidratos e {gord:.2f}g de gordura.")

        # Captura de dados de exercício
        print("Digite o número do exercício que você pratica:")
        print("1 - Musculação média")
        print("2 - Musculação alta")
        print("3 - Não pratico nenhum desses exercícios / Sair")
        exercicio = int(input("Digite o numero do exercício desejado: "))
        tempo = float(input("Por quanto tempo você pratica essa atividade em horas: "))
        gasto_calorico = calcular_gasto_calorico(exercicio, peso, tempo)

        # Exibição do gasto calórico
        if gasto_calorico is not None:
            if exercicio == 1:
                print(f"Durante {tempo} horas de Musculação média, você queimou {gasto_calorico:.2f} calorias.")
            elif exercicio == 2:
                print(f"Durante {tempo} horas de Musculação alta, você queimou {gasto_calorico:.2f} calorias.")
        else:
            print("Exercício não reconhecido.")
    else:
        print("Não foi possível calcular a TMB. Verifique os dados fornecidos.")

if __name__ == "__main__":
    main()

