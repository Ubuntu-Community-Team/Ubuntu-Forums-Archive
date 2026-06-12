---
title: "Problem with ATI graphics driver"
date: 2009-11-12
forum: Multimedia Software
---

### Post by Blake_K on 2009-11-12
Hi, I am a new ubuntu user but I am somewhat familiar with linux. I have recently installed Ubuntu 9.10 32-bit onto my laptop, a Toshiba Satellite model A305-S6916. The problem that I run into is when I have to install the graphics drivers for the video card. The laptop has an ATI Radeon HD 3650. When I use Ubuntu to automatically install the driver for me and then restart the computer will no longer boot. I get to a screen that has the Ubuntu logo in white and then the screen goes black and my caps lock light flashes. And I am left to re-install Ubuntu to fix the problem. I have also gone to ATI's website and they have a linux installer for the drivers. Tried that method and the same thing happens when it has to restart.
 
I have tried looking into what gets changed and it looks as if one of the drives that is mounted in my fstab file gets a read only error. 
 
Is there another possible driver that doesn't have this problem? Or is there something that I can do to prevent this? Any and all help is greatly appreciated.

---

### Post by Zoot7 on 2009-11-12
Have a look at the guide here:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

It shows you how to install the ATi drivers but uses a package based install as opposed to the other conventional method of running the script directly.
Granted it's for Jaunty but the procedure for karmic is pretty much the exact same, the only difference being that you have to build packages for Karmic as opposed to Jaunty, so this line:
```
sh ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/jaunty 
```
would become:
```
sh ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/karmic 
```

This is pretty much what I do to get my 4870 up and running in Ubuntu, hasn't failed on me yet.

---

### Post by Blake_K on 2009-11-12
Thank you, I notied the buildpkg command but was uncertain of how to use it. I will give this a shot and let you know how things work out.

---

### Post by Zoot7 on 2009-11-12
I think it gave me errors processing one of the packages when installing them over the command line with dpkg -i, but I'm yet to get graphics troubles.

---

### Post by Blake_K on 2009-11-12
That method worked! I got the drivers installed. And the computer will reboot just fine. Thank you!:)

---

### Post by Zoot7 on 2009-11-12
You're very Welcome! Glad I could be of help! :)

---

