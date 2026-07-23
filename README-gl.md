🌍
*[Čeština](README-cs.md) ∙ [Deutsch](README-de.md) ∙ [Ελληνικά](README-el.md) ∙ [English](README.md) ∙ [Español](README-es.md) ∙ [Français](README-fr.md) ∙ [Galician](README-gl.md) ∙ [Indonesia](README-id.md) ∙ [Italiano](README-it.md) ∙ [日本語](README-ja.md) ∙ [한국어](README-ko.md) ∙ [polski](README-pl.md) ∙ [Português](README-pt.md) ∙ [Română](README-ro.md) ∙ [Русский](README-ru.md) ∙ [Slovenščina](README-sl.md) ∙ [Українська](README-uk.md) ∙ [简体中文](README-zh.md) ∙ [繁體中文](README-zh-Hant.md)*


# A arte da liña de comandos

*Nota do autor: Teño previsto revisar isto e estou a buscar un novo coautor para axudar a expandilo nunha guía máis completa. Aínda que é moi popular, podería ser máis ampla e un pouco máis profunda. Se che gusta escribir, tes un amplo coñecemento deste tema e estás disposto a axudar, envíame unha nota a josh (0x40) holloway.com. –[jlevy](https://github.com/jlevy), [Holloway](https://www.holloway.com). Grazas!*

- [A arte da liña de comandos](#a-arte-da-liña-de-comandos)
  - [Meta](#meta)
  - [Básicos](#básicos)
  - [Uso cotián](#uso-cotián)
  - [Procesando arquivos e datos](#procesando-arquivos-e-datos)
  - [Depuración do sistema](#depuración-do-sistema)
  - [Liñas únicas](#liñas-únicas)
  - [Escuro pero útil](#escuro-pero-útil)
  - [Só para macOS](#só-para-macos)
  - [Só para Windows](#só-para-windows)
    - [Formas de obter ferramentas Unix baixo Windows](#formas-de-obter-ferramentas-unix-baixo-windows)
    - [Ferramentas útiles da liña de comandos de Windows](#ferramentas-útiles-da-liña-de-comandos-de-windows)
    - [Consellos e trucos de Cygwin](#consellos-e-trucos-de-cygwin)
  - [Máis recursos](#máis-recursos)
  - [Aviso legal](#aviso-legal)
  - [Licenza](#licenza)


![curl -s 'https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md' | egrep -o '`\w+`' | tr -d '`' | cowsay -W50](cowsay.png)

A fluidez na liña de comandos é unha habilidade a miúdo descoidada ou considerada arcana, pero mellora a túa flexibilidade e produtividade como enxeñeiro tanto de xeitos obvios como sutís. Esta é unha selección de notas e consellos sobre o uso da liña de comandos que atopamos útiles ao traballar en Linux. Algúns consellos son elementais, e outros son bastante específicos, sofisticados ou escuros. Esta páxina non é longa, pero se podes usar e lembrar todos os puntos que aquí se recollen, saberás moito. 

Esta obra é o resultado de [moitos autores e tradutores](AUTHORS.md).
Parte disto apareceu 
[orixinalmente](http://www.quora.com/What-are-some-lesser-known-but-useful-Unix-commands)
[appeared](http://www.quora.com/What-are-the-most-useful-Swiss-army-knife-one-liners-on-Unix)
en [Quora](http://www.quora.com/What-are-some-time-saving-tips-that-every-Linux-user-should-know),
pero desde entón trasladouse a GitHub, onde persoas con máis talento que o autor orixinal fixeron numerosas melloras.
[**Envía unha pregunta**](https://airtable.com/shrzMhx00YiIVAWJg) se tes algunha dúbida relacionada coa liña de comandos. [**Por favor, contribúe**](/CONTRIBUTING.md) se ves algún erro ou algo que podería mellorar!

## Meta

Alcance:

- Esta guía é tanto para principiantes como para usuarios con experiencia. Os obxectivos son *amplitude* (todo o importante), *especificidade* (dar exemplos concretos dos casos máis comúns), e *brevedade* (evitar cousas que non sexan esenciais ou digresións que poidas buscar facilmente noutro lugar). Cada consello é esencial nalgunha situación ou aforra significativamente tempo fronte a outras alternativas.
- Está escrito para Linux, agás as seccións de "[Só para macOS](#macos-only)" e "[Só para Windows](#windows-only)". Moitos dos outros puntos son aplicables ou pódense instalar noutros sistemas Unix ou en macOS (ou mesmo en Cygwin).
- O enfoque está en Bash interactivo, aínda que moitos consellos se aplican a outras shells e á programación xeral en Bash.
- Inclúe tanto comandos "estándar" de Unix como outros que requiren a instalación de paquetes especiais -- sempre que sexan o suficientemente importantes como para merecer a súa inclusión.

Notas:

- Para manter isto nunha soa páxina, o contido inclúese implícitamente por referencia. Es o suficientemente intelixente para buscar máis detalles noutro lugar unha vez que coñezas a idea ou o comando para usar en Google. Emprega `apt`, `yum`, `dnf`, `pacman`, `pip` ou `brew` (segundo corresponda) para instalar programas novos.
- Emprega [Explainshell](http://explainshell.com/) para obter unha explicación útil do que fan as ordes, opcións, tubos(pipes), etc..


## Básicos

- Aprende o básico de Bash. Daquela, escribe `man bash` e polo menos repasa todo; é bastante doado de seguir e non é tan longo. As outras shells poden ser agradables, pero Bash é potente e sempre dispoñible (aprender *só* zsh, fish, etc., aínda que sexa tentador no teu propio portátil, limítache en moitas situacións, como ao usar servidores existentes).

- Aprende ben polo menos un editor de texto. O editor `nano` é un dos máis sinxelos para edición básica (abrir, editar, gardar, buscar). Con todo, para o usuario avanzado nunha terminal de texto, non hai substituto para Vim (`vi`), un editor difícil de aprender pero venerable, rápido e con todas as funcións. Moita xente tamén usa o clásico Emacs, particularmente para tarefas de edición máis amplas. (Por suposto, calquera desenvolvedor de software moderno que traballe nun proxecto extenso é improbable que use só un editor de texto puro e tamén debería estar familiarizado con IDEs e ferramentas gráficas modernas.)

- Atopar documentación:
  - Saber ler a documentación oficial con `man` (para os curiosos, `man man` lista os números de sección, por exemplo 1 son comandos "regulares", 5 son ficheiros/convencións e 8 son para administración). Atopa páxinas man con `apropos`.
  - Aprende que algúns comandos non son executábeis, senón comandos internos de Bash, e que podes obter axuda sobre eles con `help` e `help -d`. Podes descubrir se un comando é un executábel, un comando interno do shell ou un alias empregando `type command`.
  - `curl cheat.sh/command` devolverá unha breve "folla de trucos" con exemplos comúns de como usar un comando de shell.

- Aprende sobre a redirección de saída e entrada usando `>` e `<` e as tuberías usando `|`. Aprende que `>` sobrescribe e `>>` engade o ficheiro de saída. Aprende sobre `stdout` e `stderr`.

- Aprende sobre a expansión de glob de ficheiros con `*` (e quizais `?` e `[`...`]`) e sobre a notación de citas, así como a diferenza entre as comiñas dobres `"` e as simples `'`. (Ver máis sobre a expansión de variables a continuación.)

- Coñece a xestión de traballos en Bash: `&`, **ctrl-z**, **ctrl-c**, `jobs`, `fg`, `bg`, `kill`, etc.

- Coñece `ssh` e os conceptos básicos da autenticación sen contrasinal, mediante `ssh-agent`, `ssh-add`, etc.

- Xestión básica de ficheiros: `ls` e `ls -l` (en particular, aprende o que significa cada columna en `ls -l`), `less`, `head`, `tail` e `tail -f` (ou aínda mellor, `less +F`), `ln` e `ln -s` (aprende as diferenzas e vantaxes dos enlaces duros fronte aos enlaces simbólicos), `chown`, `chmod`, `du` (para un resumo rápido do uso do disco: `du -hs *`). Para a xestión do sistema de ficheiros, `df`, `mount`, `fdisk`, `mkfs`, `lsblk`. Aprende que é un inodo (`ls -i` ou `df -i`).

- Xestión básica de redes: `ip` ou `ifconfig`, `dig`, `traceroute`, `route`.

- Aprende e usa un sistema de control de versións, como `git`.

- Coñece ben as expresións regulares e as diversas opcións de `grep`/`egrep`. Cómpre coñecer as opcións `-i`, `-o`, `-v`, `-A`, `-B` e `-C`.

- Aprende a usar `apt-get`, `yum`, `dnf` ou `pacman` (segundo a distribución) para buscar e instalar paquetes. E asegúrate de ter `pip` para instalar ferramentas de liña de comandos baseadas en Python (algunhas das que aparecen máis abaixo son máis sinxelas de instalar con `pip`).


## Uso cotián

- En Bash, usa **Tab** para completar argumentos ou listar todos os comandos dispoñibles e **ctrl-r** para buscar no historial de comandos (despois de premalo, escribe para buscar, preme **ctrl-r** repetidamente para alternar entre máis coincidencias, preme **Enter** para executar o comando atopado ou preme a frecha á dereita para colocar o resultado na liña actual e permitir a edición).
  
- En Bash, usa **ctrl-w** para eliminar a última palabra e **ctrl-u** para eliminar o contido desde o cursor actual ata o comezo da liña. Emprega **alt-b** e **alt-f** para desprazarte por palabra, **ctrl-a** para levar o cursor ao comezo da liña, **ctrl-e** para levalo ao final da liña, **ctrl-k** para eliminar ata o final da liña e **ctrl-l** para limpar a pantalla. Consulta `man readline` para ver todas as combinacións de teclas predeterminadas en Bash. Son moitas. Por exemplo, **alt-.** cíclase polos argumentos anteriores, e **alt-*** expande un glob.


- Alternativamente, se che gustan os atallos de teclado ao estilo vi, usa `set -o vi` para activalo (e `set -o emacs` para desactivalo).

- Para editar comandos longos, despois de configurar o teu editor (por exemplo, `export EDITOR=vim`), **ctrl-x** **ctrl-e** abrirá o comando actual nun editor para edición multilínea. Ou en estilo vi, **escape-v**.

- Para ver os comandos recentes, usa `history`. A continuación, escribe `!n` (onde `n` é o número do comando) para executalo de novo. Tamén hai moitas abreviaturas que podes usar, sendo as máis útiles probablemente `!$` para o último argumento e `!!` para o último comando (ver "EXPANSIÓN DE HISTORIA" na páxina do manual). Con todo, estas adoitan substituírse facilmente por **ctrl-r** e **alt-.**.

- Vai ao teu directorio persoal con `cd`. Accede aos ficheiros relativos ao teu directorio persoal co prefixo `~` (por exemplo, `~/.bashrc`). Nos scripts de `sh`, refírese ao directorio persoal como `$HOME`.

- Para volver ao directorio de traballo anterior: `cd -`.

- Se estás a medio escribir un comando pero cambias de idea, preme **alt-#** para engadir un `#` ao principio e introdúceo como comentario (ou usa **ctrl-a**, **#**, **enter**). Logo podes volver a el máis tarde a través do historial de comandos.

- Usa `xargs` (ou `parallel`). É moi potente. Ten en conta que podes controlar cantos elementos se executan por liña (`-L`) así como o paralelismo (`-P`). Se non estás seguro de que funcione correctamente, usa primeiro `xargs echo`. Ademais, `-I{}` é útil. Exemplos:
  ```bash
  find . -name '*.py' | xargs grep some_function
  cat hosts | xargs -I{} ssh root@{} hostname
  ```

- `pstree -p` é unha visualización útil da árbore de procesos.

- Emprega `pgrep` e `pkill` para atopar ou sinalar procesos polo nome (`-f` é moi útil).

- Coñece os distintos sinais que podes enviar aos procesos. Por exemplo, para suspender un proceso, usa `kill -STOP [pid]`. Para a lista completa, consulta `man 7 signal`.

- Usa `nohup` ou `disown` se queres que un proceso en segundo plano siga funcionando para sempre.

- Comproba que procesos están escoitando mediante `netstat -lntp` ou `ss -plat` (para TCP; engade `-u` para UDP) ou `lsof -iTCP -sTCP:LISTEN -P -n` (que tamén funciona en macOS).
  
- Proba tamén `lsof` e `fuser` para sockets e ficheiros abertos.

- Consulta `uptime` ou `w` para saber canto tempo leva o sistema en funcionamento.

- Usa `alias` para crear atallos para comandos de uso común. Por exemplo, `alias ll='ls -latr'` crea un novo alias `ll`.

- Garda os alias, a configuración do shell e as funcións que utilizas con frecuencia en `~/.bashrc`, e [configúrao para que os shells de inicio de sesión o carguen](http://superuser.com/a/183980/7106).  Isto fará que a túa configuración estea dispoñible en todas as túas sesións de shell.

- Pon na túa `~/.bash_profile` a configuración das variables de contorno e os comandos que se deben executar cando inicias sesión. Será necesaria unha configuración separada para as shells que lanzas desde inicios de sesión en contornos gráficos e para os traballos de `cron`.

- Sincroniza os teus ficheiros de configuración (por exemplo, `.bashrc` e `.bash_profile`) entre varios ordenadores con Git.

- Comprende que cómpre ter coidado cando as variables e os nomes de ficheiros inclúen espazos en branco. Rodea as túas variables Bash con comiñas, por exemplo `"$FOO"`. Prefire as opcións `-0` ou `-print0` para permitir que os caracteres null delimiten os nomes de ficheiros, por exemplo `locate -0 pattern | xargs -0 ls -al` ou `find / -print0 -type d | xargs -0 ls -al`. Para iterar sobre nomes de ficheiros que conteñan espazos nun bucle `for`, configura o IFS para que sexa só un salto de liña usando `IFS=$'\n'`.

- En scripts de Bash, usa `set -x` (ou a variante `set -v`, que rexistra a entrada en bruto, incluíndo variables non expandidas e comentarios) para a saída de depuración. Emprega os modos estritos a menos que teñas un bo motivo para non facelo: usa `set -e` para abortar en caso de erros (código de saída *nonzero*). Emprega `set -u` para detectar usos de variables non definidas. Considera tamén `set -o pipefail` para abortar en erros dentro de tubos (pipe), aínda que léeo con máis detalle se o fas, xa que este tema é algo sutil. Para scripts máis complexos, emprega tamén `trap` en EXIT ou ERR. Unha práctica útil é comezar un script deste xeito, o que lle permitirá detectar e abortar en erros comúns e imprimir unha mensaxe:

  ```bash
  set -euo pipefail
  trap "echo 'error: Script failed: see failed command above'" ERR
  ```

- En scripts de Bash, as subshells (escritas con parénteses) son xeitos convenientes de agrupar comandos. Un exemplo común é cambiar temporalmente a un directorio de traballo diferente, e.g.
  ```bash
  # fai algo na carpeta actual
  (cd /some/other/dir && other-command)
  # continuar na carpeta orixinal
  ```

- En Bash, observa que hai moitos tipos de expansión de variables. Para comprobar se unha variable existe: `${name:?mensaxe de erro}`. Por exemplo, se un script de Bash require un único argumento, simplemente escribe `input_file=${1:?usage: $0 input_file}`. Para usar un valor predeterminado se unha variable está baleira: `${name:-valor predeterminado}`. Se queres engadir un parámetro adicional (opcional) ao exemplo anterior, podes usar algo como `output_file=${2:-logfile}`. Se se omite `$2` e, polo tanto, está baleiro, `output_file` establecerase en `logfile`. Expansión aritmética: `i=$(( (i + 1) % 5 ))`. Secuencias: `{1..10}`. Recorte de cadeas: `${var%suffix}` e `${var#prefix}`. Por exemplo, se `var=foo.pdf`, entón `echo ${var%.pdf}.txt` imprime `foo.txt`.

- A expansión de parenteses usando `{`...`}` pode reducir a necesidade de reescribir texto similar e automatizar combinacións de elementos.  Isto é útil en exemplos como `mv foo.{txt,pdf} some-dir` (que move ambos ficheiros), `cp somefile{,.bak}` (que se expande a `cp somefile somefile.bak`) ou `mkdir -p test-{a,b,c}/subtest-{1,2,3}` (que expande todas as combinacións posibles e crea unha árbore de directorios). A expansión de parenteses curvos realízase antes de calquera outra expansión.

- A orde das expansións son: expansión de chaves, expansión de tilde, expansión de parámetros e variables, expansión aritmética e substitución de comandos (realizada de esquerda a dereita); división de palabras; e expansión de nomes de ficheiros. (Por exemplo, un intervalo como `{1..20}` non se pode expresar con variábeis usando `{$a..$b}`. En vez diso, usa `seq` ou un bucle `for`, por exemplo, `seq $a $b` ou `for((i=a; i<=b; i++)); do ... ; done`.)

- A saída dun comando pódese tratar como un ficheiro mediante `<(some command)` (coñecido como substitución de proceso). Por exemplo, compara o `/etc/hosts` local cun de xeito remoto:
  ```sh
  diff /etc/hosts <(ssh somehost cat /etc/hosts)
  ```

- Ao escribir scripts, pode que queiras poñer todo o teu código entre chaves curvas. Se falta a chave de peche, impedirase que o teu script se execute debido a un erro de sintaxe. Isto ten sentido cando o teu script vai descargarse da web, xa que impide que os scripts descargados parcialmente se executen:
  ```bash
  {
     # o teu código aquí
  }
  ```

- Un "here document" permite [redirección de varias liñas de entrada](https://www.tldp.org/LDP/abs/html/here-docs.html) como se fose dun ficheiro:
  ```
  cat <<EOF
  input
  on multiple lines
  EOF
  ```

- En Bash, redirixir tanto a saída estándar como o erro estándar mediante: `some-command >logfile 2>&1` ou `some-command &>logfile`. Moitas veces, para garantir que un comando non deixe un manexo de ficheiro aberto para a entrada estándar, vinculándoo á terminal na que te atopas, tamén é boa práctica engadir `</dev/null`.

- Emprega `man ascii` para unha boa táboa ASCII, con valores hexadecimais e decimais. Para información xeral sobre codificación, os manuais `man unicode`, `man utf-8` e `man latin1` son útiles.

- Emprega `screen` ou [`tmux`](https://tmux.github.io/) para multiplexar a pantalla, especialmente útil en sesións SSH remotas e para desapegar e reapegar unha sesión. `byobu` pode mellorar screen ou tmux ao proporcionar máis información e unha xestión máis sinxela. Unha alternativa máis minimalista só para a persistencia de sesións é `dtach` (https://github.com/bogner/dtach).

- En SSH, saber como facer túneles de porto con `-L` ou `-D` (e ocasionalmente `-R`) é útil, por exemplo para acceder a sitios web desde un servidor remoto.

- Pode ser útil facer algunhas optimizacións na túa configuración de ssh; por exemplo, este `~/.ssh/config` contén axustes para evitar perdas de conexión en determinados contornos de rede, emprega compresión (o que é útil co scp en conexións de baixa ancho de banda) e multiplexa canles ao mesmo servidor cun ficheiro de control local:
  ```
  TCPKeepAlive=yes
  ServerAliveInterval=15
  ServerAliveCountMax=6
  Compression=yes
  ControlMaster auto
  ControlPath /tmp/%r@%h:%p
  ControlPersist yes
  ```

- Algunhas outras opcións relevantes para ssh son sensibles á seguridade e deben habilitarse con coidado, por exemplo por subrede ou por host ou en redes de confianza:
 `StrictHostKeyChecking=no`, `ForwardAgent=yes`

- Considera [`mosh`](https://mosh.org/) como unha alternativa a ssh que usa UDP, evitando conexións perdidas e engadindo comodidade cando viaxas (requer configuración no lado do servidor).

- Para obter os permisos dun ficheiro en forma octal, que é útil para a configuración do sistema pero non está dispoñible en `ls` e é fácil de estropear, usa algo como
  ```sh
  stat -c '%A %a %n' /etc/timezone
  ```

- Para a selección interactiva de valores desde a saída doutra orde, usa [`percol`](https://github.com/mooz/percol) ou [`fzf`](https://github.com/junegunn/fzf).

- Para a interacción con ficheiros baseados no resultado dunha orde diferente (como `git`), usa `fpp` ([PathPicker](https://github.com/facebook/PathPicker)).

- Para un sinxelo servidor web para todos os ficheiros do directorio actual (e subdirectorios), dispoñible para calquera na túa rede, usa: 
`python -m SimpleHTTPServer 7777` (para o porto 7777 e Python 2) e `python -m http.server 7777` (para o porto 7777 e Python 3).

- Para executar un comando como outro usuario, usa `sudo`. Por defecto executase como root; usa `-u` para especificar outro usuario. Usa `-i` para iniciar sesión como ese usuario (pediranche a _túa_ contrasinal).

- Para cambiar de usuario na shell, usa `su username` ou `su - username`. Este último, co "-", obtén un contorno como se outro usuario acabase de iniciar sesión. Se omites o nome de usuario, asumes a conta root. Preguntarache a contrasinal do usuario ao que vas cambiar.

- Coñece o [límite de 128K](https://wiki.debian.org/CommonErrorMessages/ArgumentListTooLong) nas liñas de comandos. Este erro "Argument list too long" é común ao usar comodíns para coincidir con un gran número de ficheiros. (Cando isto sucede, alternativas como `find` e `xargs` poden axudar.)

- Para unha calculadora básica (e, por suposto, acceso a Python en xeral), usa o intérprete `python`. Por exemplo:

  ```
  >>> 2+3
  5
  ```


## Procesando arquivos e datos

- Para localizar un ficheiro polo seu nome no directorio actual, `find . -iname '*something*'` (ou similar). Para atopar un ficheiro en calquera lugar polo seu nome, usa `locate something` (pero ten en conta que `updatedb` pode non ter indexados os ficheiros creados recentemente).

- Para buscas xerais en arquivos de código fonte ou de datos, hai varias opcións máis avanzadas ou rápidas que `grep -r`, incluíndo (nunha orde aproximada de máis vellas a máis novas) [`ack`](https://github.com/beyondgrep/ack2), [`ag`](https://github.com/ggreer/the_silver_searcher) ("o buscador de prata"), e [`rg`](https://github.com/BurntSushi/ripgrep) (`ripgrep`).

- Para converter HTML a texto: `lynx -dump -stdin`

- Para Markdown, HTML e todo tipo de conversión de documentos, proba [`pandoc`](http://pandoc.org/). Por exemplo, para converter un documento Markdown ao formato Word: `pandoc README.md --from markdown --to docx -o temp.docx`

- Se tes que manexar XML, `xmlstarlet` é antigo pero bo.

- Para JSON, usa [`jq`](http://stedolan.github.io/jq/). Para uso interactivo, tamén consulta [`jid`](https://github.com/simeji/jid) e [`jiq`](https://github.com/fiatjaf/jiq).

- Para YAML, usa [`shyaml`](https://github.com/0k/shyaml).

- Para Excel ou arquivos CSV, [csvkit](https://github.com/onyxfish/csvkit) proporciona `in2csv`, `csvcut`, `csvjoin`, `csvgrep`, etc.

- Para Amazon S3, [`s3cmd`](https://github.com/s3tools/s3cmd) é conveniente e [`s4cmd`](https://github.com/bloomreach/s4cmd) é máis rápido. O [`aws`](https://github.com/aws/aws-cli) de Amazon e o mellorado [`saws`](https://github.com/donnemartin/saws) son esenciais para tarefas relacionadas con AWS.

- Coñece `sort` e `uniq`, incluíndo as opcións `-u` e `-d` de uniq -- véxanse os comandos dunha liña máis abaixo. Vexa tamén `comm`.

- Coñece `cut`, `paste` e `join` para manipular ficheiros de texto. Moita xente usa `cut` pero esquece `join`.

- Coñece `wc` para contar saltos de liña (`-l`), caracteres (`-m`), palabras (`-w`) e bytes (`-c`).

- Coñece `tee` para copiar de stdin a un ficheiro e tamén a stdout, como en `ls -al | tee file.txt`.

- Para cálculos máis complexos, incluíndo agrupamentos, inversión de campos e cálculos estatísticos, considera [`datamash`](https://www.gnu.org/software/datamash/).

- Sabe que a localización afecta moitas ferramentas da liña de comandos de xeitos sutís, incluíndo a orde de ordenación (collation) e o rendemento. A maioría das instalacións de Linux establecerán `LANG` ou outras variables de contorno a un axuste local como o inglés dos EUA. Pero teña en conta que a ordenación cambiará se cambia o contorno. E saiba que as rutinas i18n poden facer que sort ou outros comandos funcionen moitas veces máis lentos. En algunhas situacións (como as operacións de conxunto ou as operacións de unicidade que se describen a continuación) pode ignorar con seguridade as rutinas i18n lentas por completo e usar o tradicional orde de ordenación baseado en bytes, empregando `export LC_ALL=C`.

- Podes configurar o contorno dun comando específico engadindo como prefixo á súa invocación as configuracións da variable de contorno, como en `TZ=Pacific/Fiji date`.

- Coñece o básico de `awk` e `sed` para a manipulación sinxela de datos. Consulta [Liñas únicas](#one-liners) para exemplos.

- Para substituír todas as ocorrencias dunha cadea no mesmo lugar, nun ou máis ficheiros:
  ```sh
  perl -pi.bak -e 's/old-string/new-string/g' my-files-*.txt
  ```

- Para renomear varios ficheiros e/ou buscar e substituír dentro dos ficheiros, proba [`repren`](https://github.com/jlevy/repren). (En algúns casos, o comando `rename` tamén permite renomear varios ficheiros á vez, pero ten coidado, xa que a súa funcionalidade non é a mesma en todas as distribucións de Linux.)
  ```sh
  # Renome completo de nomes de ficheiros, directorios e contidos foo -> bar:
  repren --full --preserve-case --from foo --to bar .
  # Recuperar ficheiros de copia de seguridade .whatever.bak -> .whatever:
  repren --renames --from '(.*)\.bak' --to '\1' *.bak
  # O mesmo que arriba, usando rename, se está dispoñible:
  rename 's/\.bak$//' *.bak
  ```

- Como di a páxina do manual, `rsync` é realmente unha ferramenta de copia de ficheiros rápida e extraordinariamente versátil. É coñecida por sincronizar entre máquinas, pero tamén é igualmente útil localmente. Cando as restricións de seguridade o permiten, usar `rsync` en lugar de `scp` permite recuperar unha transferencia sen ter que comezar de novo desde cero. Tamén é unha das [formas máis rápidas](https://web.archive.org/web/20130929001850/http://linuxnote.net/jianingy/en/linux/a-fast-way-to-remove-huge-number-of-files.html) para eliminar un gran número de ficheiros:
  ```sh
  mkdir empty && rsync -r --delete empty/ some-dir && rmdir some-dir
  ```

- Para monitorizar o progreso ao procesar ficheiros, usa [`pv`](http://www.ivarch.com/programs/pv.shtml), [`pycp`](https://github.com/dmerejkowsky/pycp), [`pmonitor`](https://github.com/dspinellis/pmonitor), [`progress`](https://github.com/Xfennec/progress), `rsync --progress`, ou, para a copia a nivel de bloques, `dd status=progress`.

- Usa `shuf` para barallar ou seleccionar liñas aleatorias dun ficheiro.

- Coñece as opcións de `sort`. Para números, usa `-n`, ou `-h` para manexar números lexibles por humanos (por exemplo, de `du -h`). Coñece como funcionan as claves (`-t` e `-k`). En particular, ten coidado: necesitas escribir `-k1,1` para ordenar só polo primeiro campo; `-k1` significa ordenar segundo a liña enteira. A ordenación estable (`sort -s`) pode ser útil. Por exemplo, para ordenar primeiro polo campo 2 e, en segundo lugar, polo campo 1, podes usar `sort -k1,1 | sort -s -k2,2`.

- Se algunha vez necesitas escribir un literal de tab nunha liña de comandos en Bash (por exemplo, para o argumento -t de sort), preme **Ctrl+V** **[Tab]** ou escribe `$'\t'` (este último é mellor, xa que podes copialo e pegalo).

- As ferramentas estándar para aplicar parches ao código fonte son `diff` e `patch`. Consulta tamén `diffstat` para obter estatísticas resumidas dun diff e `sdiff` para un diff lado a lado. Ten en conta que `diff -r` funciona con directorios enteiros. Emprega `diff -r tree1 tree2 | diffstat` para obter un resumo das modificacións. Emprega `vimdiff` para comparar e editar ficheiros.

- Para ficheiros binarios, usa `hd`, `hexdump` ou `xxd` para volcados hexadecimais sinxelos e `bvi`, `hexedit` ou `biew` para edición binaria.

- Tamén para ficheiros binarios, `strings` (xunto con `grep`, etc.) permíteche atopar fragmentos de texto.

- Para diferenzas binarias (compresión delta), usa `xdelta3`.

- Para converter codificacións de texto, proba `iconv`. Ou `uconv` para un uso máis avanzado; admite algunhas características avanzadas de Unicode. Por exemplo:
  ```sh
  # Amosa os códigos hexadecimais ou os nomes reais dos caracteres (útil para a depuración):
  uconv -f utf-8 -t utf-8 -x '::Any-Hex;' < input.txt
  uconv -f utf-8 -t utf-8 -x '::Any-Name;' < input.txt
  # Minúsculas e elimina todos os acentos (expandíndoos e descartándoos):
  uconv -f utf-8 -t utf-8 -x '::Any-Lower; ::Any-NFD; [:Nonspacing Mark:] >; ::Any-NFC;' < input.txt > output.txt
  ```

- Para dividir ficheiros en anacos, véxase `split` (para dividir por tamaño) e `csplit` (para dividir por un patrón).

- Data e hora: Para obter a data e a hora actuais no formato útil [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601), usa `date -u +"%Y-%m-%dT%H:%M:%SZ"` (outras opcións [son](https://stackoverflow.com/questions/7216358/date-command-on-os-x-doesnt-have-iso-8601-i-option) [problemáticas](https://unix.stackexchange.com/questions/164826/date-command-iso-8601-option)). Para manipular expresións de data e hora, usa `dateadd`, `datediff`, `strptime` etc. de [`dateutils`](http://www.fresse.org/dateutils/).

- Usa `zless`, `zmore`, `zcat`, e `zgrep` para operar con ficheiros comprimidos.

- Os atributos de ficheiro pódense configurar mediante `chattr` e ofrecen unha alternativa de nivel máis baixo aos permisos de ficheiro. Por exemplo, para protexer contra a eliminación accidental de ficheiros, a bandeira inmutable: `sudo chattr +i /critical/directory/or/file`

- Usa `getfacl` e `setfacl` para gardar e restaurar os permisos de ficheiro. Por exemplo:
  ```sh
  getfacl -R /some/path > permissions.txt
  setfacl --restore=permissions.txt
  ```

- Para crear ficheiros baleiros rapidamente, usa `truncate` (para crear [ficheiro espallado](https://en.wikipedia.org/wiki/Sparse_file)), `fallocate` (sistemas de ficheiros ext4, xfs, btrfs e ocfs2), `xfs_mkfile` (case calquera sistema de ficheiros, inclúese no paquete `xfsprogs`), `mkfile` (para sistemas semellantes a Unix como Solaris, Mac OS).
  

## Depuración do sistema

- Para a depuración web, `curl` e `curl -I` son útiles, ou os seus equivalentes en `wget`, ou o máis moderno [`httpie`](https://github.com/jkbrzt/httpie).

- Para coñecer o estado actual da CPU e do disco, as ferramentas clásicas son `top` (ou o mellor `htop`), `iostat` e `iotop`. Emprega `iostat -mxz 15` para obter estatísticas básicas da CPU e información detallada do disco por partición e do seu rendemento.

- Para obter detalles da conexión de rede, usa `netstat` e `ss`.

- Para unha visión rápida do que está a suceder nun sistema, `dstat` é especialmente útil. Para a visión máis ampla con detalles, usa [`glances`](https://github.com/nicolargo/glances).

- Para coñecer o estado da memoria, executa e comprende a saída de `free` e `vmstat`. En particular, ten en conta que o valor "cached" corresponde á memoria mantida polo núcleo de Linux como caché de ficheiros, polo que efectivamente conta para o valor "free".

- A depuración do sistema Java é outra historia, pero un truco sinxelo en Oracle e nalgúns outros JVMs é que podes executar `kill -3 <pid>` e un rastrexamento completo da pila e un resumo do heap (incluíndo detalles da recollida de lixo xeracional, que poden ser moi informativos) serán escritos en stderr/logs. As ferramentas `jps`, `jstat`, `jstack` e `jmap` do JDK son útiles. [Ferramentas SJK](https://github.com/aragozin/jvm-tools) son máis avanzadas.

- Usa [`mtr`](http://www.bitwizard.nl/mtr/) como un mellor *traceroute*, para identificar problemas de rede.

- Para ver por que un disco está cheo, [`ncdu`](https://dev.yorhel.nl/ncdu) aforra tempo fronte aos comandos habituais como `du -sh *`.

- Para descubrir que socket ou proceso está a usar ancho de banda, proba [`iftop`](http://www.ex-parrot.com/~pdw/iftop/) ou [`nethogs`](https://github.com/raboof/nethogs).

- A ferramenta `ab` (incluída en Apache) é útil para comprobar de xeito rápido e sinxelo o rendemento do servidor web. Para probas de carga máis complexas, proba `siege`.

- Para depuración de rede máis seria, [`wireshark`](https://wireshark.org/), [`tshark`](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html), ou [`ngrep`](http://ngrep.sourceforge.net/).

- Coñece `strace` e `ltrace`. Poden ser útiles se un programa falla, se bloquea ou se bloquea e non sabes por que, ou se queres obter unha idea xeral do rendemento. Ten en conta a opción de profiling (`-c`) e a posibilidade de anexarte a un proceso en execución (`-p`). Emprega a opción de rastrear fillos (`-f`) para non perder chamadas importantes.

- Coñece `ldd` para comprobar bibliotecas compartidas, etc. — pero [nunca o executes en ficheiros non fiables](http://www.catonmat.net/blog/ldd-arbitrary-code-execution/).

- Saber como conectarse a un proceso en execución con `gdb` e obter as súas trazas de pila.

- Emprega `/proc`. Ás veces é sorprendentemente útil ao depurar problemas en tempo real. Exemplos: `/proc/cpuinfo`, `/proc/meminfo`, `/proc/cmdline`, `/proc/xxx/cwd`, `/proc/xxx/exe`, `/proc/xxx/fd/`, `/proc/xxx/smaps` (onde `xxx` é o ID de proceso ou PID).

- Ao depurar por que algo saíu mal no pasado, [`sar`](http://sebastien.godard.pagesperso-orange.fr/) pode ser moi útil. Mostrar estatísticas históricas de CPU, memoria, rede, etc.

- Para análises máis profundas dos sistemas e do rendemento, consulta `stap` ([SystemTap](https://sourceware.org/systemtap/wiki)), [`perf`](https://en.wikipedia.org/wiki/Perf_%28Linux%29), e [`sysdig`](https://github.com/draios/sysdig).

- Comproba en que sistema operativo estás con `uname` ou `uname -a` (información xeral de Unix/núcleo) ou con `lsb_release -a` (información da distribución Linux).
  
- Emprega `dmesg` sempre que algo se comporte de xeito moi estraño (pode ser un problema de hardware ou de controladores).

- Se eliminas un ficheiro e non libera o espazo en disco esperado segundo informa `du`, comproba se o ficheiro está en uso por un proceso:
`lsof | grep deleted | grep "filename-of-my-big-file"`


## Liñas únicas

Algúns exemplos de combinar comandos:

- Ás veces é notablemente útil que poidas facer a intersección, a unión e a diferenza de ficheiros de texto mediante `sort`/`uniq`. Supoñamos que `a` e `b` son ficheiros de texto que xa foron filtrados con `uniq`. Isto é rápido e funciona con ficheiros de tamaño arbitrario, de ata varios gigabytes. (`sort` non está limitado pola memoria, aínda que pode que necesites usar a opción `-T` se `/tmp` está nunha partición raíz pequena.) Vese tamén a nota sobre `LC_ALL` máis arriba e a opción `-u` de `sort` (eliminada para maior claridade a continuación).
  ```sh
  sort a b | uniq > c   # c is a union b
  sort a b | uniq -d > c   # c is a intersect b
  sort a b b | uniq -u > c   # c is set difference a - b
  ```

- Formata de xeito atractivo dous ficheiros JSON, normalizando a súa sintaxe, e logo colorea e pagina o resultado:

  ```bash
  diff <(jq --sort-keys . < file1.json) <(jq --sort-keys . < file2.json) | colordiff | less -R
  ```

- Emprega `grep . *` para examinar rapidamente o contido de todos os ficheiros nun directorio (de xeito que cada liña estea emparellada co nome do ficheiro), ou `head -100 *` (para que cada ficheiro teña un encabezado). Isto pode ser útil en directorios cheos de axustes de configuración, como `/sys`, `/proc` e `/etc`.

- Suma todos os números na terceira columna dun ficheiro de texto (isto é probablemente 3X máis rápido e 3X menos código que o Python equivalente):
  ```sh
  awk '{ x += $3 } END { print x }' myfile
  ```

- Para ver os tamaños/datas nunha árbore de ficheiros, isto é como un `ls -l` recursivo pero máis doado de ler que `ls -lR`:
  ```sh
  find . -type f -ls
  ```

- Imaxina que tes un ficheiro de texto, como un rexistro dun servidor web, e un determinado valor que aparece en algunhas liñas, como o parámetro `acct_id` presente na URL. Se queres un reconto de cantas solicitudes hai para cada `acct_id`:
  ```sh
  egrep -o 'acct_id=[0-9]+' access.log | cut -d= -f2 | sort | uniq -c | sort -rn
  ```

- Para monitorizar continuamente os cambios, usa `watch`, por exemplo, para comprobar as modificacións nos ficheiros dun directorio con `watch -d -n 2 'ls -rtlh | tail'` ou para supervisar a configuración de rede mentres solucionas os problemas do teu wifi con `watch -d -n 2 ifconfig`.

- Executa esta función para obter unha anotación aleatoria deste documento (analiza Markdown e extrae un elemento):
  ```sh
  function taocl() {
      curl -s https://raw.githubusercontent.com/jlevy/the-art-of-command-line/master/README.md |
      sed '/cowsay[.]png/d' |
      pandoc -f markdown -t html |
      xmlstarlet fo --html --dropdtd |
       xmlstarlet sel -t -v "(html/body/ul/li[count(p)>0])[$RANDOM mod last()+1]" |
      xmlstarlet unesc | fmt -80 | iconv -t US
  }
  ```


## Escuro pero útil

- `expr`: realizar operacións aritméticas ou lóxicas ou avaliar expresións regulares

- `m4`: procesador de macros sinxelo

- `yes`: imprimir unha cadea moitas veces

- `cal`: bonito calendario

- `env`: executa un comando (útil en scripts)

- `printenv`: Imprimir variables da contorna (útil para a depuración e scripts)

- `look`: atopa palabras en inglés (ou liñas nun ficheiro) que comezan cunha cadea

- `cut`, `paste` e `join`: manipulación de datos

- `fmt`: formato de parágrafos de texto

- `pr`: Formatear texto en páxinas/columnas

- `fold`: colapsar liñas de texto

- `column`: formatear campos de texto en columnas aliñadas de anchura fixa ou en táboas

- `expand` e `unexpand`: converter entre tabulacións e espazos

- `nl`: engadir números de liña

- `seq`: imprimir números

- `bc`: calculadora

- `factor`: factorizar enteiros

- [`gpg`](https://gnupg.org/): encriptar e asinar ficheiros

- `toe`: táboa de entradas de terminfo

- `nc`: depuración de redes e transferencia de datos

- `socat`: relevo de sockets e reenviador de portos TCP (semellante a `netcat`)

- [`slurm`](https://github.com/mattthias/slurm): visualización do tráfico de rede

- `dd`: mover datos entre ficheiros ou dispositivos

- `file`: identificar o tipo dun ficheiro

- `tree`: mostrar directorios e subdirectorios como unha árbore aniñada; coma `ls` pero recursivo

- `stat`: información do ficheiro

- `time`: executar e cronometrar un comando

- `timeout`: executar un comando durante un tempo especificado e deter o proceso cando remate ese tempo

- `lockfile`: crear un ficheiro semáforo que só se poida eliminar con `rm -f`

- `logrotate`: rotar, comprimir e enviar rexistros por correo electrónico.

- `watch`: executar un comando repetidamente, amosando resultados e/ou destacando cambios

- [`when-changed`](https://github.com/joh/when-changed): Executa calquera comando que especifiques sempre que detecte que un ficheiro cambiou. Consulta tamén `inotifywait` e `entr`.

- `tac`: imprimir ficheiros en sentido inverso

- `comm`: comparar ficheiros ordenados liña a liña

- `strings`: extraer texto de arquivos binarios

- `tr`: tradución ou manipulación do carácter

- `iconv` ou `uconv`: conversión para codificacións de texto

- `split` e `csplit`: dividindo ficheiros

- `sponge`: le todo o input antes de escribilo, útil para ler e despois escribir no mesmo ficheiro, por exemplo, `grep -v something some-file | sponge some-file`

- `units`: conversións de unidades e cálculos; converte furlongs por quincena a twips por parpadeo (ver tamén `/usr/share/units/definitions.units`)

- `apg`: xera contrasinais aleatorios

- `xz`: compresión de ficheiros de alta relación
  
- `ldd`: información da biblioteca dinámica
  
- `nm`: símbolos de arquivos de obxecto

- `ab` ou [`wrk`](https://github.com/wg/wrk): medición comparativa de servidores web

- `strace`: depuración de chamadas ao sistema

- [`mtr`](http://www.bitwizard.nl/mtr/): mellor *traceroute* para a depuración de redes

- `cssh`: shell visual concorrente

- `rsync`: sincronizar ficheiros e cartafoles por SSH ou no sistema de ficheiros local

- [`wireshark`](https://wireshark.org/) e [`tshark`](https://www.wireshark.org/docs/wsug_html_chunked/AppToolstshark.html): captura de paquetes e depuración de redes

- [`ngrep`](http://ngrep.sourceforge.net/): *grep* para a capa de rede

- `host` e `dig`: buscas DNS

- `lsof`: procesar o descriptor de ficheiro e a información do socket

- `dstat`: estatísticas útiles do sistema

- [`glances`](https://github.com/nicolargo/glances): visión xeral de alto nivel de múltiples subsistemas

- `iostat`: estatísticas de uso do disco

- `mpstat`: estatísticas de uso da CPU

- `vmstat`: estatísticas de uso da memoria

- `htop`: versión mellorada do top

- `last`: historial de inicio de sesión

- `w`: quen está conectado

- `id`: información de identidade de usuario/grupo

- [`sar`](http://sebastien.godard.pagesperso-orange.fr/): estatísticas históricas do sistema

- [`iftop`](http://www.ex-parrot.com/~pdw/iftop/) ou [`nethogs`](https://github.com/raboof/nethogs): uso da rede por socket ou proceso

- `ss`: estatísticas de sockets

- `dmesg`: mensaxes de erro de arranque e do sistema

- `sysctl`: ver e configurar parámetros do núcleo de Linux en tempo de execución

- `hdparm`: manipulación/rendemento de discos SATA/ATA

- `lsblk`: listar dispositivos de bloque: unha vista en árbore dos teus discos e particións de disco

- `lshw`, `lscpu`, `lspci`, `lsusb`, `dmidecode`: información do hardware, incluíndo CPU, BIOS, RAID, gráficos, dispositivos, etc.

- `lsmod` e `modinfo`: lista e amosa os detalles dos módulos do kernel.

- `fortune`, `ddate`, e `sl`: ehm, ben, depende de se consideras as locomotoras de vapor e as citas de Zippy "útiles"


## Só para macOS

Estes son elementos relevantes *só* en macOS.

- Xestión de paquetes con `brew` (Homebrew) e/ou `port` (MacPorts). Estes poden usarse para instalar en macOS moitos dos comandos anteriores.

- Copia a saída de calquera comando nunha aplicación de escritorio con `pbcopy` e pega a entrada doutra con `pbpaste`.

- Para habilitar a tecla Option no Terminal de macOS como tecla Meta (como se usa nos comandos anteriores, como **alt-b**, **alt-f**, etc.), abre Preferencias -> Perfiles -> Teclado e selecciona "Usar Option como tecla Meta".

- Para abrir un ficheiro cunha aplicación de escritorio, usa `open` ou `open -a /Applications/Whatever.app`.
  
- En foco: busca ficheiros con `mdfind` e lista metadatos (como a información EXIF das fotos) con `mdls`.

- Teña en conta que macOS está baseado en BSD Unix, e moitos comandos (por exemplo `ps`, `ls`, `tail`, `awk`, `sed`) teñen moitas variacións sutís respecto de Linux, que está en gran medida influído polo estilo de Unix System V e polas ferramentas de GNU. Moitas veces podes distinguir a diferenza ao notar que unha páxina man ten o encabezado "BSD General Commands Manual". En algúns casos tamén se poden instalar versións de GNU (como `gawk` e `gsed` para GNU awk e sed). Se escribes scripts de Bash multiplataforma, evita estes comandos (por exemplo, considera Python ou `perl`) ou proba con coidado.

- Para obter a información de versión de macOS, usa `sw_vers`.

## Só para Windows

Estes elementos son relevantes *só* en Windows.

### Formas de obter ferramentas Unix baixo Windows

- Acceda ao poder do shell de Unix en Microsoft Windows instalando [Cygwin](https://cygwin.com/). A maioría das cousas descritas neste documento funcionarán de serie.

- En Windows 10, podes usar o [Subsistema de Windows para Linux (WSL)](https://msdn.microsoft.com/commandline/wsl/about), que proporciona un contorno Bash familiar con utilidades da liña de comandos de Unix.

- Se principalmente queres usar as ferramentas de desenvolvemento de GNU (como GCC) en Windows, considera [MinGW](http://www.mingw.org/) e o seu paquete [MSYS](http://www.mingw.org/wiki/msys), que proporciona utilidades como bash, gawk, make e grep. MSYS non ten todas as funcións en comparación con Cygwin. MinGW é particularmente útil para crear portos nativos de Windows de ferramentas de Unix.

- Outra opción para conseguir o aspecto e a sensación de Unix en Windows é [Cash](https://github.com/dthree/cash). Teña en conta que só están dispoñibles moi poucos comandos e opcións de liña de comandos de Unix neste contorno.

### Ferramentas útiles da liña de comandos de Windows

- Pode realizar e gravar en scripts a maioría das tarefas de administración do sistema de Windows desde a liña de comandos aprendendo a usar `wmic`.

- As ferramentas nativas de liña de comandos de Windows para redes que podes atopar útiles inclúen `ping`, `ipconfig`, `tracert` e `netstat`.

- Podes realizar [moitas tarefas útiles de Windows](http://www.thewindowsclub.com/rundll32-shortcut-commands-windows) invocando o comando `Rundll32`.

### Consellos e trucos de Cygwin

- Instala programas Unix adicionais co xestor de paquetes de Cygwin.

- Usa `mintty` como a túa xanela de liña de comandos.

- Accede ao portapapeis de Windows a través de `/dev/clipboard`.

- Executa `cygstart` para abrir un ficheiro arbitrario a través da túa aplicación rexistrada.

- Accede ao rexistro de Windows con `regtool`.

- Ter en conta que unha ruta de unidade de Windows `C:\` convértese en `/cygdrive/c` en Cygwin, e que o `/` de Cygwin aparece como `C:\cygwin` en Windows. Convirte entre rutas de ficheiros de estilo Cygwin e Windows con `cygpath`. Isto é máis útil en scripts que invocan programas de Windows.
  
## Máis recursos

- [awesome-shell](https://github.com/alebcay/awesome-shell): unha lista coidadosamente seleccionada de ferramentas e recursos de shell.
- [awesome-osx-command-line](https://github.com/herrbischoff/awesome-osx-command-line): unha guía detallada para a liña de comandos de macOS.
- [Strict mode](http://redsymbol.net/articles/unofficial-bash-strict-mode/) para escribir mellores scripts de shell.
- [shellcheck](https://github.com/koalaman/shellcheck): unha ferramenta de análise estática de scripts de shell. Esencialmente, lint para bash/sh/zsh.
- [Filenames and Pathnames in Shell](http://www.dwheeler.com/essays/filenames-in-shell.html): As minucias tristemente complexas sobre como manexar correctamente os nomes de ficheiro nos scripts de shell.
- [Data Science at the Command Line](http://datascienceatthecommandline.com/#tools): Máis comandos e ferramentas útiles para a ciencia de datos, do libro do mesmo nome

## Aviso legal

Agás en tarefas moi pequenas, o código escríbese para que outros poidan lelo. Co poder ven a responsabilidade. O feito de que poidas facer algo en Bash non significa necesariamente que debas facelo! ;)


## Licenza

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)

Esta obra está licenciada baixo a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).
