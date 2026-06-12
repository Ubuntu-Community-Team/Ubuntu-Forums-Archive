---
title: "XF86Audio[Raise/Lower]Volume and Alsa Mixer Master Controls not bound"
date: 2009-03-22
forum: Multimedia Software
---

### Post by Anaximander Thales on 2009-03-22
I have a G15 Gaming Keyboard and an Auzentech X-Meridian sound card.

When I open Alsa Mixer, I have 5 'Master' controls.  3 are Stereo Controls, 2 are Mono controls.  These Master controls handle each of the amps for the 7.1 sound card.

The issue I'm having is when I use the volume control on the keyboard, the 1st Master is controlled, and the other 4 masters get set to zero, thereby disabling my surround sound settings.  

In investigating the keybind settings, I've set the Keyboard Setting (for XFCE) for G15 Keyboard.  The volume control is bound to XF86Audio[Raise/Lower]Volume.  

My question is what to set so that all 5 'master' controls are affected when I use the volume control.

---

### Post by Anaximander Thales on 2009-03-24
Bump

---

### Post by Anaximander Thales on 2009-03-27
Any type of information -- even if it's search the forums better, especially if you could give me some search words.  I've been searching and haven't been able to find anything that was useful.

---

### Post by Anaximander Thales on 2009-03-28
Okay -- poking around, found a bit more information, aumix is the culprit.

Now, I need to figure out how to get aumix to adjust all the 'master, 0 - 4' controls in alsamixer instead of just 'master, 0'

I'll post more as I figure it out.

---

### Post by Anaximander Thales on 2009-03-28
well, it seems removing aumix and using amixer will solve the problem.

However, the odd problem is that I must use a 5% increment, otherwise it will only effect Master, 0 - Master, 1 - 4 aren't effected with 2%.

Strange?

Any ideas on that would be appreciated.

---

### Post by cubeist on 2009-03-28
I wish I could help, but I have the same problem.  I have an apple keyboard, and the volume up/down and mute are correctly linked to xf86audio... in the keyboard prefs, but pressing the keys won't actually change the volume.  I have tried every setting in volume control and sound prefs with no luck, for me, the xf86audio command in not linked correctly.

Perhaps if a couple more people have the same problem with no apparent workaround, I will file a bug report.

ps, I didn't have aumix installed and I don't use pulseaudio, just alsa.

---

### Post by mjbcoug on 2009-05-05
I am having the same problem.  Can't figure out how to link the volume keys to actually control the volume.  They issue the proper XF86Audio commands, but don't affect the volume output.

---

### Post by mjbcoug on 2009-05-05
FOUND IT~!  This applies to JAUNTY.  
Make sure you have Volume [Mute/Up/Down] in Keyboard Shortcuts mapped to the matching XFAudio command key.  Then Open up System -> Preferences -> Sound.  Whatever you have selected for Sound Events-Sound Playback at the top (I have ALSA), you must select the same thing below under Default Mixer Tracks - Device (for me it's HDA Intel (Alsa mixer)).  Then in the list box below that select the device you want to control (probably Master, but you can shift-select multiple).

Works for me now.

---

### Post by CaspianCanuck on 2009-06-09
**mjbcoug**, thanks for the solution!  Works like a charm for me!  :D

---

