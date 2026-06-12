---
title: "Problems with minidlna"
date: 2011-07-26
forum: Multimedia Software
---

### Post by Error403 on 2011-07-26
Hello, I just reinstalled Ubuntu at least twice for this problem: Minidlna starts fine for a few minutes, I can see it on the network with my television, windows and even my phone. However, after a few minutes (say one hour), it stops being there. The process keeps running, and is kinda responsive to rescans and restarts. However it becomes unusable after a few minutes. The last reinstall was pretty basic: Installed Ubuntu 9.04, upgraded to 10.04 (servers), installed minidlna, wait and... bam! So there were no conflicts in all that, so what could make minidlna stop being responsive? Also, the logs show no indication of possible problems.

---

### Post by Error403 on 2011-07-28
Well, I tried with serviio, mediatomb and others, but I'm coming back to minidlna because it was working just fine before I reinstalled ubuntu.

So I got 10.04 server with minidlna, samba, ssh and webmin, and the TV is a Samsung LN55C630. It was working perfectly until some power surges corrupted my boot drive and had to reinstall everything from scratch. I'm trying again with ufw completely disabled from bootup. We'll see in a few minutes if it's still visible on the network.

---

### Post by Error403 on 2011-07-29
Well I think I fixed my problem by disabling ufw from booting.

---

