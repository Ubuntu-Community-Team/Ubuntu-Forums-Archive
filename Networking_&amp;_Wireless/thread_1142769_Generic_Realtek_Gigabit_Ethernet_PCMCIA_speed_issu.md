---
title: "Generic Realtek Gigabit Ethernet PCMCIA speed issues"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by gundog on 2009-04-29
I need some help with a Generic Ethernet PCMCIA card which I am trying to get working at gigabit speed in Ubuntu 9.04 on an old Samsung P35 laptop (circa 2004). The Samsung P35 has an onboard NIC but it only supports 10/100 speed ethernet. The card states that it is 10/100/1000 speed but I have not tested it as I do not have an XP notebook with a PCMCIA port.

In Ubuntu "Connection Information" for the card (when connected) states that the driver is r8169 and that the connection speed is 100Mbps.

I am aware that a gigabit device connected to a 100Mbps network is not going to operate at gigabit speed. The network is fully gigabit capable and has been set up as follows:

The laptop is connected (via cat5e) network cable to a Netgear Gigabit Ethernet Switch. Two other computers, a desktop (Marvell Yukon Gigiabit NIC) also running Ubuntu 9.04 and an iMac (onboard gigabit NIC also made by Marvell Yukon) are also connected to this switch. Both the desktop and the iMac report that the network speed is 1000Mbps. Files can be transferred from the desktop to the iMac and back at around 35 MBps - not brilliant but a lot faster than a 100Mbps network can handle. Files transferred from either the iMac or the desktop to the laptop or back the other way go at around 4Mbps. All machines have fixed IP addresses.

I have heard that there are problems with gigabit PCMCIA cards using the Realtek 8169 chipset. The card is generic (i.e. the manufacturer doesn't even have a website) so no drivers specific for it are available. There are drivers for the 8169 chipset on the Realtek website:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)%3Cbr%3ERTL8169](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB(L)/RTL8169SB(L)/RTL8169SC(L)%3Cbr%3ERTL8169)

I'm an experienced Linux (4 years; Knoppix, Ubuntu and Fedora) user but not an expert administrator and I tend to steer clear of modules and the kernel if I am not absolutely sure what I am doing. I do not want to mess with the system at this level unless I am fairly certain that doing so will fix the problem.

Does anyone have any ideas how I might get this card working at Gigabit speed? 

Any help would be much appreciated.

---

