---
title: "No Sound, CT4740, Ubuntu 7.06"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by Imperdimper on 2007-09-30
Oh do I need help with this, I can't even begin.  Sound is the only thing that is keeping me from moving away from Microsoft.  I think I'm half excited about moving to the new OS and half excited to be getting rid of Windows.  But the lack of sound is really ruining the "new OS vibes", so I'm here to find out what to do so I can get things bopping along again.  I will try to be as detailed as possible.

Card Reads: Creative Sound Studio, Model: CT4740
aplay -l:
  **** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When using GNOME ALSA Mixer I get the following error:
An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/Cirrus_Logic_CS4297A_rev_4-Line_In->Rear_Out": `>' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/Cirrus_Logic_CS4297A_rev_4-Line_In->Rear_Out": `>' is an invalid character in key/directory names

If I activate the "EIC958 1" option on the Alsa mixer I do get sound from my speakers.  If I play an .ogg I can hear the music slightly, but the static kills any possible enjoyment that could be gained from Ludwig.  This 'static' noise is only at one level, if I turn down the master volume, or even mute it, it has no effect.

I have also gone through the 'alsamixer' items, making sure none was muted and that I had tried all the options.


Oh my, oh my do I hope I can get this resolved.  I've done loads of searches online, tried loads of things, even ended up killing Ubuntu at one point.

This is a brand new install of Ubuntu 7.06, so the sound has never worked.   At least that's a good starting point, I hope.

Imper

Edit:  Stupid me, you can see how new I am to Linux, 7.04 obviously.

---

### Post by Imperdimper on 2007-10-02
Is there any thing I can add that might help illicit a response?  The sound is the only thing that is keeping me from Ubuntu, it is just unusable in its current state.

---

### Post by Imperdimper on 2007-10-04
Oh well, downloading OpenSUSE now, maybe I'll have better luck with my sound there.

---

### Post by radj2 on 2007-10-04
try this

You go to Sound in Ubuntu preferences and no matter what you try - your selection for a default sound card will not stick! No need to fear. Just watch the video above and use the following scripts. Copy each script, then right click on you desktop and choose create document. Paste each script in there. Once the correct card name has been pasted into the script (you’ll likely want a script for the sound card and for the headset if needed), you are half way there. Right click on it afterward and then goto properties, choose permissions then allow to be executed.

What sound cards do you have? Open up a terminal and paste in:

sudo asoundconf list

Make note of each card. Use trial and error if you are unsure which card is which. The process of elimination will only take a few tries.

#! /bin/sh -f

sudo asoundconf set-default-card name-of-card-to-be-default

---

