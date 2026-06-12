---
title: "weird network behaviour"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by Sum Guy on 2009-04-19
after much labor my ubuntu installation can connect to my dsl g604t router, with one catch. for some reason, it will only connect over wireless once a wired connection has been established. after this, the wire can be removed and the connection will be sustained. how can i use this information to remove the requirement of connecting through ethernet first?

---

### Post by superprash2003 on 2009-04-19
remove wired connection..restart machine.. then post output of following commands
1)ifconfig
2)iwconfig

---

### Post by Sum Guy on 2009-04-20
**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:13:a9:8c:07:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:4092 (4.0 KB)  TX bytes:4092 (4.0 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:18:de:9a:43:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-9A-43-4D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

**iwconfig**

lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11abg  ESSID:"home"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 

Additionally, the computer works fine on the XP install, and the security is MAC address exclusion as ubuntu struggles with this routers wep encryption

---

### Post by Sum Guy on 2009-04-21
i do kind of need a fix here guys. thanks in advance

---

### Post by superprash2003 on 2009-04-22
your wlan0 isnt getting an ip.. type **sudo dhclient wlan0** in your terminal and then try

---

### Post by Sum Guy on 2009-04-24
the command output the following


Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:18:de:9a:43:4d 
Sending on   LPF/wlan0/00:18:de:9a:43:4d 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 


and the network remained unconnected

---

### Post by Sum Guy on 2009-04-26
is there anything else i can do to fix this, or should i just scrap the router?

---

### Post by superprash2003 on 2009-05-08
it still isnt getting an ip address.. try static ip [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by rules on 2009-05-08
Do you mean it doesn't see your wireless connection (SSID) or do you mean it sees the connection but just can't get connected/assigned an IP?

I have the same router and have found that although wireless is active when I boot up my laptop, it does not see any wireless connections. I have to click on the network icon and select connect to other wireless network, type in the SSID and tell it to connect. It fails first because I didn't enter a password, but this causes it to see wireless networks and a couple of seconds later keyring will kick into action asking me for the password and it will then establish the connection. In 8.10 they seem to have solved this problem because as soon as you boot up and activate the wireless, it will automatically detect networks in range (just a pity they couldn't get the ATI screen drivers right :P)

---

### Post by Sum Guy on 2009-05-08
setting a static address this way killed network manager altogether.

the problem is that i can't seem to get an ip address. network manager just repeatedly fails to connect unless i get an ip address from ethernet first

---

### Post by Sum Guy on 2009-05-16
Well, I tried a different router, and that gave me as many problems so I returned it, but trying to get it to work I tried Wicd after seeing someone was having similar problems with the card in the computer (3945ABG) I also upgraded to 9.04. Now the computer can't see the network unless I'm within 5 metres of the network, are already connected, or have just disconnected, in the last situation I can't reconnect. Note that in the first situation, with a static ip on Wicd, I can connect without the previously needed wire. Could this be fixed with a high gain antenna? Or do I need to update the driver?

---

