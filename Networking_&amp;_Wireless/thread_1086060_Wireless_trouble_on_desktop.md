---
title: "Wireless trouble on desktop"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by Shady2175 on 2009-03-03
i have a compaq presario sr1124nx desktop, with a linksys wireless n pci adaptor  i successfully installed ubuntu 8.10 but it cannot find any wireless extensions. i typed the commands sudo ifconfig and sudo iwconfig, it finds no lo, no eth0 and no pan0.  can someone help me? im sort of a newbie at this so please no difficult language lol thanks:D

---

### Post by N04h on 2009-03-03
It looks like it maybe a driver issue. 

Can you please paste the exact text that ifconfig and iwconfig return?

---

### Post by Shady2175 on 2009-03-03
sudo ifconfig

eth0  Link encap:Ethernet  HWaddr  00:11:2f:15;db:b6
      UP BROADCAST MULTICAST  MTU:1500  Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
      Interrupt:23 Base address:0x8000

lo    Link encap:local Loopback
      inet addr:127.0.0.1  Mask 255.0.0.0
      inet6 addr: ::1/128 Scope Host
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:246 errors:0 dropped:0 overruns:0 frame:0
      TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

sudo iwconfig

lo    no wireless extensions.

eth0  no wireless extensions.

pan0  no wireless extensions.

I am on my laptop typing this out exactly how it is stated on my desktop. (just for reference)

---

### Post by N04h on 2009-03-03
You should learn to copy and paste from the command line.  You may need to hold shift or alt. I can't remember and I'm not on a *nix machine to find out how.

To address your wireless issue:

Your LO is your loopback, your Eth0 is your ethernet card, and I assume your pan0 is bluetooth.  That means that your card isn't being recognized.  

How do you know it is successfully installed?  It appears as though it is not.

What is your model number of your linksys adapter?

---

