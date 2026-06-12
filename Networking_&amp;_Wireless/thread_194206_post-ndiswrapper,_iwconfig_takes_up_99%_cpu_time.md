---
title: "post-ndiswrapper, iwconfig takes up 99% cpu time"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by mpa on 2006-06-11
I bought a Digitus Wireless PCI NIC DN-7006GR which supposedly use a Ralink RT2561 chipset. So I use ndiswrapper to install rt61.inf which couldnt detect the nic, thus I tried rt2500 and another driver whose name escapes me at the moment. None could detect the card so I gave up and reboot to Windows.

The next time I boot to Ubuntu, it was slow like molasses because iwconfig was using 99% of CPU time and the process could not be killed even as root using kill -9. Then I boot to recovery mode kernel and removed all installed ndiswrapper drivers and reboot. Unfortunately its still the same, iwconfig is still making ubuntu unusable ](*,)  What is to be done ?

---

### Post by cas_becker on 2006-06-27
Hi, i have the same problem. And think a have a clue for tip for you.
Goto the recovery-console at start.
type:      $ nano /etc/network/interfaces  

There, delete all lines wich are in relation to your wlan-card
save the file, restart, ready. so....that was the good news. The bad news is: You have to do that EVERY RESTART of your computer! Until now i have not found any other way.

If you have any solutions please tell me so

---

