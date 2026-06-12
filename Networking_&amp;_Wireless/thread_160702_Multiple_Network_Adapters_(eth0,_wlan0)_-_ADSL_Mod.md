---
title: "Multiple Network Adapters (eth0, wlan0) - ADSL Modem and Wireless Router - Advice"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by Parrot_Guy on 2006-04-15
Hello,

Firstly, have a look at the attached plan.

**[COLOR="#ff0000"]Summary:[/COLOR]**
```
Internet
        |____ ADSL Modem
             |____ Computer #1 (eth0)
             |____ Router
                  |____ Computer #1 (wlan0)
                  |____ Computer #2 (wlan0)
```

Computer #1 connects to internet via eth0 -> ADSL Modem (I need to do this for BitTorrent).
Computer #2 connects to internet via wlan0 -> Router -> ADSL Modem (I need to do this for BitTorrent).
Now I need Computer #1 to communicate with Computer #2 via the Router (I need this for file transfer and etc. between #1 and #2).

[COLOR="Red"]**My question is as follows:**[/COLOR]
What IP Address/Netmask do I have to choose in the Router (Linksys WRT54GS)?

**ADSL Modem**
Local IP: 192.168.1.1 (unchangeable)
Netmask: 255.255.255.0 (unchangeable)

**Router**
Local IP Address: ?
Netmask: ?

**Computer #1 - eth0**
Local IP Address: 192.168.1.100 (or may be something lower)
Netmask: 255.255.255.0 (unchangeable)
Gateway: 192.168.1.1 (ADSL Modem IP Address - unchangeable)

**Computer #1 - wlan0**
Local IP Address: ?
Netmask: ?
Gateway: (Router IP Address)

**Computer #2 - wlan0**
Local IP Address: ?
Netmask: ?
Gateway: (Router IP Address)

*Also, what are the values that I must use for broadcast and network (in /etc/network/interfaces)?*

If you fill out the **?** (question marks) for me, I could figure out the rest. :) 

Thanks. :)

---

### Post by DJ Scribblinni on 2006-04-15
I have a quick question for ya.  I don't know what kind of modem you have, but you have two ethernet connections on it?  Thats pretty cool, I guess.  Anyways, why not just connect the router to the modem, and connect all computers to the router using ethernet and wireless, and let DHCP on the router take care of handing out IP's to all 3 computers.?

 My take on this situation:
The modem will pass out an IP and gateway that will allow internet access for the router.
Set up the router to use DHCP.  This will give everything the computers need to access the internet through the router.
You mention a lot about  BitTorrent, unless that works right out of the box, you may need to figure out what port is currently used, and open it up in Linksys's Filter's settings.


