---
title: "Samba (and Vista) tuning for gigabit ethernet?"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by spotter on 2008-12-07
does anyone have any reccomendations for samba/ubuntu (intrepid) tuning to get the most out of gigabit ethernet, as well as tuning reccomendations for Vista?

What I can tell you.

I believe I have a jumbo packets setup, MTU size of 7200 (can't do 9000 as the vista drivers for the realtek card don't seem to support) and seems to be ok.

I can write to the samba server from vista at approx 50MB/s, but can only read from the samba server at approx 20+MB/s

I'm ok with the write speeds, but would want bette read speeds.  any reccomendations would be appreciated.

---

### Post by jmoorse on 2008-12-07
In practice Jumbo Frames do not create a very significant performance increase except in large SANs or backup environments.  You may want to test with MTU set back to 1500

I would verify that your network cards and switch ports are hard coded for 1000Mbit, as auto negotiation can create some odd problems.

I would also check the interface (ifconfig -a) for errors, `top` to check resource utilization, and you may want to consider doing protocol analysis (wireshark) to see if the problem is network related or Kernel/Disk subsystem/etc

---

### Post by spotter on 2008-12-07
> **jmoorse said:**
> In practice Jumbo Frames do not create a very significant performance increase except in large SANs or backup environments.  You may want to test with MTU set back to 1500p

I can play with that and see.

> I would verify that your network cards and switch ports are hard coded for 1000Mbit, as auto negotiation can create some odd problems.

it's deffinitely running in 1000Mbit (as would break much higher than 10MB/s otherwise)

> I would also check the interface (ifconfig -a) for errors, `top` to check resource utilization, and you may want to consider doing protocol analysis (wireshark) to see if the problem is network related or Kernel/Disk subsystem/etc

hmm, that may be it and maybe jumbo related

RX packets:90477818 errors:0 dropped:48920276 overruns:0 frame:0
TX packets:54231428 errors:0 dropped:0 overruns:0 carrier:0

---

### Post by spotter on 2008-12-07
turned off jumbo packets on the windows side and reading from the samba server dropped to under 10MB/s

---

### Post by jmoorse on 2008-12-07
> **spotter said:**
> turned off jumbo packets on the windows side and reading from the samba server dropped to under 10MB/s

Did the you notice a change in the frequency in the augmentation of drop counts?  If not go ahead and put it back on.

I would move to protocol analysis as the dropped # is strikingly high

You could also try swapping out the ethernet cable for kicks

---

### Post by spotter on 2008-12-07
it has to be a bug in ifconfig, just rebooted

eth0      Link encap:Ethernet  HWaddr 00:22:15:a1:d2:41  
          inet addr:192.168.0.41  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fea1:d241/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:499 errors:0 dropped:2867537736 overruns:0 frame:0
          TX packets:538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38995 (38.9 KB)  TX bytes:87571 (87.5 KB)
          Interrupt:222 Base address:0xe000 

and the dropped count just keeps on looping through its entire space, and this is with a regular mtu.

---

### Post by jmoorse on 2008-12-07
I would check and see if anyone has been having similar problems with the same network adapter (driver problem?)

Also the SAMBA group has some great documentation on configuration options that may help you tweak your connection.

Good luck!

---

