---
title: "spca5xx in ubuntu 7.0.4? Please help"
date: 2008-04-30
forum: Multimedia Software
---

### Post by packetmover on 2008-04-30
I have a usb microscope camera with a chipset(Micron MT9M001) that is purported to be supported by the spca5xx driver. The problem is, spca5xx doesn't seem to be included with Ubuntu 7.0.4. 

 I did a 'find . -name spc*' in my /lib/modules directory and got no results, so I'm pretty sure it's not there.

 I got the source code and tried to compile it, but it complains that it must have read/write access to the source code.

 Thing is, I installed the kernel source code package too, but it's not finding it.

 It's complaining that it can't find some "build" subdirectory in /lib/modules or /usr/src or something like that(can't remember the exact path - I'm at work).

 off topic rant: The kernel source wouldn't compile either - make xconfig and make menuconfig are both broken. I really like ubuntu, but seriously folks, who puts out a distro that can't compile the kernel cleanly out of the box? Gimme a break!

 Anyway, I'm having trouble finding info on how to get this camera capturing video and images under linux. What app would I use once the drivers are in place? bttv? Is there something better?

 I'm new to this forum and ubuntu, but I've been running Linux since around '95.

 Any advice or help is GREATLY appreciated by myself and a young biology student who would really like to get this running under linux!

Thank you!

---

### Post by packetmover on 2008-04-30
Sorry correction:

"I got the source code and tried to compile it, but it complains that it must have read/write access to the source code."

 Should be:

 I got the **spca5xx** source code and tried to compile it, but it complains that it must have read/write access to the **kernel** source code.

---

### Post by bwallum on 2008-04-30
I think the package for web cams is called gspca in Ubuntu. I don't know if your camera is for video or stills.

This might be a useful resource:-

[http://www.exploits.org/v4l/](http://www.exploits.org/v4l/)

---

### Post by packetmover on 2008-04-30
Thanks for the reply and the URL, I will check it out.  

 As for the camera, it is supposed to be able to do both stills and full motion video.

 I'm pretty sure I'm going to need some kind of kernel module, or modules, I just don't know which one(s).

---

### Post by arman.haghi on 2008-05-13
Hey mate,

I had the exact same problem, tried everything... was getting the "/dev/video0 doesn't exist etc. etc." even though lsusb and dmesg said it was detected.

I've now got my antique DSC-350 working!

Check out my post:

[http://ubuntuforums.org/showthread.php?p=4941520](http://ubuntuforums.org/showthread.php?p=4941520)

and let me know if it helps or if you need help.

Cheers,

Arman.

---

