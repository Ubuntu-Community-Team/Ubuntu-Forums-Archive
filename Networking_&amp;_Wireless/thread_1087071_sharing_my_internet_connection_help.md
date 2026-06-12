---
title: "sharing my internet connection help"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by ryuchao009 on 2009-03-04
alright here's my setup. I have a wireless router that I connect to the internet through via my atheros-based network card. I have an ethernet connection (eth0) that is connected to another router. My xbox360 (and eventually my original xbox and a pc) are also connected to my second router. the second router has its dhcp server turned off and I need to use my eth0 to forward the internet from my ath0 to the switch.

From what I understand, I need to have ath0 as dynamic and assign a static IP to my eth0. I did this and enabled Internet Connection Sharing via Firestarter. It didn't give me any errors, but my xbox360 cannot connect to the internet.

I have my first router as 192.168.1.1 w/ dhcp server on. My second router is set to 192.168.2.1 w/ dhcp off. My eth0 is 192.168.2.101 w/ no default gateway supplied.

The xbox recognizes my pc and the local network, but I get the error "cannot resolve DNS". Do I use my DNS for the first router or for ath0? or should I stop using firestarter and implement this differently? Pinging to the 360 from router 1 always seems to fail too. 

I'm fairly new to ubuntu so please try to explain it in non-complex terms so that I can understand :D

---

### Post by ryuchao009 on 2009-03-05
OK I got this working now. For anyone else w/ the same problem go to: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370) 

I would recommend firestarter but it wouldn't work for me. The command-line steps took about 10mins and they weren't nice and pretty, but they worked (that IS what matters after all :P)

---

