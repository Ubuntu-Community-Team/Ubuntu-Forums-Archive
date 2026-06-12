---
title: "Network Card Not Detected"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by cosh on 2006-01-15
Hello.

I am currently trying to set up a home server/firewall using Ubuntu 5.10.

I have two network cards, one is built into the motherboard, the other is a 3Com EtherLink III (3C509).

After installing Ubuntu, I had trouble getting it to detect the 3Com.


I couldn't figure out what was wrong, so I ran the install cd twice: once with the built in port connected to my modem, and once with the 3Com port connected to my modem.

Turns out that DHCP failed when the 3Com port was connected to my modem, but succeeded when the built in port was connected.

 
I have have got both cards working on a different linux distro. Any suggestions about how to get the 3Com to work with Ubuntu?

Any help much appreciated.
Cheers!

---

### Post by lizardking on 2006-01-21
me too :(

---

### Post by hulk on 2006-01-25
make sure in your bios that IRQ 10 is set to ISA Legacy, not PNP/ISa.  How it is worded may differ, but IRQ 10 worked for me.

---

### Post by twistie on 2006-01-25
I am also having the same problem. However, i have tried changing IRQ 10 and indeed all the other IRQ's to ISA Legacy but Ubuntu still isn't detecting it.

---

