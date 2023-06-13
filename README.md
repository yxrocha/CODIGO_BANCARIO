# CODIGO_BANCARIO
import time
menu = """
[1] DEPOSITO
[2] SAQUE
[3] EXTRATO
[4] SAIR
"""
saldo = 0
limite = 500
extrato = ""
numeros_saque = 0
LIMITE_SAQUE = 3

while True:
    opcao = str(input(menu)).strip()

    if opcao == '1':
        saldo += float(input(('DEPOSITO: QUANTO DESEJA DEPOSITAR ? R$ ')))

        if saldo < 1:
            print('você digitou um número negativo, favor tente novamente')
            break
        print(f'Deposito realizado com sucesso, seu saldo é de R$ {saldo:.2f}')
        r = str(input((" \n  \n deseja fazer mais Alguma operação ?[S/N]: "))).upper().strip()

        if r not in ('S','SIM','YES'):
            break        

    elif opcao == '2':
        print('SAQUE')
        numeros_saque += 1
        saque = float(input('QUANTO DESEJA SACAR ? R$ '))
                      
        if saque > saldo or saque > limite:
            print('você não tem saldo suficiente e não pode sacar mais de R$ 500.00 por vez')
            time.sleep(3)
            break

        if numeros_saque > LIMITE_SAQUE:
            print('Você so pode fazer 3 saques por dia.')
            time.sleep(3)
            break

        saldo -= saque
        extrato +=f'{saldo} - {saque}\n'
        print(f'SAQUE REALIZADO COM SUCESSO, SEU SALDO É DE R$:{saldo:.2f}')
        r = str(input((" \n  \n deseja fazer mais Alguma operação ?[S/N]: "))).upper().strip()
        if r not in ('S','SIM','YES'):
            break   

    elif opcao == '3':
        print('EXTRATO')
        extrato = f"""
        =-=-=-=-=-=-=-=-=EXTRATO=-=-=-=-=-=-=-=-=  
         SALDO R${saldo}                           
         SAQUES: {numeros_saque}
         SAQUER:                                        
         {extrato}                                 
        ========================================= 
        """
        print(extrato)
        r = str(input((" \n  \n deseja fazer mais Alguma operação ?[S/N]: "))).upper().strip()
        if r not in ('S','SIM','YES'):
            break   
    elif opcao == '4':
        break
    else:
        print('OPERAÇÃO INVALIDA, FAVOR DIGITE UMA DAS OPÇÕES.')

