---
title: "can't  eject new Kindle"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by sallymc on 2011-12-13
Hi hi,
I have a problem with my new Kindle.  It mounts onto Ubuntu 10.04 beautifully, but when I press eject , the box says :
Volume is busy
One or more applications are keeping the volume busy.
vlc/media/Kindle
When I press "unmount anyway" the message reappears again and again..

When I press  Safely Remove Drive, the box says :
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Hoping someone can HELP ?  Hope this is the correct forum for Kindle.
Sallymc

---

### Post by kgarbutt on 2011-12-13
From the terminal type this (exactly this):

sudo eject Kindle

it works for me.

Ken

---

### Post by sallymc on 2011-12-14
> **kgarbutt said:**
> From the terminal type this (exactly this):

sudo eject Kindle

it works for me.

Ken

The message then reads :  
eject: unable to find or open device for: `kindle'

---

### Post by kcirrab on 2011-12-14
your k appears to be lower case and the guys suggestion above appears to be upper case.. try it again with a capital K instead of a lower case k... linux is very picky about CASE Good Luck

---

