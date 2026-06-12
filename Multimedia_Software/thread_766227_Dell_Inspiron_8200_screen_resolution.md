---
title: "Dell Inspiron 8200 screen resolution"
date: 2008-04-25
forum: Multimedia Software
---

### Post by tompagenet on 2008-04-25
Hello all - many thanks for reading. I'm new to Ubuntu and Linux, so please be patient. I've searched the forums for Inspiron 8200 and for the screen resolutions with no luck.

i installed 8.04 last night using Wubi. All went well, but when it started up it was clearly using a slow graphics driver. Once I connected to the internet Ubuntu told me there were drivers available for my hardware. I tried installing the nVidia one as my Inspiron 8200 laptop has a GeForce Go 440 in it. When Ubuntu restarted I got a black screen (although Ubuntu was evidently still working in the background - I got the system start-up sound for example).

I then re-booted Ubuntu and put it into recovery mode and asked it to fix X - this got me back the ability to see things and start Ubuntu in what looked like the same screen set up it had installed. Looking at these forums I then used EnvyNG to install the driver. This worked much better (incredible tool!), but when I restarted although graphics acceleration was enabled I was stuck with a max screen resolution of 1400 by 1050. My LCD screen is 1600 by 1200.

However, the 1400 by 1050 picture is not scaled to the screen - instead it's just showed in the top left section, with the remaining 200 200 pixels to the right and 150 to the bottom being filled with other rubbish. On the right the rubbish is just a set of colour bars. On the base it's a repeat of what's shown in the top 150 pixels of the screen. This may sound confusing so I've put a picture here:

[http://www.flickr.com/photos/tompagenet/2440648128/](http://www.flickr.com/photos/tompagenet/2440648128/)

I've had a similar problem in Windows with some versions of nVidia drivers - normally the solution in windows has been to get a version of the driver where the INF file has been patched to remember that 1600 by 1200 panels do exist. Anyone got any ideas - I'll be very thankful!

Tom

Update:

I have still not found a fix to this. This is not a unique to Ubuntu/Linux problem though, as I said above. This has nothing to do with my graphics card being faulty or anything similar. The LCD panel (Dell SEC3255) needs to be enabled correctly so that the machine knows it supports 1600 by 1200. *If* this were Windows, then the solution for this is here:

[http://www.laptopvideo2go.com/forum/index.php?showtopic=6686](http://www.laptopvideo2go.com/forum/index.php?showtopic=6686)

i.e. editing the graphics driver's INF file to fix the issue. Does anyone know how to do such a thing in Ubuntu - i.e. to override the incorrect EDID that my display provides?

---

### Post by tompagenet on 2008-04-28
Okay, I'm making progress, even if it is excruciatingly slow.

I have found this post in the forum archive:

[http://ubuntuforums.org/showthread.php?t=573926](http://ubuntuforums.org/showthread.php?t=573926)

it.henrik proposes a solution, but I don't understand it at all - would anyone be so kind as to help me out with this? I tried googling it, as suggested, but to no avail.

Many thanks, Tom

---

### Post by tompagenet on 2008-05-18
I have finally fixed this, although I should say that having done so VLC no longer plays back smoothly in full screen.

The answers lay in this post:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/33075/comments/4](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/33075/comments/4)

Downloads the nvnew.raw file and copy it to /etc/X11/:

sudo cp nvnew.raw /etc/X11/

Then edit the xorg.conf file - to do this press Alt+F2 and type:

gksu gedit /etc/X11/xorg.conf

and hit enter

Then under the section marked Section "Device" comment out the line with UseDisplayDevice in it (put a # at the start of the line) and put these two new lines in this section:

Option "UseDisplayDevice" "DFP-0"
Option "CustomEDID" "DFP-0:/etc/X11/nvnew.raw"

Save, close and restart - problem solved! I wish it had been slightly less frustrating to find the solution. If anyone can help with the VLC choppiness (I've tried OpenGL, X11 and XVideo under Preferences -> Video -> Output modules) then I'd be very happy!

---

