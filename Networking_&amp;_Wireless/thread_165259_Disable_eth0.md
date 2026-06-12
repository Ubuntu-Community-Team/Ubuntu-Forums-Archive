---
title: "Disable eth0"
date: 2006-04-24
forum: Networking &amp; Wireless
---

### Post by tnpete on 2006-04-24
Silly me - I got it. I just had to disable it in connection properties. Everything is smooth now. 


Really simple question - I have 2 network cards installed - ath0 and eth0. I want to disable eth0. My system hangs at boot while trying to connect to ntp.ubuntulinux.org. I'm figuring it is some sort of conflict. I also have to disable eth0 manually everytime I reboot in order to get on the internet. Such a hassle...

TIA.

---

### Post by ssalman on 2006-04-24
edit your /etc/network/interfaces file and comment out the eth0 section , use # at the begining of the line to comment it out. use "gksudo gedit /etc/netwok/interfaces" command to edit the file... hope this helps.

---

### Post by opus on 2006-04-24
How are you disabling the network card?

If you go into System->Administration->Networking, go to properties for eth0, and uncheck the box, that should disable it on boot.

---

