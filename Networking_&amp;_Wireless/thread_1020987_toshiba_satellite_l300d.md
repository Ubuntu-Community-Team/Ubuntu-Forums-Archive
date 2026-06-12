---
title: "toshiba satellite l300d"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by TheMixtureMedia on 2008-12-24
Hi there I have Ubuntu 8.10 install and the wi-fi card will not work but it works in windows xp and no I do not want to go to xp can anyone help me??

---

### Post by TheMixtureMedia on 2008-12-25
any help

---

### Post by Vendettaseve on 2008-12-25
I also have this laptop, just got it today. 

Will be putting ubuntu on it shortly. Just because something works out of the box on XP does not mean it will work right away on Ubuntu, please be patient. Its also a good idea to hook it up to the net via a cable so your system can update etc. you may find it will work after that. if not youl need to find linux drivers for the card manualy.

Will post again once im done.

---

### Post by narcisgarcia on 2009-01-01
I've started a wiki page for a model of L300D:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL300D-13B](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL300D-13B)

I don't know if wireless NIC is seen or not with the "lspci" command, because I only see 1 network device. Can be the same Realtek for both devices (wired and unwired)?

---

### Post by blueturtl on 2009-01-04
I just posted a [guide to Ubuntu 8.10 and Toshiba Satellite L300D]("http://www.cs.uku.fi/~modinos/ubuntu.html").
It's probably not the same model exactly, but as far as I know the wireless networking fix should work for you too.

edit:
A quick note: the model I've tested has Realtek wired & wireless networking, but the wireless card is an internal USB device so you can't see it with 'lspci'. You have to use 'lsusb' instead.

---

### Post by narcisgarcia on 2009-01-04
Thanks. I've linked it on this wiki sheet:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL300D-13B](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL300D-13B)

---

