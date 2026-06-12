---
title: "Australian mobile broadband problems (Vodafone network)"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by bmett on 2009-07-09
Hi everyone,  For a couple of days now, I try to get my HUAWEI USB Modem to work with Ubuntu Jaunty. I have no problems connecting via XP.  I search the web for some help, but it seems that not many people have problems with it.  Ubuntu recognizes the device corretly and I can set up a mobile boradband connection via the network manager. But for some reason I cant connected. If I try to connect via the created connection with the network manager, the message pops up, that the connection is disconnected.  Anybody out there who can give me some hints? Are there any special settings I have to put in?  Thanks  Björn

---

### Post by superprash2003 on 2009-07-10
post output of ifconfig . are you able to access the modem from your browser?

---

### Post by AndyCee on 2009-07-10
I was able to get the Optus one working off the bat - but the 3 usb modem took some serious tweaking.

What is the value of the "Carrier APN" in network manager? Is it set to "vfinternet.au"? (something I came across - can't hurt to try).

---

### Post by bmett on 2009-07-13
yep Carrier APN is set to vfinternet.au.  ifconfig doesnt show any unusual, but I will post it in a couple of minutes.  Cheers Björn

---

### Post by bmett on 2009-07-13
[FONT=Arial]alrighty here is what ifconfig and lsusb has to say:

mett@bmett:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mett@bmett:~$ ifconfig -a
eth1      Link encap:Ethernet  Hardware Adresse 00:13:77:02:59:48  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

eth2      Link encap:Ethernet  Hardware Adresse 00:12:f0:ea:74:24  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Basisadresse:0xc000 Speicher:c8010000-c8010fff 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:8160 (8.1 KB)  TX bytes:8160 (8.1 KB)

pan0      Link encap:Ethernet  Hardware Adresse 0a:82:a0:f9:66:c5  
          BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I cant access the USB Modem like I can under XP.

ANd dont be puzzled by the language, its a german ubuntu ;)


Anybody any Idea?

Cheers
BJörn

[/FONT]

---

### Post by bmett on 2009-07-15
Anyone out there who can help?
Cheers
Björn

---

