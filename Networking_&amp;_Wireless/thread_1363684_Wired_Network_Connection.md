---
title: "Wired Network Connection"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by chpage07 on 2009-12-24
I recently acquired an older Dell DHM (Closest thing to a model name I can find on it) for free. I installed everything alright but now when I log in and try to connect to my network it wont. I have this one and every other pc on my network set to auto configure. It can see that the network cable is plugged in and it even saw the network for a second then it disconnects instantly without any warning. 

I tried to swap out the NIC with one that I know works, the light on the back was lighting up red and and I wasn't sure if the card itself went bad. Still the same issue though. 

Any help would be much appreciated.

---

### Post by Iowan on 2009-12-24
From a terminal, check **lshw -C network** to see what it has for interface - and if it has alias like eth0.

---

### Post by chpage07 on 2009-12-24
I literally just now fixed it! It was missing a driver for some reason, found it online and installed through a thumb drive. Thanks though.

---

### Post by Iowan on 2009-12-25
Congrats! Fixed is good - sometimes "in spite" of advice. ;)
If it *stays* fixed, mark the thread [SOLVED] (Thread Tools)

---

