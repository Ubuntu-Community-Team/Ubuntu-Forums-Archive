---
title: "Ralink 3062 chipset"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by stonegrey on 2011-11-20
hi all, 

i'm a serious newbie to linux. i have read as many of the threads relating to installing the driver for this as possible. there is a 2860sta file in the staging folder, but i cannot get it to install. i have followed posts by chili555 on this subject and only get errors!. i'm also running 11.04 (NN)

i have also blacklisted all rt2800 driver files to try and mack this work.

basic info:

$ locate 2860sta
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

$ lspci -nn

00:08.0 Network controller [0280]: Ralink corp. Device [1814:3062]

my attempt at making the driver file for said device:

root@blackthornserver:/home/peter/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217  rt2860sta.ko# **make**
make -C tools
make[1]: Entering directory `/home/peter/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217  rt2860sta.ko/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/peter/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217  rt2860sta.ko/tools'
/home/peter/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217  rt2860sta.ko/tools/bin2h
make: /home/peter/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217: Command not found
make: *** [build_tools] Error 127


all help gratefully apreciated.

---

### Post by chili555 on 2011-11-20
> i have followed posts by chili555 on this subject Hmmm? What?? OK, I'm awake. Let's take a look at a few things. Please post:```
lspci -nn | grep 0280
modinfo rt2860sta
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by stonegrey on 2011-11-20
output looks like this:

peter@blackthornserver:~$ lspci -nn | grep 0280
00:08.0 Network controller [0280]: Ralink corp. Device [1814:3062]

peter@blackthornserver:~$ modinfo rt2860sta
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
srcversion:     C22EE7282F9A519D7E9A764
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

---

### Post by chili555 on 2011-11-20
I don't quite understand this:> root@blackthornserver:/home/peter/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 [COLOR="Red"]rt2860sta.ko[/COLOR]# make???

You should, instead, do:```
root@blackthornserver:/home/peter/Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
```Please open Synaptic Package Manager. Do you have linux-headers-generic and build-essential installed? They are required to compile this package.

---

### Post by stonegrey on 2011-11-20
build essential, and headers installed.

just goind through the other bit

---

### Post by stonegrey on 2011-11-21
next step was to have a go at installing 11.10 oneiric ocelot. in the hope that the relevent drivers may have been packaged in the new version.

3 downloads and 4 CD's later, it still willnot install, and crashes at the restart section.

i'm seriously getting fed up with this now....... 

looks like it may be a winows based install then :(.

---

### Post by chili555 on 2011-11-21
So what went wrong after 'make' and 'make install?' Can't we fix it?

---

### Post by stonegrey on 2011-11-21
not sure what i did, but, a fresh reinstall, and rerun though "make" , "make install" and it all worked, then a quick software update killed the wlan connection, this time, modprobe did the job. everything is up and running.

my next two searches will be, "how to mount a secondary hard drive", and how to access this pc/server on my home network.


thank you for your help so far.

how do i change this to solved?

---

### Post by chili555 on 2011-11-21
Glad it's working. Please use thread tools at the top to Mark Solved.

---

