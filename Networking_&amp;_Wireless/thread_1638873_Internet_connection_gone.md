---
title: "Internet connection gone"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by chrislang on 2010-12-06
Until Friday afternoon I had an internet connection. It suddenly disappeared (without me changing any settings). I've managed to get a laptop connected (using Windows 7 and Ubuntu) but my desktop will not re-connect.

I'm using Ubuntu 10.04 LTS. Here's some more information that might be useful - if you want more information, please let me know.

Any help would be gratefully received!

```
:~$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 40:61:86:ab:59:f6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:28 memory:fea77000-fea77fff ioport:c880(size=8) memory:fea7e800-fea7e8ff memory:fea7e400-fea7e40f
```

```
:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7100 / nForce 620i] (rev a2)
01:05.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
``` 

```
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:ab:59:f6  
          inet6 addr: fe80::4261:86ff:feab:59f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:247649 (247.6 KB)  TX bytes:4444 (4.4 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:433600 (433.6 KB)  TX bytes:433600 (433.6 KB)
```

```
:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

---

### Post by TBABill on 2010-12-06
Have you reset your router and/or modem (assuming cable modem or DSL modem)? Looks like the ethernet is working, just not receiving anything. Can you ping any sites, such as Google?

---

### Post by dineshs on 2010-12-06
Your ethernet doesnt seem to have got an IP address.Please run```
sudo dhclient eth0
```and see if there is any progress

---

### Post by chrislang on 2010-12-06
Thanks dineshs. Here's what I got from "sudo dhclient eth0":

```
:~$ sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/40:61:86:ab:59:f6
Sending on   LPF/eth0/40:61:86:ab:59:f6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

N.B. Please note that to send this message, I'm using the same modem, but with my laptop (windows 7). So I'm assuming, for the time-being at least, that the modem is OK....

---

### Post by dineshs on 2010-12-06
You may try configuring IP manually as in this link
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)
Details such as IP ,mask, gateway etc can be obtained from Windows machine by running```
ipconfig /all
```If possible pl post the output of ipconfig/all

---

### Post by chrislang on 2010-12-06
This is what I got from ipconfig/all on the windows machine (in German - sorry! - hopefully it still makes sense). I tried putting in the address, mask and gateway numbers [as here]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")). My desktop NM now says that I have a connection, but when I open firefox I can't connect to any websites.

