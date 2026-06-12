---
title: "Networking Questions"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by burcyril10 on 2009-03-03
Hello,
I have a few questions:
1. I can't get the box to connect to my home wired network. My XP box connects and gets dhcp assigned ip just fine. To remove possible hardware errors I used the cables that my XP box uses, and to the best of my knowledge the motherboards ethernet works just fine. I can get as far as selecting eth0 and it tires to get an ip address but then just fails. I tried assigning it an ip myself and pinging the router - no luck.
2. I want to use this box as a bittorrent dummy (but also as a switch to save me buying one haha). So i have 3 nics (all wired) in it (plus the onboard one). I was wondering if there is anything special I am going to have to do to get it to behave like a switch.

Thanks for any help,
 - Cyril

---

### Post by Iowan on 2009-03-04
Possible driver issue (unfortunately, I can't help). What are results of **ifconfig** and **lshw -C network**?

---

