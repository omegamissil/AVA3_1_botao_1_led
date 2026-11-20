# AVA3 — Situação 1: Placa 1 (1 Botão — Módulo Transmissor)

Código-fonte referente à **Placa 1** na **Situação 1** (comunicação serial ponto a ponto unidirecional entre duas placas Arduino Uno simuladas no **Tinkercad Circuits**), atuando como nó transmissor a partir do acionamento de um botão.

## Arquivo Principal
- `Placa 1_um_led_um_botao.txt`

## Visão Geral do Circuito e Funcionamento
- **Microcontrolador:** Arduino Uno (Placa 1 — transmissora, à esquerda na simulação)[cite: 1].
- **Entrada (`BOT1`):** botão (*push button*) conectado ao pino digital `6` (`INPUT_PULLUP`) e ao terra comum (`GND`)[cite: 1].
- **Comunicação Serial (UART):** taxa de `9600` bps (`Serial.begin(9600)`), interligada de forma cruzada (`TX` $\rightarrow$ `RX` e `RX` $\rightarrow$ `TX`) com compartilhamento de `GND` junto à placa receptora[cite: 1].
- **Lógica (`loop()`):** lê o estado de `BOT1` com `digitalRead(BOT1)` e aplica negação lógica (`!`), fazendo com que o pressionamento (`LOW` no `INPUT_PULLUP`) envie o valor `1` e o repouso (`HIGH`) envie `0` por meio de `Serial.write()`, com intervalo de `500 ms` (`delay(500)`).

## Cenários Documentados no Tinkercad
- **Sistema inicial com um botão e um LED desligado:** estado de repouso (`BOT1` solto, valor enviado `0` e `LED1` apagado na placa receptora)[cite: 1].
- **Sistema inicial com um botão e um LED ligado:** acionamento de `BOT1`, enviando `1` pela UART para acender `LED1` na placa receptora.
