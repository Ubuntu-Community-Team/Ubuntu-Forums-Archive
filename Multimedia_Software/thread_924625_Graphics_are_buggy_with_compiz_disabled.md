---
title: "Graphics are buggy with compiz disabled"
date: 2008-09-19
forum: Multimedia Software
---

### Post by Rianthas on 2008-09-19
Setting System -> Preferences -> Appearance -> Visual Effects to none makes my menu bars and windows don't display icons right, and have like a weird tearing. I have a constant problem with Amarok displaying correctly.

Video card is an ATI Radeon X1250 using the proprietary fglrx driver. I haven't been able to find any solutions, short of turning Compiz back on, which I'm trying to avoid due to the flickering it causes with programs utilizing OpenGL.

---

### Post by markbuntu on 2008-09-19
You can look here for a possible solution to your problem:


[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by Rianthas on 2008-09-19
Turning AIGLX on in my xorg.conf file and restarting the X server prevents fglrx from loading and default to vesa. On top of that, there isn't a driver for my video card on the ATI site mentioned in the link. I'm using whatever driver Envy downloaded and set up.

Note that Compiz works fine, even before making this thread. It's just that anything using OpenGL flickers unless I turn my visual effects to none, which causes the problems I mentioned in my original post.

---

### Post by markbuntu on 2008-09-19
If you are using fglrx, then you are using the ati proprietary driver. I'm sorry, I should have warned you that these options are not necessarily stable and will not necessarily work for all ati cards that are using the flgrx driver. Have you tried playing with the TexturedVideo or OpenGlOverlay or VideoOverlay options?

---

### Post by Rianthas on 2008-09-20
No, I haven't. Fortunately, I no longer need to.

I commented out the lines regarding AIGLX in my xorg.conf file. Apparently, one of the other options mentioned in the link fixed my problem. I can now run OpenGL games with no flicker with Compiz running. I didn't think this was going to be possible, and was fully expecting to switch to metacity for the time being. Thanks a bunch.

---

