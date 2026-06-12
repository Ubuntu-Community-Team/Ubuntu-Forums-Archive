---
title: "Console wireless management alternatives ?"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by pabloandresvb on 2010-11-06
Hi people! I'm actually preparing a little storage server for implementing using the Bacula suite and as I'm using only wireless connections I've been trying to find useful console applications/methods to manage wireless connections of the two laptops I'm planning to use.

Do someone of you know some good solutions (besides NetworkManager cause I need to save as much disk space as I can and NetworkManager has a lot of dependences to install) that could allow me to create and use profiles for different wireless connections when moving through different places?

Wicd didn't work for me as someones recommend me :(

---

### Post by chili555 on 2010-11-06
Do I *know* how to do it? Nope. However *man interfaces* suggests:> auto lo eth0
       
       iface lo inet loopback

       mapping eth0
            script /usr/local/sbin/map-scheme
            map HOME eth0-home
            map WORK eth0-work

       iface eth0-home inet static
            address 192.168.1.1
            netmask 255.255.255.0If at home, I assume one would then issue a command:```
sudo ifup eth0-home
```I have never tried this, but it looks promising. I suggest you study *man interfaces* and experiment.

---

### Post by pabloandresvb on 2010-11-09
> **chili555 said:**
> Do I *know* how to do it? Nope. However *man interfaces* suggests:If at home, I assume one would then issue a command:```
sudo ifup eth0-home
```I have never tried this, but it looks promising. I suggest you study *man interfaces* and experiment.


Thanks man, this can be used as you show me. I'll keep looking for a ncurses-based application or something like that but meanwhile I'm using your method.

---

