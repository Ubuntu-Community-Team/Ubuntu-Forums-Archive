---
title: "Ubuntu Server 12.04 eth subdevice? Avahi?"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by CarolusChristo on 2012-10-08
Hi!
First, excuse me for my somewhat bad english, it´s not my native language.
I am running Ubuntu 12.04 Server, mainly as a SAMBA backup and storage for my Windows PC and Mac.

I noticed when checking the local network map on my router that under my Ubuntu Server 12.04 that is connected to an eth port there is another "subdevice" connected with it´s own MAC adress and with a static IP adress. I use DHCP and i use reserved adresses for my devices, not static.

Something like this: 

Router 
|--------- eth1:ubuntuserver DHCP reserved: 192.x.x.x ----- otherdevice STATIC: 192.x.x.x
              | 
              |-------eth2 
              |
              |-------eth3
              |
              |-------eth4

What might this device be?
Except for SAMBA and XRDP i don´t have any other network services running on my server.
I did install Avahi and Netatalk to use for TimeMachine Backups, but the stability with that was not so good so i uninstalled them. 
Anyway, I suspect that Avahi is the "device". Based on research I would guess that it´s running as a separate host on my network. When i ran Avahi the TimeMachine share showed up in Finder as an Xserve beside my Ubuntu/Samba server.

Could someone clarify this and correct me if i´m wrong?
Is this the way Avahi works???
Or should i investigate further and suspect some kind of security breach?

Thankful for help.

---

