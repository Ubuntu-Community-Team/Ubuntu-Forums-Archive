---
title: "eeePC 701SD Realtek wireless cannot connect to WEP shared key network"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by keplerspeed on 2009-10-29
I have an eeePC 701SD, where wireless connected fine with all networks in 9.04 (including my WEP shared key network at home). Wireless card is **supported out of the box** with the r8180 driver. I use the normal ubuntu desktop, not the UNR edition.

lshw:
```
RTL8187SE Wireless LAN Controller
```

However, now with a clean 9.10 reinstall, I cannot connect to my WEP shared key network (this also occured when testing the beta, but I didnt think anything of it and went back to 9.04). The eeePC **can connect to other networks**, like at my university and friends place (both WPA2), so its only  an issue with my WEP shared key network. By not connecting, I mean that I put in the key, set the network configurations to shared key, however, it times out and asks for the key again (right after this I get kernel problem message, see below).

I have a desktop running 9.10 and it can connect to the WEP shared key network with no issues, and there were no issues when running 9.04 either.

Thus, I come to the conclusion that this is related to some change that must have occured 9.04 to 9.10 with the r8180 driver for my eeePC. Any insight?

PS: I am aware of the bug announced in release notes (i have a different card, but same issue). I experience a kernel crash if I use the hot key to turn on/off wireless antenna. [http://www.ubuntu.com/getubuntu/releasenotes/910#Disabling%20Ralink%20rt2860%20wifi%20on%20EeePC%20with%20Fn+F2%20hotkey%20causes%20a%20kernel%20crash](http://www.ubuntu.com/getubuntu/releasenotes/910#Disabling%20Ralink%20rt2860%20wifi%20on%20EeePC%20with%20Fn+F2%20hotkey%20causes%20a%20kernel%20crash) Interesting thing is that when nm-applet times out and asks for the password again, I get a red kernel crash icon pop up in the system tray, saying "your system encounted a serious kernel problem".

Cheers!

---

### Post by coltranem on 2009-11-03
I have a similar issue.  I just upgraded to 9.10 and when I connected to my home wireless network via a WEP key.  It connects and then immediately loses the connection.  This was not an issue when I ran 9.04.  I did a fully clean install of 9.10.  Oddly enough this is not an issue if I try to connect to an unsecured network.
 
Any ideas?
 
btw I have one of those B43XXX wireless chip sets

---

### Post by keplerspeed on 2009-11-07
I have tested with other networks and its fine, just seems to be the wep network. However, I have a realtek wireless card, your's is broadcom.

---

### Post by rrisley on 2010-01-17
Anyone find a workaround for this? My wife finally assented to installing Ubuntu on her EeePC900SD netbook and was thrilled with it, until she found out she couldn't access two important wireless networks because they use WEP (no, she can't reconfigure them).

If anyone knows of a way to make it work, you'd save me from having to support a Windows instance. :(

--Ron

---

### Post by sgosnell on 2010-01-17
I've never seen this problem, with a 701 and two 900s.  They work every time, every network, and I've connected to a lot of WEP networks.  That said, I don't use 9.10.  I had too many issues with it, and I'm still on 9.04.  10.04 works alpha works for me on WEP networks, too.

---

### Post by Mr.Auer on 2010-02-13
I also have problems with an Eee pc 701SD 8GB model. It is the one with the Realtek RTL8187SE wireless - this is different from the other early Eees - I have a 701 4GB and 901 and they both work fine on every network and I can toggle the wlan on and off now that this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404626?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404626?comments=all) has been fixed. 

Sadly, there seems to be a different bug concerning the 701SD`s wireless driver - mine hangs every time I toggle the wlan off. I have not found a solution to that and have not yet opened a bug report. the SD model is not my own, I was merely supposed to upgrade it for someone else. 

I am thinking of perhaps installing 9.04 on it, since you say that one worked fine - or trying the [http://eeebuntu.org/](http://eeebuntu.org/) EB4 beta recently released, based directly on Debian Unstable. 

Any suggestions welcome if some of you figures out a way to fix that in Karmic.

---

### Post by coupedeluxe on 2010-02-13
I have the same setup and I can't even get an ethernet internet connection. I have installed Wicd and that didn't help.

---

### Post by Mr.Auer on 2010-02-13
Tried EB4 from usb stick, toggling off wireless hangs the machine with that one too... :( At least eth0 works. Gonna try if I can get Jaunty working on it - off the live image with no updates, wlan toggle does not work and neither does the wlan connection.

---

### Post by sgosnell on 2010-02-13
Have you tried upgrading the kernel?  2.6.32 seems to work pretty well, and I've been using the 2.6.33rc with success.  With 2.6.28 the wireless won't toggle at all on my 900, but it works fine with the later series.

---

### Post by Mr.Auer on 2010-02-15
I tried Lucid Lynx alpha 2 on it as well with the 2.6.32-10.14, it exhibits the same crash behaviour. I am opening a bug report about this, here -
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522119)

My own 701 4GB and 901 models work perfectly, as they have different wlan chipsets than the 701SD model that has the Realtek RTL8187SE. I tried Jaunty and EB4 distros from a USB stick on it as well, they crash exactly the same as Karmic. Asus has used quite a few different chipsets in the machines even when the model names sound almost exactly alike - like regular 701 and 701SD - they have quite different hardware even thou the model name is similar. Also, the mic does not seem to work on the SD model, but does work fine on the 901 and regular 701.

---

### Post by dark_333 on 2010-02-28
> **Mr.Auer said:**
> I tried Lucid Lynx alpha 2 on it as well with the 2.6.32-10.14, it exhibits the same crash behaviour. I am opening a bug report about this, here -
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522119](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/522119)

My own 701 4GB and 901 models work perfectly, as they have different wlan chipsets than the 701SD model that has the Realtek RTL8187SE. I tried Jaunty and EB4 distros from a USB stick on it as well, they crash exactly the same as Karmic. Asus has used quite a few different chipsets in the machines even when the model names sound almost exactly alike - like regular 701 and 701SD - they have quite different hardware even thou the model name is similar. Also, the mic does not seem to work on the SD model, but does work fine on the 901 and regular 701.

i also upgraded to lucid, and my wireless doesn't work... :S
my netbook is a rebrand of msi wind u100 and the chip is a rtl8187se

---

### Post by cmackay on 2010-04-17
> **dark_333 said:**
> i also upgraded to lucid, and my wireless doesn't work... :S
my netbook is a rebrand of msi wind u100 and the chip is a rtl8187se

Same issue here, wireless works for a couple of minutes only. Installed 10.04 netbook edition. Tried also blacklisting rtl8187se and using windows drivers with ndiswrapper with no success

---

