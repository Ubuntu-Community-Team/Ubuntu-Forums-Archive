---
title: "Video Colors (Hue) Are Distorted"
date: 2009-01-04
forum: Multimedia Software
---

### Post by GenuineXP on 2009-01-04
I'm having a problem with video playback. For some reason, the colors are distorted (everything looks very blue/purple). I've seen some other threads discussing this issue, but most seem years old, don't fix my problem, or are concerned with ATI video hardware.

I have an nVidia GeForce 8600 GT. It works very well with Ubuntu (Intrepid), and I have also installed nVidia's X configuration tool. Video worked just fine until I installed the totem-xine package, which I occasionally use when the Xine backend outperforms the Gstreamer backend (for DVD playback, for instance). Once I installed this package, video colors became skewed.

Originally, I removed totem-xine and all Xine packages, removed ~/.gconf/apps/totem, and restarted X. This worked, but I still needed an alternate video engine. I tried installing the gmplayer package. The same problem occured. I prefer to use totem-xine as my alternate, so I removed all MPlayer packages and reinstalled totem-xine. The problem persists.

The strange thing is, if I adjust the hue in Totem I can temporarily fix the problem, but it just reoccurs as soon as I close and relaunch Totem again. Even stranger, if I launch the nVidia X configuration tool, any playing video's colors are suddenly fixed (even though I did nothing but launch the tool). I can then close the tool, and the video remains fixed until I it stops/restarts or I close Totem.

Is there a definitive way I can fix this problem? It's getting very annoying, especially when watching shorter videos are viewing visualizations, which are also affected. Videos played in my web browser seem unaffected.

Thanks!

---

### Post by GenuineXP on 2009-01-04
Bump.

---

### Post by hougSTAR on 2009-01-04
You need to edit XORG.CONF in: /etc/X11/XORG.CONF probably.

The file can only be altered as root.  I think I edited mine with that GEDIT thing, I had the same problem.  Do some searches on here for what to add in to each module in the XORG.CONF file, I'd give you what I wrote but I'm on a different PC :)

---

### Post by RedRat on 2009-01-04
OK I had a similar problem when I upgraded to 8.04 and I finally got a solution from here in the forums, but for the life of me I do not know why it works.

When I would double click on some videos, Totem would come up and the video would be this purple/blue, as if the red had been reduced. Oddly, even VLC and other players exhibited this behavior once the video came up and had these hue problem. Initially the only way around this was to reboot. Finally someone here said just go to Totem preferences and push the HUE slider all the way over. It worked and I have not had a problem since. 

You get to the preferences in Totem: Edit>Preferences>Display tab.

Why this odd video behavior carried over from Totem to VLC and other players is beyond me.

---

### Post by todthefox on 2009-01-31
I have this same issue- any media player I try will show up with messed up colors- and as soon as I open the nvidia xserver settings, it snaps to normal--- obviously that gets old- opening the settings whenever I want to watch a video- I haven't tried your solution yet though....

---

### Post by DeMus on 2009-01-31
> **GenuineXP said:**
> I'm having a problem with video playback. For some reason, the colors are distorted (everything looks very blue/purple). I've seen some other threads discussing this issue, but most seem years old, don't fix my problem, or are concerned with ATI video hardware.

I have an nVidia GeForce 8600 GT. It works very well with Ubuntu (Intrepid), and I have also installed nVidia's X configuration tool. Video worked just fine until I installed the totem-xine package, which I occasionally use when the Xine backend outperforms the Gstreamer backend (for DVD playback, for instance). Once I installed this package, video colors became skewed.

Originally, I removed totem-xine and all Xine packages, removed ~/.gconf/apps/totem, and restarted X. This worked, but I still needed an alternate video engine. I tried installing the gmplayer package. The same problem occured. I prefer to use totem-xine as my alternate, so I removed all MPlayer packages and reinstalled totem-xine. The problem persists.

The strange thing is, if I adjust the hue in Totem I can temporarily fix the problem, but it just reoccurs as soon as I close and relaunch Totem again. Even stranger, if I launch the nVidia X configuration tool, any playing video's colors are suddenly fixed (even though I did nothing but launch the tool). I can then close the tool, and the video remains fixed until I it stops/restarts or I close Totem.

Is there a definitive way I can fix this problem? It's getting very annoying, especially when watching shorter videos are viewing visualizations, which are also affected. Videos played in my web browser seem unaffected.

Thanks!

I have had the same problem some time ago, now it doesn't happen anymore. I was given this as answer to my problems and although it's a crappy solution, it does work:

The crux of it is you can test for this bug using the following:
Code in Terminal:

xvinfo | grep -A2 XV_HUE

The XV_HUE should be 0... but for some reason it gets set to 178 when opening a movie in Totem using the GStreamer backend.

You can fix it using the following (temporary!) fix. This will need to be run after every boot, so you might want to set it to run automatically when you login possibly...
Code:

xvattr -a XV_HUE -v 0

NOTE: you'll need to install xvattr for this to work:
Code:

sudo apt-get install xvattr

Good luck

---

### Post by Judders on 2009-11-30
I now have the same problem after upgrading to Karmic.
Logging Off and back on Fixes the issue, So does running NVidia X server Settings.

---

### Post by BlueCanary9999 on 2009-12-12
Try this, it worked for me:
[http://ubuntuforums.org/showpost.php?p=8250944&postcount=12](http://ubuntuforums.org/showpost.php?p=8250944&postcount=12)

---

