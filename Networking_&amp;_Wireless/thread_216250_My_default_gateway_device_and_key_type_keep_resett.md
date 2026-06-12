---
title: "My default gateway device and key type keep resetting."
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by ZenobiaBE on 2006-07-15
During the alternate install my internet settings worked fine and everything was auto-detected. My first boot into Ubuntu was also without any problems, but yesterday I couldn't connect to the internet anymore and saw that everytime I changed them, my default gateway devie and key type would change immediately. The gateway device should be eth1, but it resets to a blank setting, the keytype should be ASCII/plain text but resets to hexadecimal. Please answer as thoroughly as possible, I'm new to linux.

Thanks a lot in advance.

---

### Post by Topflite on 2006-07-25
I am having exactly the same problem.  Any suggestions, anyone?

---

### Post by daou on 2006-08-13
It might be possible to use the route command to fix the default gateway device as I described [here]("http://www.ubuntuforums.org/showthread.php?t=234300"). My problem was with two ethernet devices and Ubuntu always choosing the wrong one for the default gateway device. But running just the "route add" command might fix it for you (not sure if it works with DHCP, mine was for a static IP connection).

---

### Post by drtvasudevan on 2006-08-13
it is a bug which has been reported.

---

