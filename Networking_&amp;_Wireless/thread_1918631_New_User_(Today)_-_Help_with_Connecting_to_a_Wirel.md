---
title: "New User (Today) - Help with Connecting to a Wireless LAN that needs VLAN"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by seveneh on 2012-02-01
Hi there, 

I don't usually like my first post on a forum to be asking for help, but I'm really stuck and I hope that someone can help me. I've just started using Ubuntu today (v11.10) and I've never used any kind of Linux install before.... so please be gentle :)

I've installed 11.10 and tried to connect it to my Wireless network at work to use Wireshark as we've been having some problems with our Wireless telephone system. I can connect to other wireless networks with no problem, so the WiFI card seems to be working ok. 

Unfortunately, the network I need to connect to, is on VLAN5 on my network. I can't seem to figure out how to set a VLAN in the settings anywhere. I did some research and used some Terminal commands to try and do this manually (made some changes to /etc/network/interfaces) I'm sure I probably did this incorrectly as it cause the machine to take much longer to boot, and whatever I did didn't work anyway so I reverted my changes back to default. 

Can someone please point me in the right direction as to how I connect to a particular SSID and set the VLAN to 5? I'd appreciate any help that anyone is willing to offer. I did do a search but couldn't find anything relating to my problem. 
I don't think I am smart enough to use even a GUI based Linux :D

Thanks for taking the time to read
Best Regards 

:)

PS - Sorry for my English, it's not my first language.

---

### Post by WthIteh on 2012-02-01
Welcome to forums ;)

If you mean [Virtual LAN]("http://en.wikipedia.org/wiki/Virtual_LAN") from VLAN, I should note that it could not be configured from your machine. VLANs are configured on ports of switches to divide LAN in several logically separated layer 2 networks.

Do you get connected to that wireless network but could not continue sending/receiving packets? or it fails before connecting?
Only the first case could be related to VLAN. If it's the case, try pinging gateway IP which should be in your own VLAN. If the second case is true, first try using graphical network manager (the radio icon in top-right side of the screen) to find and connect to that network.

---

### Post by seveneh on 2012-02-02
Thanks for taking the time to reply WthIteh,

Hmmm.... this is probably lack of knowledge on my part then. The wireless network is used by our phone systems and I have to actually input 'VLAN 5' on the phones themselves when connecting to the network, so I assumed I'd have to do the same on a laptop. 

When I try to connect to the WLAN on a laptop, I can see the network, it just never connects. Never mind, from the sounds of it this isn't an Ubuntu issue so I don't expect people to help me with this problem. 

Thanks for the help anyway, I appreciate it :)

On a side note - Ubuntu is pretty cool, functionality seems good, it also seems fairly easy to for a windows user to transition too, I've not really had any trouble navigating my way around it. It's easy on the eye too which is a nice touch :)

---

