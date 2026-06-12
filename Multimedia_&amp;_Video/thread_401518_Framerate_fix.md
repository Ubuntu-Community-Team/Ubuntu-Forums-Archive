---
title: "Framerate fix"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by goodnereod on 2007-04-04
Fist off I am new to linux as a whole but here is my problem and what I have observed so far. I have a Sony Vaio laptop with an Intel 915GM chipset and gma 900 graphics card. It is 1.73 Ghz Intel centrino with 512 mb ram.

The problem is that ever since I started using ubuntu everything is moving very sluggish. Movies and videos run jerky and so do games, opening new windows, programs etc... I have noticed something strange though.... if I run "glxgears" in the terminal window and leave it open all of a sudden everything runs extremely fast and smooth and the moment I close it the computer slows down again. I can also produce the affect strangely enough by dragging a window around the desktop rapidly... while i am moving it around everything runs smooth and movies are fast... the minute i stop everything goes back to running sluggish and jerky. If you have any suggestions please help!?!?

---

### Post by djrobthaman on 2007-04-04
Well,  if glxgears fixes it, then what you can do is go into the admin menu and add it to the startup for the session that you login to.  I'm not using ubuntu right now so i can't say exactly how to navigate there, but it's somewhere in the admin menu.

---

### Post by djrobthaman on 2007-04-04
Here it is:

System > Preferences > Sessions > Startup Programs (tab) > Add (button)

Then insert the command in the text area that pops up

---

### Post by Mxo on 2007-06-13
I have the same problem. Video playback, scrolling and 3d screensavers run sluggish. Strangely running glxgears solves the problem(as well as waving around a window, but this slows down everything else). Still I think finding the reason for this might be a lot more useful than wasting system resources by constantly running glxgears in background.

My system: Pentium M 1.6GHz, 512Mb Ram, intel 915gm graphic, running kubuntu feisty and using the intel-video driver (though i had the same problem with the i815 driver).

Stephan Burkhardt

---

