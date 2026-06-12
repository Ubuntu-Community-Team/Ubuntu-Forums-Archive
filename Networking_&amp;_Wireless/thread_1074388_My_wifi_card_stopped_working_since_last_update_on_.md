---
title: "My wifi card stopped working since last update on 18th feb"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by asheokand on 2009-02-19
Hi guys, i am a really newbie on ubuntu and loved it  until yesterday.I updaated the system and after the reboot, my wifi card has stopped working. I have duaal boot with ubuntu and windows xp  sp3. My wifi card is Broadcom internal wifi for compaq presario f500. And the problem is its not working in xp either. Its not detected in either of them. All i see now is a yelloww light. should i buy aa new one or how would i know its working???:(

---

### Post by emelce on 2009-02-19
i have the same problem with Intel PRO/Wireless 3945ABG using ubuntu 9.04. after the update of 18th feb. wireless doesn't work anymore... it's not that bad because I use this computer just for testing, but still I like to know how to fix it.

---

### Post by superprash2003 on 2009-02-19
you dont have to buy a new one!!go to the terminal and post output of the following commands
1)ifconfig
2)iwconfig
3)iwlist scanning

---

### Post by asheokand on 2009-02-19
thats what i got in the terminal............plz help


alpha@LMG:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:68:8c:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

alpha@LMG:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

alpha@LMG:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

alpha@LMG:~$

---

### Post by philosophia on 2009-02-19
I have the same problem with my Broadcom 4036 card - I started a separate thread for it.

---

### Post by SmileyChris on 2009-02-19
Bah! I've got the same problem but didn't know until now because I shut the lappy down for the first time last night (same iwconfig output)

EDIT: Guess I spoke too soon. Did another full restart and the problem resolved itself. Still leaves me feeling a bit uneasy, but for me at least, the problem is resolved.

---

### Post by superprash2003 on 2009-02-20
follow this to get your broadcom back [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

