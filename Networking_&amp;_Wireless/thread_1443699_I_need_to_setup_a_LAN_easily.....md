---
title: "I need to setup a LAN easily...."
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by Blacklightbulb on 2010-03-31
between two Ubuntu machines. I need to be able to share folders and an internet connection. How can I manage this? Thanks!

---

### Post by Blacklightbulb on 2010-03-31
OK following this guide: 

[https://help.ubuntu.com/9.04/internet/C/connecting-wired.html](https://help.ubuntu.com/9.04/internet/C/connecting-wired.html)

and using ifconfig 

I managed to establish a 100Mbit/s connection between the two.

Now I need to figure out how to manage folders and internet connection through the eth0 network.

Anyone help me please?

---

### Post by Blacklightbulb on 2010-03-31
OK I installed and am trying to configure firestarter however it returns the error 

Failed to start firestarter device ethX is not ready. 

If this help Network Manager doesn't recognise my internet or my lan connection either however both are up and running.

Help.

---

### Post by Blacklightbulb on 2010-03-31
OK so I'm trying to get network manager to recognize my connections figuring firestarter will follow on my success however although network manager is working and so is the nm-applet I can find in in my notification area. I restart the computer and the gnome panel already.

Help.

---

### Post by Blacklightbulb on 2010-03-31
```
gksu gedit /etc/network/interfaces
```

Went there deleted everything and saved.
Network manager works fine know.

---

### Post by Blacklightbulb on 2010-03-31
Firestarter is finally up and running however it returned an unknown error with unknown consequences. 

However now I have not idea was else to do. I have 2 connections established:
1. LAN through 8p8C/Rj45 from one NIC to another.
2. USB connection to ADSL modem (internet)

How should I proceed to get the client to share the internet connection of the host?
How do I share folders?

---

### Post by theozzlives on 2010-03-31
I could help if you're using SAMBA, but NFS will have to wait til after my Linux+ class. Seems like you're doing OK on your own, however.

---

### Post by 98cwitr on 2010-03-31
buy a router, jp...kinda...well...not really

Current Solution:
you'll need to set up an ad hoc network:

You'll need to set static IPs (private Class C addresses), DNS and Gateway to whatever the modem has set

---

### Post by theozzlives on 2010-03-31
> **98cwitr said:**
> modem + router = done

It's not a simple as that and you know it!

---

### Post by 98cwitr on 2010-03-31
no, it's as simple as that on 9.04+

anyways, see edit.

---

### Post by Blacklightbulb on 2010-03-31
> **98cwitr said:**
> buy a router, jp...kinda...well...not really

Current Solution:
you'll need to set up an ad hoc network:

You'll need to set static IPs (private Class C addresses), DNS and Gateway to whatever the modem has set

I was under the impression that this could be achieved without the need for a router by setting up a dhcp server from the host???

---

### Post by lisati on 2010-03-31
> **theozzlives said:**
> It's not a simple as that and you know it!

It sounds like our experiences differ in some aspects......

---

### Post by 98cwitr on 2010-03-31
you said easy...the easy way is using static IPs...

it can be achieved without a router, read my post. A current router would PROPERLY handle any protocols you try to pass across the network, if you're going to try and use UPnP or other secondary protocols you may want to take that into consideration before progressing and relying on an ad hoc network to fulfill your needs.

---

### Post by Blacklightbulb on 2010-03-31
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Hopefully my last post in this thread.

---

### Post by 98cwitr on 2010-03-31
deleted...found some answers to my questions :)

---

