menu = """

[3] Depositar
[2] Sacar
[1] Extrato
[0] Sair

=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao == "3":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! O valor informado é inválido.")
            
    elif opcao == "2":
        valor = float(input("Informe o valor de saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1


        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "1":
        print("\n================ EXTRATO ================")
        print("Não foram realisadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.f}")
        print("==========================================")

    elif opcao == "0":
        breack

    else:
        print("Operação inválida, por favor selecionar novamente a operação desejada.")
        
