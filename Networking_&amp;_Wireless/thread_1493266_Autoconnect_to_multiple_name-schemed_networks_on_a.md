---
title: "Autoconnect to multiple name-schemed networks on a city bus?"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by tarahmarie on 2010-05-25
Hi!

I do a lot of work on the Seattle bus system on my Jolicloud netbook (I'm a hardcore Kubuntu user, and Jolicloud is based on Ubuntu Netbook).

All Seattle buses have free wifi.  They have a name scheme like "ST_9545" for the 545 from Redmond to Seattle, or "ST_7483" for whatever.  You get the idea...all the free wifi on the buses are "ST_****".

Here's what I want.  I want to autoconnect to whatever my current bus's wifi network is based on a name scheme.  "ST_****" will be the name of the open wifi network on the bus.  How do I set it up so my netbook automatically finds and connects to an open wifi network with that specified naming schema?

---

### Post by tarahmarie on 2010-06-09
bump

---

### Post by tgalati4 on 2010-06-09
I'm not familiar with jolicloud.  I presume it has some form of Network Manager running to connect to wireless networks.  You can manually add network connections.  Right-click on the wireless icon and select Edit Connections.  You can add all of your bus networks and then your netbook should automatically connect.  It's possible that the network manager in jolicloud has been simplified such that your preferred networks are ones that you manually connect to.  If that is the case, then spend the day riding the bus and connect to as many networks as you can find.

My other thought has to do with dhcp.  There may some options for the dhcp client to improve autoconnection:

apt-cache search dhcp
man dhcp-options

---

### Post by tarahmarie on 2010-06-09
> **tgalati4 said:**
> I'm not familiar with jolicloud.  I presume it has some form of Network Manager running to connect to wireless networks.  You can manually add network connections.  Right-click on the wireless icon and select Edit Connections.  You can add all of your bus networks and then your netbook should automatically connect.  It's possible that the network manager in jolicloud has been simplified such that your preferred networks are ones that you manually connect to.  If that is the case, then spend the day riding the bus and connect to as many networks as you can find.

I'm aware that I can manually connect to networks. 

I'm trying to find out if there's a way to automatically connect to  name-schemed networks.  Is there any wildcard usage?

---

### Post by tgalati4 on 2010-06-09
What wireless network backend does Jolicloud use?
Find the source could for that backend.
Modify it such that it will preferentially seek ST_* named SSID's.

I believe Network Manager is just a front end for iwconfig and iwconfig can't take wild cards since it has to match SSID's exactly in order to connect and perform WEP/WPA authentication.  iwconfig does have a promiscuous mode called "any" which will connect the the strongest/open network during the last scan.

man iwconfig

---

### Post by tarahmarie on 2010-06-09
> **tgalati4 said:**
> What wireless network backend does Jolicloud use?
Find the source could for that backend.
Modify it such that it will preferentially seek ST_* named SSID's.

I believe Network Manager is just a front end for iwconfig and iwconfig can't take wild cards since it has to match SSID's exactly in order to connect and perform WEP/WPA authentication.  iwconfig does have a promiscuous mode called "any" which will connect the the strongest/open network during the last scan.

man iwconfig

Jolicloud is a fork of Buntu.  iwconfig can't take wildcards? If not, then there's no way to do what I want it to do.

---

### Post by tgalati4 on 2010-06-10
Try setting promiscuous mode using iwconfig.

You can also write a scanning script that connects whenever an "ST_***" network shows up:

tgalati4@tpad-Gloria7 ~ $ sudo iwlist eth1 scan | grep ESSID
                    ESSID:"Galati Slow Lane"
                    ESSID:"metalhead"
                    ESSID:"2WIRE799"

---

