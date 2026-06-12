---
title: "Internet bandwidth does not share effectively"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by JFekete9076 on 2011-05-16
Hello.

I have an Ubuntu box, and there are two another PCs with Windows XP at my home.
There is a TP-Link WR340GD wireless broadband router, and a Motorola SB5101E cable modem. Maximum download speed of the Internet connection is about 6 Mbit/sec.

While I'm starting some download processes on the Ubuntu box, the other two PCs get only small bandwidth according to their users, although download speed on my computer does not often exceed its maximum.

More precisely: I usually download files at approx. 1 Mbit. The other users complain about that I slow down the Internet connection at their computers, and tell me to stop using the Internet.

Is it possible to improve the usage of internet bandwidth, and share the connection fairly between computers?

I'm looking forward to your answers.

JFekete9076

---

### Post by poolet on 2011-05-16
Yes can share your bandwidth accorting to your needs.... The only thing that you need is to use a router which is capable of QoS (Quality of Service.) This kind of router controls your traffic....

First of all you need to assigned static IP address in all your computers... 

on ubuntu:
gksudo gedit /etc/network/interfaces

auto "interface name"
iface "interface name" inet static

address 192.168.X.XX
gateway 192.168.X.X (The same as your router)
netmask 255.255.255.0
network 192.168.X.Xbroadcast 192.168.X.XX

windows: 
Control Panel -> network
Right Clicklocal area connection, select and click **Properties.**
 Select Internet Protocol (TCP/IP) and go to properties

The IP address should be in range of 192.168.1.2 to 192.168.1.253... Be sure that the IP of each computer are different. Your gateway is the ip of your router and your DNS (contact with your ISP) 

**Note: **
Before you do anything of the above make sure that your ISP supoort Static IP... Usually cable networks doesn't allow you to assigned static IP  since cable modem service uses a shared cable line to provide service to an  entire neighborhood. Essentially, all cable customers in the region  belong to the same LAN. So contact with you ISP first...
 
When you finished with the the above just login as admin on your router and follow, the structure of the LINK 

[http://www.tp-link.com/support/showfaq.asp?id=194](http://www.tp-link.com/support/showfaq.asp?id=194)

I hope to help you!!!!

---

