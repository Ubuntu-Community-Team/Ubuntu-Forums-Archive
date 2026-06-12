---
title: "share internet via multiple network cards"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by hen3rz on 2006-02-15
Hello,

I have an ubuntu box with 4 network cards in it. Currently eth3 is recieving my internet from my modem and I wish to use eth0, eth1 and eth2 to share the internet with my windows machines. So far I have eth0 sharing the internet by following this tutorial:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

But I'm now unsure how to get eth1 and eth2 to share the internet. I have tried repeating the tutorial for each of cards but it didnt seem to work.

If anyone knows how I would go about doing this i would greatly appreciate any input.

---

### Post by schdefan on 2006-02-15
You need a masquerading for your other networks which you can do with iptables. There are a lot of tutorilas about iptables. And google for routing with multiple network cards is a good start.
schdefan

---

### Post by mips on 2006-02-15
Only a search away....

[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

