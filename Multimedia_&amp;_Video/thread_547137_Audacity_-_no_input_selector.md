---
title: "Audacity - no input selector"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by le_vainqueur on 2007-09-09
Here's my problem: 

In Audacity, there is no input selector available on the Mixer Toolbar.  I have found Audacity's possible reasons for this.  They are:

> Input Selector minimised, sliders present

If the selector just appears as a small lump but you have the input and output volume sliders, this usually means that there is currently no audio device available to, or recognised by Audacity for recording on your system. There are various possible causes for this. They include:

   1. Another audio program like XMMS is using the sound device
   2. A sound daemon like esound (ESD) or aRts is using the sound device
   3. You have system sounds turned on in a desktop environment like Gnome or KDE
   4. You don't have the correct permissions to access the sound device
   5. You are using Audacity 1.2.6 and are selecting the ALSA device but don't have the necessary OSS emulation modules installed.
   6. The recording device you currently have selected on the Audio I/O tab of the Preferences only has one input source, and so there is no choice that can be made. Many USB and Firewire Input/Output devices fall into this category. 

So, any other applications using the sound device must be disabled, unless you are using the OSS device and the aRts daemon, in which case you can use the wrapper provided by aRts and run
$ artsdsp audacity
Note that some users report recording issues when doing this.

If you use OSS, you need to check that /dev/dsp (the OSS device) is present. If you use ALSA, you need to get the OSS emulation for ALSA installed, unless you are using Audacity 1.3.x which supports ALSA natively. You can launch Audacity from the command line as
$ aoss audacity
which will load OSS emulation modules for ALSA if you have them installed.

On many distributions you need to add your user to the "audio" group so they have permissions to access the sound devices. 

This does not completely describe my problem, though.  I do not have a bump where the selector should be, I have nothing there at all.  The two sliders are present on the toolbar as they should be, but there is no drop-down menu available.  

I couldn't seem to extract anything helpful from the recommendations quoted above.  I tried what I knew how to do, and I ran the program with the commands they gave, but nothing worked.

My sound device is just my chipset.  My motherboard is a: Intel D946GZISSL Intel Socket 775 MicroATX Motherboard.  

Any pointers here?

---

### Post by le_vainqueur on 2007-09-11
*bump

---

### Post by dabl on 2007-09-11
There is some device on your motherboard that is actually the sound system.  Probably entering ```
lspci
``` in the console will turn it up on the list. On my Intel motherboard it is a STAC92xx chip.

What does the "Input" tab on your ALSA mixer show?   That's the thing that looks like a speaker in the upper right corner of your screen.  Right-click it, and "open mixer", then examine the input tab.  There should be a couple of selections, like "Line In" and "Mic".  There should also be a device shown.

Have you installed the packages alsamixer-base, alsagui, and alsaoss (or maybe alsa-oss)?

One more thing - Audacity is very picky about having exclusive access to the sound system -- close any and all apps that might want to make a sound, like Firefox, for example, and Mplayer and stuff like that.

Hope there's some help in here somewhere.

---

### Post by wrathkeg on 2007-09-21
> **le_vainqueur said:**
> 
This does not completely describe my problem, though.  I do not have a bump where the selector should be, I have nothing there at all.  The two sliders are present on the toolbar as they should be, but there is no drop-down menu available.  

I have exactly the same problem (mixers showing up, but no drop down menu).  Did you, or anyone else for that matter, solve this? Audacity is a great program, but without being able to change the inputs it is, for me at least, useless.
TIA,
WK

---

### Post by wrathkeg on 2007-09-21
For reference:  downgrading to an earlier version of audacity (available here: [http://packages.ubuntu.com/edgy/sound/audacity](http://packages.ubuntu.com/edgy/sound/audacity) ) worked for me.

WK.

---