```
Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation. Alle Rechte vorbehalten.

C:\Users\chris>ipconfig/all

Windows-IP-Konfiguration

   Hostname  . . . . . . . . . . . . : chris-laptop
   Primäres DNS-Suffix . . . . . . . :
   Knotentyp . . . . . . . . . . . . : Hybrid
   IP-Routing aktiviert  . . . . . . : Nein
   WINS-Proxy aktiviert  . . . . . . : Nein

Ethernet-Adapter Bluetooth-Netzwerkverbindung:

   Medienstatus. . . . . . . . . . . : Medium getrennt
   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Bluetooth-Gerät (PAN)
   Physikalische Adresse . . . . . . : F0-7B-CB-E1-02-F7
   DHCP aktiviert. . . . . . . . . . : Ja
   Autokonfiguration aktiviert . . . : Ja

Ethernet-Adapter LAN-Verbindung:

   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Atheros AR8131 PCI-E Gigabit Ethernet Con
troller
   Physikalische Adresse . . . . . . : 00-24-BE-5E-BC-49
   DHCP aktiviert. . . . . . . . . . : Ja
   Autokonfiguration aktiviert . . . : Ja
   Verbindungslokale IPv6-Adresse  . : fe80::fd77:97e7:2cbf:cb38%12(Bevorzugt)
   IPv4-Adresse  . . . . . . . . . . : 118.137.235.19(Bevorzugt)
   Subnetzmaske  . . . . . . . . . . : 255.255.255.0
   Lease erhalten. . . . . . . . . . : 07 December 2010 10:41:08
   Lease läuft ab. . . . . . . . . . : 07 December 2010 11:11:07
   Standardgateway . . . . . . . . . : 118.137.235.1
   DHCP-Server . . . . . . . . . . . : 10.255.9.24
   DHCPv6-IAID . . . . . . . . . . . : 285222078
   DHCPv6-Client-DUID. . . . . . . . : 00-01-00-01-13-9E-B7-46-00-24-BE-5E-BC-49

   DNS-Server  . . . . . . . . . . . : 202.73.99.2
                                       61.247.0.2
   NetBIOS über TCP/IP . . . . . . . : Aktiviert

Drahtlos-LAN-Adapter Drahtlosnetzwerkverbindung:

   Medienstatus. . . . . . . . . . . : Medium getrennt
   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Atheros AR9285 Wireless Network Adapter
   Physikalische Adresse . . . . . . : 78-DD-08-DC-32-D6
   DHCP aktiviert. . . . . . . . . . : Ja
   Autokonfiguration aktiviert . . . : Ja

Tunneladapter 6TO4 Adapter:

   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Microsoft-6zu4-Adapter
   Physikalische Adresse . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP aktiviert. . . . . . . . . . : Nein
   Autokonfiguration aktiviert . . . : Ja
   IPv6-Adresse. . . . . . . . . . . : 2002:7689:eb13::7689:eb13(Bevorzugt)
   Standardgateway . . . . . . . . . : 2002:c058:6301::c058:6301
   DNS-Server  . . . . . . . . . . . : 202.73.99.2
                                       61.247.0.2
   NetBIOS über TCP/IP . . . . . . . : Deaktiviert

Tunneladapter isatap.{DC021824-3036-4DDB-B5CB-923602A21399}:

   Medienstatus. . . . . . . . . . . : Medium getrennt
   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Microsoft-ISATAP-Adapter #6
   Physikalische Adresse . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP aktiviert. . . . . . . . . . : Nein
   Autokonfiguration aktiviert . . . : Ja

Tunneladapter isatap.{8CF04EAD-1470-4821-AE15-92CE7A09974F}:

   Medienstatus. . . . . . . . . . . : Medium getrennt
   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Microsoft-ISATAP-Adapter #10
   Physikalische Adresse . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP aktiviert. . . . . . . . . . : Nein
   Autokonfiguration aktiviert . . . : Ja

Tunneladapter Teredo Tunneling Pseudo-Interface:

   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physikalische Adresse . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP aktiviert. . . . . . . . . . : Nein
   Autokonfiguration aktiviert . . . : Ja
   IPv6-Adresse. . . . . . . . . . . : 2001:0:4137:9e76:3023:2df3:8976:14ec(Bevo
rzugt)
   Verbindungslokale IPv6-Adresse  . : fe80::3023:2df3:8976:14ec%16(Bevorzugt)
   Standardgateway . . . . . . . . . :
   NetBIOS über TCP/IP . . . . . . . : Deaktiviert

Tunneladapter isatap.{6FEBD14F-F779-4CBD-8B5B-19159489AB38}:

   Medienstatus. . . . . . . . . . . : Medium getrennt
   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Microsoft-ISATAP-Adapter #11
   Physikalische Adresse . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP aktiviert. . . . . . . . . . : Nein
   Autokonfiguration aktiviert . . . : Ja

```

---

### Post by chrislang on 2010-12-07
One more piece of information - that may be relevant.

I was using OpenDNS. I got a connection on my laptop by disabling OpenDNS.

When I try to connect using OpenDNS on my laptop (Ubuntu 10.04 or Windows) I do not get a connection. And I've disabled OpenDNS on my desktop (Ubuntu 10.04) but I don't get a connection.

---

### Post by dineshs on 2010-12-07
> I tried putting in the address, mask and gateway numbers as here). My desktop NM now says that I have a connection, but when I open firefox I can't connect to any websites.
Did you try open DNS 4.2.2.1 ? Can you ping 4.2.2.1?```
ping -c5 4.2.2.1
```

