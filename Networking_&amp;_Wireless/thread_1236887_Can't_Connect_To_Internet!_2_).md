---
title: "Can't Connect To Internet! 2 :)"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by Ichido on 2009-08-10
I'm having the same problem with a friend's Desktop PC.

"Network Tools":
eth1
Tx Bytes 14.4kb
Tx Packets 78
Rx Bytes 11.3kb
Rx Packets 58
MAC *Shows Correct MAC*
Multi-cast Enabled
MYU: 1500
Link Speed: Not Available
State: Active

"Connection Info":
eth1
Mac *shows correct MAC*
Driver 8139too
Speed 100Ms/s
Security None
I.P. *shows correct I.P.*

"Terminal" *sudo ifconfig*
eth1 MAC
Rx Packets 116, Errors 0,Dropped 0
Tx Packets 136, Errors 0, Dropped 0
Interrupt: 21
Base Add: 0xc800

I thought that the On-Board Ethernet was bad so I installed a PCI 10/100 Ethernet Card, but we still cannot get On-Line!?
I also tried different Cat5e cables.

Can anyone help, please?

---

### Post by jgull8502 on 2009-08-10
Ichido, you say that the IP address is correct. Is this the local IP you're talking about? Can you connect to the router through your browser? If so, perhaps you aren't getting the correct DNS servers via DHCP. (This has happened to me before, although on wireless) 

You could look at the internet settings of a Windows computer or [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/) to get some DNS servers and then add them to network manager.

---

### Post by Ichido on 2009-08-10
To ebartolon; First let me apologize for the apparent "Hi-Jacking".
I am having the same type of problem, and I also seek help.
The more info we give, the better are our chances of finding a "Fix"!

> **jgull8502 said:**
> Ichido, you say that the IP address is correct. 
Is this the local IP you're talking about? Can you connect to the router through your browser? If so, perhaps you aren't getting the correct DNS servers via DHCP. (This has happened to me before, although on wireless) 

I didn't try to connect to a router because he connects directly from his modem.
Thanks for the tip! I will try to connect to his modem's I.P..:)

You could look at the internet settings of a Windows computer or [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/) to get some DNS servers and then add them to network manager.

I took my Dell 1525n Laptop over to his house and I connected his Cat5e cable to my PC.
It worked! I can get on-line and 'surf' without ant trouble.

I check the "settings" in both PCs, "IPv4 = Auto DHCP", "Network Tools", "Connection Info", "Terminal" *sudo ifconfig* and I cannot find any difference, except of course the MAC Address :confused:
This is why I installed a new PCI Ethernet Card.
Thank you for your reply.

---

### Post by overdrank on 2009-08-10
> **Ichido said:**
> To ebartolon; First let me apologize for the apparent "Hi-Jacking".
I am having the same type of problem, and I also seek help.
The more info we give, the better are our chances of finding a "Fix"!





I have moved your post to its own thread. :)

---

### Post by Ichido on 2009-08-13
> **jgull8502 said:**
> Ichido, you say that the IP address is correct. Is this the local IP you're talking about? Can you connect to the router through your browser? If so, perhaps you aren't getting the correct DNS servers via DHCP. (This has happened to me before, although on wireless) 

You could look at the internet settings of a Windows computer or [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/) to get some DNS servers and then add them to network manager.

I am able to connect with my Laptop running the same Ubuntu 9.04.
All the settings I can find between the two PCs are identical.

---

### Post by Iowan on 2009-08-14
Re-establish baseline - some info didn't make the transition. Your 9.04 laptop works on friend's connection. His doesn't?

---

### Post by Ichido on 2009-08-15
> **Iowan said:**
> Re-establish baseline - some info didn't make the transition. Your 9.04 laptop works on friend's connection. His doesn't?

Correct.
I plug his Cat5e into his PC, No joy.
I plug it into my Laptop, it works fine.
Same O.S., cable, settings.
I suspected his On-board ethernet went bad, so I installed a PCI Ethernet Card, but still no connection!?

---

### Post by Ichido on 2010-06-11
Now running 10.04 Lucid Lynx and problem is gone.

---

### Post by Iowan on 2010-06-11
Wow! Took awhile, but glad you finally got it. :)

---

