---
title: "PCTEL Modem problems"
date: 2005-03-01
forum: Networking &amp; Wireless
---

### Post by Dragonfly_X on 2005-03-01
Hi, I have a pctel HSP 56 micromodem in my pc but linux doesn't detect it. I've tried to configure it but I wasn't very succesful what can i do to get myself on-line again. ](*,)

---

### Post by az on 2005-03-01
Pctel does not care about open source software users.  They only have released a binary driver for the 2.4 kernel.  There are hacks to make it work with several versions of that kernel.  There is nothing for the 2.6 kernel.

Either use a 2.4 kernel or get a supported modem.

Take a look at:
linmodems.org

---

### Post by Dragonfly_X on 2005-03-01
[QUOTE=azz]Pctel does not care about open source software users.  They only have released a binary driver for the 2.4 kernel.  There are hacks to make it work with several versions of that kernel.  There is nothing for the 2.6 kernel.

Either use a 2.4 kernel or get a supported modem.

Take a look at:
linmodems.org[/QUOTE]

I guess a new modem may be in order. I thank you! =D>

---

### Post by watchthisspace on 2005-03-31
Hello, PCtel modems drivers are here: [http://linmodems.technion.ac.il/pctel-linux/](http://linmodems.technion.ac.il/pctel-linux/)

I have a PCtel Hsp56 modem and I'm going to try these drivers, hopfully they work  :smile: 


Watchthisspace

---

### Post by az on 2005-03-31
If your pctel modem is an ac97 codec modem, you may getit to work with the sl-modem drivers in multiverse.

---

### Post by watchthisspace on 2005-04-01
I dont think mines a ac97 codec modem,Which drivers should I download because there's alot   ](*,)

---

### Post by az on 2005-04-01
Start from the beginning.

Go to linmodems.org and download scanmodem.  Put it on a floppy and boot into ubuntu.  Put scanmodem on the desktop.

Open a terminal, 
cd Desktop
unzip ScanModem
sudo ./ScanModem

Look at the modemdata file it creates.  It will tell you what modem you have and what drivers may work.
If you are using Hoary, the sl-modem packages are in multiverse.  I have some precompiled modules....

I'll post them.

---

### Post by watchthisspace on 2005-04-01
I downloaded Scan modem and extracted it, but nothing happens when I run it   :confused:

---

### Post by Zonkle on 2005-05-21
[QUOTE=azz]If your pctel modem is an ac97 codec modem, you may getit to work with the sl-modem drivers in multiverse.[/QUOTE]

Mine has the AC'97 thing is windows device manager ..... i still can't make this modem works on the Linux Ubuntu :(

Can you help me please ?

Thanks.

---

