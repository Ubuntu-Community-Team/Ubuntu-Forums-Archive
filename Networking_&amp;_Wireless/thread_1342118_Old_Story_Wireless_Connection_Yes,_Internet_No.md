---
title: "Old Story: Wireless Connection Yes, Internet No"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by saroman0414 on 2009-11-30
Three months ago my daughter went off to college with a new computer.  I zapped her old system and successfully installed Ubuntu 9.04 from a CD.  Everything worked fine including all the peripherals and the wireless internet connection.  I was able to download and update applications without a hitch.  Great system and so much cleaner and quicker than Win XP on the old machine.  Then the system was shut down and lay idle for three months.

When I fired it up a couple of days ago, all seemed normal except I could no longer access the internet even though the wireless network icon showed four or five bars.  I first discovered the problem when I tried to update though Update Manager and noticed that 22 identified files could not be fetched.  Neither Firefox, Skype nor Goodgle Earth can connect.

The router is a Linksys WRT54G router that connects to the computer through a Linksys WUSB54G USB network adapter.  The router serves three other computers without a problem, including one using the same model network adapter.

I don't have much experience with Ubuntu, but this is some of the information I have been able to generate.

Active Network Connections-
Interface: 802.11 WiFi (wlan0)
Hardware Address: 00:18:39:0C:26:2B
Driver: rt2500usb
Speed: 54 Mb/s
Security: WPA/WPA2
IP Address: 192.168.1.101
Broadcast Address: 198.162.1.255
Subnet Mask: 255.255.255.0
Default Route: 192.168.1.1
Primary DNS: 192.168.1.1

Editing Auto roman (where "roman" is the SSID)-
Connect automatically: checked
Wireless tab-
SSID: roman
Mode: Infrastructure
BSID: "blank"
MAC address: "blank"
MTU: automatic

IPv4 Settings tab-
Method: Automatic (DHCP)
Available to all users: checked

Pinging localhost affords an endless series of increasing icmp_seq numbers, all 64 bytes from localhost (127.0.0.1) with an average time of 0.07 ms.  I can also connect to the router (192.168.1.1) through Firefox but I can not ping external sites using their url.

I tried a few of the recommendations found in other threads, but nothing seems to do the job.  I am perplexed because everything was great until I shut down the system for three months and then started it up again.  I appreciate any assistance and would be happy to provide additional information as requested.

---

### Post by saroman0414 on 2009-11-30
As a followup to my original post, this is the output of my ifconfig command:

eth0      
Link encap:Ethernet HWaddr 00:0c:6e:5b:b4:6e          
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000           
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)          
Interrupt:19 Base address:0x9800 

lo        
Link encap:Local Loopback        
inet addr:127.0.0.1 Mask:255.0.0.0          
inet6 addr: ::1/128 Scope:Host          
UP LOOPBACK RUNNING MTU:16436 Metric:1          
RX packets:3631 errors:0 dropped:0 overruns:0 frame:0          
TX packets:3631 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:0           
RX bytes:301751 (301.7 KB) TX bytes:301751 (301.7 KB)

wlan0     
Link encap:Ethernet HWaddr 00:18:39:0c:26:2b           
inet addr:192.168.1.101 Bcast:192.168.1.255 Mask:255.255.255.0          
inet6 addr: fe80::218:39ff:fe0c:262b/64 Scope:Link          
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1          
RX packets:11177 errors:0 dropped:0 overruns:0 frame:0          
TX packets:765 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000           
RX bytes:4158009 (4.1 MB) TX bytes:77488 (77.4 KB)

wmaster0  
Link encap:UNSPEC HWaddr 00-18-39-0C-26-2B-36-32-00-00-00-00-00-00-00-00  
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000           
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

