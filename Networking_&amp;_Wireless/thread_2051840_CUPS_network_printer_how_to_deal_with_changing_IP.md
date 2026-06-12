---
title: "CUPS network printer: how to deal with changing IP?"
date: 2012-09-02
forum: Networking &amp; Wireless
---

### Post by chogg on 2012-09-02
I have a network printer (Brother HL-2270DW) and it works great.  The problem is that its IP address periodically changes.  When that happens, the computers can no longer find it.

It's setup under CUPS as "lpd://192.168.1.104/BINARY_P1".  If the address changes to 192.168.1.102, say, I can still print if I go into CUPS and change it.  But my wife can't do that, and anyway there has to be a better solution.

Any advice to setup the printer under CUPS in an IP address-independent way?

---

### Post by ajgreeny on 2012-09-02
Just give the printer a static IP address and your problem is over.

How best to do that depends on your router hardware, on my netgear I can reserve IP addresses for all the machines that connect to it, including the printer, which makes both printing to that printer, and also ssh connections between computers much easier.

See these two sites for more info:-
[https://help.ubuntu.com/11.04/ubuntu-help/net-fixed-ip-address.html](https://help.ubuntu.com/11.04/ubuntu-help/net-fixed-ip-address.html) (for 11.04, but I think it will still be correct)
[http://ubuntuforums.org/showthread.php?t=1985170](http://ubuntuforums.org/showthread.php?t=1985170)

---

