---
title: "curious - eth0 showing as disabled in panel"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by stardotstar on 2009-07-26
Hi guys, 

I am a bit perplexed that having done some fiddling to create a bridge for eth0 and ultimately removing it I am left with a panel applet that shows my wired network as disabled and yet it clearly is not.

I may have broken a hook that tells the system which applet/config prog rules the network when upgrading a mythbuntu to full desktop mode.

```
root@myth:/media# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:ac:78:93  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:feac:7893/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22183370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11086942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2404496158 (2.4 GB)  TX bytes:760546740 (760.5 MB)
          Interrupt:250 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75427 (75.4 KB)  TX bytes:75427 (75.4 KB)

root@myth:/media# 
root@myth:/media# host google.com
google.com has address 74.125.127.100
google.com has address 74.125.45.100
google.com has address 74.125.67.100
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
root@myth:/media# 

```
Even when I try to create/add an interface to the applet and put the name and mac addy in nothing happens...

my /etc/network/interfaces is very basic:
```
stardotstar@myth:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```

any help or insight appreciated guys!
\\'

---

### Post by Iowan on 2009-07-26
Possibly  Network Manager is claiming it is disabled because eth0 is defined in */etc/network/interfaces*. You could try commenting out the definition for eth0, and restarting.

---

