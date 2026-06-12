---
title: "Networking with Android: Sharing a tethered connection with an additional laptop?"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by Dr.Helperstein on 2011-03-23
Hello,

First off let me explain the problem I'm trying to solve:

I have an Android 2.2 phone that tethers its internet connection through USB to a laptop running Ubuntu 10.10. What I want to do is share this internet connection through an ethernet cable with another laptop running Ubuntu 10.10.

**I've been looking on the internet but I haven't seen any cases of anyone else trying to to do this. If anyone knows of any resource for this, please let me know.**

I believe that I have gotten it the devices to communicate one way via ping but I cannot go the other way. This is where I believe the internet connection is getting blocked.

How I did this was through Firestarter installed on the machine the phone is plugged into and using the following guide: [http://www.fs-security.com/docs/connection-sharing](http://www.fs-security.com/docs/connection-sharing).

Basicly, the interface that is giving the connection is usb0 and im trying to share the connection through eth0. I basicly just followed the above guide, replacing the instances of eth0 with usb0 an etho1 with etho0. The only thing it says to do that I'm not able to do is to enable DHCP on the Android phone, because frankly I don't know how.


I manually configured the network instead of using Firestarter's DHCP option because I'm hoping to ultimately not have to use firestarter to do this. 

To be more specific, this is what I did:
through the GUI Network Connections:

On the first laptop (the one connected to the phone)

IP address: 192.168.0.1
Netmask: 255.255.255.0
Default gateway (IP): <leave empty>

On the second latop, again through Network Connections:
IP address: 192.168.0.2
Netmask: 255.255.255.0
Default Gateway: 192.168.0.1
*My /etc/resolv.conf file actually doesn't show anything so that may be a problem.

*Also I just tried to share my wireless connection through ethernet through Firestarter and that didn't work either. I can ping between the two laptops but I can't get internet. 

At the bottom, it tells how to test the setup. I can ping 192.168.0.2 like it says in the guide and get a response. However, I can't go to google.com on the laptop thats supposed to be getting the shared connection. In addition, on the 2nd laptop, I can ping to the phone. However, I can't ping from the phone to the 2nd laptop. This is why I believe I can't get to the internet.

I'm at a loss for what I need to do to get this connection to work. Do I need to brige the connection between usb0 and eth0 on the latop the phone is connected to? or is that what Firestarter is already doing?

**Side note: I cannot ping from the 2nd laptop to the phone if I turn Firestarter off on the machine it is running on.

If anyone has an idea of how to get this working, it would be greatly appreciated.

---

