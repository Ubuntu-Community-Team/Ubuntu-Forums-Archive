---
title: "Camcorder Not Working With Kino"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by pbCAM on 2007-08-09
Hello All,

I can't seem to get a camcorder working with kino. I have Ubuntu Studio 7.04 installed and am using a Panasonic PV-GS180 camcorder.

The camcorder works fine with Windows. Using the same camcorder and IEEE1394 cable I connect it to the Ubuntu box, the camcorder shows up as PV-GS180 in the Device Manager under my IEEE1394 card (also detected and working fine as I am using the USB ports on the same card for an external hard drive just fine). I have /dev/dv1394, /dev/raw1394 and /dev/video1394 all created just fine on startup but when I use kino it says "No AV/C compliant cam connected or not switched on?" even though it is connected and switched on. I figured maybe it was a permissions issue so I changed permissions and still no luck. I noticed I had no video group and that /dev/dv1394 was set to root:root ownership. I created the group video and added both the user and /dev/dv1394 to that group with no success still. I ran sudo kino and still no luck.

The IEEE 1394 card is a Belkin USB 2.0 + FireWire card that uses the M5253 chipset. I seem to recall reading this may be a problem, yet the camcorder and card seem to be detected just fine.

Any advice or assistance that anyone could offer would be greatly appreciated.

---

### Post by pbCAM on 2007-08-10
Can anyone offer advice?

---

### Post by DellAnderson on 2007-08-14
I joined the forum specifically to respond to your question.   I had exactly the same problem, (except using an Adaptec Firewire card) so I think the problem is not your Belkin.   I have been successful at capturing - to the main harddrive, but not to an external firewire hard drive.   I will post my experience next in the hopes that someone with more experience with permissions in Linux (and especially Ubuntu/Sudo) will come to our aid.  I have only used Ubuntu about 6 months or less, and only last weekend attempted to actually install Cinerella (which seems to require Kino or some other DV capture software).  FWIW, I'm not at all put off by this - it only reminds me of the early days of difficulties doing video editing on Windows.   We'll look back on this and smile at the "old days" sometime soon hopefully....

Dell 

(summary of my experiences in the next post)

---

### Post by rovernaut on 2007-08-14
I had the same problem with my panasonic.
 I followed the video tutorial and got it working.
 I don't recall what excactly I did as I don't use kino anymore but I think I had to  to add  "  /0 " to the end of /dev/dv1394 making it 
  /dev/dv1394/0
 also have a look at this
[http://www.robfisher.net/video/kino.html](http://www.robfisher.net/video/kino.html)

---

### Post by pbCAM on 2007-08-15
> **pbCAM said:**
> "No AV/C compliant cam connected or not switched on?"

Well, I'm not sure exactly how it happened because I'm still using /dev/dv1394/0 for the camcorder, but now kino will capture video, but I still get the above error and I still can't control the camcorder through the program. I'll take it, though! At least now I can capture, which is a good thing.

I wish I could share with others what I did, but honestly I have no idea what happened. It just worked. :confused:

---

### Post by pbCAM on 2007-08-16
I'm still persisting to get AV/C control. Here's what I've done thus far and I've had some degree of success. I still need some help, though.

First I edited /etc/udev/rules.d/40-permissions.rules to change the GROUP for /dev/raw1394 to video.
Next I changed permissions on /dev/raw1394 with sudo chmod g+rw /dev/raw1394 to give the group read/write permissions.
I checked my normal user and it does belong to the video group.
Then I changed the IEEE1394 preferences in Kino to use /dev/raw1394. 

For my normal user and even with sudo Kino gives me an error message in capture now that says that I don't have read/write access to /dev/raw1394. When I start Kino as root I not only can capture but I also have AV/C control.

Obviously there is something funky with permissions, but I'm at a loss as to what permissions need to be changed to let a normal user start Kino and have AV/C control of the camcorder. Any suggestions?

---

### Post by pbCAM on 2007-08-16
Okay, now I'm really confused because I switched back to /dev/dv1394/0 and I have AV/C control as normal user. :confused:

I guess I shouldn't look a gift horse in the mouth, because I accomplished what I wanted. I just wish I knew how I got there!

---

