---
title: "[SOLVED] (Gutsy) Eth0 &amp;amp; Eth1"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by E-Cecilia on 2008-12-03
I've been having problems with my wireless connection for a while now, not being able to connect to any through the Nerwork Manager but seeing them listed allright.
When I type iwconfig in terminal I get this:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Could anybody explain me what's the difference between eth0 and eth1?

---

### Post by Badly Overdrawn Boy on 2008-12-03
eth0 will be your wired ethernet connection and eth1 will be your wireless ethernet connection, I think.

---

### Post by E-Cecilia on 2008-12-07
> **Badly Overdrawn Boy said:**
> eth0 will be your wired ethernet connection and eth1 will be your wireless ethernet connection, I think.

Yeees, you were right!

---

