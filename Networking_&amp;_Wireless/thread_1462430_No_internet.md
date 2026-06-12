---
title: "No internet"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by Mr. End on 2010-04-25
hey guys, sorry for being a total noob but I just got ubuntu runnung on my laptop and I seem to be getting no internet connection whatsoever. nothing seems to work. can anyone tell me what to do to get a wireless connection, or even a wired one so I can get this thing up and running?
 
thanks.

---

### Post by Mr. End on 2010-04-25
update: got a wired connection working, now all I need is a program or something that will let me get a wireless one.

---

### Post by NichoTL on 2010-04-25
> **Mr. End said:**
> update: got a wired connection working, now all I need is a program or something that will let me get a wireless one.

First the question is: is your wireless card supported by Ubuntu?
Top-right of your screen, there is a series of icons along with the date. The left-most icon should be the network manager applet. If you click on it (left-click) you should see some kind of list with a Wired Networks section and (hopefully) a Wireless Networks section. If you don't have a Wireless Networks section then chances are your card is not supported out-of-the-box.

---

### Post by Iowan on 2010-04-25
From a terminal (Applications>Accessories>Terminal), **sudo lshw -C network** should provide information about your interfaces.

---

### Post by Mr. End on 2010-04-26
no list of wireless on network connection app, all I get when using the terminal is a Network controller and an ethernet interface... guess it isn't supported. is there any way to get it to work?  or do I have to switch to a different OS?

---

### Post by Mr. End on 2010-04-26
wireless card is realtek 8192 if that helps...

---

### Post by Iowan on 2010-04-26
There's information about the Realtek 8192 buried in the 14 pages of [this]("http://ubuntuforums.org/showthread.php?t=1457592") (solved) thread.

---

### Post by Mr. End on 2010-04-27
thanks! I'll definitely try that!

---

### Post by Mr. End on 2010-04-27
Alright, I did what the link told me to and this was the message I gotL
erik@erik-laptop:~/rtl8192e_linux_2.6.0011.1029.2009$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: Entering directory `/home/erik/rtl8192e_linux_2.6.0011.1029.2009/HAL/rtl8192'
make -C /lib/modules/2.6.31-14-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/erik/rtl8192e_linux_2.6.0011.1029.2009/HAL/rtl8192'
make: *** [install] Error 2

what does it mean and how can I fix it?

thanks.

---

