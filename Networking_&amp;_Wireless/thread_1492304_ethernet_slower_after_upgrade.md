---
title: "ethernet slower after upgrade"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by rockingabe on 2010-05-24
Hi everyone:

I just installed 10.04 LTS server edition on my intel atom board.  After the first reboot, I logged in and installed iperf and tested the speed with my windows xp computer.  iperf measured 880 Mbits/s which I thought was not bad for gigabit ethernet.  Well, when I logged in, the system said something about there being a few updated packages.  So i ran: sudo apt-get update, then sudo-apt-get upgrade.

I think it upgraded the kernel among other things.  I rebooted and now I'm only getting around 500-600 Mbit/s form iperf.  I have tried this between my ubuntu box and my windows machine, and also with my imac running os x.

Does anyone have any suggestions?  If it is the kernel, is there a way to downgrade back to the original one?

---

