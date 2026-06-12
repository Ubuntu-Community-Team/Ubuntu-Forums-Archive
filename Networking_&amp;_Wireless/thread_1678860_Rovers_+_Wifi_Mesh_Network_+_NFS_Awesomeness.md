---
title: "Rovers + Wifi Mesh Network + NFS Awesomeness"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by Beyond Aphelion on 2011-01-31
Hi, I have a small problem, but it might require a bit of background:

I  am designing a multi-rover system for my capstone project which  utilizes WiFi as a primary means of communication. There is one mother  rover and two child rovers.  The  mother rover is effectively a netbook  running Ubuntu 10.10.  Each child rover has a Gumstix board with  embedded Linux and WiFi adapter.  All rovers have a dedicated mesh  router node that (for the sake of argument) will always be accessible by  the rover it travels with -- allowing communication between all rovers  as long as there is a path to hop from one to any other.

The  mother rover hosts an NFS file share such that file transfers are  transparent between the rovers and stored in a central location to be  passed to the ground station for parsing.

The ground station is a  computer which may or may not be running Linux.  The ground station  should in NO way whatsoever be able to communicate with the child rovers  wirelessly.  My solution to this was to place the ground station on a  completely different wireless network than the "Mesh" network the rovers  communicate over.

At this ponit, I've gotten gotten pretty much  everything working except for the ground station to mother rover part.  I  have a working NFS share wherein each rover can access and write to and  can be seen by the other rovers.  Each rover can ping each other rover  and each rover can ping each of the mesh routers.  I can easily SSH and  SCP between the rovers... etc.

Currently, I am using a laptop  with a built in wireless adapter (Intel PRO / Wireless LAN 2100 3B Mini  PCI Adapter) and an external USB wireless adapter (Ralink 802.11 n WLAN)  to be able to connect to two networks simultaneously.  In order to do  this, I am simply using NetworkManager, and assigning the MAC address of  an adapter to it's desired network.

According to NetworkManager,  I am able to connect to both the Mesh network and my home network, but  as long as I am connected to the Mesh network, I am unable to access the  internet.  As soon as I disconnect Mesh, the internet becomes  immediately available to me.

Switching between interfaces like  this works fine at the moment because I am not testing the full ground  station to child rover path, but I am unsure how this issue will  translate once the full path is in place.

The internet connection  is DHCP and the Mesh network is static.  I recall that after restarting  the mother rover laptop once, I was actually connected simultaneously  to both networks (I could access the internet while being SSHd into a  child rover); however, I haven't been able to recreate this behavior  since I have been tinkering around with settings to get other things  working.

Is there anything obvious that I should be looking for  or doing here that I'm missing?  A lot of configuration has gone into  this setup, but I feel like this one last piece should be pretty  straightforward -- I just don't know enough to get there and I'm not  really in the mood to start hacking again since everything is in a  pretty good place right now.

Any ideas would be appreciated.

Thanks!

---

