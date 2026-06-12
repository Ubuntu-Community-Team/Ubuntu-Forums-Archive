---
title: "[SOLVED] Video only works fullscreen..."
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by Son of Silas on 2007-12-07
I have obviously tweaked something somewhere to have caused this...

I have 2 identical laptops both (in theory at least) running identical builds. One however ONLY plays video fullscreen. If i try to play it in a window I get a black screen and audio.

This applies to video embedded in web pages, DVDs Video files locally. It also occurs regardless of the player I use, Totem, VLC etc.

Any Suggestions?

---

### Post by Son of Silas on 2007-12-07
OK... After 2 weeks banging my head against a wall, I finally decided to post here and I immediately find the answer. Turning off visual effects fixed it.

---

### Post by bthoward on 2008-03-29
Thats not a fix... Thats a work around....  Would be nice if there was an actual fix so that we can have compiz and windowed mode video at the same time....  I had this working in 7.10 before upgrading to 8.04 and going to the ATI drivers.  I was using the open source drivers before.

---

### Post by thumper_e on 2008-04-28
I also only get video playback in full screen unless i switch off compiz.

using the proprietry ATI drivers on hardy heron.

fglrx returns;
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7415 Release

Modules loded in xorg;
glx
GLcore
dri
v4l

Anyone any ideas?

Ian

---

### Post by thumper_e on 2008-05-04
Problem fixed by;

System --> Preferences --> Multimedia Systems selector 

On the video tab changing to X window system (no Xv) on the plugin type.

Ian

---

### Post by avra911 on 2008-05-07
> **thumper_e said:**
> Problem fixed by;

System --> Preferences --> Multimedia Systems selector 

On the video tab changing to X window system (no Xv) on the plugin type.

Ian

... and for VLC to also play not only fullscreen after the settings "X window system (no Xv) on the plugin type" open in VLC 
-Settings 
-Prefeferences 
-Video 
-Output Modules 
-Advanced options 
and select X11video output (this one worked for me)

---

### Post by Bookman on 2008-06-30
> **thumper_e said:**
> Problem fixed by;

System --> Preferences --> Multimedia Systems selector 

On the video tab changing to X window system (no Xv) on the plugin type.

Ian

Dude what build arr you on? I have no Multimedia Systems option

---

### Post by thumper_e on 2008-06-30
Using Hardy Heron mate. 

If its not there, try right clicking on system up at the top, then edit menu's, scroll down to preferences on the left click it and scroll down on the right and see if it's(Multimedia System Selector) there, if so click the check box to enable it in the menu.

Ian

---

### Post by nosfer82 on 2008-07-14
> **avra911 said:**
> ... and for VLC to also play not only fullscreen after the settings "X window system (no Xv) on the plugin type" open in VLC 
-Settings 
-Prefeferences 
-Video 
-Output Modules 
-Advanced options 
and select X11video output (this one worked for me)

Thanks man I was breaking my head

---

