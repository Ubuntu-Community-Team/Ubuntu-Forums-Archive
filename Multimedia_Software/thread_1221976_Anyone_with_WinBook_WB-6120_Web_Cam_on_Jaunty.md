---
title: "Anyone with WinBook WB-6120 Web Cam on Jaunty?"
date: 2009-07-24
forum: Multimedia Software
---

### Post by notfound123 on 2009-07-24
It kind of works (in Skype), but the image quality is poor. I can't find any web cam settings (it adjusts nicely in Slype/Win32). I was unable to install the drivers for it, as EasyCam2 cannot even see this camera.

Any suggestions?

---

### Post by igorzwx on 2009-07-24
and sound quality?
noise?
delay?
latency?

---

### Post by notfound123 on 2009-07-24
It is very grainy, sound is poor also. How do I install native drivers for it? Thanks.

---

### Post by igorzwx on 2009-07-24
I have a solution which works well on old boxes (2003, 2001)

Check if your hardware is supported
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by notfound123 on 2009-07-24
Thanks for the link. I am not sure if this really applies to me as I run a very up to date Lenovo T61. I do have the sound and the video working. My only issue is that I can't get to access any settings of my web camera which uses some "out of the box" drivers in Jaunty.

lsusb gives me the following:

Bus 005 Device 002: ID 093a:2621 Pixart Imaging, Inc.

---

### Post by igorzwx on 2009-07-24
you can make an experiment

install another Ubuntu in dual boot,
remove pulseaudio.
You may not have sound, but video may work better.

---

### Post by notfound123 on 2009-07-24
BTW, looks like I am not alone:

[http://ubuntuforums.org/showthread.php?t=1197027&highlight=Pixart+Imaging](http://ubuntuforums.org/showthread.php?t=1197027&highlight=Pixart+Imaging)

---

### Post by notfound123 on 2009-07-24
Okay, so it seems like the kernel supports my camera, 
[http://moinejf.free.fr/webcam.html](http://moinejf.free.fr/webcam.html) (Search for 093a:2621)

And it even looks like it selects the right subdriver, but the difference in quality between the windows version and what I get here in Linux is just unbelievable.

:(

Yet another disappointment with Ubuntu...

---

