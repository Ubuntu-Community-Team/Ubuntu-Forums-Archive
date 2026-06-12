---
title: "Ubuntu 11.10 Atheros AR5B97 / AR9287"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by mtt on 2011-10-19
With "ubuntu 10.10" i have no problem with wireless connection.
With this new 11.10 update I'm not able to use wireless internet...

A crappy fix is to compile compact-wireless at every boot, with this i can connect,  but at slow speed compared with windows speed.

I have tested with no success.

[LIST]
[*]wlan0 power off
[*]disable IPv6
[*]options ath9k nohwcrypt=1
[/LIST]

Any solution ?

---

### Post by mtt on 2011-10-19
fixed with kernel 22.6.37-020637-generic , but now i can't activate ati proprietary driver ... lol this ubuntu is a poor patchwork

---

### Post by DdannyY on 2011-10-21
I got the same problem with an Atheros 242x / 542x after updating today. I'm still figuring out how to fix it, compiling compact-wireless doesn't work for me.

---

### Post by mtt on 2011-10-21
> **DdannyY said:**
> I got the same problem with an Atheros 242x / 542x after updating today. I'm still figuring out how to fix it, compiling compact-wireless doesn't work for me.
:(

---

### Post by dixoncx on 2011-10-22
[B]Same problem here with Atheros AR9285 in Ubuntu 11.10..
I posted posted details about it here..

[/B][http://ubuntuforums.org/showthread.php?p=11380434](http://ubuntuforums.org/showthread.php?p=11380434)

---

### Post by kr0n1x on 2011-10-26
I talked about this problem some time ago.
[http://ubuntuforums.org/showthread.php?t=1835190](http://ubuntuforums.org/showthread.php?t=1835190)
I still have this problem.
I had it in Ubuntu 11.04, Xubuntu 11.10 and Arch Linux.

It is a chip/driver problem for sure... :(

---

### Post by raphsabb on 2011-10-26
Anything on this? I juss got this laptop and wireless was working fine at first but now its gone...

---

### Post by STUPID USERNAME on 2012-01-13
raphsabb I have exactly the same problem.
First, after installing Ubuntu 11.10 my wireless connection was very good. The signal was strong. But after a day it suddenly became very weak and slow!
This is very weird and it pisses me off!

---

