---
title: "help with sound card drivers"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by paydaydaddy on 2007-02-15
I am a noob and need some help installing sound card drivers. I tried following the instructions in the comprehensive sound sticky and at the alsa website. I could locate the drivers, but following the instructions just gets me the "no such command" response. Anybody here willing to help a noob get this figured out? Dapper Drake. Avance als4000 sound card. [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) . I tried posting this in the beginner section and got no response.

---

### Post by renzokuken on 2007-02-15
which commands in particular give the "no such command" output?

---

### Post by paydaydaddy on 2007-02-15
From alsa site:
{Quick Install

NB. If you are using cvs then you need to type

         ./cvscompile "or" make build

instead of

         ./configure

In a shell type these commands:

Make a directory to store the alsa source code in.

        cd /usr/src
        mkdir alsa
        cd alsa
        cp /downloads/alsa-* .}

From terminal:
{diamond@diamond:~$ ./configure         cd /usr/src
bash: ./configure: No such file or directory
diamond@diamond:~$         mkdir alsa
diamond@diamond:~$         cd alsa
diamond@diamond:~/alsa$         cp /downloads/alsa-* .
cp: cannot stat `/downloads/alsa-*': No such file or directory
diamond@diamond:~/alsa$ bunzip2 alsa-driver-xxx
bunzip2: Can't open input file alsa-driver-xxx: No such file or directory.
diamond@diamond:~/alsa$         tar -xf alsa-driver-xxx
tar: alsa-driver-xxx: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
diamond@diamond:~/alsa$         cd alsa-driver-xxx
bash: cd: alsa-driver-xxx: No such file or directory
diamond@diamond:~/alsa$         ./configure --with-cards=als4000 --with-sequencer=yes;make;make install y
bash: ./configure: No such file or directory
bash: make: command not found
bash: make: command not found
diamond@diamond:~/alsa$
}
Not the least of my problems is that I can't even figure out how to download the drivers.

---

### Post by renzokuken on 2007-02-15
ok, ill run you through ow to do it another way.......

download this file to your desktop [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2)

then run these commands in the order they are shown

```

sudo apt-get install build-essential   (you need these to be able to compile)
cd Desktop
tar xjf alsa-driver-1.0.14rc2.tar.bz2
cd alsa*
./configure
make
sudo make install

```

reboot and see what happens

---

### Post by paydaydaddy on 2007-02-15
Got sound. Many thanks. Now I just need to figure out how to play wmv files. I get sound but no vid.

---

### Post by renzokuken on 2007-02-16
you need the correct codecs for wmv........they are proprietry codecs so you have to install them yourself.

this can be done very easily with Automatix or Easyubuntu

[www.getautomatix.com](www.getautomatix.com)

---

