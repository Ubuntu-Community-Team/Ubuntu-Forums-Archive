---
title: "[SOLVED] Flickering Video in VLC, MPlayer"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by DingsBumps on 2008-02-25
I'm trying to play a DVD but the image is very flickery in Mplayer, Totem (same app as mplayer?), and VLC. I am running compiz-fusion, but I have a fairly new/powerful system (radeon HD3850, 4GB ram, E6750@2.8ghz). What could be causing this? Playback flickers even when playing from a file on my HD. 
Another observation is that even when VLC or MPLAYER is in the background, behind another window, the video part of the app is still flickering above the window in the foreground. The visualizer in MPlayer displays the same flicker.

The above observations cause me to beleive that it might be a problem with my compiz config. Any ideas?

Edit: and turning off compiz caused the problem to go away. But I really like compiz. How can I fix this?

---

### Post by Melcar on 2008-02-25
Either turn off Compiz, or change your video player's rendering method to X.

---

### Post by DingsBumps on 2008-02-25
How can I do that. I see in VLC's video options a box for X11 Display. What goes in here? 0 (for monitor 0)? I'm pulling at straws, I have no idea how to do this. 

Also, my screensaver also flickers. Can I change video output on a global level for all video output?

---

### Post by Melcar on 2008-02-25
For VLC, click on the Settings tab and go to Preferences.  On the new window check the Advanced Options box.  Now browse the three menu on the left and go to Video>Output Modules.  Use the drop down box on the left to select X11 Output.
For Totem, you need to open the Multimedia Systems Selector window.  This menu item does not show on the default menu configuration, so you have to open the menu customizer (System>Preferences>Main Menu) and enable it.  Once you can access it, just look under the Video tab and select X Window System from the default output plugin drop down menu.
For Mplayer, just open the Preferences window, select the Video tab, and select X11.

As for the screensavers, as long as you're running Compiz you will get the flickering, but only when running opengl screensavers.  Savers that use regular X to render work fine.

---

### Post by banelos on 2008-02-26
You're the man Melcar, that fixed all the flickering video issues I had [-o<

---

### Post by ZombiePinguin on 2008-02-26
> **Melcar said:**
> For VLC, click on the Settings tab and go to Preferences.  On the new window check the Advanced Options box.  Now browse the three menu on the left and go to Video>Output Modules.  Use the drop down box on the left to select X11 Output.

I have exact the same problem, but there's no dropdown menu there, only an entering line

and there's not enough red color in videos, but it does not seems the vlc's problem, where's the general color setting?

P.S.: I'm running i386 7.10 on a Core2Duo TX7200 and X1600, so there should be no problems with not enough power, it seems a software problem

EDIT:
if I'm starting xine (v0.99.5) with the console, it gives me this error message:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  14 ()
  Serial number of failed request:  2404
  Current serial number in output stream:  2404

now I'm somewhat confused

---

### Post by Melcar on 2008-02-26
> **ZombiePinguin said:**
> I have exact the same problem, but there's no dropdown menu there, only an entering line

and there's not enough red color in videos, but it does not seems the vlc's problem, where's the general color setting?

P.S.: I'm running i386 7.10 on a Core2Duo TX7200 and X1600, so there should be no problems with not enough power, it seems a software problem

EDIT:
if I'm starting xine (v0.99.5) with the console, it gives me this error message:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  14 ()
  Serial number of failed request:  2404
  Current serial number in output stream:  2404

now I'm somewhat confused


You need to check the 'Advanced Options' box (bottom right corner), then navigate using the tree menu on the left.

---

### Post by ZombiePinguin on 2008-02-27
well, I temporally solved the problem by deactivating the restricted ATI drivers for my X1600, the standart Linux driver seems to working flawlessly

and for VLC, I have the "advanced options" checked, but if I select X11 from the tree menu on the left, what I'm supposed to do on the right side, there's this entering line for an X11 hardware monitor?

P.S.: Xine is still crashing...

---

### Post by DingsBumps on 2008-02-27
Zombie Penguin: Instead of opening the "output modules" tree, just click on output modules. Do not open the tree and hit X11 on the left side in the tree view. 

Simpler explanantion: go to Video->Output modules and use the drop down box. NOT Video->Output modules->X11.

I had the same confusion at first. 

Good luck!
Oh, and for your color adjustment, I would try changing it on your monitor (unless you dual-boot and that would change the colors for your other OS)

---

