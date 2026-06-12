---
title: "ethernet connection broken after dapper"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by friendly_guy on 2006-07-02
Hi

I have an internet connection through a windows box & my ubuntu machine connects to the net through that via an ethernet cable, or at least it did under breezy.  I have made a clean install dapper & this no longer works.  

My ifconfig is
one@scooby:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:44:82:5F:E3
          inet6 addr: fe80::202:44ff:fe82:5fe3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5422 (5.2 KiB)  TX bytes:17766 (17.3 KiB)
          Interrupt:169 Base address:0xcf0

& I use DHCP.  

Any help mucho appreciated

Guy

---

### Post by lurchi on 2006-07-02
Which chipset is in your network card? Perhaps you have to install into seperatly. The output of "lspci" and "lsmod" could help.

---

### Post by steve.horsley on 2006-07-02
You seem to have an active ethwenet connection - both transmit and receive bytes counted. But no IP address assigned. Try this command, and post hte result:
**sudo dhclient eth0**

---

### Post by friendly_guy on 2006-07-02
Wow - thanks for the interest & two such quick replies.

I have just switched on the computer & would you believe it now works.  

Why? The only thing I can think of is that I turned off IPV6 earlier by renaming the kernel module (ipv6.ko to ipv6.ko.bak) as suggested on one of the wiki pages: even after a reboot it didn't work but I have since had a power off - I wonder if that is the difference.  I once had to reset a borked modem with a power off, advice I was sceptical of but it did work.  

The other significant thing is that in network settings the ethernet is now set as the default gateway device where previously it would not allow me to set it at all. 

I would be interested to know what has made the difference as I will have to duplicate this on my daughters computer in a few weeks time.  

Thank you again for your prompt interest.  IMHO the ubuntu community is one of the star attractions of Ubuntu.

---

### Post by fragos on 2006-07-02
Messing with kernel drivers frequently requires a reboot to rediscover the hardware and associate it with drivers.  It's just safe practice.

---

### Post by friendly_guy on 2006-07-03
Hi Fragos

If you re-read what I said, the reboot didn't actually work - it was actually a total power off that seemed to do the trick.  (Not just powering the PC off, it was off at the mains).

I have encountered this with hardware problems but only twice before.

---

