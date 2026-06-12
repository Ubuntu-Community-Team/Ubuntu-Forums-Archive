---
title: "NVIDIA driver problem"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by mattydee on 2008-02-23
I am running Ubuntu 7.10 with nvidia 6600gt. I used the restricted drviers manager to install the nvidia driver. When I open up a terminal and type "who", I get the following:
```
matty    tty7         2008-02-23 10:17 (:0)
matty    pts/0        2008-02-23 10:18 **(:1.0)**

```
Instead of the usual (when using the nv driver)
```
matty    tty7         2008-02-23 10:17 (:0)
matty    pts/0        2008-02-23 10:18 **(:0.0)**
```
This is causing a whole bunch of issues, namely that I have to use "export DISPLAY=:0.0" to run flightgear or torcs (3d apps) and also when playing back dvds (ex: DISPLAY=:0.0 vlc) or else I get pretty bad tearing during playback.

What's going on with the NVIDIA drivers with ubuntu? How can I fix this? 

Thanks

---

### Post by mattydee on 2008-02-24
This sucks... 
Nvidia works fine on PClinuxOS and Slackware installs.

---

### Post by aysiu on 2008-02-24
I have no idea what the problem is, but I can assure you that it doesn't happen to everyone. I have Nvidia drivers installed from the Restricted Drivers Manager, and I get (:0.0).

Maybe a workaround would be creating a simple shell script that runs ```
#!/bin/bash
export DISPLAY=:0.0
vlc
``` or something similar for flightgear or torcs?

---

### Post by mattydee on 2008-02-25
> **aysiu said:**
> I have no idea what the problem is, but I can assure you that it doesn't happen to everyone. I have Nvidia drivers installed from the Restricted Drivers Manager, and I get (:0.0).

Maybe a workaround would be creating a simple shell script that runs ```
#!/bin/bash
export DISPLAY=:0.0
vlc
``` or something similar for flightgear or torcs?

Unfortunately, this is not really an option because

1. I get ugly looking windows with no borders when using the export method
2. I have to restart the xserver after using torcs
3. I'm pretty sure this is realated to the other problem I am having where totem (as well as vlc and mplayer) does not disable the screensaver.

I'm liking Ubuntu a lot, but this is a major pain. I installed kubuntu first then decided to "change it" into ubuntu. Maybe gdm taking over from kdm caused something? Xserver settings? Who knows... I even tried to compile and install the Nvidia drivers form their website, but to no avail. 

 I might try a reinstall, although this seems like a windows solution. :-k

---

### Post by aysiu on 2008-02-25
Perhaps you could try using Envy to install the Nvidia drivers instead of Restricted Drivers Manager?

RDM works fine for me, but if you're having a problem, using another method might help.

---

### Post by mattydee on 2008-02-25
ok thanks, i will give it a try and post back. Is this correct site for the trusted program?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by aysiu on 2008-02-25
> **mattydee said:**
> ok thanks, i will give it a try and post back. Is this correct site for the trusted program?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Yes, that's it.

---

### Post by mattydee on 2008-02-25
Unfortunately, that didn't work, but thanks for your help.

 I think I may do a clean install when the next version of Ubuntu is released.

---

### Post by aysiu on 2008-02-25
> **mattydee said:**
> Unfortunately, that didn't work, but thanks for your help.

 I think I may do a clean install when the next version of Ubuntu is released.
If you do a clean install, you may want to try something else, like maybe Linux Mint or PCLinuxOS. Maybe you'll have better luck with those. Sorry I couldn't be more help.

---

### Post by LoSt180 on 2008-02-29
If you have the last Nvidia drivers from ENVY, Open a terminal window and type: nvidia-settings there might be a setting in there to help with your screen.

---

### Post by mattydee on 2008-03-25
This problem has disappeared with 8.04...
:)

---

