---
title: "MythTV playback way too dark"
date: 2008-01-25
forum: Mythbuntu
---

### Post by chickengirl on 2008-01-25
I'm running Mythbuntu on top of Xubuntu Gutsy and in the video selection screen, the little thumbnail videos look fine, but in actual playback, they're way too dark.

I know that I can futz with brightness, contrast, etc for individual channels, but it's not just one or two channels, it's *every channel* and the ones I have futzed with, the problem is still not fixed. Is there any way I can fix the brightness and contrast levels *universally* for all MythTV playback?

---

### Post by novellahub on 2008-01-25
What video card are you using?  If you are using a Nvidia card with the restricted driver enabled, you can use the following from a command prompt:

```
nvidia-settings
```

From there you can adjust the individual settings.

---

### Post by chickengirl on 2008-01-25
I'm not sure exactly what video card is in the computer. It's not nvidia, though. It's one of those cheap Linspire boxes that fry's used to sell. (The Linspire is long gone, of course.)

---

### Post by harmonyMyth on 2009-04-30
> **chickengirl said:**
> I'm not sure exactly what video card is in the computer. It's not nvidia, though. It's one of those cheap Linspire boxes that fry's used to sell. (The Linspire is long gone, of course.)

You can find your video card under Ubuntu at:

   System->Preferences->Hardware Information

or by running:

    python /usr/bin/hal-device-manager

(you may have to install it on Xubuntu).


Regarding your original question, 
Surprisingly, at least for me running 
Ubuntu desktop on Mythbuntu Hardy, 
you adjust the brightness, contrast, etc, 
for all channels in MythTV, by playing 
a video in Totem (aka Movie Player), 
and adjusting the sliders at the bottom 
of the Display tab under the 
Edit->Preferences menu, because 
adjustments made there are system wide 
(except, perhaps even more inexplicably, 
MythTV's little preview videos).  
If you want to use a specific scene 
(e.g., where you noticed the problem) 
to tune the settings, you may find it 
in one MythTV's recent .mpgs 
(in /var/lib/mythtv/recordings).

Cheers

---

