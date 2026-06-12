---
title: "ttaenc true audio codec install puzzle"
date: 2010-01-10
forum: Multimedia Software
---

### Post by shantiq on 2010-01-10
[B][COLOR=Navy]well i am on ubuntu karmic koala and i have been trying to install true audio codec ttaenc

the file we have is[   ttaenc-3.4.1-src]("http://sourceforge.net/projects/tta/files/tta/ttaenc-src/ttaenc-3.4.1-src.tgz/download")   this came directly from aleksandr djuric who looks after true audio



now he tells me to use    ```
Compilation and installing
(your work dir) - the path where you have unpacked the codec sources

$ su -
# cd /(your work dir)/ttaenc-3.4.1-src
# make; make install

```to install it     so i modified that for ubuntu and this is what i got[/COLOR][/B]  


```
shantiq@shantiq-desktop:~$ cd ./ttaenc-3.4.1-src
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ make
make: `ttaenc' is up to date.
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ make install
[ -d "/usr/bin" ] || mkdir /usr/bin
if [ -n "ttaenc" ]; then \
        strip ttaenc ; \
        install -m 755 ttaenc /usr/bin ; \
    fi
install: cannot remove `/usr/bin/ttaenc': Permission denied
make: *** [install] Error 1
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ sudo make install
[ -d "/usr/bin" ] || mkdir /usr/bin
if [ -n "ttaenc" ]; then \
        strip ttaenc ; \
        install -m 755 ttaenc /usr/bin ; \
    fi
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ 


```[COLOR=Navy][B]

any ideas as to how to progress from there?


will also post in multimedia as i am not sure whether this is general help or multimedia specific


thanx in advance for all useful help[/B][/COLOR]

---

### Post by shantiq on 2010-01-10
[B][COLOR=Blue]sorry guys all sorted   i reran ttaenc in the terminal and got this[/COLOR]

[/B]```
shantiq@shantiq-desktop:~$ cd ./ttaenc-3.4.1-src
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ make
make: `ttaenc' is up to date.
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ make install
[ -d "/usr/bin" ] || mkdir /usr/bin
if [ -n "ttaenc" ]; then \
        strip ttaenc ; \
        install -m 755 ttaenc /usr/bin ; \
    fi
install: cannot remove `/usr/bin/ttaenc': Permission denied
make: *** [install] Error 1
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ sudo make install
[ -d "/usr/bin" ] || mkdir /usr/bin
if [ -n "ttaenc" ]; then \
        strip ttaenc ; \
        install -m 755 ttaenc /usr/bin ; \
    fi
shantiq@shantiq-desktop:~/ttaenc-3.4.1-src$ cd ../
shantiq@shantiq-desktop:~$ ttaenc
TTA1 lossless audio encoder/decoder, release 3.4.1
Copyright (c) 2007 Aleksander Djuric. All rights reserved.
For more information see http://tta.sourceforge.net
------------------------------------------------------------
usage:    ttaenc [command] [options] file(s).. <output path/>

------------------------------------------------------------
commands:
------------------------------------------------------------
    -e    encode file(s)
    -d    decode file(s)
    -t    test file(s)
    -o name    specify output file name
    -v    show codec version
    -h    this help
------------------------------------------------------------
options:
------------------------------------------------------------
    -x    wave-extensible output file format
    -u    delete source file if successful
------------------------------------------------------------
when file is '-', use standard input/output.

shantiq@shantiq-desktop:~$ cd ./shakira
bash: cd: ./shakira: No such file or directory
shantiq@shantiq-desktop:~$ cd /home/shantiq/Music
shantiq@shantiq-desktop:~/Music$ cd ./shakira
shantiq@shantiq-desktop:~/Music/shakira$ pacpl -t tta  a.shn
Perl Audio Converter - 4.0.5

Converting:  [a.shn] -> [tta] ..done. 

Total files converted: 1, failed: 0
shantiq@shantiq-desktop:~/Music/shakira$ 



```
[COLOR=Navy]**so all good this may help someone else sometime i hope    shan**[/COLOR];););););)

---

