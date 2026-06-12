---
title: "eth0 printer problem"
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by gdlx on 2006-01-17
New to Linux. Desperatly need help.
Running Ubuntu 5.10 AMD64 on a laptop (dual boot with XP home)
connected to lan thru a linksys EZXS55W 5 port switch

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

eth0      Link encap:Ethernet  HWaddr 00:03:25:0D:99:F0
          inet addr:192.168.0.159  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe0d:99f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:626 errors:0 dropped:0 overruns:0 frame:0
          TX packets:656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:617225 (602.7 KiB)  TX bytes:83140 (81.1 KiB)
          Interrupt:23 Base address:0x1800

HP business jet 1200dn printer connected to switch

My desktop is running winXP pro
connected to the switch
Internet connection is from desktop to ISDN thru the serial port.

XP prints from desktop or laptop

I can access the printer from Ubuntu using Firefox ([http://192.168.0.161](http://192.168.0.161))
I have set the printer ip address as static
When I try to print from linux there is no response from the printer and when I look at the printer properties there is a message that the ip address (192.168.0.161) is busy and cups will try again in 30 seconds.

---

### Post by darth_vector on 2006-01-18
try setting up your printer again and using hp direct jet. go to system->administration->printing and select "add a printer". select network printer and choose HP DirectJet.

---

### Post by gdlx on 2006-01-18
THANK YOU!!!! It WORKS!
I have struggled with this for weeks.

Thanks again

---

