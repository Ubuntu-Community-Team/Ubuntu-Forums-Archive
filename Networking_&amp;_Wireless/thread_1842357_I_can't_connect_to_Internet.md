---
title: "I can't connect to Internet"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by shnura on 2011-09-11
Hi there,

I'm new to Linux, I've never used it before and I'm still confused. I've just installed Ubuntu 10.04. on my Asus x73sl laptop alongside Windows 7.

I'm using Ethernet connection, which is working flawlessly on windows. When I switch to Ubuntu, I can't download drivers or install any software. I can't connect to websites either.

Now, I tried a couple of things, as the Ubuntu's Help and Troubleshoot sections suggested. 

[LIST]
[*]I entered ifconfig command in the terminal and I saw that the system had obtained an IP address automatically.
[*]I took a look at the "Automatic Ethernet" connection and everything was set to Automatic, which my ISP support representatives said should be. They also saw my computer in their system and they confirmed that I've obtained an IP address.
[*]I performed a PING test to ubuntu.com website and I have 100% success rate.
[*]Now I tried to download and install some applications, but I couldn't. The downloading bar wasn't moving and some error message appeared.
[*]I run Firefox and tried to go on a couple of webpages, but it couldn't load them.
[*]The only internet activity I was able to do was to use the google search toolbar - it works and gives the search results, but I can't load any webpage listed.
[*]I logged in Windows and I had no problems. When I switched back to Ubuntu, the problem was still present.
[/LIST]

I'll be very happy if somebody could give me some ideas what the problem might be and how should I fix it. Note that I'm an absolute newbie, so please keep the explanations as simple as possible, if possible. :)

Thank you in advance!
Best regards,
Svetlin Kolev,
Bulgaria

---

### Post by ashickur.noor on 2011-09-11
Which connection you use? Static or dynamic? 

I mean how you connect to Internet after installing windows. Tell us the procedure.

---

### Post by shnura on 2011-09-11
After installing Windows, the connection sets itself up automatically. I virtually don't do anything. The ISP support always tells me that all the settings must be set to Automatic and everything works fine.

---

### Post by ashickur.noor on 2011-09-11
Please give the output of **ipconfig /all** from windows and **ifconfig** from Ubuntu.

---

### Post by shnura on 2011-09-11
Here's what windows says:

Windows IP Configuration

   Host Name . . . . . . . . . . . . : koleff-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : spnet.net

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter
   Physical Address. . . . . . . . . : 06-22-43-85-A8-61
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter  Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : spnet.net
   Description . . . . . . . . . . . : Atheros AR928X Wireless Network Adapter
   Physical Address. . . . . . . . . : 00-22-43-85-A8-61
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Connection:

   Connection-specific DNS Suffix  . : spnet.net
   Description . . . . . . . . . . . : SiS191 Ethernet Controller
   Physical Address. . . . . . . . . : 00-24-8C-7A-6C-60
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::c4d8:2294:20f4:b83f%10(Preferred)
   IPv4 Address. . . . . . . . . . . : 78.83.51.71(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Lease Obtained. . . . . . . . . . : 11 sept 2011 18:52:59.
   Lease Expires . . . . . . . . . . : 11 sept 2011 22:53:16.
   Default Gateway . . . . . . . . . : 78.83.48.1
   DHCP Server . . . . . . . . . . . : 212.50.0.15
   DHCPv6 IAID . . . . . . . . . . . : 234890380
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-15-7E-8B-7D-00-24-8C-7A-6C-60

   DNS Servers . . . . . . . . . . . : 212.50.10.50
                                       212.50.10.51
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.spnet.net:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{468B3145-8500-4F88-836A-A9F00C6289DF}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{B6DDCF45-9BE8-45C7-B4F9-FB75C2BF4FDE}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #4
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

C:\Users\koleff>


I'll paste the Ubuntu information in a minute.

---

### Post by shnura on 2011-09-11
And here's what ifconfig says:


koleff@ubuntu:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:8c:7a:6c:60  
          inet addr:78.83.51.71  Bcast:78.83.63.255  Mask:255.255.240.0
          inet6 addr: fe80::224:8cff:fe7a:6c60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:9140 errors:61 dropped:0 overruns:0 frame:61
          TX packets:4645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13154699 (13.1 MB)  TX bytes:329467 (329.4 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by shnura on 2011-09-12
Thanks a lot to all who tried to help me! :)
I think I found a solution of my problem. I've read several similar threads here and I found these commands, which, although I don't know (yet) what do they mean, they seemed to work. I'll be more than thankful if someone explain briefly to the newbie what are these. :)

```
sudo ifconfig eth0 mtu 1492
 
ifconfig | grep MTU
```

---

### Post by shnura on 2011-09-12
Hi again,
Hmmmm.... Not really solved. :( I found that every time I start the  computer and run Ubuntu, I have to paste 'sudo ifconfig eth0 mtu 1492'  in the Terminal, otherwise the problem is still present.
Any ideas?

---

