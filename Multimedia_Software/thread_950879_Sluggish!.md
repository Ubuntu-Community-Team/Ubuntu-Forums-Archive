---
title: "Sluggish!"
date: 2008-10-17
forum: Multimedia Software
---

### Post by Ubun00btu on 2008-10-17
Ok, I had to do a complete reinstall of Hardy due to some problems with my previous install of Feisty and Gutsy during the upgrade.  

So far I've reinstalled the Nvidia drivers from the Nvidia site and had to install the HDA intel audio (ALC888) for my 780i board, plus added compiz-fusion and Emerald.

I don't know what the problem is, but it is very sluggish now.  For instance when watching youtube, the video/sound clicks, pops, and stutters when I'm switching tabs or doing other tasks such as opening a new app.  It is very slow switching tabs.  glxgears returns 3000+ FPS, but I can see it skip when switching apps. 

I've tried disabling emerald and that seems to have no effect.  

Any ideas what I should look at to fix the problem and get it back up to speed?  Hardware performance is absolutely not a factor, it's a new build with 9800GTX+ cards, 4GB ram and a E8400 dual-core processor.  Gutsy/Feisty ran better on my old build.

---

### Post by kaivalagi on 2008-10-17
> **Ubun00btu said:**
> Ok, I had to do a complete reinstall of Hardy due to some problems with my previous install of Feisty and Gutsy during the upgrade.  

So far I've reinstalled the Nvidia drivers from the Nvidia site and had to install the HDA intel audio (ALC888) for my 780i board, plus added compiz-fusion and Emerald.

I don't know what the problem is, but it is very sluggish now.  For instance when watching youtube, the video/sound clicks, pops, and stutters when I'm switching tabs or doing other tasks such as opening a new app.  It is very slow switching tabs.  glxgears returns 3000+ FPS, but I can see it skip when switching apps. 

I've tried disabling emerald and that seems to have no effect.  

Any ideas what I should look at to fix the problem and get it back up to speed?  Hardware performance is absolutely not a factor, it's a new build with 9800GTX+ cards, 4GB ram and a E8400 dual-core processor.  Gutsy/Feisty ran better on my old build.

Rather than installing the nvidia drivers based on the nvidia download have you tried using envy, it might give better results?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Ubun00btu on 2008-10-17
I just installed envy and unfortunately it seems to have killed the previous driver installation's functionality.  compiz/emerald no longer works, and when I try either the Nvidia Settings Manager or glxgears it gives a glx error.  I also get the clicks/pops on youtube still when switching windows.  It may be the codec or plugin in youtube, or even the sound card drivers consuming processing power.  I'm not sure though, using Amarok there was no problem with playback quality but the GUI was still sluggish.

---

### Post by kaivalagi on 2008-10-17
> **Ubun00btu said:**
> I just installed envy and unfortunately it seems to have killed the previous driver installation's functionality.  compiz/emerald no longer works, and when I try either the Nvidia Settings Manager or glxgears it gives a glx error.  I also get the clicks/pops on youtube still when switching windows.  It may be the codec or plugin in youtube, or even the sound card drivers consuming processing power.  I'm not sure though, using Amarok there was no problem with playback quality but the GUI was still sluggish.

Flash issues with youtube?

I don't suppose you kept your old xorg config file?

---

### Post by Ubun00btu on 2008-10-17
The sluggishness does not apply solely to Youtube or Firefox.  I just restarted with the RDM ACL888/Intel HDA driver disabled and the issue still applies.  

Moving windows around, switching tabs, opening/closing apps.  Starting to seem like more than just a multimedia issue.

EDIT:  I DL'd and installed Sauerbraten (Game) to see how that would run and it was pretty messed up.  The mouse control was "rubber-bandy" as well as the keyboard input, and the mouse couldn't "hold still", it was almost constantly twitching.  

What else would cause this, an interrupt issue or conflict of some type?

---

### Post by kaivalagi on 2008-10-17
I'm assuming you have no issues with either Feisty or Gutsy?

It sounds like the first thing to do is make sure the xorg stuff is setup correctly, and that the correct drivers are in use.

Did you try using the standard restricted drivers first of all? If those work stick with them. The nvidia drivers in Hardy are fairly recent and might work with your mobo/graphics card

I would do some digging around your xorg.conf, search for details on the right settings etc (/etc/X11/xorg.conf). My xorg.conf is attached in case that will help, it is pretty much default settings with a few tweaks, nothing serious. I am using a nvidia 8800 graphics card on a GeForce 680i SLI board.

I get the feeling we're going to need some help from other forum users here...

---