---

### Post by chrislang on 2010-12-07
Thanks again dineshs. Still no luck, I'm afraid....

Just in case I'm doing something daft, here are my IPv4 settings:

```
Method: Manual

Address: 118.137.235.19
Netmask: 255.255.255.0
Gateway: 118.137.235.1

DNS Servers: 202.73.99.2, 61.247.0.2
```

To try open DNS 4.2.2.1 I changed the settings to this:

```
Method: Automatic (DHCP) addresses only

DNS Servers: 4.2.2.1
```

This gave me no connection.

With both settings, when I pinged 4.2.2.1 I got the same result:

```
chris@chris-desktop:~$ ping -c5 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
From 118.137.235.19 icmp_seq=1 Destination Host Unreachable
From 118.137.235.19 icmp_seq=2 Destination Host Unreachable
From 118.137.235.19 icmp_seq=3 Destination Host Unreachable
From 118.137.235.19 icmp_seq=4 Destination Host Unreachable
From 118.137.235.19 icmp_seq=5 Destination Host Unreachable

--- 4.2.2.1 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4024ms
, pipe 3

```

---

### Post by dineshs on 2010-12-08
> Ethernet-Adapter LAN-Verbindung:
   Verbindungsspezifisches DNS-Suffix:
   Beschreibung. . . . . . . . . . . : Atheros AR8131 PCI-E Gigabit 
   IPv4-Adresse  . . . . . . . . . . : 118.137.235.19(Bevorzugt)
   Subnetzmaske  . . . . . . . . . . : 255.255.255.0
   Lease erhalten. . . . . . . . . . : 07 December 2010 10:41:08
   Lease läuft ab. . . . . . . . . . : 07 December 2010 11:11:07
   Standardgateway . . . . . . . . . : 118.137.235.1
   DHCP-Server . . . . . . . . . . . : 10.255.9.24
   DHCPv6-IAID . . . . . . . . . . . : 285222078
 
118.137.235.19 seems to be a public IP.Can you tell how you configured your LAN card in windows?Manually or automatically(In windows Rightclick Local area connection-properties-ipv4 properties...and see)
Also while trying ping command you should connect only your ubuntu machine ie the desktop

---

### Post by chrislang on 2010-12-08
The windows IPv4 is on automatic set up. 

The "ping -c5 4.2.2.1" was using the desktop.

Any more suggestions? And thanks for the help so far!

---

### Post by chili555 on 2010-12-08
I think my colleague dineshs will also be interested to know what your setup is; for example:

==internet==>DSL modem==>router??==>computer(s)??

Or maybe:

==internet==>DSL modem==>desktop computer==>Internet Connection Sharing==>laptop computer

dineshs will be better able to assist you if he knows your precise connection details.

---

### Post by dineshs on 2010-12-08
I think the problem is with the file /etc/dhcp3/dhclient.conf.Ensure that it has lines 
```
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
```
without a # before
Then make NM configuration [COLOR="Blue"]automatic(DHCP)[/COLOR] and restart
If it is not working still let us wait for chili555s suggestion(I have sent a private message)

---

### Post by chrislang on 2010-12-08
My desktop now has an internet connection - I'm writing this message from it. Thanks dineshs for all the help, but I have no idea why I suddenly have a connection....

This is what happened.

I checked the file /etc/dhcp3/dhclient.conf - the lines you asked about were there without a #.

I then tried to connect with automatic(DHCP). Without success.

I switched the modem off and back on, tried again and got an internet connection - which works.

So, my current set up (to answer chili555's question) is:

=internet==>DSL modem==>==> desktop computer

My set up on Friday, before all this happened was

=internet==>DSL modem==>router==>desktop computer (via a cable) + laptop (via wifi)

I just tried connecting the router but couldn't get a connection either on the laptop or on the desktop.

So we are at least half way there. I have an internet connection on my desktop :D

If you still have the patience - do you have any suggestions for getting the router up and running again?

---

### Post by dineshs on 2010-12-09
Please post the result of ```
ifconfig -a
``` (ubuntu machine) when the setup is
1) internet-DSL modem-desktop (connection working)
and
2)internet-DSL modem-router-desktop (connection not wkg)

