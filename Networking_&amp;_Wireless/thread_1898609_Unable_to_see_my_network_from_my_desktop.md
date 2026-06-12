---
title: "Unable to see my network from my desktop"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by reesaal on 2011-12-21
Hello, 
Im having trouble connecting to my router, everything was working fine till two weeks ago, I have a Vonage D-Link router model: VWR-VD and and have 3 computers total, 2 of them are desktops running windows 7 ultimate and 1 Laptop running windows 7 home. one of the desktops is connected directly to the router and works fine, the laptop is connected wireless and it works fine too. the other desktop has a Realtek 8185 extensive 802.11 bg wireless devise VEN 10EC / DEV 8185. the computer was working fine till 2 weeks ago that I don't know what happened but now I'm able to see other connections but unable to see my connection (my router). on the task bar when I click on the bars for my connections, my connection does not appear. and shows wireless network connection 2, which I think it didn't see that before. can somebody please help me. 
I've tried the following: 

Reinstall the Driver 
reset IP 
I tried to change the homegroup, but I couldent due to the fact that I'm not connected 
I did a IPconfig /all and the following are the results


Windows IP Configuration

   Host Name . . . . . . . . . . . . : RenatoSalgado
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek 8185 Extensible 802.11b/g Wireless Device
   Physical Address. . . . . . . . . : 00-18-E7-63-C6-36
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
   Physical Address. . . . . . . . . : 00-17-31-5C-3D-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 9:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{EFDC2E92-3E64-42A8-9496-E4E6A15BE112}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{98A5F345-BBF2-4826-9538-2971F810AD74}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


I also did an ipconfig on my laptop and the following is the result:

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Renato-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Broadcom 43225 802.11b/g/n
   Physical Address. . . . . . . . . : C4-17-FE-4E-19-71
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::d839:785c:7ad7:dd97%11(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.15.3(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Wednesday, December 21, 2011 2:36:08 PM
   Lease Expires . . . . . . . . . . : Wednesday, December 21, 2011 7:36:08 PM
   Default Gateway . . . . . . . . . : 192.168.15.1
   DHCP Server . . . . . . . . . . . : 192.168.15.1
   DHCPv6 IAID . . . . . . . . . . . : 230955006
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-15-75-B0-5B-00-26-9E-F2-17-5F
   DNS Servers . . . . . . . . . . . : 192.168.15.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{45AFC589-973C-4DE5-966A-8AA106A9F55E}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:867:ba9f:41d4:780f(Preferred) 
   Link-local IPv6 Address . . . . . : fe80::867:ba9f:41d4:780f%12(Preferred) 
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled


I'm also adding screen shots of the desktop and laptop
thank you in advance for your help

---

### Post by mbuell on 2011-12-21
Wow. Kinda ballsy of ya - running windows and looking for help with windows - on a ubuntu forum???

But ok - I'll give it a shot.

1. Check to make sure your hardware wifi switch is ON.
2. Router - try rebooting the router
3. Windows - try rebooting windows.
4. Security - what kind of security are the wifi access points running? Try running them as open - no security - see if they connect. 


Ok - well where are we now?

If it isn't the hardware switch (and do NOT laugh at this - you might be amazed at how many times I have fixed a nasty connection problem by discovering that the hardware switch was OFF), rebooting the router, or rebooting Windows, then the router security has a good chance of being the problem. 

Why did it change? I do not know - but obviously something in the system was changed. 

Good luck!

---

### Post by mbuell on 2011-12-21
Oh, and by the way - homegroup name - good guess to be the problem. You were thinking on the right track with that one. 

Firewall settings - could be the problem. 

There are probably a couple of other minor settings that could create this issue - but I am tired and it is time to sleep. So, good luck!

---

