---
title: "Internet Connection Sharing with Dial-Up"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by King_Critter on 2009-08-18
Here's the deal: I have two computers. One computer connects to the internet via a dial-up modem, and the other computer is connected to the first via LAN. Until yesterday, the first computer was running Windows, and Internet Connection Sharing was working perfect. Now? Not so much.

The actual Internet is working fine (I'm typing this from the first computer). And after some fiddling around, I finally got a LAN back up and running using wicd... but the problem is that when the LAN is up, the internet is unreachable. No idea why. There's no option that I can see in wicd for ICS, so I did a few google searches. Plenty of solutions... and none of them worked. 

So, I ask you: is there anyway of setting up Internet sharing as easy as it was in Windows?

---

### Post by superprash2003 on 2009-08-19
try this [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) or you could use firestarter

---

### Post by King_Critter on 2009-08-19
Awesome -- that guide worked perfect! Well, mostly perfect -- I did find that I had to add a connection using network-manager on the client, but whatever. All good now. Thanks. ^_^

---

### Post by King_Critter on 2009-08-21
OK, looks like  I spoke a bit too soon, because I have two problems.

First, I have to reapply the settings everytime the computer reboots. Is there a way to lock them down?

Second, Pidgin's Bonjour plugin is not working. The avahi-daemon is running on both the computers, so I really don't know what's wrong.

---

