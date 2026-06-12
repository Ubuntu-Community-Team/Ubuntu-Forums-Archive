---
title: "Connect to wireless internet"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by ThaGerm on 2010-01-29
Sorry if there is a tread that can answer this, but I want a personal answer to   my problem.

Soo, I just installed Ubuntu 9.10 and everything was ok util I was going to connect to internet. I just cant't find any way to connect to any wireless networks. I'm living in a board school so wireless is my only way to connect to internet. 

Can anybody help me? I have a Dell latitude e5500 and I can without any problem connect to internet on windows that I also have installed.

---

### Post by chili555 on 2010-01-29
> I want a personal answer to my problem.I'll be happy to help. First, we need to know what kind of wireless card you have. Let's ask the computer! If it's a built-in wireless card. please open a terminal (Applications -> Accessories -> Terminal) and do:```
lspci -nn | grep Network
```If it's a USB device, do:```
lsusb
```I hope it's not a PCMCIA device, but, just in case it is:```
lspcmcia
```Also, let's see:```
iwconfig
```With a few details in hand, we can proceed.

---

### Post by bbuster on 2010-01-29
I'm having the same problem with the same laptop.  I performed the commands you listed and got the following information:

The wireless card is a Broadcom BCM4322 802.11 a/b/g/n Wireless LAN Controller (rev 01)

iwconfig shows "no wireless extensions" next to the loopback and ethernet interfaces.  No wireless interface is listed.

Thanks in advance for any help you can provide.  I'm setting up this laptop for my dad who previously was running XP which got hammered by a virus.  I decided to run Ubuntu so we won't have that problem again.  ;-)

---

### Post by chili555 on 2010-01-29
This will probably do it. Post back if you get stuck.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by bbuster on 2010-01-29
That got it.  Thanks again for your help.

---

### Post by ThaGerm on 2010-02-01
Okey.
I typed in lspci -nn | grep Network
and got the answer: Broadcom corporation BCM4322 802.11a/b/g/n Wireless Lan Controller [14e4:4326] (rev 01)

Typed in iwconfig and got the answer : 
Lo   No wireless extensions
eth0   No wireless extensions

Thanks for caring :)

---

### Post by chili555 on 2010-02-01
> **ThaGerm said:**
> Okey.
I typed in lspci -nn | grep Network
and got the answer: Broadcom corporation BCM4322 802.11a/b/g/n Wireless Lan Controller [14e4:4326] (rev 01)

Typed in iwconfig and got the answer : 
Lo   No wireless extensions
eth0   No wireless extensions

Thanks for caring :)Can you confirm that you took all the steps outlined in the link I gave in post #4?

---

### Post by ThaGerm on 2010-02-01
I just typed in the two that I wrote in.

---

### Post by chili555 on 2010-02-01
> **ThaGerm said:**
> I just typed in the two that I wrote in.Please go to the link in post #4 and follow those steps. Until you get the firmware loaded for your Broadcom card, you will get nowhere.

---

