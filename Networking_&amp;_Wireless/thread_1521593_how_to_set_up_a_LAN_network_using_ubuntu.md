---
title: "how to set up a LAN network using ubuntu"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by abhigyan91 on 2010-07-01
This is a hypothetical situation:
Suppose there is a building which has Ethernet wiring already done i.e if there was a LAN port in every room of the building. Basically, im assuming that all the required hardware is already available and installed. I now want to start the network.. how do i do it? do i just physically connect the computer nodes to the lan ports in the rooms or do i need a central server or something to start it out. Basically how to give "life" to the network.. i presume there is some server at work.. 
Please give me an overview of how this all works...


also is it possible to connect two windows xp or vista or 7 or ubuntu karmic/lucid machines directly using a cross-over/straightthrough Ethernet wire to start a small LAN connection? 
Thank you!

---

### Post by McRat on 2010-07-01
> **abhigyan91 said:**
> This is a hypothetical situation:
Suppose there is a building which has Ethernet wiring already done i.e if there was a LAN port in every room of the building. Basically, im assuming that all the required hardware is already available and installed. I now want to start the network.. how do i do it? do i just physically connect the computer nodes to the lan ports in the rooms or do i need a central server or something to start it out. Basically how to give "life" to the network.. i presume there is some server at work.. 
Please give me an overview of how this all works...


also is it possible to connect two windows xp or vista or 7 or ubuntu karmic/lucid machines directly using a cross-over/straightthrough Ethernet wire to start a small LAN connection? 
Thank you!

The most common way is it have a router (usually your internet access point) which assigns each machine it's own local IP address, such as 192.168.0.10, then 192.168.0.11, then 192.168.0.12, etc.  This is done through DHCP.  Inside your router is a check box for DHCP service.  When you check it, you will also have to give it a range, say 192.168.0.10 to 192.168.0.50.  Then as new computers hook up to the LAN, the router gives them an address.

To share files, you go into your PUBLIC directory and change the permissions on each computer to READ/WRITE.  In Windows it's called sharing.

---

### Post by abhigyan91 on 2010-07-01
> **McRat said:**
> The most common way is it have a router (usually your internet access point) which assigns each machine it's own local IP address, such as 192.168.0.10, then 192.168.0.11, then 192.168.0.12, etc.  This is done through DHCP.  Inside your router is a check box for DHCP service.  When you check it, you will also have to give it a range, say 192.168.0.10 to 192.168.0.50.  Then as new computers hook up to the LAN, the router gives them an address.

To share files, you go into your PUBLIC directory and change the permissions on each computer to READ/WRITE.  In Windows it's called sharing.

is there a link or reference which explains all this properly starting from scratch?

---

### Post by McRat on 2010-07-01
> **abhigyan91 said:**
> is there a link or reference which explains all this properly starting from scratch?

Simple ethernet networks are star shaped, with the router in the center.  If your building is pre-wired, there SHOULD already be a router (sometimes it's called a firewall) where all the ethernet wires meet in the center.  The previous tenant might have removed it though.  The router has multiple ports that go to the computers, and the one port that goes to the internet modem.

Most of today's routers have built-in help as far as setting them up goes.  A good router can be had for under $50.  If you are going to use an internet connection make sure it says internet.  One of the ethernet ports on it will be a different color.  This one goes to the cable modem, dsl modem, or satellite modem.

As far as setting permissions, all different computers do it slightly differently.  Normally you will right-click the folder you want to share and look for Options, Sharing, Get Info, Permissions, etc.  I'm on a Mac tonight, and it's called Get Info.  Most computer will "see" the network automatically when they are plugged into it.  If other computers are on the network, you will see them by finding the Network folder.  

If you have a "mixed" network with a Linux machine on it, you need to load SAMBA from the Software Library in Ubuntu to easily access the Windows machines and share resources with them.

---

### Post by Sanjeevtrip on 2010-07-01
you can find many sites for setting up network
e.g.
[http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
[http://www.reallylinux.com/docs/sambaserver.shtml](http://www.reallylinux.com/docs/sambaserver.shtml)

if you can give ip addresses to your machines then you can setup to
connect two windows xp or vista or 7 or ubuntu karmic/lucid machines directly using a cross-over/straightthrough Ethernet wire to start a small LAN connection.

---

### Post by Moozillaaa on 2010-07-01
I think when OP says start from scratch, he might mean literally the physical interfacing...
> 
do i just physically connect the computer nodes to the lan ports in the  rooms or do i need a central server or something to start it out.Yes. It's like people communicating. You can have one person standing in the door, who relays all messages, from people inside the room, to the outside world, OR, each person in the room can have access directly to the outside world. Each person in the communication link MUST hear (ping) AND see (MAC?) who's communicating.

> also is it possible to connect two windows xp or vista or 7 or ubuntu  karmic/lucid machines directly using a cross-over/straightthrough  Ethernet wire to start a small LAN connection? 
Yes - 2 people in the room can talk directly to each other, or talk to each other through the person in the doorway.

But there's a couple of ways to do this, if you want multiple computers in your own LAN.

You can do as was first suggested, by connecting a router to the ethernet port, and then plugging each computer INDIVIDUALLY with hardwire or wireless into the router.

OR

You can connect one computer directly to the ethernet port, and have it serve as the router, with your other computers connected to the first computer wirelessly (if it has a wireless card), or hardwired (less practical).

Then if connections and IP assignment is not automatic, you'll have to start pinging / scanning / log on to router 'page' / etc, as the other have posted...

What hardware (computers/wireless/ethernet cabling) do you have now?

---

