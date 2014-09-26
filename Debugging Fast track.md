# Debugging fast track

* Inspirado na apresentação

[Debugging Distilled with Xcode 6 & friends](https://bitbucket.org/kgelner/debuggingdistilled360idev)

* Kendall Helmstetter Gelner (@kendalldevdiary)



---

## Tales Pinheiro de Andrade
### @talesp

- Mestre em computação pelo IME-USP
- Desenvolvedor C desde 2002
- Objective-C desde 2007 (coisas basicas antes do iPhone!)
- iOS desde 2010

---

> We can not solve our problems with the same level of thinking that created them
-- Albert Einstein/Carl Jung

---

> The first moral of the story is that program testing can be used very effectively to show the presence of bugs but never to show their absence.
-- Edsger W. Dijkstra

[On the reliability of programs.](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD03xx/EWD303.html)

---

# Tópicos

- Depuração visual
- Depurando fluxo
- Depurando estado

---

## Depuração visual

---

# Depuração visual

- Simulador ajuda com aspectos visuais
	* Animações lentas
	* Mesclagem ou desalinhamento grafico

---

#core Animation

- Performance de UI mensuravel
- Inspeção visual de atributos aocultos
- Exame limitado da estrutura de aplicações de terceiros

---

# Xcode 6: View Debugging

- Dispositivos iOS 8+
- Ativado via ```Debug -> View Debugging -> Capture View
	- Paralisa a aplicação e monta hierarquia de views

---

# Reveal

- [revealapp.com](revealapp.com) - trial disponivel, $89
	- Mostra hierarquia de forma 2D ou 3D, permite manipulação das propriedades
	- Integração simples
	- Facil de usar/integrar
		- `static library`
		- `Dynamic Library`
		- `cocoapod`

---

#Flex

- FLEX: _Flipboard EXplorer_
- "Debug" visual in-app criado pelo Flipboard
- cocoapods
	- inspeção de elementos
	- navegação na arvore de subviews
	- manipulação de atributos

Para exibir

```oBjectivec
[[FLEXManager sharedManager] showExplorer];
```

![right,fit](https://camo.githubusercontent.com/9986601c5e4306f7935032465911c0f70596e046/687474703a2f2f656e67696e656572696e672e666c6970626f6172642e636f6d2f6173736574732f666c65782f62617369632d766965772d6578706c6f726174696f6e2e676966)

---

# Xcode 6: Constraint debugging

- warnings do Interface Builder

![inline](https://photos-5.dropbox.com/t/0/AAC2K8Ni-dpGH-1YV1CHutaVwZmuX5gskp9m8M7XdY9urA/12/43417/png/1024x768/3/1411678800/0/2/Captura%20de%20tela%202014-09-25%2016.22.18.png/7YVQ-pmr_eXS5jYnpYsaIESJNDv5z-uXfx0-PVJQstc)

---

# Xcode 6: Constraint debugging

- warnings do Interface Builder

![inline](https://photos-3.dropbox.com/t/0/AAA8Sf1pGNmoMu2Lhea3U6eLk1SNZZgDNEsuUxR92QoFjA/12/43417/png/1024x768/3/1411678800/0/2/Captura%20de%20tela%202014-09-25%2016.24.31.png/w4FxFEjYv71xX0R98djLtfYox7mjVaQKWH8D3bTMdyo)


---

# Xcode 6: Constraint debugging

- warnings do Interface Builder

![inline](https://photos-5.dropbox.com/t/0/AACemam2IcBDO0wLhttg1KRsyirJYtQHHUMMny9YvkS2pA/12/43417/png/1024x768/3/1411678800/0/2/Captura%20de%20tela%202014-09-25%2016.25.34.png/5WIlomFEgobQaNTT3mmMr4WeFa-K1LsbkZWVKV6mPOQ)

---

# Xcode 6: Constraint debugging

- warnings do Interface Builder
	- View Debugging exibe constraints

---

# Xcode 6: Constraint debugging


- Pense sobre restrições como largura / altura mais a informação de onde algo deve ir. 
- Um único erro pode cascatear para muitos, assim que encontrar a raiz do que a restrição problema está vinculado. 

---

# Simulando a Localização

- É possível configurar manualmente a localização no simulador;
- Usar arquivo GPX (simulando um caminho)
- Automator permite simulação mais precisa (direção e velocidade)
	- Apenas no simulador, não no dispositivo

![right, fit](https://photos-5.dropbox.com/t/0/AACBfS9Ry3a5ZcC07wTPnIpYlA0gc4T-Gx9Z9oYxZeCilw/12/43417/png/1024x768/3/1411678800/0/2/Captura%20de%20tela%202014-09-25%2016.36.35.png/xxU6dpODxgKbXzCPrGc1s0gEwBoXAoqjj5HsLjRZRCE)

---
 
# Breakpoints

- mais util quando ele não para
- uso de expressões como condição de parada
- Expressão deve ser usada na linguagem onde o código está

---

#Breakpoints
##Condições e expressões

- lldb deve poder interpretar o breakpoint
- com breakpoint "auto-continue", é possível aidionar pequenos blocos de código para adicionar logica _on the fly_

![inline](https://photos-4.dropbox.com/t/0/AAAvp5I7RI5sLrb2nVnXIY3LDVCpptx_8wIkNQwdeD-UNQ/12/43417/png/1024x768/3/1411678800/0/2/Captura%20de%20tela%202014-09-25%2016.46.13.png/jz2rVY1jKnpFfEb4sRb_dtz5xO2EBhyfSoMar5jyPVg)

---

#breakpoints

- Exception breakpoints
- Symbolic Breakpoints

![right, fit](https://photos-2.dropbox.com/t/0/AACmDsko21Hm8Q65zaWtG7oc-Dq3hkG_cx-QWHvP7QW-nQ/12/43417/png/1024x768/3/1411678800/0/2/Captura%20de%20tela%202014-09-25%2016.51.28.png/f8wZdGbyObGTr51jT2-009WWzW9ZuYs5bCu4ySVyMTU)

---

#Exception Breakpoint

[Selectively ignoring Objective-C exceptions in Xcode](http://chen.do/blog/2013/09/30/selectively-ignoring-objective-c-exceptions-in-xcode/)

Adicione a linha abaixo no arquivo `~/.lldbinit`


```bash
command script import ~/Library/lldb/ignore_specified_objc_exceptions.py
```

![inline](https://photos-4.dropbox.com/t/0/AABb_qVJxR4yq4nuZu1V-tJZh1d693BEUgy6yzA_0Eh51g/12/43417/png/1024x768/3/1411682400/0/2/Captura%20de%20tela%202014-09-25%2017.04.31.png/BekiztWCgwGsh5VHaGEMG9ET7_c3TigskxHSUAFT7Q4)

---

#Symbolic Breakpoint

Permite parar na chamada de um método

![inline](https://photos-6.dropbox.com/t/0/AACaCVq9BJLkS7mlnxzblIddZKROZEykZKzuWhZxG9WFYw/12/43417/png/1024x768/3/1411682400/0/2/Captura%20de%20tela%202014-09-25%2017.08.26.png/5gvI-RHT1SlwBzZ5lfI54R7xvHhL5ilTtSp_CYZCeSw)

---

#Symbolic Breakpoint

Permite parar na chamada de um método

```objectivec
([@"User" isEqualToString:[(NSEntityDescription*)[(NSManagedObject*)*(int*)($esp+4) entity] name]] && 
	[@"contact" isEqualToString:(NSManagedObject*)*(int*)($esp+16)]) || 
([@"Contact" isEqualToString:[(NSEntityDescription*)[(NSManagedObject*)*(int*)($esp+4) entity] name]] && 
	[@"user" isEqualToString:(NSManagedObject*)*(int*)($esp+16)])
```

---

#Log melhorado

- Função/método + número da linha:

```objectivec
#define ALog(format, ...) DLog((@"%s [L%d] " format), __PRETTY_FUNCTION__, __LINE__, ##__VA_ARGS__)
#define DLog(format, ...) ALog(format, ##__VA_ARGS__)
```

- Swift não tem `#DEFINE`, use bibliotecas externas
	- XCGLogger

---

#Log melhorado

- Opção melhor para Objective-C: CocoaLumberjack
	- niveis de debugs
	- cores no console via plugin `XcodeColors` (Alcatraz)
	- loggers para serviços de terceiros

```objectivec
    [DDLog addLogger:[DDASLLogger sharedInstance]];
    [DDLog addLogger:[DDTTYLogger sharedInstance]];
    [[DDTTYLogger sharedInstance] setColorsEnabled:YES];
    [[DDTTYLogger sharedInstance] setForegroundColor:[UIColor blueColor]
                                     backgroundColor:nil
                                             forFlag:LOG_FLAG_INFO];
    [DDLog addLogger:[CrashlyticsLogger sharedInstance]];

```

---

#Log melhorado

- Logs são pesados, use com cuidado
- Use blocks para logs pesados
- Background logging com Notificações locais (neanderthal debugging - Michael Oliver)
	(*APENAS EM DESENVOLVIMENTO!!!1!!1!1!!*)

--- 

# Instrument: Time Profiler

- Forma ótima de verificar onde o app está lento
- Ajuda a focar primeiro onde tem mais problema de performance
- Permite visualizar por nucleo de processador
- Xcode Profiler serve como guide line
- Record Waiting threads ajuda

---

# Instrument: Time Profiler

![inline](/Users/talesp/Dropbox/Public/time profiler.mov)

---
# lldb - expressions

- acessada via `expr` no console do `lldb`
- Permite rodar código real em run-time
- permite definir variáveis globais com prefixo (use `id` para tipos complexos)
- patcht em real-time!

---
# lldb - comandos uteis

- `po recursiveDesccription`: dump da hierarquia de views
- crash na chamada de `objc_msgsend`?
	- `p (char *)$ecx` (simulator) 
	- `p (char *)$r1` (device)
- Watchpoints
	- `watchpoint set variable self->_myProp`
	- `watchpoint delete <number>`

---

# Outras ferramentas

- Network link conditioner
	- Parte do "Hardware IO Tools"
	- Afeta todo o sistema
- [Charles Proxy](http://www.charlesproxy.com)
- [Chisel](https://github.com/facebook/chisel)
- [CoreDataPro](https://github.com/yepher/CoreDataUtility)
- [Core Data Editor](https://github.com/ChristianKienle/Core-Data-Editor)

