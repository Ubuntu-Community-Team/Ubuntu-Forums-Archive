---
title: "Problem to connet to internet"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by marobg on 2009-12-18
Hi , the members of this nice ubuntu forums. I have a great problem that i couldn't solve. I have already installed Ubuntu 9.10. i can't connect to the internet. I use the ADSL inernet using the wired telephone with a modem ZTE ZXDSL 831 Series  . I have done all my best  to find its driver and  to perform its configuration . I'd like your help PLEASE.

---

### Post by lidex on 2009-12-18
Can you post the output of these commands? Enter them in a terminal: "Accessories>Terminal". One line at a time then press enter after each. Copy and paste the text from terminal into a post and then highlight that text and click the "#" symbol in the toolbar.

```
ifconfig
```
```
lspci | grep -e Ethernet 
```

---

### Post by jeffrey77 on 2009-12-18
I have the same issue:

jeffrey@Ubuntu:~$ [COLOR=Red]ifconfig[/COLOR]
eth1      Link encap:Ethernet  HWaddr 00:15:f2:53:c2:ed
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe53:c2ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:42133 (42.1 KB)  TX bytes:12489 (12.4 KB)
          Interrupt:23 Base address:0x4400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

jeffrey@Ubuntu:~$ [COLOR=Red]lspci | grep -e Ethernet[/COLOR]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
jeffrey@Ubuntu:~$

thanks for help

---

