---
title: "wlan0 and eth0 both active but no internet connection"
date: 2012-07-12
forum: Networking &amp; Wireless
---

### Post by DrScum on 2012-07-12
I am trying to set up internet connection sharing through a desktop with a wireless card wlan0 connected to the internet via a Wlan router. I'd like to share the internet connection to a subnet connected through a wired connection eth0. I have followed the directions available in help.ubuntu.com.

Both cards are active, I can ping the wlan router as well as the systems connected to the subnet. Wlan router network and subnetwork are on different IP addresses. 

Here is the problem: as soon as I plug in the LAN cable, the internet connection is gone. If I unplug the LAN cable, the internet connection is back.

Obviously I am missing something.

Some help would be greatly appreciated.

---

### Post by Kirk Schnable on 2012-07-12
I have never tried to do something like this before, so I'm not 100% sure but I think this is what's going on:

By default, on Ubuntu and many other operating systems, when the wired network is plugged in, it defaults to that.  This allows you to be on your WiFi 24/7 but quickly plug in to obtain faster speeds\more reliable connection, etc.

I am betting we need to somehow tell Ubuntu to keep your WiFi the default connection, though I've never attempted this before.

I wonder if it's messing with your routing tables or something.  Could you post the output of this command BEFORE and AFTER plugging in the ethernet cable?

```
route -n
```

Wouldn't hurt to also do:

```
ifconfig
```

Kirk

---

### Post by Cheesehead on 2012-07-12
> **DrScum said:**
> I have followed the directions available in help.ubuntu.com.

Exactly which directions? [https://help.ubuntu.com/community/Internet/ConnectionSharing/](https://help.ubuntu.com/community/Internet/ConnectionSharing/) ? Which method on that page? There are several incompatible methods there.

---

### Post by DrScum on 2012-07-12
@cheesehead: I've followed the "Ubuntu Internet Gateway Method"

---

### Post by Cheesehead on 2012-07-12
Then Kirk Schnable is right. We need to see your routing table and ifconfig.

---

### Post by DrScum on 2012-07-13
In the meantime I solved the problem with no internet connection, when eth0 is plugged in. The solution: remove any gateway information from the eth0 configuration and make sure that eth0 connects BEFORE wlan0. I don't know exactly how I did the last but at some point I disabled wlan0, enabled eth0 and after the wired connection was established enabled wlan0. From then on the sequence was kept even during boot. A relieable indicator seems to be which network icon shows on the main menue bar. If it's the wlan icon things work ok, if it's the wired icon (two arrows, one up one down) wlan0 is still active, but there is no internet.

However, one problem remains: the internet connection is not shared. From a client computer connected to the eth0 network I don't have internet access.
The client computer also runs Ubuntu 12.04, it can ping both network adresses and it can ping the wlan router of the internet providing network. 
To set up the client I also followed the "Ubuntu Internet Gateway Method"
Are the routing tables necessary for this too? Isn't it dangerous to post ones routing tables?

Thanks for your help guys!

---

### Post by DrScum on 2012-07-13
I think I have the problem solved now.
I just went along and followed the instructions from [https://help.ubuntu.com/community/In...ectionSharing/](https://help.ubuntu.com/community/In...ectionSharing/) "Advanced Gateway Configuration. 
This makes the Gateway computer (the one with the two network cards) a DHCP server. If you configure the clients ethX to "automatic" i.e. it gets its IP address assigned from the DHCP server, internet connection sharing works.

Here the method in short:

Ubuntu 12.04 system with a wlan0 and a eth0 card
the cards configured on different subnets
follow help.ubuntu....(see above) "Ubuntu Internet Gateway Method" 
and then follow "Advanced Gateway Configuration"

Thanks for the help provided.

---

### Post by Kirk Schnable on 2012-07-13
Glad you got it working!  You should update your subject line to indicate your thread is Solved.

Kirk

---

