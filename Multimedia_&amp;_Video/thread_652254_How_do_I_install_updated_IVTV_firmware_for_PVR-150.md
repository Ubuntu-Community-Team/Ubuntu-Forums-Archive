---
title: "How do I install updated IVTV firmware for PVR-150 on gutsy?"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by Mysticle31 on 2007-12-28
I have been trying to solve a flickering problem while using my PVR150 capture card.  I've tried playing with the PCI latency with no solution.  It has been sugested that I try and upgrade the firmware as I find.

"Dec 24 16:37:47 Desktop kernel: [   39.473558] ivtv0: Encoder revision: 0x02050032
Dec 24 16:37:47 Desktop kernel: [   39.473561] ivtv0: Recommended firmware version is 0x02060039."
 
In my var/log/messages file.

How do I do it? 

This is the process which I've done to try and make this work.

Check the "regular" Ubuntu repositories.
There are no firmware anything in the "regular" Ubuntu repositories.

I look at the IVTV Howto's Ubuntu section here:
[http://ivtvdriver.org/index.php/Howto:Ubuntu](http://ivtvdriver.org/index.php/Howto:Ubuntu)
No Gutsy section.

I find this thread, read it, and try to examine and follow the directions given in post 12:
[http://ubuntuforums.org/showthread.php?t=584303&page=2](http://ubuntuforums.org/showthread.php?t=584303&page=2)
However those files mentioned don't exist in that tarball, and 1.0.3 is the latest offered on the link.  I tried both the link on the wiki, and the link to the file on the forum, which are the same anyway.  I'm desperate.

I try to compile the tarball using make and get:
> make[1]: *** [v4l2-ctl.o] Error 1
make[1]: Leaving directory `/home/steve/Desktop/ivtv-1.0.3/utils'
make: *** [all] Error 2

I Google the problem:
[http://www.google.com/search?q=***+%5Bv4l2-ctl.o%5D+Error+1](http://www.google.com/search?q=***+%5Bv4l2-ctl.o%5D+Error+1)
 and find nothing but log files and someone saying that
> You have an outdated videodev2.h in /usr/include/linux. I've added a 
correct copy to the ivtv utils directory since so many linux 
distributions are sloppy with how often they update this file.
I didn't get anywhere with this.

I try to see if there is a gutsy repository for IVTV:
[http://dl.ivtvdriver.org/ubuntu/](http://dl.ivtvdriver.org/ubuntu/)
There isn't.

Here, on the forums, I find a "Massive Gutsy Repo List" here:
[http://ubuntuforums.org/showthread.php?p=3908327](http://ubuntuforums.org/showthread.php?p=3908327)
Loe and behold, there is a gutsy IVTV section
> # IVTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
# GPG key-file: [http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg](http://dl.ivtvdriver.org/ubuntu/80DF6D58.gpg)
deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) gutsy all
deb-src [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) gutsy all
But it doesn't work, I can't add the GPG key.

So, frustrated, I find this:
[http://ivtvdriver.org/index.php/Firmware](http://ivtvdriver.org/index.php/Firmware)
I perhaps learn that the tarball I downloaded above is not the firmware afterall, it's something else.
The interesting thing is that the firmware page on the wiki says that the older drivers (0.4.0 and below) are located in /lib/modules.  I have the files for ivtv-0.4.1 and above (that's the v4l-cx2341.... ones) located in /lib/firmware.  
The firmware page of the wiki says that the 0.4.1 filrs are located in /uar/lib/hotplug/firmware.  And hotplug folder does not exist on my computer.

What's going on.  Why is everything wrong?  How do I fix this?  How do I update my firmware?

---

### Post by Docteh on 2007-12-29
Try in /lib/firmware :)

I cant get my pvr150 to give me more than garbage :(

---

