---
title: "Ubuntu Server 10.04 As Internet Gateway"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by joebell on 2011-10-29
In the beginning I want to emphasize I'm completely new to Ubuntu Linux systems having been a Microsoft Windows freak till now (please do not laugh). In spite of it I decided to build up a Linux Home Server with Internet connection for all my home LAN workstations (Linux, Windows and Max OSX Lion). Till now I succeeded to configure a Linux box based on the Ubuntu Server 10.04 LTS with sevices like DNS, DHCP, iptables and Twonky Media Server (I am quite proud of it). 
 
The next step is far behind my knowledge and experience in the Linux world, i.e. I want to have a home Internet gateway from that Linux box that will provide a PPPoE connection through an ADSL modem in a bridge mode. I am using the Vigor 2600 Ge ADSL modem/router. Is there somebody among you to help with this configuration and setup? I would be in the seventh heaven to have a step-by-step guide how to complete it to a functional state. Searching the Internet gave a huge number of results, but with none of them I succeeded to get the PPPoE working. The Ubuntu Server 10.04 is now always showing DHCPDISCOVERY on ethX to 255.255.255.255 port 67 interval y (y is equal to 4, 10, 18, 17, 12 in a roll for example) when booting and/or restarting the network services. I am completely lost for now. Will there be somebody among you guys nice enough and provide some information on how to configure it correctly?
 
Many thanks in advance.
 
Joe

---

### Post by Dangertux on 2011-10-29
While not step by step this information should answer most of the questions you have, if you're still having issues afterwards feel free to post back.

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Also for the ppoe part, the link in that document does not seem to be correct, this should help you get your ppoe connection up

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by joebell on 2011-10-29
> **Dangertux said:**
> While not step by step this information should answer most of the questions you have, if you're still having issues afterwards feel free to post back.
 
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
 
Also for the ppoe part, the link in that document does not seem to be correct, this should help you get your ppoe connection up
 
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)
 
Many thanks to you Dangertux. I do appreciate your quick response. I will study both links for sure and use those manuals to get the PPPeO connection working. As soon as I feel I need your help, I will be back here with a new post.
 
Joe

---

### Post by Dangertux on 2011-10-29
Great hope it all works out :-)

Good luck.

---

### Post by joebell on 2011-10-31
Hi Dangertux,
 
I am sorry to write I failed. I could not achieve the external NIC succeeded in acquiring of a public IP address from my ISP. Everything was done as per those manuals you gave me Internet links of in your reply to my question. All the configuration files were checked many times. They all are correct as per my opinion. There must be something other that is wrong. But I do not know what it might be. 
 
My problem is my poor knowledge of Ubuntu/LINUX as I am totally newbie here in your world. 
 
First, of all I am not sure my ADSL device is in a bridge mode in spite of the fact I did all the steps in the setup correctly in effort to put the device in a bridged mode. 
 
Second, I have to check with my ISP provider if I can use my Vigor 2600Ge modem in a bridged mode at all and get the full Internet services from him. 
 
Third, I have to keep on researching Internet very intensively to get on the level as I am with the Windows Servers/Workstations. 
 
Well, I wish to express my best thanks to you for your effort to help me, anyway. If you have any idea what could be wrong with my Ubuntu box configuration and/or you feel to provide some other important ideas to overcome the connection troubles, it could be great to hear from you soon again.
 
Just for order's sake here is my explanation why I wanted to make it the way I described earlier - my idea was to control the Internet traffic with iptables through a Ubuntu Server acting as a PPPoE client, router, firewall and Internet gateway at the same time. 
 
As I did not succeed, I am thinking right now I could solve the problem with using the modem as PPPoE client as it is the case right now and separate my home LAN through the Ubuntu Server - 1 NIC for my home LAN, the second NIC with private IP address on a different subnet for the ADSL modem part. The Ubuntu Server would act as a router between the two subnets. Moreover, with iptables I can control the Internet traffic from all the workstations and devices on the LAN. That was the primary idea, indeed. I know this solution is not what I and all IT professionals would prefer, but it could solve my problem temporarily at least. What do you think about this idea? Is it crazy? Or would you do the same in case you know so small about Ubnuntu Linux Server as I do?
 
Joe

---

### Post by joebell on 2011-11-01
Hi Dangertux,
 
Sorry to trouble you with my problem again. Please send your comments to the eth1 configuration in my /etc/network/interfaces file for the external network card:
 
```
auto eth1
iface eth1 inet manual
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider
```
 
Is that correct? Why do I have 'auto eth1' and then 'iface dls-provider inet ppp' in that config file? The configuration was automatically created and added to my network config file after I finished the procedure with the command 'pppoeconf'. Now there is no DHCPDISCOVERY on eth1 when I restart the network service (/etc/init.d/networking restart), but the NIC does not show any public IP address after I use the 'ifconfig' command. That means I still do not have any PPPoE connection. Here is what I see there:
 
```
eth1 Link encap:Ethernet HWaddr ...............................
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23 Base address:0xa400
```
 
The command 'lshw -C network' shows:```

*-network
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@0000:00:12.0
logical name: eth1
version: 7c
serial: 00:15:f2:c7:4c:46
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
resources: irq:23 ioport:d400(size=256) memory:febff400-febff4ff
```
 
Any support is highly appreciated.
 
Joe

---

### Post by joebell on 2011-11-06
Dangertux,
 
I have finally suceeded after I realized how to configure my Vigor 2600Ge ADSL modem/router correctly for a PPPoE bridge mode. That device was the only reason for my porevious troubles. The network configuration of my Ubuntu server was OK all the time thanks to your help. Once again, I do appreciate your nice support. 
 
Joe

---

