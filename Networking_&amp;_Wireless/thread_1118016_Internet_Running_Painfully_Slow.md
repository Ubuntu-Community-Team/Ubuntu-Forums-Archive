---
title: "Internet Running Painfully Slow"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by Danger Fox on 2009-04-06
I am new to Ubuntu so there is probably a simple solution to this, but my wireless connection is extremely slow in Ubuntu. Whenever I am in Windows it runs very fast and perfectly fine, but in Ubuntu it sometimes takes up to a minute to load a page. It is a Linksys PCI wireless networking card if that helps any and I can supply any additional data needed. Any help is appreciated.

---

### Post by khelben1979 on 2009-04-06
What is the exact model of the Linksys PCI card?

---

### Post by sn0m on 2009-04-06
I'm having the same problem. My wireless is ok as I can transfer files between my computer's but wondering whether it has to do with the way firefox handles some files. Eg I can't open my gmail account, anything to do with executing secure scripts.....

---

### Post by Danger Fox on 2009-04-06
> **khelben1979 said:**
> What is the exact model of the Linksys PCI card?

It is WMP54G

---

### Post by Danger Fox on 2009-04-06
Bump

---

### Post by khelben1979 on 2009-04-07
You can start to troubleshoot using a guide from [this thread]("http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys+WMP54G"). Maybe it's badly configured?

---

### Post by superprash2003 on 2009-04-07
also post output of **ifconfig** from the terminal.. it could also be your DNS servers.. try switching to opendns servers .. their ips are 208.67.222.222 and 208.67.220.220

---

### Post by Danger Fox on 2009-04-08
Here are the results from the ifconfig if that helps:

eth0      Link encap:Ethernet  HWaddr 00:50:8d:9d:e3:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:50:8d:9d:e3:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6180029 (6.1 MB)  TX bytes:6180029 (6.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:90:85:f8  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe90:85f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7930695 (7.9 MB)  TX bytes:1010020 (1.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-90-85-F8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2009-04-10
your MTU values look good..try the opendns servers..

[http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Danger Fox on 2009-04-11
Ok, connecting to the opendns severs did help alot. Another problem I have is that my wireless signal can get very weak at times. I did not have this problem in Windows and was wondering if downloading any drivers would help this?

---

### Post by superprash2003 on 2009-04-11
post output of **lshw -C network**

---

### Post by Danger Fox on 2009-04-11
*-network               
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:90:85:f8
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.101 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:ce:51:59:0e:e7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by superprash2003 on 2009-04-13
[http://ubuntuforums.org/showthread.php?t=369100](http://ubuntuforums.org/showthread.php?t=369100)

---

