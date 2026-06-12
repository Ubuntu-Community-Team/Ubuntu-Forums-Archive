---
title: "VLC window goes black after 10 mins playing DVD whereas totem (xine) is OK!"
date: 2009-09-28
forum: Multimedia Software
---

### Post by feizex on 2009-09-28
Hi Guys,

Not sure if this is the right place to post this.

I am using 9.04 desktop and VLC 0.9.9a to run DVD.

VLC window goes black after about 10 mins playing DVD, but audio is OK. Playing video from network share is fine. Also using totem xine for DVD is fine.

The only thing that fixes the black screen is stopping and starting DVD.

Any idea what is causing VLC to behave like this?

Thanks,
Feizex.

---

### Post by feizex on 2009-10-20
Hi Guys, 

I posted issue on videolan forum and got a solution.
[http://forum.videolan.org/viewtopic.php?f=13&t=66694&p=222295#p222295]("http://forum.videolan.org/viewtopic.php?f=13&t=66694&p=222295#p222295")

Upgrading VLC to 1.1.0 fixed it.

I decided to put together a brief how to for those that have similar issue. See below...

Regards,
Feizex.

HOW to install VLC on UBUNTU 9.04 (Jaunty) from PPA repository

Run:
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D

Edit /etc/apt/sources.list
Paste the following lines:
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main

NOTE: If you're using another version of ubuntu, check this page for different PPA to add...
[https://launchpad.net/~c-korn/+archive/vlc]("https://launchpad.net/~c-korn/+archive/vlc")


Run:
sudo apt-get update

You should not get any errors.

Open:
System > Administration > Synaptic Packagage manager
Click "Origin" button at bottom left
Select and highlight launchpad PPA from list above the buttons (the PPA you just added above ^^)

If you already have VLC installed click "Mark All Upgrades" on the toolbar.
Otherwise you will need to select it for install from list on right.
Click Apply.

This should install latest VLC all going well.

---

