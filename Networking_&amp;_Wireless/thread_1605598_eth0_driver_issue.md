---
title: "eth0 driver issue?"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by denti on 2010-10-25
Hi, i just installed ubuntu 10.10 and i seem to be having some problems with my eth0.  there's not link light or activity light.
I beleive my network card is an intel 86522MM.  i've tried ifconfig to bring eth0 up but nothing.

lspci gives:
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)

dmsg | grep eth0
[    1.254508] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1b:38:93:2a:92
[    1.254511] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.254540] e1000e 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: 1032ff-0ff
[   15.524376] ADDRCONF(NETDEV_UP): eth0: link is not ready
[15050.052715] ADDRCONF(NETDEV_UP): eth0: link is not ready

any help or suggestions as to why this isn't working?  i know the network cable is good as when i plug the cable into another computer it works fine.
thank you

edit:  just wanted to add that ifconfig -a give this..
eth0      Link encap:Ethernet  HWaddr 00:1b:38:93:2a:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Memory:e8020000-e8040000 

not sure why i'm getting that interrupt.
thank you

---

