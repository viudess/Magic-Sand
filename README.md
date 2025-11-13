# Magic Sand

Magic Sand é um software para operar uma **caixa de areia de realidade aumentada** como esta:

<img width="500" alt="Visão de uma Magic Sandbox" src="https://github.com/user-attachments/assets/eda1a91e-b9ce-4fab-9b7d-64f9babbcee5" />

Uma caixa de areia de realidade aumentada é composta por uma caixa de areia, um sensor de profundidade (como o Kinect) e um projetor acoplados.  
O software deste repositório controla o projetor e o Kinect para projetar sobre a areia **cores relacionadas à altura da areia**.

Este projeto foi inspirado e adaptado do [Augmented Reality Sandbox](https://arsandbox.ucdavis.edu), desenvolvido pela [UC Davis](http://idav.ucdavis.edu/~okreylos/ResDev/SARndbox/).  
É uma versão parcialmente portada do projeto [SARndbox](https://github.com/KeckCAVES/SARndbox) de Oliver Kreylos, feita em [openFrameworks](http://openframeworks.cc/), e também adaptada do [ofxKinectProjectorToolkit](https://github.com/genekogan/ofxKinectProjectorToolkit) por Gene Kogan.

Ele foi portado para o openFrameworks com **suporte multiplataforma (Linux/MacOS/Windows)**, uma **interface simples** e um **procedimento de calibração robusto e fácil**, por [Thomas Wolf](https://thomwolf.io) e posteriormente modificado e expandido com alguns jogos por [Rasmus R. Paulsen](http://people.compute.dtu.dk/rapa).

![Animação de uma Magic Sandbox](./art/animated-box.gif)

Magic Sand foi desenvolvido com o objetivo específico de **simplificar o uso de uma caixa de areia de realidade aumentada em ambientes domésticos/familiares**:
- Funciona em um notebook ou computador doméstico intermediário (Windows / Mac OS X / Linux, requisitos mínimos de GPU).
- Calibração simples para fácil montagem e desmontagem da caixa de areia.
- Interface fácil de usar.
- Framework para futuros jogos e aplicativos baseados em sandbox.

<img width="500" alt="image" src="https://github.com/user-attachments/assets/f0f5b4d8-9261-44e1-ae49-0f22fe99ce98" />

## Principais Recursos

Funciona em um computador conectado a um projetor e a um sensor Kinect.  
O software controla o projetor para projetar cores de acordo com o nível da areia medido pelo Kinect, transformando a caixa de areia em um **playground colorido**.

![Interface do Magic Sandbox](./art/explication.png)

---

## Primeiros Passos

O modo mais fácil de começar é montar o setup físico seguindo o guia encontrado na [página do tutorial](https://imgur.com/gallery/Q86wR) e/ou conferir o [tópico no Reddit](https://www.reddit.com/r/DIY/comments/4v1gfi/a_magic_sandbox_i_made_for_my_3_yo_sons_birthday/).

Em seguida, baixe e instale/descompacte a versão mais recente do software na [página de lançamentos](https://github.com/thomwolf/Magic-Sand/releases/latest).  
Siga as instruções na página de lançamento para baixar e instalar os drivers necessários.

---

### Configurando o Sistema

Conecte e ligue o projetor e o Kinect e inicie o software.

Por padrão, o software inicia no modo **setup**, onde a imagem de profundidade ou de cor do Kinect pode ser visualizada na interface, e o projetor exibe uma imagem branca.  
Assim, é possível verificar se o Kinect está funcionando (no Windows 10, às vezes é necessário conectar e desconectar o Kinect algumas vezes) e se o projetor está operando.  
O status do Kinect e do projetor é exibido na janela inferior esquerda da interface.

No modo **setup**, é possível otimizar a posição física do Kinect e do projetor.

---

### Calibração

Para calibrar o sistema e alinhar o Kinect ao projetor, siga estes passos:

- Alise a areia dentro da caixa.
- Verifique se você vê a imagem de profundidade ou de cor do Kinect (clique em **advanced | Display Kinect Depth View**).
- Pressione **Calibration | Manually Draw Sand Region**.
- Defina a região da areia desenhando um retângulo com o mouse.
- Pressione **Automatically Calibrate Kinect & Projector** — padrões de tabuleiro de xadrez serão projetados na areia.
- Quando solicitado, cubra a caixa de areia com um pedaço de papelão claro.
- Pressione OK — novos padrões de xadrez serão projetados sobre o papelão.

Se a calibração for bem-sucedida, o status será atualizado indicando que tudo está correto.

#### Modo de depuração da calibração

Se a calibração falhar, é possível habilitar o modo de depuração, que criará arquivos na pasta **data\DebugFiles**.  
Esses arquivos podem ajudar a identificar o motivo da falha.  
Para isso, habilite **advanced | Dump Debug** e execute novamente a calibração.

---

## Iniciando a Aplicação

Se a calibração foi bem-sucedida (ou já realizada anteriormente), pressione **espaço** ou o botão **Run**.

Agora, um **mapa colorido com linhas de contorno** deve aparecer sobre a areia.  
A taxa de quadros deve ser próxima de **60 FPS** em PCs modernos.

---

## Jogos na Caixa de Areia

O Magic Sand inclui alguns jogos.

### Shape an Island (Molde uma Ilha)

O jogo se baseia no fato de que a Dinamarca possui mais de [400 ilhas](https://en.wikipedia.org/wiki/List_of_islands_of_Denmark).  
O objetivo é moldar uma ilha que corresponda a uma ilha real.

#### Como jogar:
1. Pressione **espaço** para iniciar.
2. Modele uma grande ilha no centro (em até 30 segundos), **sem tocar nas bordas da caixa**.
3. O sistema verificará se uma ilha existe.
4. Um nome de ilha será exibido (por exemplo, “Austrália”).
5. Você terá 30 segundos para moldá-la.
6. O sistema mostrará sua pontuação.
7. Você terá 1 minuto para ajustar a ilha.
8. Uma pontuação final será exibida, comparada com o recorde.

Foi usado em um evento educacional na Ilha dinamarquesa de Bornholm, mostrado neste [vídeo](https://www.youtube.com/watch?v=dDMrxtH1hyU).

Desenvolvido por **Rasmus R. Paulsen**.

---

### Sandimals (Jogo de 2 Jogadores)

Neste jogo, a caixa é dividida em duas metades.  
Cada jogador pode mover apenas a areia da sua parte.  
O objetivo é **coletar o máximo de comida e peles possível em 5 minutos**.

- Comece o jogo pressionando **f** no teclado.  
- Após 5 minutos, o jogo termina e o jogador com mais pontos vence.
- Também é possível iniciar com **1 (iniciante)**, **2 (novato)**, **3 (normal)** e **4 (expert)**.

#### Comportamento dos Peixes:
- Cinza claro.
- 10 a 30 peixes, dependendo do nível.
- Movem-se em cardumes e fogem de tubarões.
- Possuem um ciclo de vida limitado.
- O peixe mais velho é o “peixe-mãe”.

#### Comportamento dos Tubarões:
- Brancos, dois por caixa.
- Quando bem alimentados, têm barriga branca; quando famintos, preta; e quando caçando, vermelha.
- Caçam os maiores peixes próximos.
- Se ficarem presos e não comerem, morrem e renascem.

#### Coelhos:
- Vivem em terra firme.
- Movem-se em pausas.
- Quantidade varia por nível.

Peixes e tubarões podem ser movidos com as mãos em forma de tigela.  
Desenvolvido por **Rasmus R. Paulsen**.

---

### O Jogo dos Animais e suas Mães

Um peixe-mãe e uma coelha-mãe podem ser ativados.  
O jogador ajuda os filhotes a alcançarem suas mães, moldando rios ou montanhas.

Inicie com a tecla **m**.  
Desenvolvido por **Thomas Wolfe**.

---

## Codificação e Extensão do Magic Sand

### Código-Fonte

O código completo está disponível em:  
👉 [github.com/thomwolf/Magic-Sand](https://github.com/thomwolf/Magic-Sand)

---

### Dependências

Magic Sand é baseado no [openFrameworks](http://openframeworks.cc/) versão 0.9.3 e usa os seguintes addons:

- **Addons oficiais** (já inclusos):
  - ofxOpenCv  
  - ofxKinect  
  - ofxXmlSettings  
- **Addons da comunidade:**
  - [ofxCv](https://github.com/kylemcdonald/ofxCv)  
  - [ofxParagraph](https://github.com/braitsch/ofxParagraph)  
  - [ofxDatGui (versão modificada)](https://github.com/thomwolf/ofxDatGui)  
  - [ofxModal](https://github.com/braitsch/ofxModal)  

---

### Início Rápido para Edição do Código

1. Baixe o [openFrameworks](http://openframeworks.cc/download/) para seu sistema operacional.  
2. Descompacte o Magic Sand na pasta **apps/myApps**.  
3. Adicione os addons listados acima na pasta **addons**.  
4. No Windows, instale os drivers do Kinect conforme indicado na [página de lançamentos](https://github.com/thomwolf/Magic-Sand/releases/latest).  
5. Divirta-se! (projetos para Xcode e VS2015 incluídos).

---

## Diferenças Principais em Relação ao [SARndbox](https://github.com/KeckCAVES/SARndbox)

- **Multiplataforma:** Magic Sand roda em Windows, Mac e Linux.  
- **Mais simples de modificar:** SARndbox herda ferramentas de VR mais complexas.  
- **Calibração automática:** Magic Sand usa o registro embutido do Kinect, dispensando calibração por pixels.  
- **Menor precisão:** ligeiramente menos preciso que o SARndbox.  
- **Sem chuva dinâmica:** recurso não incluído (exige GPU mais potente).

---

# Changelog

## [1.5.4.1](https://github.com/thomwolf/Magic-Sand/releases/tag/v1.5.4.1) - 10/10/2017
**Correções de bugs**
- O procedimento de calibração estava quebrado na versão 1.5.4 — agora corrigido.  
**Adicionado**
- Makefiles para Linux (experimental)

## [1.5.4](https://github.com/thomwolf/Magic-Sand/releases/tag/v1.5.4) - 23/09/2017
**Melhorias**
- Contador de FPS do Kinect.
- Arquivos de build XCode.
- Filtro de quadro completo.
- Opção de InPainting para remover ruídos.
- Melhor escala da GUI.
- Recursos de debug (ROI e coordenadas).
- Atualização de GUI do jogo dos animais.
- Modos de dificuldade (1–4).

**Correções**
- Filtro espacial agora funciona corretamente.

## [1.5.0](https://github.com/thomwolf/Magic-Sand/tree/v1.5) - 08/08/2017
**Lançamento inicial do Magic-Sand com jogos**
