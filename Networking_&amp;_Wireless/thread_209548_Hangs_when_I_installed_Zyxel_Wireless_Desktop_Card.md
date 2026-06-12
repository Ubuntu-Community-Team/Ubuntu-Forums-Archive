---
title: "Hangs when I installed Zyxel Wireless Desktop Card"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by sunny007 on 2006-07-05
Hi,

Well this is what happening...

When I put my Zyxel G-302 v2 Wireless desktop card without installing the driver first, while starting my computer, it hangs at "loading the hardware drivers" stage.  Is there anybody came across with this issue with same or different wireless card?  This is happening prior to the installation of driver for it.

So, I removed the card and started my computer. I fould that Zyxel has driver support for their Zyxel G-302 V3 model and not for V2. So I downloaded the driver for that one. Copied it my home directory. When I run ./makedrv to compile, it errors out. It is trying find "Build" folder under lib\module\linux2.6.X.X. It says no directory or file.  I can not create a folder here. I don't know why.. 

Also, what is the meaning of the following command..

make -c XXX\XXX SUBDIR=YYY\YY\YYYY MODVERDIR=ZZZ\Z\ZZZ\ZZ module

XXX is dir
YYY is dir
ZZZ is dir

I am fairly new to linux and I still understaning it. Can someone explain me where the driver should go in this folder structure. Also, please feel free to guild me so that I get this working. 

Thanking you in advance...

---

### Post by YtseWolf on 2007-01-29
I'm having the same issue.  I had the thing in my box while trying to install Ubuntu, and it would of course hang at the same moment.  I was really confused because I was able to install Debian without the same thing happening.  Anyway, I got Ubuntu installed by taking the card out, then after I at least had the OS in, I put the card in and booted in recovery mode, then initted up to run level 3.  Now I'm at the point everyone else is at where I'm trying to get the driver installed, but ./makedrv pukes with 

 *** No rule to make target `blahblahblah/rtl818x-0.1/Makefile'.  Stop.

Lovin' it!  I will report my findings if I get the thing to work.

---

### Post by YtseWolf on 2007-01-29
OK, nevermind most of what I said.  I had a different card in there when I thought I had the Zyxel card in there.  In recovery mode, I can at least see some output.  The thing recognizes that it has a card, it says 'this is a PCI NIC' and a bunch of other stuff, then it says, 'successfully reset somethingorother' in its dying breath, and stops responding.  I will try to get more specific output when I can have a laptop next to it when it goes into the weeds.

---

### Post by YtseWolf on 2007-02-24
OK, so after not touching this for a while, I'm back.  When I have the NIC in the box and I start up in recovery mode, I see messages prepended with rtl8180 (which is a network card chipset), and the last message it comes up with is that it successfully reset the card.  Then it dies.  I'm trying to find out where this driver lives ("find -name rtl8180" gets me nothing) so I can stop it from attempting to do its thing.  Maybe when it comes up we can use ndiswrapper or whatever instead.

---

### Post by YtseWolf on 2007-03-02
OK, I think this may have been reported in another thread as well, but I was able to find that the driver r818x is what is loading which then hangs when trying to reset the Zyxel card.  If you put "blacklist r818x" into your /etc/modprobe.d/blacklist file, it will skip trying to configure it and at least boot the machine.  Now I am at least caught up to everyone else, which means messing with ndiswrapper or trying to get stuff to make that doesn't want to make, etc.

---

