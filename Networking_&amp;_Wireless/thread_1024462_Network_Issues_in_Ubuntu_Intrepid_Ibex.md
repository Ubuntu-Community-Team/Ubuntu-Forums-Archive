---
title: "Network Issues in Ubuntu Intrepid Ibex"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by k_pavan2 on 2008-12-29
It was all cool (in Gutsy) until I upgraded to Intrepid. 
Wireless networks still show up, but don't connect. Wired Networks don't even show up. I get a "Device is Unmanaged" message.

My Network Card is:
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

My Kernel version:
2.6.27-9-generic

Iwlist scan outputs:

bah@blah:~$ sudo iwlist scan
[sudo] password for bah: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:1D:D0:4C
                    ESSID:"pavan"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=86/100  Signal level:-47 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000452866a9122
                    Extra: Last beacon: 64ms ago

bah@blah:~$ 

Trying to simply dhclient eth1 does not work either.

Any pointers on what's wrong and how to fix it?

---

