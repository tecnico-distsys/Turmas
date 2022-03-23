# FAQ

## Estou a usar IntelliJ e o autocomplete não funciona!

Confirme que:

1. O SDK do Java está configurado no projeto (*File > Project Structure -> Project > SDK*)
2. A integração do Maven está ativada. Caso não tenha um menu Maven na barra lateral direita, clique com o botão direito
   do rato na raiz do projeto, escolha **"Add Framework Support"**, selecione Maven e clique em OK.
3. Corra a fase `install` do Maven no módulo contrato.
4. Caso já tenha corrido a fase `install`, use o botão **"Reload All Maven Projects"** no menu Maven da barra lateral
   direita (botão com setas circulares mais à esquerda desse menu).

Quando `mvn install` é corrido de um terminal, seja dentro ou fora do IntelliJ, pode ser necessário repetir o último
passo.

## Há situações em que não há um único erro a retornar ao cliente. Qual deles escolho?

Este aspeto nem sempre é especificado em sistemas reais. Para facilitar testagem, foi construída esta ordem:

1. INACTIVE\_SERVER
2. WRITING\_NOT\_SUPPORTED
3. ENROLLMENTS\_ALREADY\_OPENED
4. ENROLLMENTS\_ALREADY\_CLOSED
5. STUDENT\_ALREADY\_ENROLLED
6. NON\_EXISTING\_STUDENT
7. FULL\_CLASS
8. OK

As situações com índice menor tomam sempre precedência sobre as restantes, caso ocorram.

## Que formato de saída deve ter o meu programa?

Para permitir testagem automática, **têm** de
seguir [este formato](https://discord.com/channels/949644248045719622/955528908885868555/955529219629273119)

## O que acontece se um professor reabrir com capacidade inferior?

Seguindo o seguinte exemplo: um professor abre uma turma com 20 alunos, fecha a turma e reabre com 10.

- Caso estejam menos de 10 alunos inscritos a capacidade passa a 10 e abre.
- Caso estejam 10 alunos inscritos ou mais retorna FULL_CLASS ao professor.
