---
title: "Firefox won't"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by hayre on 2009-01-16
UBUNTU 8.04:
Comes up slowly.  Hit firefox sometimes doesn't even show a screen.  Stuff works fine on WinXP.  Sometimes I do get a firefox screen.

What on earth does it take to get UBUNTU to run firefox?  Have tried all the network settings till
I am exhausted.

Any suggestions will be appreciated.  

Thanx in advance.
Johnny


Here are some screeen from the XP.

ipconfig -all:

Windows IP Configuration          
Host Name . . . . . . . . . . . . : xxxxx        
Primary Dns Suffix  . . . . . . . :          
Node Type . . . . . . . . . . . . : Unknown         
IP Routing Enabled. . . . . . . . : No         
WINS Proxy Enabled. . . . . . . . : No  
Ethernet adapter Local Area Connection:          
Connection-specific DNS Suffix  . :          
Description . . . . . . . . . . . : Atheros L2 Fast Ethernet 10/100 Base-T Controller         
Physical Address. . . . . . . . . : 00-1E-8C-9F-7F-3D         
Dhcp Enabled. . . . . . . . . . . : Yes         
Autoconfiguration Enabled . . . . : Yes         
IP Address. . . . . . . . . . . . : 192.168.15.101         
Subnet Mask . . . . . . . . . . . : 255.255.255.0         
Default Gateway . . . . . . . . . : 192.168.15.1         
DHCP Server . . . . . . . . . . . : 192.168.15.1         
DNS Servers . . . . . . . . . . . : 192.168.15.1 
 

Internet Protocol (TCP/IP) Properties
OBTAIN an IP address automatically
Obtain DNS server address automatically

General: Atheros L2 Fast Ethernet 10/100 Bas

IP Settings
DHCP Enabled
Gateway (empty)
DNS Screen (empty)
WINS screen 
  Enable LMHOSTS lookup
  NetBIOS settings = DEFAULT
OPTIONS Screen
  TCP/IP Filtering

---

### Post by cariboo on 2009-01-16
I would suggest you create a new Firefox profile. Be sure to backup your bookmarks first then open Nautilus(Places-->Home Folder) and press Ctrl-h, this will show the hidden files and directories. Navigate to .mozilla/firefox and delete xxxxxxx.default, where the xxxxxxx is a random string of letters and numbers. When you restart Firefox the default directory will be recreated.

Jim

---

