---
title: "Direct Rendering: Failed with i810 in Dapper"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by Paradoxdruid on 2006-08-08
Hello all!

I have a wonderful Koala Mini micro-PC from system76.com that I use as a media center, but after upgrading to Dapper, it became sluggish--  very sluggish.  I finally figured out why:  the direct rendering is no longer working.

Looking at my xorg.conf, I'm loading DRI and GLX modules, the card is set to use driver "i810" and I specified a VideoRam of 65536.

lsmod | grep i8  shows that I have modules i810 and drm loaded.

But when I run glxinfo it says it can't find the GLX extension.

Looking at /var/log/Xorg.0.log, I see the problem--

I810(0): Direct Rendering: Failed.

Looking around, it seems like the upgrade from Xorg 6.8 to newer versions has killed direct rendering on a lot of people's boxen.

---

So...  does anyone have any ideas?  If not, how could I downgrade back to an older version of Xorg, where the direct rendering still worked?

Thanks for any help.  My media center is pretty toasted without direct rendering.

---

### Post by sherpah on 2006-08-08
I have what I think is a very similar problem - check out my thread I started on it - still no solutions yet.... take a look and see if  you have any more ideas on what we have in common.

[http://ubuntuforums.org/showthread.php?t=231781](http://ubuntuforums.org/showthread.php?t=231781)

---

### Post by Paradoxdruid on 2006-08-08
I just posted my latest efforts to your thread, but in case someone looks here--  Below is the advice I've collected and tried so far.

I was told to try ```
sudo ln -s /usr/lib/dri/ /usr/X11R6/lib/modules/dri
```
which didn't help.

Also, I was told that the BIOS frequently reports the video RAM as too low for 3d, so my xorg.conf has "VideoRam    65536" in the graphics card area.  No luck.

Lastly, I saw in some thread that people are saying Xorg 6.8 worked, but 7.0 and 7.1 broke something...  not sure, and I don't know how to downgrade to test that.

Trying a LiveCD is a good next step--  I'd hate to reformat and start over, but if that worked for my media PC, it's doable.

Beyond that, I'm at a loss--  the driver is in my kernel modules, the xorg.conf is set-up correctly, but my /var/log/Xorg.0.log reports ```
I810(0): Direct Rendering: Failed
```.

Here's hoping something comes along!

---

### Post by Paradoxdruid on 2006-08-09
So...  we can file this thread under "stupid user mistakes".

Apparently, at some point I accidently installed the package nvidia-glx , which is clearly wrong for an integrated graphics solution by intel.

so, I simply:```
sudo apt-get remove nvidia-glx
sudo apt-get --reinstall install libgl1-mesa-dri
sudo apt-get --reinstall install libgl1-mesa
``` and my rendering is working just fine! 

Thanks to anyone who was trying to help.

---

