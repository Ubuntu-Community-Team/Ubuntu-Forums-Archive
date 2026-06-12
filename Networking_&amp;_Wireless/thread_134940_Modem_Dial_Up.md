---
title: "Modem Dial Up"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by manwebcam on 2006-02-22
hi... can someone help me to install my dial up modem? it's a HSP 56MR, i don't know how install it... i hope someone can help me!!!

---

### Post by aggiechemist on 2006-02-22
Well I think the fist question is what do you mean by install. Here are a few options:

1. You have a brand new modem. You need to turn off the computer, take off the panels, and plug the thing in.

2. It is physically in the computer, but you need to configure it.

3. It is physically there and seems to be working, you just need guidance on what software to use to call your ISP and connect.

Once you let us (the other people on the forums) know exactly what your need is, we can usually give a really detailed answer\\:D/ . But for now things are a bit vague.

---

### Post by manwebcam on 2006-02-25
ok! i configure logically my modem... the modem are installed fisically on my pc, but i don't know how configure to conect me to internet.. understand? i just wanna know how install the "drivers" for my dial up connection

---

### Post by Matchless on 2006-02-25
[QUOTE=manwebcam]ok! i configure logically my modem... the modem are installed fisically on my pc, but i don't know how configure to conect me to internet.. understand? i just wanna know how install the "drivers" for my dial up connection[/QUOTE]

Hi,
   Go to the Wiki and search for Dialupmodemhowto it should put you on your way.

---

### Post by manwebcam on 2006-03-02
well... always the same problem, when is compiling the follow message appear... 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... no
checking build driver for... HAL_PCT789
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH


this menssage appear before i enter ./configure... 


why this error??? i don't understand... 

this error appear when i compile everything...

---

### Post by towsonu2003 on 2006-03-02
see second link in my signature. I believe it includes the following info as well: 
do the following before first ever compiling
```

put in the cdrom
make sure it is mounted
sudo apt-get update
sudo apt-get install linux-headers-`uname -r` build-essential checkinstall
```
build-essential has the compiling utilities, linux-headers function as linux source files during compiling. checkinstall is a very nice utility to install compiled code as a package (that can later be uninstalled using synaptic).

Note: to compile, the sequence is:
./configure
make
sudo make install

Another note: 
With checkinstall in your system, the sequence is:
./configure
make
sudo checkinstall

---

