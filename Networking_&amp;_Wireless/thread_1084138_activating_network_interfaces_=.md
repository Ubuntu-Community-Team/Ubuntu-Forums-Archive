---
title: "activating network interfaces =\"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by ewbewtew on 2009-03-01
ok, so i'm a piping hot new ubuntu user. installed yesterday. 
i have breezy on an old dell inspiron 8000. 
i have a 2WIRE at&t modem and a belkin wireless g f5d7010 card

i have read through [this thread](http://ubuntuforums.org/showthread.php?t=272813)
and the trouble starts at 16. the problem seems to be that i cannot activate my wlan0 or eth0 interfaces. the ethernet card in this computer may be broken so i'm focusing on the wireless. 
i have also read through [this thread](http://ubuntuforums.org/archive/index.php/t-85811.html) with no luck :confused: 

here are a few common terminal outputs that i think may help.
but i am ready and eager to resolve this issue and willing to take direction  :D
```
root@ubuntu-disc:~# ndiswrapper -l
Installed ndis drivers:
net5211 driver present, hardware present

root@ubuntu-disc:~# ifconfig
lo        
Link encap:Local Loopback          
inet addr:127.0.0.1  Mask:255.0.0.0          
inet6 addr: ::1/128 Scope:Host          
UP LOOPBACK RUNNING  MTU:16436  Metric:1          
RX packets:2212 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:2212 errors:0 dropped:0 overruns:0 carrier:0
         
 collisions:0 txqueuelen:0    
RX bytes:199305 (194.6 KiB)  
TX bytes:199305 (194.6 KiB)

root@ubuntu-disc:~# ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 0

Internet Systems Consortium DHCP Client V3.0.2

opyright 2004 Internet Systems Consortium.
All rights reserved.

For info, please visit http://www.isc.org/products/DHCP

sit0: 
unknown hardware address type 776
SIOCSIFADDR: 
No such device
eth0: ERROR while getting interface flags: 
No such device
eth0: ERROR while getting interface flags: 
No such device
sit0: unknown hardware address type 776

Bind socket to interface: No such device

Failed to bring up eth0.

root@ubuntu-disc:~# ifup wlan0

Ignoring unknown interface wlan0=wlan0.
root@ubuntu-disc:~#

```
i think i have properly blacklisted the default drivers.
and i added auto eth0 to interfaces with no luck. 
but like i said the ethernet card is most likely toast 
and i need to focus on the wireless card

---

### Post by Iowan on 2009-03-01
I have a server running Breezy... I need to upgrade it.  Breezy is quite "long in the tooth" - support ended a while ago. Still...
Check **lshw -C network**

---

### Post by ewbewtew on 2009-03-02
sorry i took so long. here it is 
```
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@07:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:11000000-1100ffff irq:10

```

---

