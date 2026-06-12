---
title: "webcam won't work"
date: 2010-02-14
forum: Multimedia Software
---

### Post by koolkid93 on 2010-02-14
i have ubuntu 9.04. i have a logitech webcam300. i went through all the steps to install UVC i got to the second to last command lsusb and i got 

Bus 002 Device 006: ID 046d:0805 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 03f0:7e04 Hewlett-Packard Deskjet F4100 Printer series
Bus 005 Device 003: ID 413c:2105 Dell Computer Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:3012 Dell Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

so my webcam showed up on the list like it should. so i entered the last step
 
 sudo modprobe uvcvideo

and nothing happened. i assumed it worked so i tried to use my webcam on skype but it still doesn't work. does anyone know what to do here?

---

### Post by gordintoronto on 2010-02-14
Does the webcam work in Cheese?

In my experience, Skype requires a high-performance system.  I have an "old computer" and a "new computer," both with webcams.  Skype videoconferencing works nicely on the new computer -- and system monitor says both CPUs are working at 50% or so -- but not at all on the old computer, a five-year-old 2 GHz AMD.

---

### Post by manny43 on 2010-02-14
Same problem here.It used to work fine with both apps in Ubuntu 8.04.

---

### Post by koolkid93 on 2010-02-14
mine is a 1.8GHZ so thats probably pretty bad. ha no i don't have chees and i don't know how to get it can you help me there? with cheese can i talk to people on skype? or can a microsoft computer use cheese?

---

### Post by no2498 on 2010-02-15
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each
cheese brakes v4l1 so if you use v4l1 do not open cheese
try wxcam
my cam opens with more programs now
skype has some install problems now you will need to work with it
xawtv will not open for me on 910
i do not have skype loaded

but if you do as i said you will see your cam

---

### Post by gordintoronto on 2010-02-15
> **koolkid93 said:**
> mine is a 1.8GHZ so thats probably pretty bad. ha no i don't have chees and i don't know how to get it can you help me there? with cheese can i talk to people on skype? or can a microsoft computer use cheese?

Cheese lets you capture photos or videos from your webcam.  It is also the easiest tool to see that your webcam works in Ubuntu.  You can get Cheese from Administration/Synaptic.

My "old computer" on which Skype doesn't work is faster than your 1.8 GHz.

---

### Post by ethrockerdude on 2010-03-01
My webcam works fine, I open Cheese and I can take photos, but not videos. It attempts to take the video, but spazzes and freezes up, and that's how the video looks at the end after the capture. Help?

---

### Post by no2498 on 2010-03-02
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

cheese you have in the package manager

---

