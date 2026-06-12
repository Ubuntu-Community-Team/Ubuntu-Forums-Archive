---
title: "Logitech USB Headset Low Sound"
date: 2010-05-02
forum: Multimedia Software
---

### Post by Just_Edd on 2010-05-02
hi, i just upgraded to ubuntu 10.04 and everything is ok except my USB Logitech Headset. The problem is that volume of the device is very low and i can't hear the music or any sound like i use to heard. Even if i increase the volume up to 100%, i still hearing the sound with a very low volume. but if i use the analog output of my sound card i can hear very well. I remember that i used to have this problem in ubuntu 9.10 but i fixed with a script that i found it in this forum, but i can't find it again. I don't know how to fix it. Thank you for your help.

:~$  lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04fc:0c25 Sunplus Technology Co., Ltd SATALink SPIF225A
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by piratude on 2010-05-02
[FONT=monospace]Open a terminal. put in [/FONT]alsmixer and select the usb headset and adjust the sound from there. I worked for me.

---

### Post by Just_Edd on 2010-05-02
hahaha, i didnt know that was that simple!! hahaha, thank you very much!!

---

### Post by kelly harlton on 2010-05-28
> **piratude said:**
> [FONT=monospace]Open a terminal. put in [/FONT]alsmixer and select the usb headset and adjust the sound from there. I worked for me.
Helped me too thanks!!!

---

### Post by IceDoE on 2010-08-12
Wow, worked for me too on Ubuntu Netbook Edition 10.04. I've been trying to figure out this one for a while. Looks like it will fix my front mic problems too.

Odd though that the graphical alsa mixer couldn't fix this.

---

### Post by znejk on 2010-08-30
Having the same problem with the platronics usb headset, but the pcm volume is 100 % at alsamixer :(

---

### Post by UDon on 2010-09-14
I got the same problem when I upgraded to Lucid (10.04). The solution given above worked beautifully -- thanks!

For newbies like myself: To fix this, I put "alsamixer" in terminal, then pressed F6 to select my sound card, used side arrows to select, then up arrow to increase volume.

---

### Post by mal39 on 2010-09-17
I just downloaded GNOME ALSA sound mixer from software centre, or you can try another one - ALSA utilities. Both them can let us adjust volume and switch sound card to use.

---

### Post by beeboob on 2010-11-16
So many thanks "alsamixer" verly verly cool

---

### Post by zelalem on 2011-02-04
It worked for me as well but the volume gets back to low when i reboot it. What must i do to keep my settings. 

Thank you.

Zelalem

---

