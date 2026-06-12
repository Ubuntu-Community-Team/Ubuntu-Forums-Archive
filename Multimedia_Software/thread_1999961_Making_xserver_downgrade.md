---
title: "Making xserver downgrade?"
date: 2012-06-08
forum: Multimedia Software
---

### Post by sm786 on 2012-06-08
Hello, 

I recently installed Ubuntu 12.04 and my monitor's settings say that it uses a 1440 by 900 resolution, but the highest I can set it using the 'Display' option is 1220 by 1180. I already tried using Xrandr to change the resolution and I've always gotten the error: [COLOR=Red]Failed to get size of gamma for output default
[/COLOR]
I am unable to use Nvidia-current because whenever I open the settings dialog I always get the error saying I need to use nvidia-xconfig and restart which I've done multiple times and unfortunately that doesn't work either. 

I'm using a super old Dell Dimension E520 with the following video driver:
VESA: NV34 Board - p162-1nz

I read in this [thread]("http://ubuntuforums.org/showthread.php?t=1965671&page=2") that in order to get Nvidia to work I would need to install Nvidia-173 and to do so I would need to force xserver to downgrade. The procedure is below. 

> 1) In /etc/apt/sources.list :

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) oneiric main

2) In /etc/apt/preferences:

Package: xorg xserver-xorg*
Pin: release a=oneiric
Pin-Priority: 1050

3) Note related to nvidia-173/96 on Ubuntu 12.04 (optional if you face slow graphics)
I'm using old hardware with nvidia-173 drivers and I don't like the fact   "composite" is mandatory to use Unity correctly (very laggy) I had to   force composite to switch it "off" to avoid laggy windows by modifying   /etc/X11/xorg.conf:

Section "Extensions"
    Option "Composite" "Disable"
EndSectionHowever, I have several questions with this. Regarding the first step, do I change the part that says 'precise main restricted' to simply "oneiric main"? 

During the 2nd step. there is no 'preferences' file. Do I need to create one? 

Thank you so much. :)

Also, all I really want to do is get my resolution to 1440 by 900 so if I can do that without nvidia that would be great! :)

---

### Post by sm786 on 2012-06-09
So I tried it myself, and it worked perfectly! :) 

I used synaptic to download nvidia-173 and I got an entire list of new resolutions and nvidia worked as well (this was after using 'sudo nvidia-xconfig' in terminal). 

After doing the steps I got these box things on the side of my desktop soo....

I opened the xorg.conf file and added the following lines under the "Monitor" section

```
HorizSync    30.0-85.0
VertRefresh    30.0-75.0
```

and problem solved!!!

note: after doing this and installing updates and whatnot ndiswrapper stopped working and had to be reinstalled. oh well, now everything is perfect thank God :)

---

