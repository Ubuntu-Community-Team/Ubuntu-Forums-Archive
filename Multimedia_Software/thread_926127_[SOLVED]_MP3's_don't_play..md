---
title: "[SOLVED] MP3's don't play."
date: 2008-09-21
forum: Multimedia Software
---

### Post by Roanoke on 2008-09-21
Nothing on my system seems to be able to play MP3's and I have no idea why. Can someone help me?

---

### Post by OutOfReach on 2008-09-21
Have you install the ubuntu-restricted-extras package?

---

### Post by tarahmarie on 2008-09-21
Here's a cheap and easy solution.  Install Amarok.  When you first open it, it should pop up an error message like "your computer can't play mp3s; do you want to install the stuff to do that?"  Click on yes; that will set your machine up.

---

### Post by Roanoke on 2008-09-21
> **OutOfReach said:**
> Have you install the ubuntu-restricted-extras package?
Yes.
As for amarok, it didn't say anything. Something that might be of interest is that I couldn't play the introduction track that comes with amarok.

---

### Post by tarahmarie on 2008-09-21
Could it be that you need to install the KUBUNTU-restricted-extras package instead of the UBUNTU-restricted-extras package?

---

### Post by Roanoke on 2008-09-21
> **tarahmarie said:**
> Could it be that you need to install the KUBUNTU-restricted-extras package instead of the UBUNTU-restricted-extras package?
No.

---

### Post by SuperSonic4 on 2008-09-21
Does any sound play? If you have an ogg file try that, but I think it's a general sound problem, just check the volume of the system make sure its high enough and ensure you have headphones/audio out device plugged in your PC's green jack

---

### Post by Roanoke on 2008-09-21
> **SuperSonic4 said:**
> Does any sound play? If you have an ogg file try that, but I think it's a general sound problem, just check the volume of the system make sure its high enough and ensure you have headphones/audio out device plugged in your PC's green jack
Well, sounds from programs play fine. But the OGG file doesn't play either. =/

---

### Post by tarahmarie on 2008-09-21
libxine1-ffmpeg

try that package, and see if it helps.  Once you've installed it, try to play an mp3 in Amarok.  You HAVE installed the gstreamer plugins, right?

---

### Post by Roanoke on 2008-09-21
Ok. It didn't work, but it did show me the tags, but it didn't show any movement on the progress bar. Here's the terminal stuff:
```

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8130e98 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8130e98 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )

```

---

### Post by tarahmarie on 2008-09-21
[http://ubuntuforums.org/showthread.php?t=521005](http://ubuntuforums.org/showthread.php?t=521005)

This thread may help.

---

### Post by Roanoke on 2008-09-21
> **tarahmarie said:**
> [http://ubuntuforums.org/showthread.php?t=521005](http://ubuntuforums.org/showthread.php?t=521005)

This thread may help.
Erm, I don't even USE amarok. I have no idea why this is going on an amorok-tangent. The problem is that nothing plays music files - not just amarok.

---

### Post by tarahmarie on 2008-09-21
Installing Amarok was just an idea; it worked for me, and is a sort of general fixit for the inexperienced when it comes to installing gstreamer and all the codecs.

---

### Post by Roanoke on 2008-09-21
> **tarahmarie said:**
> Installing Amarok was just an idea; it worked for me, and is a sort of general fixit for the inexperienced when it comes to installing gstreamer and all the codecs.
If that was insinuating that I am 'inexpereinced', then please refrain from that. I have no qualms with running terminal commands if that will fix it faster.

---

### Post by EDH1981 on 2008-09-21
same problem here

---

### Post by Roanoke on 2008-09-24
And the person in that thread has a whole other problem.

---

### Post by potterzot on 2008-09-24
I've got the same issue here and it's new.  I'm not sure what is going on but when (if) I fix it I'll let you know.

---

### Post by potterzot on 2008-09-24
the codecs thing from rhythmbox fixed it, but I had to restart the computer to get it actually playing mp3's.  It's weird because it has been playing audio up to a few days ago.  

I assume you have the gstreamer-plugins-good/bad/ugly set, and other than that the libxine might help.

Good luck and sorry I can't be more informative.

---

### Post by Roanoke on 2008-09-24
> **potterzot said:**
> the codecs thing from rhythmbox fixed it, but I had to restart the computer to get it actually playing mp3's.  It's weird because it has been playing audio up to a few days ago.  

I assume you have the gstreamer-plugins-good/bad/ugly set, and other than that the libxine might help.

Good luck and sorry I can't be more informative.

What do you mean by rythmbox codecs?

I can't seem to find the gstreamer plugins set or libxine.

---

### Post by Roanoke on 2008-09-24
Actually, it appears that if I install the restricted plugins and restart, it'll work.
Thanks to all those who helped :D

---