---

### Post by chrislang on 2010-12-09
Thanks dineshs - here is ifconfig -a 1) internet-DSL modem-desktop (connection working):

```
chris@chris-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:ab:59:f6  
          inet addr:118.137.236.161  Bcast:118.137.236.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:feab:59f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1027535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:633408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1381269580 (1.3 GB)  TX bytes:76127368 (76.1 MB)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10273 (10.2 KB)  TX bytes:10273 (10.2 KB)
```

And here is ifconfig -a 2) internet-DSL modem-router-desktop (connection not wkg):

```
chris@chris-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:61:86:ab:59:f6  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:feab:59f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1035069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:638502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1392298118 (1.3 GB)  TX bytes:76492769 (76.4 MB)
          Interrupt:28 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15022 (15.0 KB)  TX bytes:15022 (15.0 KB)
```

---

### Post by dineshs on 2010-12-09
Pl try this
Configure eth0 interface in ubuntu machine as Automatic DHCP via Network manger.
power cycle the router (Unplug the router,wait for say 10 seconds and plug it back)
See if there is any progress.If not go to [http://192.168.1.1](http://192.168.1.1) (ie the router page)and ensure that the WAN interface is not configured for static IP.You should get an IP starting with 118 (eg 118.137.236.161) there for the connection to work
Note: Pl see postcount 8 [here]("http://ubuntuforums.org/showthread.php?t=1640154") where the WAN side has got an IP starting with 59

---

### Post by chrislang on 2010-12-10
OK, I set up automatic DHCP on network manager. Switched the router off and back on. No progress.

On [http://192.168.1.1](http://192.168.1.1) I got the error message attached (asus-rt-N13U.png)

Another error message flashed up - also attached (network-service.png).

When I click on "Go to Setting page of the RT-N13U" link, it asks me for a user name and password - I don't have either as far as I'm aware...).

I did manage to get to this page though: [http://192.168.1.1/QIS_wizard.htm](http://192.168.1.1/QIS_wizard.htm) with a form to fill in (see attachment qis-wizard.png). I tried a couple of options - including OpenDNS 208.67.222.222, 208.67.220.220 in the "Connect to DNS Server automatically" but so far no luck.

---

### Post by dineshs on 2010-12-13
Ref [http://www.tweaktown.com/reviews/3081/asus_rt_n13u_superspeed_n_wireless_router/index5.html](http://www.tweaktown.com/reviews/3081/asus_rt_n13u_superspeed_n_wireless_router/index5.html)
Hope you have already checked
1)The ethernet port of the modem is connected to WAN port of the router
2)> There is a small switch that allows you to hard set the operation mode for the RT-N13U. The switch gives you options for Router, Repeater and AP (Access Point).
 The switch is in router mode
Now when the page says Automatic connection failed , set
IP [COLOR="Blue"]192.168.1.100[/COLOR]
mask [COLOR="Blue"]255.255.255.0[/COLOR]
gateway [COLOR="Blue"]192.168.1.1[/COLOR]
Automatic DNS yes
> When I click on "Go to Setting page of the RT-N13U" link, it asks me for a user name and password
Use [COLOR="Blue"]admin[/COLOR] as username and [COLOR="Blue"]admin[/COLOR] as password
If you can access router page see that WAN IP is set to Automatic

---

### Post by chrislang on 2011-01-26
Thanks for all your help dineshs! For more than a month I've had wireless working via the router OR LAN working directly from the modem. LAN would not work via the router - until today...

All I did was changed the IPv4 settings to "Automatic (DHCP) addresses only" and typed in the OpenDNS numbers (208.67.222.222, 208.67.220.220) under DNS Servers. And bingo! Wireless and LAN connection simultaneously. Just don't ask me to explain why....

---

