---
title: "Linksys EG1032 PCI gigabit adapter - driver?"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by Tamale on 2006-01-15
I can't for the life of me figure out what exactly I need to do to get my linksys EG1032 gigabit card working..  

root:/# lspci | grep Eth
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:0d.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
root:/# uname -r
2.6.12-8-386
root:/# uname -a
Linux mrserver 2.6.12-8-386 #1 Tue Aug 30 22:41:30 BST 2005 i686 GNU/Linux
root@mrserver:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2A:38:30:5F
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fe38:305f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10229453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5351326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1920361346 (1.7 GiB)  TX bytes:337541494 (321.9 MiB)
          Interrupt:19 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4892094 (4.6 MiB)  TX bytes:4892094 (4.6 MiB)

My onboard 10/100 seems to be working ok - (it's eth0) - but the whole point of my new setup is to have a gigabit-enabled file server....  

Under ubuntu's device manager there's a device that just says "Gigabit Network Adapter" and there's quite a bit of detail on it under the advanced tab, but under the device tab the 'Device Type' and Capabilities are both 'Unknown', and the status is "Status"... this thing definitely doesn't have the right driver loaded for it yet...

I've found a couple interesting pages on the card, but I don't have a clue what the first step I should do is... I don't know anything about installing modules or updating my kernel or any of that stuff, so any help will have to be pretty 'dumbed down'  :)

here are a couple pages I've found regarding my card:
[http://www.linuxcompatible.org/Linksys_Gigabit_Network_Adapter_EG1032_v3_c12430.html](http://www.linuxcompatible.org/Linksys_Gigabit_Network_Adapter_EG1032_v3_c12430.html)
[http://www.neowin.net/forum/index.php?showtopic=165245&st=0](http://www.neowin.net/forum/index.php?showtopic=165245&st=0)

please assist!  I've been whining in the #ubuntu room for a couple days now and no one there seems to want / know how to help...  :(

---

### Post by Tamale on 2006-01-16
bump?

---

