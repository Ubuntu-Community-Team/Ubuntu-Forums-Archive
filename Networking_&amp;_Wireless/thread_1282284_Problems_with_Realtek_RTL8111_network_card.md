---
title: "Problems with Realtek RTL8111 network card"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by damnated on 2009-10-04
Hi everyone, another new user with problems here.

I recently installed the 64 bit version of Ubuntu 9.04, and although my network card is recognized, it says it is disconnected. (I had a home network with another ubuntu 9.04, which worked flawlessly when i had xp.) I'm guessing it is a driver problem. 

I have searched all over the web, even downloaded the driver from the official Realtek site, followed the instructions in the readme, and i've encountered a problem there. 

According to the readme, i should remove the r8168.ko file first. I tried this from the terminal, it said "ERROR: Removing 'r8169': Operation not permitted". I even tried to overwrite the r8168.ko file with the newly downloaded one, but i wasn't allowed by the system. After that i tried to install the driver anyways, from the terminal, without luck however.

Any ideas, or i'm better of with buying a new network card? Thanks in advance.

---

### Post by chili555 on 2009-10-04
> although my network card is recognized, it says it is disconnected.Where does it say that? Please make sure the ethernet cable is attached, open a terminal and do:```
sudo ethtool eth0
```Please post the result.> I have searched all over the web, even downloaded the driver from the official Realtek site, followed the instructions in the readme, and i've encountered a problem there.If we may, let's troubleshoot the built-in r8169 before we move on to the downloaded driver.

---

### Post by damnated on 2009-10-04
> **chili555 said:**
> Where does it say that? 
as soon as i start ubuntu: 

[[IMG]http://i152.photobucket.com/albums/s193/Damnated/th_Screenshot.png[/IMG]](http://s152.photobucket.com/albums/s193/Damnated/?action=view&current=Screenshot.png)

Ethernet cable is attached of course, and it is working properly.

> **chili555 said:**
> Please post the result.

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes

I still have xp on another hard drive, but i don't think that should be conflicting with the card

---

### Post by chili555 on 2009-10-04
> I still have xp on another hard drive, but i don't think that should be conflicting with the cardOne would think not, however: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

You might just make the adjustments on the Windows partition, just in case. I do wonder if this is really your problem, because ethtool reports:> Link detected: [COLOR="Red"]yes[/COLOR]Please try these commands and let us know the result:```
sudo /etc/init.d/NetworkManager stop
sudo dhclient eth0
```Please post the output. Thanks.

---

### Post by damnated on 2009-10-04
I will try that solution as well, until then:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:8f:ec:0d:f4
Sending on   LPF/eth0/00:13:8f:ec:0d:f4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

BTW, I also have a Scientific Atlanta Cable Modem which is connected through a usb port. This works, i have internet connection, but this can't be sabotaging the other connection right? More so that if i stop this eth1, the network card stays the same.

---

### Post by chili555 on 2009-10-04
> BTW, I also have a Scientific Atlanta Cable Modem which is connected through a usb port. This works, i have internet connection, but this can't be sabotaging the other connection right? More so that if i stop this eth1, the network card stays the same.Well, it sure could and probably is affecting it!!! 

I do not understand your setup. If you have the cable modem attached directly to your computer, what does the ethernet cable attach to? A router? What, if anything, is the router attached to? Is the cable modem attached temporarily just until you get the Realtek sorted out? Or what?

---

### Post by damnated on 2009-10-04
> **chili555 said:**
> Well, it sure could and probably is affecting it!!! 

I do not understand your setup. If you have the cable modem attached directly to your computer, what does the ethernet cable attach to? A router? What, if anything, is the router attached to? Is the cable modem attached temporarily just until you get the Realtek sorted out? Or what?
The ethernet cable is used for a local network. There is no router, the ethernet cable is the only thing that makes the connection between the two machines. The cable modem is attached definitely.

---

### Post by chili555 on 2009-10-04
Ohhhh!!!! Is this part of an internet connection sharing setup? I know almost nothing about that subject, but I do know that your Realtek is not supposed to be *getting* a connection; it's supposed to be *giving* a connection to the other computer.

Perhaps this will be helpful: [http://ubuntuforums.org/showthread.php?t=1241786](http://ubuntuforums.org/showthread.php?t=1241786)

---

### Post by damnated on 2009-10-04
The ubuntu pc will act as a gateway, so it will only give a connection. I'll look into that link, thank you for your help.

---

