---
title: "No internet through Belkin router."
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by jameswood on 2009-04-15
Hi



I recently installed Xubuntu 8.10 (Intrepid Ibex) on my Toshiba Satellite S1410 -304. Fairly old notebook, but I only sensed that when it was running on Windows. With Linux it's on cocaine, so good news there. I'm new to Linux, so I am not familiar with commands. If you want me to get something detail please write the commands I'll do my best. I have checked on this topic before I did what was writting, but no result.

My problem is that when I connect the notebook to the internet it is still offline. I have a Belkin router connected to the &#8221;net oulet&#8221; (I don't know the real term) and I have a Windows XP stationary and the Toshiba connected to the router. However the Toshiba is the only one that cant go online. I'm sure it has something to do with the router since when I connect the cable directly from the &#8221;net outlet&#8221; to the Toshiba will go online.

So I hope it gives you a picture what my problem is.

What do I have to do to solve this? :)




With kind regards 


James Woods

---

### Post by RedSingularity on 2009-04-15
Are you trying to connect wirelessly?

---

### Post by jameswood on 2009-04-16
Hi Shadow

No, I'm trying to connect wired.

---

### Post by chili555 on 2009-04-16
> when I connect the cable directly from the ”net outlet” to the Toshiba will go online.Before we proceed, let's recheck our connections. On the back of your Belkin router, there are five ethernet jacks. One is labelled 'WAN' and four are labelled 'LAN'. Your cable modem should be connected to 'WAN'. All the computers in the house should be connected to 'LAN' jacks or connected wirelessly. Before we go to other diagnostic steps, please check carefully that these connections are correct.

---

### Post by jameswood on 2009-04-16
Thanks for responding Chili ;)


Well the WAN is connected to cablemodem while the computers are connected to the LAN-ports.

---

### Post by chili555 on 2009-04-16
> the WAN is connected to cablemodem while the computers are connected to the LAN-ports.Excellent. Now open up a terminal and do this command and let us know the result:```
ifconfig
```May I assume you are using Network Manager, which is installed by default? When you click the icon, do you see the option to activate your wired connection?

---

### Post by jameswood on 2009-04-17
Sorry for the delay.


Well I wrote the "ifconfig" command and this is what I get.

lanka@Toshiba:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:0d:4b:5f:02  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1491 (1.4 KB)  TX bytes:1844 (1.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:800 (800.0 B)  TX bytes:800 (800.0 B)



Well I looked for the Network Manager, but I don't see anything like that. Perhaps it's because it on Xfce? However you know that icon on the bar above to the right I can right click on that and choose edit connections. It opens up a dialog box called "Network Connections" with 5 tabs. Wired, Wireless, Mobile Broadband, VPN & DSL.


Hope it helps ;)

---

### Post by chili555 on 2009-04-17
> It opens up a dialog box called "Network Connections" with 5 tabs. Wired, Wireless, Mobile Broadband, VPN & DSL.Can you select Wired and ask it to connect automatically? What are the options under the Wired tab?

---

### Post by abn91c on 2009-04-17
post the output of
**sudo dhclient eth0**

---

### Post by jameswood on 2009-04-18
To Shadow.

Under the Wired tab to the right it has 3 buttons; Add, Edit & Delete
To the left it has the "list" of the different connections. In this case there only "Auto eth0" and a bit to the right it says "never"


When I click on edit it opens up a dialog box called "Editing Auto eth0"

It's checked to "Connect automatically" and System settings.

Underneath the checkboxes there are 3 tabs; Wired, 802.1x Security & IPv4 Settings.


Wired tab:

Mac address: 00:08:0D:4B:5F:02
MTU: automatic


802.1x Security tab:

Well the "Use 802.1x security for this connection" checkbox is unchecked so the rest of the forms are greyed out.


IPv4 Settings:

Method: (It has a drop sheet with multiple options) Automatic (DHCP), Automatic (DHCP) addresses only, Manual, Link-Local only & Shared to other computers

---

### Post by jameswood on 2009-04-18
> **abn91c said:**
> post the output of
**sudo dhclient eth0**

This is what I get.

lanka@Toshiba:~$ sudo dhclient eth0
[sudo] password for lanka: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No buffer space available
Listening on LPF/eth0/00:08:0d:4b:5f:02
Sending on   LPF/eth0/00:08:0d:4b:5f:02
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

