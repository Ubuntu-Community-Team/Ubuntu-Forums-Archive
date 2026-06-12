---
title: "LAN Issue Need a help"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by Lunixer on 2010-06-04
Dears, 

I've been install Ubuntu 10.04 with "wubi" tool inside windows XP sp 3 

after I complete the installation and log-in into ubuntu I had LAN issue with eth0 it can't work 

I'm using Speed touch as modem with connect Ethernet cable with automatic configuration

I hope from you all to guide me how to solve the issue and i'm ready for any information it will help to find the solution.

and be informed that I'm new Linux ubuntu user and realy I like to move to ubuntu without using any other OS such as Win:

---

### Post by Zakhafr on 2010-06-04
As far as I know, the (Alcatel?) Speed touch is (or was at the time it was used in France... many decades ago!) a USB modem.

If is still so, you would have to find a driver for this USB modem, it does probably exist as it is a very old device.

If it is such a modem, it has nothing to do with eth0, as USB is NOT ethernet! (eth0 stands for the first ethernet device).

---

### Post by lisati on 2010-06-04
If you want to install Ubuntu without having Windows around, you might want to look into "[Dual Boot]("https://help.ubuntu.com/community/WindowsDualBoot")": a WUBI installation commonly requires you to have Windows present, even if you don't use Windows much.

> **Zakhafr said:**
> As far as I know, the (Alcatel?) Speed touch is (or was at the time it was used in France... many decades ago!) a USB modem.

If is still so, you would have to find a driver for this USB modem, it does probably exist as it is a very old device.

If it is such a modem, it has nothing to do with eth0, as USB is NOT ethernet! (eth0 stands for the first ethernet device).
Aside: My router/modem is a "speedtouch" model by [Thomson]("http://www.thomsontelecom.com.au/speedtouch/index.htm") and definitely connects by ethernet; it needed no special configuration within Ubuntu to work.

---

### Post by Zakhafr on 2010-06-04
Ok!

So it's a new version, and indeed, if it is now Ethernet, it should need no tweeking. Alcatel & Thomson were very close once. My first employer (back in 1985) was *Alcatel-Thomson Hertzian Beams*. ;)

In some countries Thomson is was a more popular trademark, so depending on the country, they used Alcatel or Thomson for the same product.

---

### Post by Lunixer on 2010-06-04
Dears 

1- I'm using THOMSON modem/router which is connected directly to my pc with Ethernet cable it doesn't has a USB port

2- currently I have WinXp and ubntu is installed with WUBI tool for practice on ubuntu until I reach the intermediate level after that I  will be ready to install Ubuntu without havin' and other OS

---

### Post by Lunixer on 2010-06-05
any update!!

---

### Post by Bucky Ball on 2010-06-05
> **lisati said:**
> Aside: My router/modem is a "speedtouch" model by [Thomson]("http://www.thomsontelecom.com.au/speedtouch/index.htm") and definitely connects by ethernet; it needed no special configuration within Ubuntu to work.

+1. Built and set up machine for mother-in-law and she has Speedtouch. No problem. Same as Lisati. 

Open a terminal and paste this, in Ubuntu ...

```
lspci
```That will let us know what's in the box.

Also, dual-boot could be the way to go. Once you are confident with Ubuntu you can wipe Windows and use the space for storage or another install of something else. ;)

---

