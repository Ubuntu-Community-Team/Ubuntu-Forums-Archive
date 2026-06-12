---
title: "Issues with Netbook Wireless Hotspot"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by kaspar_silas on 2011-05-06
Hi Guys, 

I am looking for a little bit of help basically setting up a netbook's wireless access point (to allow remote connection to a network drive connected to the netbook). I know this sounds daft but there is a reason.

I just switched workplace and have all my projects on one drive. 
However my new workplace's network only assigns ip to certain Mac addresses. So I can't just plug in the network drive. 
My new work desktop is MS loaded, warranty sticker sealed and shared so I can't change this. 
Well I will, but not in the first week. 

The simplest solution I thought of was to bring in my ubuntu netbook connect this to the network drive and wirelessly connect the netbook to the new desktop this via a wireless USB dongle. 

I connected the netbook to the network drive with no problem using the wired card. I done this by adding

```
auto eth0
iface eth0 inet static
    address 192.168.4.1
    network 192.168.4.0
    netmask 255.255.255.0
    broadcast 192.168.4.255
    gateway 192.168.4.1
```

to /etc/network/interfaces setting the network drive to a static ip of 192.168.4.2 and restarting networking.

For the wireless bit, on the netbook, I right clicked on the network indicator icon and selected "Create New Wireless network" then entered a network name and WEP passphase. 

Over to the desktop (XP). I plugged in a wireless dongle, get it load the driver then selected my new network and entered the passphrase. It came up connected and sure enough I check and it got assigned a sensible IP.  

All seemed well and I even connected my android phone with no issues. The phone and desktop can ping each other. However for some reason I can't actually ping or ssh to or from the netbook. 
So whilst it's happily providing the wireless network it can't use it itself.  

Any one got any ideas, what wrong or why this is. 
Thanks for any help.


p.s. Incidentally I am allowed to plug in USB drives so this isn't an access issue or me trying to sneakily circumvent rules. I even told my IT department about the wireless dongle plan.

---

### Post by kaspar_silas on 2011-05-06
I actually "solved" this by letting my phone act as a hotspot.

So now the crazy path between desktop to network drive is Desktop wireless dongle connection via android hotspot to Netbook's shared wired connection.

Not exactly elegant or good for the phone's battery life.

If anyone has other suggestions, let me know.

---

### Post by kaspar_silas on 2011-05-06
Okay I have fully solved my problem (as in now the netbook hotspot is working) by deleting all the settings and exactly copying the steps in the following video. 
No idea what was different or wrong last time but I just don't care:

[http://www.youtube.com/watch?v=pt-gFJTgp9k]("http://www.youtube.com/watch?v=pt-gFJTgp9k")

My talking to myself will henceforth cease.

---

