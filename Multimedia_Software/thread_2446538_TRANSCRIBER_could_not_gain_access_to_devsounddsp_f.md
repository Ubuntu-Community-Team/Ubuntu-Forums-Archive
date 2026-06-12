---
title: "TRANSCRIBER: could not gain access to /dev/sound/dsp for writing."
date: 2020-07-02
forum: Multimedia Software
---

### Post by monrijoe on 2020-07-02
Hello.

I am with unsolved problems in transcriber using latest version ubuntu 20.04 lts.

I checked the previous thread in this forums and all I tried doesn t work. Also, I am a basic user so you got to really explain things otherwise i won t  understand.

I  see transcriber has a problem because the icon image is not displayed properly in the left size bar as it should.

The same ogg file runs well in "rhythmbox and audacity

I used transcriber previously in other ubuntu version and it ran perfectly well.

Now, the only think that helps is "padsp transcriber" but after the program blocks and I have to kill it after using one file.

The original file was wma, i used "audacity" to convert into ogg and when opening file: 

Could not gain access to /dev/sound/dsp for writing.Could not gain access to /dev/sound/dsp for writing.
Could not gain access to /dev/sound/dsp for writing.Could not gain access to /dev/sound/dsp for writing.
while executing
"player play -start [expr int($begin*$rate)] -end [expr int($end*$rate)]"
(procedure "PlayRange" line 56)
invoked from within
"PlayRange $pos $end $script"
(procedure "Play" line 64)
invoked from within
"Play"
(procedure "PlayOrPause" line 10)
invoked from within
"PlayOrPause"
invoked from within
".cmd.play invoke"
("uplevel" body line 1)
invoked from within
"uplevel #0
[list $w invoke]"
(procedure "tk::ButtonUp" line 22)
invoked from within
"tk::ButtonUp .cmd.play"
(command bound to event)


PLEASE, HELP!

---

### Post by Holger_Gehrke on 2020-07-02
The [transcriber-project on sourceforge]("https://sourceforge.net/projects/trans/") has not had any changes since 2005. As matter of fact there is a [follow up project]("https://sourceforge.net/projects/transag/") (written in C using gtk 2 instead of TCL/TK) - TranscriberAG - which has not had any official updates since 2011 (though there is an [unofficial one on github]("https://github.com/eroux/transcriber-ag") from 2014). So I guess this is a dead end. Searching with apt for 'transcribe' (apt search transcribe) lists a package named gtranscribe and that -- while it looks simpler and less ambitious than transcriber -- seems to work and the author seems to still be active on that project.

If you still want to try to get transcriber to work, you could tell padsp to produce some debug-output by giving it the option '-d' (padsp -d transcriber) to see why it blocks after the first file. Or you could try to deactivate pulseaudio for the time you're running transcriber by trying 'pasuspend transcriber'. You might also want to create a link to /dev/dsp (which should exist on Linux systems using ALSA with OSS-compatibility) in /dev/sound (sudo mkdir /dev/sound; sudo ln /dev/dsp /dev/sound/dsp).

Holger

---

### Post by monrijoe on 2020-07-03
Hello,

That are sad news....

More sad news, now transcriber does run any more file.

Following your instructions:

```
 ubuntu@ubuntu-HP-260-G3-DM:~$ padsp -d transcriber
utils/padsp.c: mixer_open()
utils/padsp.c: fd_info_new()
utils/padsp.c: mixer_open() succeeded, fd=4
utils/padsp.c: dsp_open()
utils/padsp.c: fd_info_new()
utils/padsp.c: dsp_open() succeeded, fd=11
utils/padsp.c: freeing fd info (fd=11)
utils/padsp.c: Draining.
utils/padsp.c: dsp_open()
utils/padsp.c: fd_info_new()
utils/padsp.c: dsp_open() succeeded, fd=11
utils/padsp.c: SNDCTL_DSP_SETFMT: 16
utils/padsp.c: SNDCTL_DSP_CHANNELS: 1
utils/padsp.c: freeing fd info (fd=11)
utils/padsp.c: Draining.
utils/padsp.c: dsp_open()
utils/padsp.c: fd_info_new()
utils/padsp.c: dsp_open() succeeded, fd=11
utils/padsp.c: SNDCTL_DSP_SPEED: 8000
utils/padsp.c: ss: u8 1ch 8000Hz
utils/padsp.c: SNDCTL_DSP_SPEED: 11025
utils/padsp.c: ss: u8 1ch 11025Hz
utils/padsp.c: SNDCTL_DSP_SPEED: 16000
utils/padsp.c: ss: u8 1ch 16000Hz
utils/padsp.c: SNDCTL_DSP_SPEED: 22050
utils/padsp.c: ss: u8 1ch 22050Hz
utils/padsp.c: SNDCTL_DSP_SPEED: 32000
utils/padsp.c: ss: u8 1ch 32000Hz
utils/padsp.c: SNDCTL_DSP_SPEED: 44100
utils/padsp.c: ss: u8 1ch 44100Hz
utils/padsp.c: SNDCTL_DSP_SPEED: 48000
utils/padsp.c: ss: u8 1ch 48000Hz
utils/padsp.c: SNDCTL_DSP_SPEED: 96000
utils/padsp.c: ss: u8 1ch 96000Hz
utils/padsp.c: freeing fd info (fd=11)
utils/padsp.c: Draining.
^C
ubuntu@ubuntu-HP-260-G3-DM:~$ 

```

