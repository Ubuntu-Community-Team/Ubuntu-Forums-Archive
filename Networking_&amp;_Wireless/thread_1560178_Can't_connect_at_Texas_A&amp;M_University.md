---
title: "Can't connect at Texas A&amp;M University"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by LIB53 on 2010-08-24
I'm having trouble connecting to the internet here at A&M through Ubuntu. It's working fine on Windows 7. I tried using manual connection settings and copying the addresses over from windows 7 and it got a connection, but no internet, and i couldn't ping anything except localhost. Can anyone help please?

---

### Post by pricetech on 2010-08-24
Wired or wireless ??  Does it work elsewhere ??  Do you install anything to access the network under windows ??

---

### Post by LIB53 on 2010-08-24
Wired. It worked wired back home under both Windows and Ubuntu. I didn't install anything. I just had to launch a web browser, and enter some student ID and it was all set after a reboot. I tried linux first and i never got that page.

---

### Post by LIB53 on 2010-08-24
This is my windows ipconfig /all output:

```
C:\Users\**edited in notepade**>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : **edited in notepad**
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Broadcast
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : resnet.tamu.edu

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : resnet.tamu.edu
   Description . . . . . . . . . . . : JMicron PCI Express Gigabit Ethernet Adap
ter
   Physical Address. . . . . . . . . : 48-5B-39-7B-D5-90
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 128.194.11.162(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.252.0
   Lease Obtained. . . . . . . . . . : Tuesday, August 24, 2010 1:12:18 PM
   Lease Expires . . . . . . . . . . : Tuesday, August 24, 2010 9:12:18 PM
   Default Gateway . . . . . . . . . : 128.194.8.1
   DHCP Server . . . . . . . . . . . : 128.194.177.199
   DNS Servers . . . . . . . . . . . : 128.194.254.2
                                       128.194.254.1
                                       128.194.254.3
   Primary WINS Server . . . . . . . : 128.194.254.2
   Secondary WINS Server . . . . . . : 128.194.254.1
                                       128.0.0.0
   NetBIOS over Tcpip. . . . . . . . : Enabled

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : gateway.2wire.net
   Description . . . . . . . . . . . : Atheros AR9285 Wireless Network Adapter
   Physical Address. . . . . . . . . : 1C-4B-D6-D4-79-BB
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:3c55:3f07:7f3d:f45d(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::3c55:3f07:7f3d:f45d%12(Preferred)
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.resnet.tamu.edu:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : resnet.tamu.edu
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter 6TO4 Adapter:

   Connection-specific DNS Suffix  . : resnet.tamu.edu
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2002:80c2:ba2::80c2:ba2(Preferred)
   Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301
   DNS Servers . . . . . . . . . . . : 128.194.254.2
                                       128.194.254.1
                                       128.194.254.3
   NetBIOS over Tcpip. . . . . . . . : Disabled

```

---

### Post by nuttycat on 2010-10-19
Did you get this fixed?
If you didn't, talk to CIS. they might be able to get you to re-do the registration issue.

If your initial attempt to authenticate with resnet was over linux (i.e. not using Internet Explorer/firefox over windows) - then that online resnet interface may not have captured all the information it requires to get you setup. 

So, it gives you an IP - since it got your MAC address when you went in from Windows - but something else that (probably) didn't get set when you first logged in to resnet, is preventing your pc from communicating past the resnet gateway.

(FWIW: I'm a grad student at TAMU)

---

