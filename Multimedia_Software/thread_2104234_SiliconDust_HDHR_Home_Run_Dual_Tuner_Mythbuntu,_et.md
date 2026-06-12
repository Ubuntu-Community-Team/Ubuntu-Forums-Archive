---
title: "SiliconDust HDHR Home Run Dual Tuner Mythbuntu, etc"
date: 2013-01-12
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2013-01-12
I have purchased a SiliconDust dual tuner. I use XFCE for my desktop. This is 32-bit Ubuntu Precise Pangolin ver. 12.04LTS. 

Does the Mythbuntu or MythTV requre 64 bit OS?

If "NO" then is Mythbuntu a set of packages that install just like Adobe Acrobat Reader (acroread) or the GIMP?

If the Mythbuntu is it's own OS, can I create a partition on the same drive as my 32-bit Ubuntu Precise Pangolin ver. 12.04LTS to provide for a 64-bit environment???

I would like to install new packages, and have a personal video recorder (PVR) which accesses my over-the-air broadcast TV Channels. I believe the SiliconDust does this as hardware.

I've read up at SiliconDust's Docs pages, LinuxTV, and assorted how-to's. For instance here is a paste of some info from the MythTV wiki:

[INDENT]"The HDHomeRun normally expects to obtain a DHCP lease. However, with the latest firmware it is also possible to configure it statically. This is particularly convenient if you want to connect the HDHomeRun directly to a NIC on your MythTV system, rather than through a switch on your network. To do this, configure your local interface with a static IP address in the range of 169.254.x.x (eg. 169.254.1.10) with a subnet mask of 255.255.0.0 and no gateway. No need to configure routes, the HDHR's will not be accessible to devices on your existing network, but your backend should have no problem seeing them."[/INDENT]

To which I must say: WWHHHAAAA?

If anyone reading this far knows a a beginners guide to Myth/buntu, please reply to this post with a link (URL). I'm a pretty fast reader.

---

### Post by gordintoronto on 2013-01-12
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by Mark_in_Hollywood on 2013-01-14
Upon reading up at the site of the URL, above, I see I must install MythTV from repos. All well and good, I know how to do that. My question is now (and pardon my ignorance, please) of the two packages: 

MythTV Backend Setup 

MythTV Fronend

HDHomeRun Config-gui

does it matter in which order they are installed? Does it matter if the "tv tuner card" is attached (by cables, ethernet, or sits on the computer's bus) FIRST, or can these Myth packages be installed and then the hardware added?

If I get enough "Pre-Information" I'll write up a Step-by-Step How-To for MythTV on Ubuntu.

---

### Post by gordintoronto on 2013-01-14
I'm sorry, I don't *know* the answers to your questions. I think I know that the Homerun is a device which sits on your network, attached to your router by Ethernet or wireless.

If it were my system, I would install backend, homerun-config and frontend in that order, then I would run homerun-config, backend, frontend. And maybe that wouldn't work. (You understand that Myth is often installed on two different computers, one connected to the media source, the other connected to your TV. However, both parts can be installed on a single computer.)

I often scan through the forums looking for questions which have not gotten a response. If I have half a clue on the topic, I will suggest it, more as a method to get you to the next step, even if I can't provide a perfect response.

---

