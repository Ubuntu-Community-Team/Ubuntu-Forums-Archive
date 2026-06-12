---
title: "Wired Connection not connecting"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by dinglebat on 2008-12-17
I'm having trouble getting the wired connection to connect. The only connection that shows up under 'Wired Network' when I plug in the Ethernet cable is Auto Ethernet. Connecting to this, however, only ever returns the message: "The network connection has been disconnected"

I have an XP on the same network, so I went to check what information THAT gave me about the network I'm trying to connect to. From that, I was able to obtain:

IP
Subnet Mask
Gateway
Physical Address
DHCP Server (both of them)
DNS
WINS Server (those words simply appeared at the bottom of all this info)


Now, I won't dismiss the possibility that the Netgear Powerline Adapter I own is the problem. I tried to use the same connection on both the Ibex and XP boots on my laptop to no avail. It seems that the only computer capable of connecting via wire is the main computer from which I obtained all the info. 

With that in mind, I've checked to make sure everything was connected, I've even swapped cables on everything just to make sure those weren't the problem.

Any suggestions or help would be greatly appreciated.

---

### Post by dinglebat on 2008-12-19
Help?

---

### Post by zman58 on 2008-12-19
> **dinglebat said:**
> I'm having trouble getting the wired connection to connect. The only connection that shows up under 'Wired Network' when I plug in the Ethernet cable is Auto Ethernet. Connecting to this, however, only ever returns the message: "The network connection has been disconnected"

I have an XP on the same network, so I went to check what information THAT gave me about the network I'm trying to connect to. From that, I was able to obtain:

IP
Subnet Mask
Gateway
Physical Address
DHCP Server (both of them)
DNS
WINS Server (those words simply appeared at the bottom of all this info)


Now, I won't dismiss the possibility that the Netgear Powerline Adapter I own is the problem. I tried to use the same connection on both the Ibex and XP boots on my laptop to no avail. It seems that the only computer capable of connecting via wire is the main computer from which I obtained all the info. 

With that in mind, I've checked to make sure everything was connected, I've even swapped cables on everything just to make sure those weren't the problem.

Any suggestions or help would be greatly appreciated.

First of all what does your network look like? Do you have a cable modem which is plugged into a powerline adapater which is then feeding your home power grid? Does the powerline adapter provide NAT and DHCP services to the nodes -or- does it work just like a network switch? In most cases, the cable modem will only provide configuration for ONE host. From what I have read "briefly" about powerline adapters, they only provide a network interconnect, such as a switch. You may need more than that. This may explain why only one system is getting a network configuration--that is all the cable modem will provide.

It is possible that you might need the WAN side of a broadband router connected to cable modem. Then plug the powerline adapter into the LAN side of the router. The broadband router will then provide DHCP (network IP config) and NAT (net address translation) for subnet hosts. To the cable modem, the router will look like one single host.

Cheers

---

### Post by superprash2003 on 2008-12-19
post output of ifconfig from the terminal

---

### Post by john_galt on 2008-12-27
Hello,

I am pretty new to Ubuntu and not so techy with respect to computers, so it may be possible that I may not be able to explain my problem accurately, but I will give it a try.

I am using Ubuntu Hardy Heron 8.04 on my laptop. The problem started about 3 months back when I noticed that it was **[SIZE="3"]taking some time(about 2-3 minutes) for the computer to detect the wired connection[/SIZE]** after plugging in the wire. I am accessing the internet through the Ethernet wire which has it's other end in a socket of our hostel room, which is fed by the college LAN. I tried to solve the problem by first making sure that I had the right IP, DNS server, Gateway, Host, Domain, etc. and that the Ethernet wire was fine. I also connected at different socket points(of a different hostel room), but the problem persisted, which led me to conclude that something had to be done within the computer.

After about one month the problem grew to such a level that it didn't detect the network at all and I had to do some crazy things to 'force' the computer to be connected. This post is a result of one of such crazy things.

Not only this, sometimes when I restart my computer, the problem doesn't show up and it detects the network after a few minutes.. But in many cases it doesn't.. 

what should I do now? Please let me know. Though I have read this thread, I would like to start from scratch.

Varun

---