Secondly, ```
ubuntu@ubuntu-HP-260-G3-DM:~$ asuspend transcriber
asuspend: comando não encontrado
ubuntu@ubuntu-HP-260-G3-DM:~$ 

```

which means command was not found

The last instruction I will try tomorrow, now I am wasted and really down for knowing about its freezing...

Thank you anyway

See you tomorrow

---

### Post by wildmanne39 on 2020-07-03
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Yellow Pasque on 2020-07-04
Maybe you could install libsnack-alsa package?

---

### Post by Holger_Gehrke on 2020-07-05
> **monrijoe said:**
> 
...
```
 ubuntu@ubuntu-HP-260-G3-DM:~$ padsp -d transcriber
...
utils/padsp.c: freeing fd info (fd=11)
utils/padsp.c: Draining.
^C
ubuntu@ubuntu-HP-260-G3-DM:~$ 

```

That looks as if transcriber closes the file handle used for transmitting sound data after a file has been played and doesn't reopen it for a new one. Classic 'use after free' error.

> **monrijoe said:**
> 
Secondly, ```
ubuntu@ubuntu-HP-260-G3-DM:~$ asuspend transcriber
asuspend: comando não encontrado
ubuntu@ubuntu-HP-260-G3-DM:~$ 

```

which means command was not found
...


It's neither '**p**asuspend' (as I wrote) nor 'asuspend' (as you used) but 'pasuspend**er**'; sorry, my mistake (I usually just type "pasus<tabulator-key>' and let command line completion do the rest ...) . This command suspends Pulse Audio for the duration of the command given so programs that use Alsa or OSS directly can do so.

Holger

---

### Post by monrijoe on 2020-07-07
Hello friends!
I have great news. It works!!! Transcriber works!!!:guitar:
I just installed libsnack-alsa package, as Yellow Pasque told to do.
It came really on the right moment to do a project I had in hands during an extra overtime period!

In that case I am not going to try to do 'pasuspender' anymore, but I am grateful for all the suggestions.

Anyway here goes the command lines and the reading. It seems that a problem still lies under. 
Give it a check please, now with more time ahead.


> ubuntu@ubuntu-HP-260-G3-DM:~$ sudo apt-get update -y
[sudo] senha para ubuntu: 
Atingido:1 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) focal InRelease
Atingido:2 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) focal-updates InRelease
Atingido:3 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) focal-backports InRelease       
Obter:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [107 kB]    
Atingido:5 [http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu) focal InRelease
Obter:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [21,2 kB]
Obter:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [35,7 kB]
Obtidos 164 kB em 1s (129 kB/s)            
A ler as listas de pacotes... Pronto
ubuntu@ubuntu-HP-260-G3-DM:~$ sudo apt-get install -y libsnack-alsa
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
O seguinte pacote foi instalado automaticamente e já não é necessário:
  libllvm10
Utilize 'sudo apt autoremove' para o remover.
Serão REMOVIDOS os seguintes pacotes:
  libsnack-oss
Serão instalados os seguintes NOVOS pacotes:
  libsnack-alsa
0 pacotes actualizados, 1 pacotes novos instalados, 1 a remover e 69 não actualizados.
É necessário obter 175 kB de arquivos.
Após esta operação, será libertado 28,7 kB de espaço em disco.
Obter:1 [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) focal/universe amd64 libsnack-alsa amd64 2.2.10.20090623-dfsg-10 [175 kB]
Obtidos 175 kB em 0s (524 kB/s)      
dpkg: libsnack-oss: problemas com dependências, mas mesmo assim a remover conforme você pediu:
 tcl-snack depende de libsnack-oss (= 2.2.10.20090623-dfsg-10) | libsnack-alsa (= 2.2.10.20090623-dfsg-10); no entanto:
  O pacote libsnack-oss vai ser removido.
  O pacote libsnack-alsa não está instalado.

(A ler a base de dados ... 193407 ficheiros e directórios actualmente instalados.)
A remover libsnack-oss (2.2.10.20090623-dfsg-10) ...
A seleccionar pacote anteriormente não seleccionado libsnack-alsa.
(A ler a base de dados ... 193400 ficheiros e directórios actualmente instalados.)
A preparar para desempacotar .../libsnack-alsa_2.2.10.20090623-dfsg-10_amd64.deb ...
A descompactar libsnack-alsa (2.2.10.20090623-dfsg-10) ...
A instalar libsnack-alsa (2.2.10.20090623-dfsg-10) ...
libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...
ubuntu@ubuntu-HP-260-G3-DM:~$ 


Thank you all!

---

### Post by Yellow Pasque on 2020-07-07
```
sudo apt-get clean
sudo apt-get install --reinstall libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg
```

---

