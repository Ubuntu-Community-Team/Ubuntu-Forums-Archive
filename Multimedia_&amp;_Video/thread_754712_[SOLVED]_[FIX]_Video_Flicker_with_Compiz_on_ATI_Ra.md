---
title: "[SOLVED] [FIX] Video Flicker with Compiz on ATI Radeon M285 (may help others)"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by jameskeagie on 2008-04-14
The following is what worked for me to get rid of the video flicker in Gutsy without breaking Compiz.  I have a Radeon Mobility X1400 with the newest ATI proprietary drivers on a Gateway M285-e using the Gstreamer ffmpeg and codecs.  

In addition to disabling Video Overlay and enabling OpenGL overlay (really improves live video on cube rotation and on the other compiz effects.  Full screen video was improved too. ) the Option  "TexturedVideo" "off" was added.  Overall this eliminates the diagonal artifacts, and the flicker when playing videos.  
[B]
Here are the step by step instructions to try what I did.  [/B]

First make a copy of the xorg.conf - I like using the days date (YYMMDD) where shown 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup<date>
```

Next we open the xorg.conf for editing.

```

sudo gedit /etc/X11/xorg.conf

```

After which I added the following to the Device section under the driver

```

Section "Device"
	........
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option      "TexturedVideo" "off"
        .........
EndSection 

```

Save the file and Reboot (sudo reboot) and hope it works! 

If this change breaks your X - boot into the recover command line from Grub (Esc then second choice while booting) and do the following

```

sudo cp /etc/X11/xorg.conf.backup<date> /etc/X11/xorg.conf

```

If you can't remember the backup name, or want to switch to a different xorg.conf do a directory listing which will list all the files.  

```

cd /etc/X11/
dir

```

Then reboot and it will be back to your old configuration.  

Hopefully this helps!


(A little more about what else I tried)
I had two device sections, as well as monitor and screen sections - I'm assuming because I have a VGA output from my laptop (the one identified by the vesa drivers and the first of each section).  I found that deleting or modifying the vesa sections (first set of sections) usually ended up in breaking X, and it would just load to a black screen after a reboot.  

Other things I tried that didn't work:

[http://ubuntuforums.org/showthread.php?t=631130](http://ubuntuforums.org/showthread.php?t=631130)

```

Section "Screen"
    ...
    Option         "XvmcUsesTextures" "True"
    ...
EndSection

```

This caused compiz to fail to load, but X would still load.  This fixed the flickering, but only because compiz wasn't loading.

Even with this I still have other problems (may be unrelated).  After GRUB I have a black screen (no usplash found) until the login screen.  I also can't create virtual terminals for some reason (Alt+Ctrl+F2?)  And sometimes even on AC power the LCD brightness on the laptop is changed to its lowest setting, which is weird since its done through the laptop's bios/ACPI controls I believe.  

Hope this helps some people out there with other Radeon Mobility cards - or even other system setups.  I'm still new to this, but I think this could work for some other people so post here if it worked.

---

### Post by erginemr on 2008-04-14
For the blank screen at boot up (which is supposed to solve the virtual terminal issue as well), please refer to:
[http://ubuntuforums.org/showthread.php?p=4356890](http://ubuntuforums.org/showthread.php?p=4356890)

to check if your symptoms match the ones I have explained in the howto.

---

### Post by jameskeagie on 2008-04-14
Working late last night I found that fix on a different post and it worked great.  Now I've got a splash loader, as well as being able to start virtual consoles.  Thanks anyways though!

---

### Post by lurkus ignoramus on 2008-05-04
This worked like a charm.

I can now watch video in a window or full-screen.

Woot!

---

### Post by AaronMT on 2008-05-06
All good, works for me. I am using Totem Movie Player and have advanced desktop effects enabled. This fixed the video flickering issue. 

My graphics display adapter is an ATI Radeon Express 1150 in my Dell Laptop

---

### Post by jusuchin85 on 2008-05-07
Thanks for this, but too bad that it only works in full screen (for me). If it was in window mode, then it would still flicker...

But, anyways...thanks!

p/s: what video driver are you all using? i'm using the "gl" one...

---

### Post by tanguyr on 2008-05-15
thanks jameskeagie, that fixed it for me like a charm: fullscreen or window, no more flickering video. This was on an ATI 1700 using fglrx from the repository

---

### Post by richter on 2008-05-25
Also worked great for me. ATI X1950 GT here.

---

### Post by revolutio on 2008-05-27
> **jusuchin85 said:**
> Thanks for this, but too bad that it only works in full screen (for me). If it was in window mode, then it would still flicker...

But, anyways...thanks!

p/s: what video driver are you all using? i'm using the "gl" one...
I have the same issue as you.  It allows me to actually have Compiz effects and watch video but only if the video is fullscreen.  I use the gl2 video drivers.

---

