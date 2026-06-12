---
title: "Wired Network disconnected when cable from Switch"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by mnaumanca on 2012-11-25
Hi,

I did a lot of research to resolve "Wired Network disconnected" issue but I couldn't find any good information so now I am writing in this forum to get help.

I have installed ubuntu 12.10 and have three quad nic ethernet card + 1 ethernet port in motherboard, All ethernet ports are being detected by ubuntu and if i plug my internet cable in any port , i can browse the internet without any issue and it also help me to understand that my quad nic cards are fine since i use all the port to connect internet one by one, but if I take cable from cisco switch and inject in one of my quad nic card port, ubuntu shows the stauts connecting and then it shows "Wired network disconnected" and this keep happening all the time connecting and disconnected.

but on the same port if i inject the internet cable it works and it shows "Wired network connected" but it won't work when cable is coming from Switch.

I read different threads and tried to implement all sort of solution but it won't help

Now I am looking your help I hope you can put me in the right direction.

My quad nic card specs after running the lscp

Digital Equipment Corporation DECchip 21142/43 (rev 41)

Regards,

---

### Post by bab1 on 2012-11-26
> **mnaumanca said:**
> Hi,

I did a lot of research to resolve "Wired Network disconnected" issue but I couldn't find any good information so now I am writing in this forum to get help.

I have installed ubuntu 12.10 and have three quad nic ethernet card + 1 ethernet port in motherboard, All ethernet ports are being detected by ubuntu and if i plug my internet cable in any port , i can browse the internet without any issue and it also help me to understand that my quad nic cards are fine since i use all the port to connect internet one by one, but if I take cable from cisco switch and inject in one of my quad nic card port, ubuntu shows the stauts connecting and then it shows "Wired network disconnected" and this keep happening all the time connecting and disconnected.

but on the same port if i inject the internet cable it works and it shows "Wired network connected" but it won't work when cable is coming from Switch.

I read different threads and tried to implement all sort of solution but it won't help

Now I am looking your help I hope you can put me in the right direction.

My quad nic card specs after running the lscp

Digital Equipment Corporation DECchip 21142/43 (rev 41)

Regards,

You are seeing the effects of Spanning Tree Protocol (STP).  This is normal activity.  There can only be a single active path between any two network nodes in an Ethernet LAN (subnet).  In other words; All nodes (endpoint) should have one port per LAN unless you bond the ports to create single path or a fall back situation (hot standby).

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/Spanning_Tree_Protocol") and [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.cisco.com/en/US/tech/tk389/tk621/technologies_configuration_example09186a008009467c.shtml") for STP info.

---

### Post by guardsman85 on 2012-11-26
Just to clarify, are you experiencing this problem when connecting only one network card is connected to the switch, or only when multiple cards are connected?  Multiple cards connected could cause the STP problem BAB1 mentioned.

If you're having the problem when only one card is connected, then you might check to see if port security (or sticky MACs or whatever it's called by Cisco) is enabled on the switch.  It's been quite awhile since I worked with Cisco, so I don't remember the exact behavior of the equipment, but essentially security settings can be enabled on the switch which only allow a device with a specific MAC address to connect.

---

### Post by mnaumanca on 2012-11-27
Thanks for your input, I have three cards connected to switch and I didn't test with one card and I didn't realize it is happening because of STP, I will check more on the weekend , so in order to set up a ccie lab i have to play with stp in order to run all those ports.

---

### Post by mnaumanca on 2012-12-01
Hi,

I tried to check if it is happening because of STP or not but STP is not the reason, since I removed all the cables from Switch and I connect only one cable from switch to Computer in the network card and now only one lan port should work but when i check the status of this port it says Connecting and then after few seconds Disconnected and it is happening all the time, STP won't work in single line.

Please help me since it is important for me to resolve this issue.

Regards,
Nauman

---

### Post by bab1 on 2012-12-01
> **mnaumanca said:**
> Hi,

I tried to check if it is happening because of STP or not but STP is not the reason, since I removed all the cables from Switch and I connect only one cable from switch to Computer in the network card and now only one lan port should work but when i check the status of this port it says Connecting and then after few seconds Disconnected and it is happening all the time, STP won't work in single line.

Please help me since it is important for me to resolve this issue.

Regards,
Nauman

Are you saying that the switch is not connected to the router also?  If so, you would only have 1 port on the switch connected to 1 port on one of the NIC's.  If this is the case what connection do you really have?  You would only have the NIC as an end node.

I think the problem (as you previously described) is due to the 1 host having multiple destinations in 1 subnet.  You do however need a source and destination before you can have traffic.  Is the port active but disconnected or maybe not configured?  I'll try and help, but I need more information.  Maybe a network layout diagram?

It helps to thing of each port on the NIC as an endpoint (node).  I'm sure if you check you will see that each port has a separate MAC (Ethernet) address.  Each node must have a separate MAC and IP address.

---

### Post by mnaumanca on 2012-12-01
Thanks bab1, I resolved my issue and now my switch is connecting to my gns3 router even though i am still getting this wired network disconnected message and connecting which is very confusing because I am new in ubuntu so my port is working and now I need to find out how i can disable these Wired network disconnected notification.

Regards,
Nauman

---

