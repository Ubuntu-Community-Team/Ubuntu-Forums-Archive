---
title: "How can I play Blu Ray/Hd-Dvd movies in Ubuntu?"
date: 2009-07-13
forum: Multimedia Software
---

### Post by fwaokda on 2009-07-13
I have purchased an LG Bluray/Hddvd player/burner from newegg a couple weeks ago.  I was hoping there is a way I can watch movies still through ubuntu or at the very least windowsxppro through virtualbox(which I haven't tried but I'm quite sure it should work).  Can someone inform me if it is possible and if so how to get them to play in ubuntu? Thanks!

---

### Post by Ra-Hoor-Khuit on 2009-07-13
Start here...

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by doas777 on 2009-07-13
it is my understanding that you cannot. 
if you find out otherwise let us know, but until BD+ can be reliably cracked so that a decoder library can be produced, it should not be possible. There are cracking tools for BD+ streams, but every few months the blueray folks manage to break the crack, at which point the guys at slysoft pick it back up. 
unfortunately, it looks like the guys at doom9 are having trouble with it. a shame.

---

### Post by fwaokda on 2009-07-13
> **Ra-Hoor-Khuit said:**
> Start here...

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

Thanks, I'll check it out and post any updates.

---

### Post by fwaokda on 2009-07-13
Seems like alot of stuff, I'm gonna look at it once more once I'm back at the computer - but - seems it'll be easier to play them if they work through virtualbox I think.

---

### Post by doas777 on 2009-07-13
> **fwaokda said:**
> Seems like alot of stuff, I'm gonna look at it once more once I'm back at the computer - but - seems it'll be easier to play them if they work through virtualbox I think.

good luck. I'm told it shouldn't work, but I hope it does for all our sakes.

---

### Post by cozmicharlie on 2009-07-13
Blu Ray in linux is not supported yet and I could not get them to play in Virtual Box.  maybe the new Vbox3 will work better.  I have to dual boot with Windows7 and Windvd.  Post back if you get it to work.

---

### Post by doas777 on 2009-07-13
I think you need an HDCP ready vidcard and driver stack to view BD+ content. In Vista\7, they had to implement a tyrannical tech called [Protected Media Path ]("http://en.wikipedia.org/wiki/Protected_Media_Path")to get licensing to be able to display content at all.  this is much of the loudly lauded "DRM" embedded in vista.

HDCP is designed to keep content encrypted as it moves through the system, and stays encrypted until it reaches the monitor itself. PMP listens on the system bus and within a highly protected part of the kernel trying to find any evidence of another module attempting to intercept the stream. if you have any unsigned drivers or process debuggers installed, or if a hiccup occures on your system bus, PMP degrades your signal to 480p. all this hardware intelligence (and 100% signed drivers for all kernel mods) says to me that it probably won't work in a virtual environment.

---

### Post by fwaokda on 2009-07-15
Well I was able to get PowerDVD to install, but I noticed that the drive shows up in VBox as "VBox CD/DVD Drive" is there a way to change this? Because starting with just that, the disk is not able to be read.

Any ideas on how to move forward?

---

### Post by fwaokda on 2009-07-15
I've been talking with a VBox person in their chatroom and here is some stuff he/she's had to say on this...



> vbox blocks any commands not in the white list for security reasons. and the bd copy protection stuff is not in there yet. feel free to contribute a change - it shouldn't be difficult.

the difficult part is distilling the needed command list out of the scsi specs...


Then I asked what the white list was because im new to all this...


> it's a list of scsi commands which are allowed to be passed to the host drive. right now the list covers everything needed for dvd...

see src/VBox/Devices/Storage/VBoxATA.cpp, function atapiParseCmdPassthrough

So maybe that can get someone on here started... I'm gonna keep looking into it and I'll try and update this if anything comes up.  This is pretty much the only thing keeping me from being in a total Ubuntu w/ VBOX environment. :)

_UPDATE:_
If your any good with C++ here is a link to the function that he/she mentioned above. (Line: 2386)
[http://www.virtualbox.org/browser/trunk/src/VBox/Devices/Storage/ATAController.cpp](http://www.virtualbox.org/browser/trunk/src/VBox/Devices/Storage/ATAController.cpp)

---

### Post by fwaokda on 2009-07-15
I've posted on their MSGBoards -- hopefully if enough people go over there and request it, it'll get put in. Or at least we might be able to cooperate and fix it ourselves.

[http://forums.virtualbox.org/viewtopic.php?f=2&t=20071](http://forums.virtualbox.org/viewtopic.php?f=2&t=20071)

---

