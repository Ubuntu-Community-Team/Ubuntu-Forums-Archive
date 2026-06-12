---
title: "Problems with video playback in VLC"
date: 2008-10-06
forum: Multimedia Software
---

### Post by orphefs on 2008-10-06
Hi,

I am new to Ubuntu and I am experiencing some problems with video playback in VLC. The video seems to get stuck at times, playback skips frames, and the pixels are visible, whereas in windows the same video file seems to be of excellent quality (using vlc there too). Any suggestions on what could be the problem and how to fix it? My graphics card is ATI_Mobility_Radeon_X700 Hypermemory 512MB.

p.s.: also, Ubuntu seems to be running slowly in general, maybe it is due to the gui itself, or would I need to reconfigure the graphics drivers?

Thank you in advance,
Orpheus :)

---

### Post by buddhadba on 2008-11-09
I upgraded to 8.04 on my Dell Inspiron 8500 laptop last night and once I got my wireless adapter back on the ndiswrapper solution, I had a generally better experience, particularly playing DVDs in Totem. However, my VLC player, which worked perfectly with 7.10, started skipping and losing frames in 8.04. I looked around, but nothing seemed to help (for example, my computer would accept the ALSA setting on everything, as suggested in some threads), but simply getting rid of pulseaudio as outlined in this thread:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg964488.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg964488.html)

made VLC work fine. I haven't tested everything, but DVDs play fine still in Totem, but I have apparently lost the ability to play CDs. I'll keep working on that, I guess, but VLC works again.

-- buddhadba

---

### Post by hades_6_6_6 on 2008-11-10
> **orphefs said:**
> I am experiencing some problems with video playback in VLC. The video seems to get stuck at times, playback skips frames, and the pixels are visible
Same thing for me. Totem plays videos like a charm, but VLC get stuck ~ every 5 minutes. Sound keeps playing but picture freezes.
Any idea?

---

### Post by Rudias on 2011-04-02
Start VLC and click on Settings, then Preferences.

o Expand Video and then expand Output modules. You will notice several options for output device.

o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.

o Pick X11 video output

o Click on Save and you are set!

* MPlayer Users (Mplayer is not installed by default)

o Start Mplayer

o Right-click on the screen and select Preferences

o Select the Video tab and under Available Drivers select “X11 (XImage/Shm)”

o Click Save and restart the program for the setting to take effect.

---