Looking at the guide that comes with the router is a big help.  If you don't have it, here's a link. [http://www.linksys.com/...VisitorWrapper]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1127782957298&pagename=Linksys%2FCommon%2FVisitorWrapper")
Just click on the Users Guide link on the web page.

Please post back up here for anything else, or to debate my theory.:cool:

---

### Post by Parrot_Guy on 2006-04-16
[QUOTE=DJ Scribblinni]I have a quick question for ya.  I don't know what kind of modem you have, but you have two ethernet connections on it?  Thats pretty cool, I guess.[/QUOTE]

It is not so cool except for the fact that it has the following:
One RJ-11 interfaces for ADSL line
Four 10/100 Base-T RJ-45 ports
One USB 1.1 interface
One PCMCIA slot for WLAN 802.11g NIC

[http://www.huawei.com/products/terminal/products/view.do?id=86](http://www.huawei.com/products/terminal/products/view.do?id=86)

[QUOTE=DJ Scribblinni]Anyways, why not just connect the router to the modem, and connect all computers to the router using ethernet and wireless, and let DHCP on the router take care of handing out IP's to all 3 computers.?[/QUOTE]

Note: There are only 2 computers, but 3 interfaces:
Computer #1 has eth0 and wlan0 (2)
Computer #2 has wlan0 (1)

Yes, this is how it is now. But I cannot get port fowarding to work as follows:
192.168.1.100 - 55555 (TCP/UDP) Computer #1 - 192.168.1.10 - 55555 (TCP/UDP) Router - 192.168.1.1 - 55555 (TCP/UDP) ADSL Modem
This wont work because the ADSL Modem does not have IP Passthrough facility.

Quote from [http://azureus.aelitis.com/wiki/index.php/NAT_problem](http://azureus.aelitis.com/wiki/index.php/NAT_problem) - If you're network consists of a DSL modem connected to a router and the local computers connect to the router, you may need to enable IP Passthrough on the modem. Otherwise, it may be impossible to successfully port forward through the router, as described in the next section.

[QUOTE=DJ Scribblinni]My take on this situation:
The modem will pass out an IP and gateway that will allow internet access for the router.
Set up the router to use DHCP.  This will give everything the computers need to access the internet through the router.[/QUOTE]

But the following sure works:
192.168.1.100 - 55555 (TCP/UDP) Computer #1 - 192.168.1.1 - 55555 (TCP/UDP) ADSL Modem

This is why I want to connect Computer #1 (eth0) to the ADSL Modem (for BitTorrent) and at the same time connect Computer #2 (wlan0) to the Router (so as to communicate with the Computer #2 (which is already connected to the Router via its wlan0.

[QUOTE=DJ Scribblinni]You mention a lot about  BitTorrent, unless that works right out of the box, you may need to figure out what port is currently used, and open it up in Linksys's Filter's settings.[/QUOTE]

It does work when Computer #1 is connected to the ADSL Modem directly.

My question is about the allocation of the IP Addresses and Subnet Masks to the various players involved, them being ADSL Modem, Router, Computer #1 (eth0 and wlan0) and Computer #2 (wlan0).

I cannot use 255.255.255.0 for both Computer #1 (eth0) and Computer #1 (wlan0) for obvious reasons.

Thanks for your help. :)

---

### Post by mips on 2006-04-16
Parrot_Guy,

I don't know why but you are really making things very difficult for yourself.

Why do you install a router/modem/gateway behind another modem ?

Remove the modem you have and plug the RJ-11 cable straight into the Hauwei Mt841 Modem port. Configure the MT841 for PPPoE & Authentication (You will need the VP/VCI info, Username&Password info, Encapsulation type for your ISP)

Once this is done you simply connect all your PC's via the ethernet ports or wireless and you wont have any of these hassles. Your PC's will just need DHCP and they will all be using the same IP subnet.

If you have difficulty finding the VPI/VCI & encapsulation info for your ISP just let me know who your ISP is and a link to their site and i'll try and find the info for you.

Do you have a PDF/Doc manual for the Hauwei, the best I could find was:
[http://www.huawei.com/products/terminal/doc/list.do?id=22](http://www.huawei.com/products/terminal/doc/list.do?id=22)

---

### Post by Parrot_Guy on 2006-04-16
[QUOTE=mips]Parrot_Guy,

I don't know why but you are really making things very difficult for yourself.

Why do you install a router/modem/gateway behind another modem ?

Remove the modem you have and plug the RJ-11 cable straight into the Hauwei Mt841 Modem port. Configure the MT841 for PPPoE & Authentication (You will need the VP/VCI info, Username&Password info, Encapsulation type for your ISP)

Once this is done you simply connect all your PC's via the ethernet ports or wireless and you wont have any of these hassles. Your PC's will just need DHCP and they will all be using the same IP subnet.[/QUOTE]

I did have that arrangement a while back. But the ADSL Modem is not half as reliable as it seems. When both my computers are connected to it and when I am downloading something (such as Ubuntu distro) off BitTorrent, it randomly chokes (once every 10-30 minutes) and I have to manually press the power button on it and get it restarted.

This is why I got myself the best of the best router - Linksys WRT54GS - [http://en.wikipedia.org/wiki/WRT54G](http://en.wikipedia.org/wiki/WRT54G).

I hope I am clear in explaining it. :)

---

