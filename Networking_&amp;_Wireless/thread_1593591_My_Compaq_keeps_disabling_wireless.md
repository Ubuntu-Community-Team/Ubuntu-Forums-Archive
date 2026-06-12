---
title: "My Compaq keeps disabling wireless"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by Torrino on 2010-10-11
[FONT=Century Gothic]I have Ubuntu 10.10, and it's keeps turning off the wireless when I'm on hotmail, or watching a video. :-| Please help![/FONT]

---

### Post by Ruebus on 2011-01-17
I've got the same problem, seems to be at random though. I use an acer. I've never had- actually that's not true - I have not had recent trouble with wireless before installing ubuntu.

---

### Post by xtacease on 2011-01-21
I too am having this issue. I'm intending to use the machine as a gateway for a small LAN and this is kind of a deal breaker.

From a LAN-side device i can always ping to the WAN interface of the gateway. Problem is, my wireless NIC (WAN interface) seems to lose layer 2 connectivity at random intervals preventing any kind of traffic from traversing out to the interwebs.

I've run both tcpdump and ping commands and caught the failure, but neither provide relevant info.

tcpdump just shows arp requests (hence layer 2 problem) and ping starts getting destination unreachable.

Perhaps this is a new issue in 10.10?

Any help is appreciated!

Update:

unplugging and hot-plugging the adapter is enough to get it working again for a short while.

---

### Post by ravengangrel on 2011-01-23
Please, check this.

[http://ubuntuforums.org/showthread.php?p=10388907#post10388907](http://ubuntuforums.org/showthread.php?p=10388907#post10388907)

If my workaround works for you, please, answer to my thread stating your hardware. I would like to know if this is related to some particular hardware.

---

