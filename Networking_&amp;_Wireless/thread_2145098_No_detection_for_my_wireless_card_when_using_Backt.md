---
title: "No detection for my wireless card when using Backtrack 5"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by yousha9290 on 2013-05-14
Hello, im a newbie here and a novice in linux, who want to learn things by any means. Hope you guys, who are expert will give me a big help. So im going directly into my problem.

Just intalled Backtrack 5 R3 (KDE 34 bit) on ubuntu by using VirtualBox. After successfully installed the OS on my VirtualBox, I have found that Backtrack didn't detect my wireless card (it is a TP-Link model WN781ND) by using the following command:-

*ifconfig* and* iwconfig*.

The result of the above command below:

[COLOR=#ff0000]iwconfig[/COLOR]

lo           no wireless extension

eth0       no wireless extension


[COLOR=#ff0000]ifconfig[/COLOR]

Same as above except for eth0 it give me details for my wired card.

[COLOR=#ff0000]Note that the wireless card is working well on my ubuntu 12.04 LTS[/COLOR].

I dont think it is a driver's problem, this is my own opinion.

Please guys help me, im get stuck in my course with this problem.

---

### Post by chili555 on 2013-05-14
> Just intalled Backtrack 5 R3 (KDE 34 bit) on ubuntu by using **VirtualBox**.Networking works a little differently in a virtual machine; normally, it's bridged from virtual interfaces in the virtual machine to the actual hardware on the host. Please see here: [http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

### Post by yousha9290 on 2013-05-15
Thanks Tarballs im trying to study the link u gave me n come back again if problem not solve.

---

