---
title: "Cannot Connect To A Home Network"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by loweehahn on 2009-05-09
I'm asking for help on my friend's behalf. He's a newbie in Ubuntu. He was using Windows XP in his laptop but lately he switched to Ubuntu 8.10 but he couldn't connect to his router at home. Previously he was able to connect to his router at home. His router enables two computer to connect to the internet simultaneously though.

---

### Post by Iowan on 2009-05-09
Unfortunately, that's not much to go on...
Wired or wireless? Does Ubuntu get IP address? (From a terminal, check **ifconfig -a**. If not, check **lshw -C network**. If you need more details on how to do these things, please post back...

---

### Post by loweehahn on 2009-05-10
Wired. The IP address is shown. There is no need to configure anything for wired ethernet right? What about home networking?

---

### Post by Iowan on 2009-05-10
Is the IP address in the same subnet as the router (*probably 192.168.X.X*), or is it 169.254.X.X (which would be **avahi** stepping in)?

---

