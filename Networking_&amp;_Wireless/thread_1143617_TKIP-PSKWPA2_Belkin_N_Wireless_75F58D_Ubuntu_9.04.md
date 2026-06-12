---
title: "TKIP-PSK/WPA2 Belkin N Wireless 75F58D Ubuntu 9.04"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by DarkFoxFurre on 2009-04-30
Hey guys,

I'm using Ubuntu 9.04.  I installed it over Slackware because of issues with SCIM.  I'm in a house with several other housemates, and we have a Belkin N Wireless router.  For the convenience of the other housemates, the WPA2 authentication is used, which means TKIP-PSK. I'm using a Dell Latitude D520 with the ipw3945 wifi chip.

The issue I'm having is stabilty.  I can't get a stable connection what-so-ever.  I've toyed around with the wireless settings, installed other network managers besides nm (wpagui, wicd). I've even set up the connection using the basic ways of ifconfig, iwconfig, and wpa_supplicant through the console.  All of which result in consistant dropping of connection.  The part I can't understand is that according to the system, I'm receiving a strong signal (Between -55dBm -65dBm)..  I still have a working IP adress and the proper DNS selected. If I disconnect and reconnect to the network, I will get a valid connection for anywhere between five seconds to half an hour.

I have used the laptop with Windows and Slackware on this connection and have had a consistantly stable connection.  The other housemates also have a stable connection to the router and Internet while I'm having constant drop offs.  I've even taken the laptop to another network area and had a stable (Non TKIP-PSK/WPA2) connection for several hours.The laptop itself has not changed locations, so the problem must be in Ubuntu.

---

### Post by conorturton on 2009-04-30
network manager expects AES on WPA2, not TKIP. TKIP is used to maintain backwards compatibility with some devices.

---

### Post by DarkFoxFurre on 2009-04-30
That has nothing to do with my issue.  If NM was unable to handle TKIP, then I wouldn't be able to connect to the Internet at all.  I can connect to the Internet, but my connection is dropped frequently.  

To eleminate the possibility that TKIP is the problem, I've even switched the router to AES and I still have the exact same issue.

It also appears as though the router has been picking up some weird traffic from my computer (My computer is associated with 192.168.2.4):
> [FONT=Verdana][COLOR=#000000]04/30/2009  10:43:08 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood Stop**  (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 46361->> 123.243.139.145, 17309 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 44213->> 121.45.180.35, 41565 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 35101->> 98.175.172.46, 42308 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 52532->> 98.16.176.42, 34595 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 59887->> 97.116.93.60, 33946 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 35582->> 86.143.126.17, 30806 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 54395->> 86.15.94.204, 56378 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 35287->> 85.196.214.31, 53747 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 41071->> 85.75.227.236, 49078 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 48867->> 85.69.85.193, 15494 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 49367->> 82.36.144.106, 42476 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 42053->> 81.107.162.131, 63763 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:07 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

192.168.2.4, 40525->> 67.155.180.20, 22965 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:06 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN Flood** 

130.13.170.191, 61749->> 72.209.165.173, 57790 (from WAN Inbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:05 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN 

Flood** 192.168.2.4, 49089->> 41.235.164.67, 58041 (from WAN Outbound)[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]04/30/2009  10:43:03 [/COLOR][/FONT][FONT=Verdana][COLOR=#000000]**SYN 

Flood** 192.168.2.4, 42519->> 118.94.141.61, 50934 (from WAN Outbound)[/COLOR][/FONT]

---

### Post by DarkFoxFurre on 2009-05-04
SOLVED:

Turns out the Belkin router was the issue.  There's a Quality of Service (QoS) option in the Belkin router that appears to have been dropping my SYN packets.  This causes the laptop's programs to just sit and wait for an ACK.  So the programs still think they're connected when they really aren't.  Luckily Belkin put in the option to disable this QoS.  By disabling the QoS, I now have a stable connection with the network-manager.

Thanks,
Dark Fox

---

### Post by ziva on 2009-05-26
I've registered just to thank you
I had the same problem
and now it's solved
thanks again 
a lot

---

### Post by bobnutfield on 2009-05-26
I read this thread with interest while searching for a solution to exactly the same issue, intermttent disconnects.  I, too, have a Belkin router, but it is a 54g (not N) and I have no such QoS settings on this router.  

In my case, I found out that Jaunty enables IPV6 inside the kernel and that was the issue.  The fix for this was not so easy and required a new kernel to disable the IPV6.

---

### Post by Mars73 on 2009-08-24
I have a Belkin Pre-N router which has served me well for over 4 years now.
Upstairs I have a desktop with a Belkin G+mimo usb adapter and while it was working okay I wasn't too fond of the speeds.
I also had a Belkin Pre-N card (a pcmcia which goes into a pci card) and inserted that into my desktop.
Sadly the kernel doesn't have any driver for the pre-n card (AGN100) so I had to resort to ndiswrapper.
Installation of ndiswrapper was suprisingly easy and got me a (unstable) connection.
After hours and hours of trying things (moving the router, changing channels etc etc) I now have a working and stable connection for a few hours. Turning off QoS seemed to have worked. It seems ndiswrapper and QoS don't go together, at least not for my Pre-n card.
For now I'm a happy man (watching dvd streams wirelessly), will update here if anything changes.

---

