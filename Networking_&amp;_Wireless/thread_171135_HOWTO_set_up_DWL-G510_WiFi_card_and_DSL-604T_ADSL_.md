---
title: "HOWTO set up DWL-G510 WiFi card and DSL-604T ADSL router (Both D-Link) on Hoary"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by kiranbr on 2006-05-06
This has been a long journey, so it's worth documenting. One important message I have is - you don't need to upgrade to Breezy just so that RaLink chipsets are automatically recognized. Hoary works with a couple of nights' sleep lost.

[SIZE="5"]**Setup**[/SIZE]

Bedroom:

I have a 32-bit Ubuntu Hoary desktop with an ASUS motherboard with AMD64 (yeah, 32-bit OS on a 64-bit machine). I've inserted a DWL-G510 PCI WiFi card in one of the availble PCI slots. There is no ethernet cable or phone cable coming into/out of the desktop.

Living room:

I've connected a DSL-604T Wireless ADSL Router to the phone socket through an ADSL splitter (don't know if it's necessary, but BSNL Bangalore gave me this, so I'm using it). With this set up, my desktop connects wirelessly to the internet. I can even connect to my company through VPN (but that's a different story). The gnome network status tool shows 90% signal quality (I've got a thick wall between the living room and the bedroom).

[SIZE="5"]**Reasons for buying those particular D-link devices**[/SIZE]

The ADSL router was gifted to me, so not much choice. I bought the WiFi card thinking it has an Atheros chipset (that's good because you've got madwifi and I've heard a lot of success stories). But unfortunately my WiFi card turned out to be a RaLink chipset.

[SIZE="5"]**Setting up the DSL-G604T ADSL router**[/SIZE]

I brought the ADSL router into my bedroom table and connected its first ethernet port to the ethernet port of my Ubuntu desktop. I had already configured eth0, so I could immediately access the router at 192.168.1.1. Then I opened 192.168.1.1 on mozilla and got the router configuration page (which you have to access as user admin with password admin). On the page, I configured "Connection 1" as a PPPoE connection with VPI/VCI=0/35 (BSNL suggests this) and made default gateway=192.168.1.1. I'm not using DHCP. The DNS Setting is "Use auto-discovered DNS Server Only".

Once this is done, I could connect to the internet through the ethernet cable connecting my desktop to the ADSL router. But that's not fun at all since the goal is to connect wirelessly.

[SIZE="5"]**Setting up the DWL-G510 WiFi card**[/SIZE]

This was more tricky than I thought, but well, I expected some problems since this damned thing doesn't have an Atheros chipset.

First, I tried to use ndiswrapper with the WinXP drivers which came on the CD shipped with the WiFi card. It seemed to install alright, but I couldn't do anything further. So I ditched ndiswrapper.

After some googling, I came to RaLink's website on [http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm") where I found the Linux driver for the RT61 chipset (Click here: [http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz]("http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz")).

I thought that's great! I unzipped and untarred it and went into the Module directory. There I read the "readme" which pretty decently explains how to compile and load and all that. I compiled it. I had to create the directory /etc/Wireless/RT61STA/ where the config file rt61sta.dat has to be kept. I edited the config file to look like this:
```
[Default]

CountryRegion=0
CountryRegionABand=7
WirelessMode=0
SSID=G604T_WIRELESS
NetworkType=Infra
Channel=6
AuthMode=OPEN
EncrypType=NONE
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=0
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=CAM
TxPreamble=0
FastRoaming=0

```
Then I wrote two scripts to bring up and bring down the wireless connection:
```

#!/bin/bash
# SCRIPT NAME: wireless_up

# Stop eth0 first
sudo ifdown eth0

# Insert kernel module
sudo insmod /opt/RT61_DLINK_DRIVER/RT61_Linux_STA_Drv1.0.4.0/Module/rt61.ko

# Configure the ra0 connection and bring it up
sudo ifconfig ra0 inet 192.168.1.3 up

# Add 1.1 as the default gateway
sudo route add default gw 192.168.1.1

```
```

#!/bin/bash
# SCRIPT NAME: wireless_down

# bring down ra0
sudo ifconfig ra0 inet 192.168.1.3 down

# remove the rt61 module from the kernel
sudo rmmod rt61

# restart eth0
sudo ifup eth0

```

After this, I moved the router to the living room. Now, I can connect wirelessly from bedroom to living room by saying wireless_up and disconnect the wireless connection by saying wireless_down. I've kept the two scripts in /usr/local/bin so that all users on the desktop can access it.

[SIZE="5"]**Scope for improvement**[/SIZE]

[LIST]Note that I use **insmod** for inserting the rt61 kernel module. I believe it's better to use **modprobe.** I haven't been able to figure out that yet. Help would be great.[/LIST]
[LIST]I don't have any encryption yet. I tried a few things, but no success yet. Help is very much appreciated.[/LIST]

---

### Post by CAE on 2006-05-08
Hi. I'm using much the same hardware as you, so I thought I'd post this here. I've got a DWL-G510 Rev C in a box running Dapper while my DSL-G604T is attached via Ethernet to an XP box.

Dapper seems to recognize my card fine, which was great. My gateway IP is 10.1.1.1 while I'm using MAC + static IP addressing to make sure the box with the wireless card always gets 10.1.1.2 while the XP box will then get 10.1.1.3 generally.

I run sudo ifconfig ra0 inet 10.1.1.2 up to bring the interface up and then sudo route add default gw 10.1.1.1 however I still can't browse/ping. The network monitor seems to indicate that while I am apparently receiving packets, nothing is apparently being sent. Do you know what the problem might be?

---

### Post by ArchStanton on 2006-05-20
I tried to do this running Breezy, but when I got to the compile instructions I got stuck. Couldn't use the make command, says it doesn't exist. Any suggestions?

---

### Post by Stone123 on 2006-05-22
[QUOTE=ArchStanton]I tried to do this running Breezy, but when I got to the compile instructions I got stuck. Couldn't use the make command, says it doesn't exist. Any suggestions?[/QUOTE]

Take a look at original howto on this forum.(there is a server script that can do most of this if you make it sh).

sudo apt-get install gcc-3.4 build-essential

and i found it :
**[http://www.ubuntuforums.org/showpost.php?p=857082&postcount=13](http://www.ubuntuforums.org/showpost.php?p=857082&postcount=13)**
add !#/bin/bash on top of it and run it as a bash scipt.

---

