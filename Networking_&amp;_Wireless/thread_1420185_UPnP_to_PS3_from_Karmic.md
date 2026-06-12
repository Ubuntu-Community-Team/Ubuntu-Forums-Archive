---
title: "UPnP to PS3 from Karmic"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by OwnLife on 2010-03-02
Hello, 
I want to do the upnp deal to my ps3. I'm running Karmic and have a Linksys router and I want to stream from an external HD(usb). I've been searching for two days to find a good walk through but every guide I find is completely different, I can't cross check anything.

Please guide me in the right direction!

---

### Post by Neezer on 2010-03-02
> **OwnLife said:**
> Hello, 
I want to do the upnp deal to my ps3. I'm running Karmic and have a Linksys router and I want to stream from an external HD(usb). I've been searching for two days to find a good walk through but every guide I find is completely different, I can't cross check anything.

Please guide me in the right direction!

I found two ways to do it...My server at home uses mediatomb. It works great. Look around for a guide to install it and configure it. I know it is in the repos, so you can just apt-get it.

One note, when you set it up, make sure you have your server and your ps3 set up for static IP. I ran into a bunch of errors if I didn't have that set up.

---

### Post by OwnLife on 2010-03-02
[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mediatomb
[/B]
I get this error with sudo apt-get install mediatomb. I can't find it in SPM either. Somehow under places I have upnp mounted but I have no idea what I'm going to do with that. This is the part where I wait for the light bulb.

---

### Post by Neezer on 2010-03-02
do you have the universe repository enabled? go System -> Administration -> software sources to check. make sure you have the universe and multiverse repos checked.

Then do a sudo apt-get update
sudo apt-get upgrade

then sudo apt-get install mediatomb

Also, you can check synaptic if that doesn't work. It should be there.

this might help as well.
[https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb)

---

### Post by buntunoob on 2010-03-02
I myself love mediatomb, its extreamy flexable. with that heres one of the best howtos [http://wiki.flexion.org/InstallingMediaTomb012.html](http://wiki.flexion.org/InstallingMediaTomb012.html),
that has the ffmpeg/transcodeing in it, if you have anyprobs with it just repost, if I rember right he did leave a few things out like d/l a compiler to build it all
 
EDIT:forgot to add a lil part about the USB drive, wanted to give you the best chance to get it going as good as can be.
 
Mediatomb will be started before you logon and mount the USB drive, and dooing so will remove everything from mediatomb that's on that drive forceing you to reimport that drive, 
to fix that mount the drive at boot, please backup anychanges your going to make.
sanderd17 shows you how if you dont know [http://ubuntuforums.org/showthread.php?t=1373939](http://ubuntuforums.org/showthread.php?t=1373939)

---

### Post by OwnLife on 2010-03-03
I don't know what the issue was with this computer, but I found a different path.

PS3 Media Server Guide:
[http://www.infobarrel.com/HOWTO:_PS3_Media_Server_on_Ubuntu_9_10_karmic_koala](http://www.infobarrel.com/HOWTO:_PS3_Media_Server_on_Ubuntu_9_10_karmic_koala)

Works great for me now!

---

