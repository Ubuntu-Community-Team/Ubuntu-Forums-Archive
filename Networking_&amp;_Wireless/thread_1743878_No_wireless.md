---
title: "No wireless"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by Z06Gal on 2011-04-29
I am running 10.10 and installed today afer receiving a new dell xps laptop.  When I go to additional drivers, none show up for wireless.  Here is the output of lspci -v:


Network controller: Intel Corporation Device 008a (rev 34)
Subsystem: Intel Corporation Device 5325
Flags: fast devsel, IRQ 17
Memory at f3b00000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel modules: iwlagn


I have been trying to figure this out for hours so I thought maybe someone here would have a clue.  Thanks


Robin;)

---

### Post by Z06Gal on 2011-04-29
Anybody??

---

### Post by Z06Gal on 2011-04-29
Just ran inxi -n and got this:



inxi -N
Network:   Card-1 Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller driver r8169
           Card-2 Intel Device 008a
robin@robin-Dell-System-XPS-L702X ~ $ I. scanning WIFI PCI devices...
I.: command not found
robin@robin-Dell-System-XPS-L702X ~ $   -- Intel Corporation Device 008a (rev 34)
bash: syntax error near unexpected token `('
robin@robin-Dell-System-XPS-L702X ~ $       ==> PCI ID = 8086:008a (rev 34)
bash: syntax error near unexpected token `('
robin@robin-Dell-System-XPS-L702X ~ $ -------------------------
-------------------------: command not found
robin@robin-Dell-System-XPS-L702X ~ $ * II. querying ndiswrapper...
Desktop: command not found
robin@robin-Dell-System-XPS-L702X ~ $ -------------------------
-------------------------: command not found
robin@robin-Dell-System-XPS-L702X ~ $ * III. querying iwconfig...
Desktop: command not found
robin@robin-Dell-System-XPS-L702X ~ $ lo        no wireless extensions.
lo: command not found
robin@robin-Dell-System-XPS-L702X ~ $ 
robin@robin-Dell-System-XPS-L702X ~ $ eth0      no wireless extensions.
eth0: command not found
robin@robin-Dell-System-XPS-L702X ~ $

---

