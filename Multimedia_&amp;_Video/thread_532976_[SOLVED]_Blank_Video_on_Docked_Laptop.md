---
title: "[SOLVED] Blank Video on Docked Laptop"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by TygerFish on 2007-08-23
I'm having a funny problem: when I play a video on a laptop, the content of the player window appears "blank" on the external monitor.  That is, the rectangle where the video should be is "light black" - that is, a slightly lighter color than the #000000 black of the window background.  The sound still works, videos are the only problem, and videos play normally if I am using the laptop LCD instead of the external monitor.  YouTube-style web videos work fine, but the blanked-out problem happens with every video player I have tried thus far.  This happens whether the monitor is plugged into the port on the back of the machine or if the laptop is docked.  I have also had this problem on two different laptops (Dell D610 and Dell Latitude C610) each with a different docking station, both running Edgy.

I found a potential fix that involved using gstreamer-properties to switch the video output to - I believe - "X Window Manager (no Xv)."  This appeared to work using the "test video" button on the gstreamer-properties window (I saw a test pattern video window appear properly) but when I went to play a video in the movie player, there was now not even a blank square where the video should be playing.  Rebooting had no further effect and neither did trying any of the other options in the gstreamer-properties window.

I'm stumped and can't find anything else on the forum or web.  Any help would be appreciated.

---

### Post by tseliot on 2007-08-23
what's your graphic card model?

---

### Post by TygerFish on 2007-08-24
I don't know what the graphics card was on the first laptop, but on this one:
```
~$ sudo lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
```

And the driver:
```
Section "Device"
        Identifier      "ATI Technologies Inc M22 [Radeon Mobility M300]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

```

---

### Post by tseliot on 2007-08-24
> **TygerFish said:**
> I found a potential fix that involved using gstreamer-properties to switch the video output to - I believe - "X Window Manager (no Xv)."  This appeared to work using the "test video" button on the gstreamer-properties window (I saw a test pattern video window appear properly) but when I went to play a video in the movie player, there was now not even a blank square where the video should be playing.  Rebooting had no further effect and neither did trying any of the other options in the gstreamer-properties window.
Select "X Window Manager (X11/XShm/Xv)" instead of "X Window Manager (no Xv)"

then type:
```
sudo nano -w /home/$(whoami)/.gnome2/totem_config
```

and get to line 93. You should see something like this:
```

# video driver to use
# string, default: auto
#video.driver:auto
```

replace it with

```

# video driver to use
# string, default: auto
video.driver:xshm
```

Press CTRL+X and exit (save the file)

close totem, launch it again and play a file

---

### Post by TygerFish on 2007-09-10
The fix worked great.

Also, to similarly fix my Swiftfox MPlayer plugin (a la Automatix), I right-clicked, clicked "configure" and under "video output" picked "X11"

---

