---
title: "Color problems with movie player"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by Torqumada286 on 2007-12-22
When using the Totem movie player the colors are off on the files.  They can run from too red, to too green, to too blue.  I have to adjust the colors for every file as it plays to get the color right.  Any ideas what the problem could be?

Torqumada

---

### Post by Josh C on 2007-12-22
I have no idea how to fix the issue, but something similar recently happened to me.  I have several video files that used to be "normal".  At some point, I suspect after a recent update, all my picture and sound got out of whack.  I still have no sound, but I did get the color back.  I had to go through and adjust the hue, contrast and such.  I still do not have it looking the way it used to, but no more black and white.  At some point all the color settings got dropped to the lowest point.  I do not know how or why and still do not have any sound.  These issues occur when using Totem, Mplayer and VLC.  It is probably the same on the other media players as well, but those are the only ones I have tried.

---

### Post by Torqumada286 on 2007-12-22
Anyone?

Torqumada

---

### Post by Torqumada286 on 2007-12-22
Guess I'll cross post this in the beginners section too.  :(

Torqumada

---

### Post by weblordpepe on 2007-12-25
You guys have nVidia graphics cards right? I had a similar issue. Something to do with a bug in the nforce chipset. Somewhere. I have no clue how. Basically I had to turn off the hardware overlay feature (tell software not to use it). VLC is smart enough to configure it like that. Not sure about Totem though. Mplayer can Im sure of it.

---

### Post by Ken Seehart on 2008-01-12
I have ATI.

It seems to be swapping RGB => BGR, or something like that, making everyone turn blue :confused: 

Adjusting the hue all the way to one side makes skin tones look somewhat okay, but with that adjustment it's still wrong (something like RGB => RBG).

Details:
  Ubuntu 7.10
  ATI Technologies Inc M58 [Radeon Mobility X1800]
  Totem Movie Player 2.20.0

Ken

---

### Post by philc on 2008-01-12
I had the same problem, or similar - green bar across the top and colours all wrong.

Try changing setting as noted on this thread:

[http://ubuntuforums.org/showpost.php?p=2896078&postcount=2](http://ubuntuforums.org/showpost.php?p=2896078&postcount=2)

In short:

Typed "gstreamer-properties" in Terminal (without the quotes obviously). Clicked on the Video Tab and under "Default Output", changed "Autodetect" to "X Window System (No Xv)".

Worked for me!

---

### Post by Parvo on 2008-01-28
That worked for me! Thanks man!

---

### Post by jis on 2008-03-09
> **philc said:**
> 
[http://ubuntuforums.org/showpost.php?p=2896078&postcount=2](http://ubuntuforums.org/showpost.php?p=2896078&postcount=2)


I use totem-xine so I changed settings in Xine. It seemed to work, but only for the totem, not for the mozilla-plugin totem-mozilla.

Correction: It didn't work for totem-xine.

---

### Post by Auslegung on 2008-03-09
Worked great for me, thanks

---

