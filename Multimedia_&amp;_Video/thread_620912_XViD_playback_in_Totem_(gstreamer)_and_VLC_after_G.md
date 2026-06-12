---
title: "XViD playback in Totem (gstreamer) and VLC after Gusty Upgrade"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by samtheozzy on 2007-11-23
Hi all

I just upgraded to Gusty this afternoon and am having huge probs with XViD movies.  When I play them in Totem (gstreamer) with the gstreamer-ffmpeg plug-in, the video is scrambled with a green vertical bar about just off-centre to the right and another horizontal bar running along the bottom of the window.

I tried removing and reinstalling both the plug-in and Totem itself with no success.  Further, I tried installing totem-xine but could not get XViD playback working in that either due to difficulties getting and installing win32codecs and libxine-extracodecs.  

I noticed the advice here --> [http://ubuntuforums.org/showthread.php?t=441993](http://ubuntuforums.org/showthread.php?t=441993) but I didn't have a .xine folder initially and even when I installed and then removed totem-xine, the green bars and the scrambling was still there.

THis wouldn't be a problem normally as I could just use VLC instead but ever since the upgrade, XViD sound playback in VLC has been terrible.  The sound channels appear to have lost volume and have an odd quality to them.

The videos play fine in windows media player and VLC on windows.  Oh, and MPlayer in Ubuntu just crashes when I try and use that so it's not an option.  I would really prefer to use Totem so any help would be most appreciated.

-Sam

---

### Post by ericartman on 2007-11-23
Check out

[http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207)

Best thing since sliced bread to me.

Cart

---

### Post by samtheozzy on 2007-11-23
I'm sorry but that appears to be a link to a thread talking about a backup utility.  Is that what you intended to link to or was it just an accident as it's not particularly relevant to the problem I detailed above.  I appreciate the help but my goal is to get totem playing XViDs properly, not uninstall a system upgrade.

---

### Post by ericartman on 2007-11-23
Its a multi use program offered, read the whole page. It also does codecs for dvd play, worked for my totem, sorry I wasn't clearer.

Cart

---

### Post by Griffiss on 2007-11-25
Hi, seems I'm having same problem as OP - a green band across the top of the movie in vlc, similar with gxine/totem-xine, except worse colour all over, and very distorted with totem-gstreamer.

All installed and newest versions: w32codecs, libdvdcss2 (don't know if this is required for xvid .avi files?), libxine1-plugins, libxine1-ffmpeg.

Any solutions out there? Or suggestions for troubleshooting?? I want to watch Letters from Iwo Jima!!! :popcorn:

ps @ cartman - I had a look through that script and already have all the codecs it installs, cheers.

---

### Post by envytin on 2007-11-30
Getting same problem with vlc and totem.... anyone got any idea why?

---

### Post by freexzai on 2007-12-18
Hate to bump but I don't see anything else on this. I tried the quick start thing but I still have a green bar and the color is very bad.

---

### Post by philc on 2007-12-18
I had the same problem, or similar - green bar across the top and colours all wrong.

Try changing setting as noted on this thread:

[http://ubuntuforums.org/showpost.php?p=2896078&postcount=2](http://ubuntuforums.org/showpost.php?p=2896078&postcount=2)

In short:

Typed "gstreamer-properties" in Terminal (without the quotes obviously). Clicked on the Video Tab and under "Default Output", changed "Autodetect" to "X Window System (No Xv)".

Worked for me!

---

### Post by freexzai on 2007-12-18
i have the xine backend...but i guess that will work for DVDs and ill use VLC for xvids.

thank you great link :)

---

### Post by aefaradien on 2007-12-18
i have exactly the same problem, but only in vlc and only with .avi files.  the default movie player plays .avi fine, but vlc adds some green bar across the top.

also since upgrading, i have noticed some (read: quite a lot) diagonal "tearing" (division from top right to bottom left).  based on my win32 experience, i would guess that this is the way video is drawn using a 3d engine (2 triangular polygons).  anyone else seen this?

---

### Post by joonjoon on 2008-03-10
philc's solution worked perfectly for me...

---

### Post by joellord on 2008-06-04
> **philc said:**
> 
In short:

Typed "gstreamer-properties" in Terminal (without the quotes obviously). Clicked on the Video Tab and under "Default Output", changed "Autodetect" to "X Window System (No Xv)".



That just worked for me...  Thanks philc!

---

