---
title: "torrent download on remote network drive"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by Zacinfinite on 2010-09-14
Is it possible to download big files throught bit torrent client on remote PC's harddisk?
I use Ubuntu on my system with quite low diskspace, and my dad uses his laptop with large diskspace. Im using Transmission and Ktorrent clients.

Im able to mount his shared drive and save my files manually over Ethernet. But I want to download torrents directly from my PC to his laptop.


How to do that?

---

### Post by valbaca on 2010-09-14
> **Zacinfinite said:**
> Is it possible to download big files throught bit torrent client on remote PC's harddisk?
I use Ubuntu on my system with quite low diskspace, and my dad uses his laptop with large diskspace. Im using Transmission and Ktorrent clients.

Im able to mount his shared drive and save my files manually over Ethernet. But I want to download torrents directly from my PC to his laptop.


How to do that?
When you start a torrent, aren't you able to select the desired download location? 
With the drive mounted, it shouldn't matter if it's your hard drive, a flash drive, or a network mounted drive, it ought to download to the location you specify.

---

### Post by MaindotC on 2010-09-14
> **valbaca said:**
> When you start a torrent, aren't you able to select the desired download location? 

That's not really relevant because the traffic still goes the network interface of the machine initiating the torrent.

valbaca - there are two ways of which I know that you can do this.  You can enable [VNC (or on Ubuntu it's called vino-server)]("https://help.ubuntu.com/community/VNC/Servers") and this will enable you to control the desktop remotely, initiate the torrent download just as you would if you were sitting at the machine, and then close the VNC connection.  The torrent will continue to download.

The other way would be to start [Transmission ]("https://help.ubuntu.com/community/BitTorrent#Transmission"), execute the torrent download via [the web interface]("https://trac.transmissionbt.com/wiki/WebInterface").  If the ip address of the machine running Transmission was 10.0.0.2 you would access the web interface by typing in the address bar of a browser: [http://10.0.0.2:9091](http://10.0.0.2:9091)  Try running transmission on your own machine and browsing the web interface - notice what happens when you close Transmission.

---

