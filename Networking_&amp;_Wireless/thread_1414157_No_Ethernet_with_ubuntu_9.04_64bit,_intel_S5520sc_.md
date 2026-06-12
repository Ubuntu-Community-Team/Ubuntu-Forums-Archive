---
title: "No Ethernet with ubuntu 9.04 64bit, intel S5520sc motherboard"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by pederworning on 2010-02-23
Hi Ubuntu forum,

I have just installed ubunto 9.04 64 bit on an Xeon server with an intel S5520Sc motherboard, but I get not connection through the onboard ethernet device. Where can I find network drivers for this motherboard. I have tried several of he recommondations on the list.
 
Can you help me getting connected?

Thanks Peder

PS here follows some of the commands I have tried to get information and solv the problem

nm-tool:

NetWorkManager Tool
State: Disconnected
 
lspci -v | grep "Ethernet" -A 1:
01:00.0 Ethernet controller: Intel Corporation Device 10aa (rev 02)
            Subsystem: Intel Corporation Device 0000
---
01:00.1 Ethernet controller: Intel Corporation Device 10aa (rev 02)
            Subsystem: Intel Corporation Device 0000

ethool -i eth0:
Cannot get driver information: No such device

pppoefconf:
Sorry, I scanned 1 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem caples. Another reason
for the scan failure may also be another running pppoe
process which controls the modem.

ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3424 (3.4 KB)  TX bytes:3424 (3.4 KB)

---

### Post by chili555 on 2010-02-23
Let's see:```
lspci -[COLOR="Red"]nn[/COLOR] | grep Ethernet
```Thanks.

---

### Post by pederworning on 2010-02-25
lspci -[COLOR=Red]nn[/COLOR] | grep Ethernet 
gives the same as lspci -v | grep "Ethernet" -A 1:



lspci -v | grep "Ethernet" -A 1:
01:00.0 Ethernet controller: Intel Corporation Device 10aa (rev 02)
            Subsystem: Intel Corporation Device 0000
---
01:00.1 Ethernet controller: Intel Corporation Device 10aa (rev 02)
            Subsystem: Intel Corporation Device 0000

Thanks 
Peder

---

### Post by chili555 on 2010-02-25
> lspci -nn | grep Ethernet
gives the same as lspci -v | grep "Ethernet" -A 1:
Not on my system. The switch -nn shows pci ids, thus:> $ lspci -nn | grep Ethernet
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [[COLOR="Red"]8086:109a[/COLOR]]May we please see your pci ids?

---

### Post by pederworning on 2010-03-01
> **chili555 said:**
> Not on my system. The switch -nn shows pci ids, thus:May we please see your pci ids?
My machine doesn't show any pci ids no matter what I do, so I have solved the problem by buying a cheap NI-707512 PCI network card and that worked immediately, without installing any drivers. Thanks for your help.
 
PederWorning

---

