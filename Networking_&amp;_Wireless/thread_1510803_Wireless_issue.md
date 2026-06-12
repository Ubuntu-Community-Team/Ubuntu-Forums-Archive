---
title: "Wireless issue"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by lunatia138 on 2010-06-16
OK, so I am rather new to Linux and just installed Ubuntu 10.04 onto my desktop and am having problems getting my wireless card to work.  I am currently using a Linksys Wireless-G PCI adapter, Model No. :WMP54GS  ver 1.1.  So if there is anyone out there that can and is willing to help me out with my problem I would be very grateful.

---

### Post by mikewhatever on 2010-06-16
OK, and what exactly is the problem? Can you post the outputs of ifconfig and iwconfig.

---

### Post by lunatia138 on 2010-06-16
~$ ifconfig
eth0[INDENT]Link encap:Ethernet HWaddr 00:1f:c6:ba02:f0
UP BROADCAST MUTLICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:26 Base address:0x2000
[/INDENT][LEFT]lo[INDENT]Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:108 errors:0 dropped:0 overruns:0 frame:0
TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:8336 (8.3 KB)  TX bytes:8336 (8.3 KB)
[/INDENT]~$ iwconfig
lo[INDENT]no wireless extensions.
[/INDENT]eth0[INDENT]no wireless extensions.
[/INDENT]wlan0[INDENT]IEEE 802.11bg  ESSID/off/any
Mode:Managed Access Point: Not-Associated   Tx-Power=0 dBm
Retry long limits:7   RTS thr/off   Fragment thr/off
Power Management/off
[/INDENT][/LEFT]

---

### Post by mikewhatever on 2010-06-17
Interesting. Can you also post the output of **lspci | grep -i network**.
Check System-Admin->Hardware Drivers just in case.

---

### Post by lunatia138 on 2010-06-17
~$ lspci | grep -i network
03:05.0 [COLOR=Red]Network[/COLOR] controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by mikewhatever on 2010-06-17
Thank you for your cooperation. Generally speaking, Broadcom card are rather well supported in Ubuntu, after the driver is enaibled through the Hardware Drivers utility. Connect wiredly for a minute and let it do its job.

---

### Post by bkratz on 2010-06-17
> **lunatia138 said:**
> ~$ lspci | grep -i network
03:05.0 [COLOR=Red]Network[/COLOR] controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)




See posts 9-13 of this thread--same device success

[http://ubuntuforums.org/showthread.php?t=1509557](http://ubuntuforums.org/showthread.php?t=1509557)


good luck

---

### Post by lunatia138 on 2010-06-24
Thanks for the help mikewhatever, I will try that last one whenever I get the chance to get another cable long enough to reach my desktop.

bkratz, I did what you said and used posts 9-13, and all I got was: "sh: Can't open b43.sh". So if there is any other ideas I am willing to try them.

---

