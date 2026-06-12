---
title: "Wired connection just refusing to work!"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by stygian_faerie on 2011-07-05
I'm a total newbie to linux and I'm a bit technologically impaired so this is driving me nuts!
I've managed to get my laptop to recognise when I plug an ethernet cable in and it shows me that there is a network available but whenever I try to connect it fails... I've been going through so many forums but I'm afraid I just have no idea what I'm doing. Can anyone help me?

---

### Post by stygian_faerie on 2011-07-05
...?

---

### Post by Iowan on 2011-07-06
A few things to try/check:
From a terminal (Applications>Accessories>Terminal), you can use **ifconfig -a** to see if your interface (*probably* eth0) gets an IP address. If not, **sudo lshw -C network** will provide more information about the hardware. If it DOES get an address, you can **ping** to check connections. **ping** is also available under System>Administration>Network tools. If the interface gets an address (other than 169.254.X.X), it might be a routing problem.

---

