---
title: "Wireless not working (yes I know, join the club)"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by ishaan123 on 2009-06-17
Here goes...
I am using the 64 bit Ubuntu version 8.04 on a Dell Latitude D830 laptop, and a SURFboard Cable Modem SB4200. I did 9.04 and had the same problems, and also it was slow and the ethernet did not work, so I downgraded. Its fast now, and ethernet works, but still no wireless. 

This is what I see on my screen: One of my wireless networks, a 24g, shows up.  Another, faster one does not. When I try to connect to the 24g network, my network icon on the top left becomes two gray circles with a blue object moving in a circular motion. Then, I get a dialogue box requesting a password or encryption key. I set the security to "WPA Personal" and enter the password. The icon remains the same and there is no connection. In a few seconds, the dialogue box pops up again, and again, and again. Mousing over the icon brings up the message: "waiting for Network Key for the wireless network (name of network)". I know my password is not wrong. 

Iowan had me run the following commands when testing this with 9.04. I have run them again. These commands have been run with the ethernet unplugged, and the wireless "waiting for the network key".

ishaan@ishaan-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:ba:9d:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:78868 errors:6 dropped:0 overruns:0 frame:83
          TX packets:59543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:98745250 (94.1 MB)  TX bytes:8082718 (7.7 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62164 (60.7 KB)  TX bytes:62164 (60.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:59:3f:11  
          inet6 addr: fe80::21d:e0ff:fe59:3f11/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:717776 (700.9 KB)  TX bytes:68868 (67.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-59-3F-11-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
-------------------
ishaan@ishaan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:59:3f:11
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:ba:9d:ea
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5755m-v3.29 latency=0 module=tg3 multicast=yes

thanks in advance
-Ishaan

--

---

### Post by ishaan123 on 2009-06-18
ok, I have no idea what is going on, but it suddenly began working for no reason about 10 minutes ago, after almost 2 days of not working. I didn't even reboot...i guess everything I wrote can be disregarded, although I would like to know out of curiosity what is going on.

---

### Post by RedSingularity on 2009-06-18
Were you using the correct WEP protocol?  I made that mistake a few times when i started ubuntu.

---

### Post by ishaan123 on 2009-06-24
the term sounds familiar, but im not sure what that is, so I don't think so....

---

