---
title: "Strange networking issues, would like some help"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by docmur222 on 2011-12-07
I have a very odd networking issue I haven't been able to solve. 

Networking Information:

Cable Modem: DCM-425
Wireless Router: D-Link DGL-4500
Wired Interface: Realtek RTL8111E chip (10/100/1000 Mbit)
Wireless Interface: TP-LINK TL-WN951N

Both the wireless and wired connections are active.

Computer Information:

CPU: i5-2500K ( Not Over-clocked well this issue exists )
Motherboard: GA-P67A-UD4-B3
Graphics: 2 x 5830 in Xfire Configuration
Sound Card: Creative XFi-Titanium 
Power: 80+ Gold 750W PSU 
Case: 500D Corsair
Hard Drives: 
SSD1: Vertex 1: OCZ - Main Linux Drive
SSD2: Vertex 2: OCZ - Main Windows Drive 
HDD1: 1.0 TB Western Black - Storage Drive 1 
HDD2: 1.0 TB Seagate - Storage Drive 2
HDD3: 1.0 TB Western Black - Storage Drive 3

Distributions that I've tested 

1) Gentoo
2) Ubuntu
3) Arch Linux

The Issue:

It seems that my cards are dropping from the router randomly and losing there address. 

Every so often I'll be in Firefox and the page will time out and then all the tabs time out. Last night I was playing around in the terminal and I was doing a terminal apt-get and I noticed that it just had halted for what I thought was no reason. I opened up a new terminal window and did an ifconfig and the interfaces had lost there DHCP lease.

Now it's a little hard to know where the issue is happening as it seems that the router is willing to reassign the lease back to the network interface after a short time < 1 minute, I can also tell dhcpcd to give me the address back.

I've noticed this problem the entire time I've been with this router, Windows doesn't seem have any issue with the router. I have the router configured in a basic mode with no fancy settings enabled or ports open etc...

I've had the same computer setup on an old network and never had any of these issues. I've tried to trouble shoot this and got no where, I'm really lost on what to try next.

Has anyone ran into similar problems? Does any one have an idea on what to try next?

Right now I'm in Ubuntu and I've tried disabling IPV6 and that had no effect

---

### Post by bluexrider on 2011-12-07
sounds like you have narrowed it down already with testing 4 distros. if you have the same result using all the linux distros then it probably is your router.

---

### Post by docmur222 on 2011-12-07
Well I'm wondering but I've never heard of a router causing issues that are Linux wide.  I can't find any reports on Google about this issue happening.  Also I have a server in the same room that is running Ubuntu and it connects to the same Router and has no issues.  

This leads me to believe that the problem is focused to the actual computer.

---

### Post by bluexrider on 2011-12-07
> **docmur222 said:**
> Well I'm wondering but I've never heard of a router causing issues that are Linux wide.  I can't find any reports on Google about this issue happening.  Also I have a server in the same room that is running Ubuntu and it connects to the same Router and has no issues.  

This leads me to believe that the problem is focused to the actual computer.

can you really say that? how hard do you LOAD the server. have you monitored the TX/RX packets on the server, that may also give you a clue

---

### Post by docmur222 on 2011-12-07
I have not monitored the server, however I do use it to stream HD movies to and from, it hosts a minecraft server that has 4 active people using it, a git hub that is hit randomly and a small private webpage internal to the house. 

If I take the server offline my desktop computer has the same issues.  If I have the server on near to nothing load aka have all the processes stopped I still have the same issues and if it's at full load again I have the same issues.

The main router is a DGL-4500 and the Cable Modem is the DCM425 from techsavvy.  I would try to follow this up with DLink but last time I called them the lady on the other end was so clueless about what a router even was I had to hang up.   There customer service is a series of Asian speaking people who read a screen and only ask if you have an ip address.  To top it off they don't even know what an IP address as I asked last time I called.  I don't want to sounds racists or prejudiced to them, just being accurate.

---

