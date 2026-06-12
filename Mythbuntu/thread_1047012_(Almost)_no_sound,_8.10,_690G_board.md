---
title: "(Almost) no sound, 8.10, 690G board"
date: 2009-01-22
forum: Mythbuntu
---

### Post by mathog on 2009-01-22
8.10, kernel 2.6.27-9-generic, installed on an ECS AMD690GM-M2 motherboard.  When mythtv is set to "Watch TV" there is almost no sound.  Alsa mixer shows 

 Card: HDA ATI SB          
 Chip: Realtek ALC883 

and all the play devices are cranked up.  When the Front Out/Line Out
jack (E in the ECS documentation) is plugged into the TV audio in, and the TV volume turned way up, the sound is barely audible.  (All other jacks were tested, a few also made dim sounds, but none were any louder.)  The sound level is the same whether the front end runs on the CRT (screen0) or TV-OUT (screen1).  Is there a setting buried in mythtv somewhere that may be defaulting to a very low volume, or perhaps mute?  The video input is from an hdhomerun.  There is also an SAA7130 board in the system, but it isn't configured in Mythtv, and the default sound device is the HDA ATI SB.

Thanks

---

### Post by mathog on 2009-01-23
> **mathog said:**
> 8.10, kernel 2.6.27-9-generic, installed on an ECS AMD690GM-M2 motherboard.  When mythtv is set to "Watch TV" there is almost no sound.  Alsa mixer shows 

 Card: HDA ATI SB          
 Chip: Realtek ALC883 

and all the play devices are cranked up. 

I tried various settings for this, for instance:

options snd-hda-intel model=3stack-6ch

but could not get enough volume to be useful.  This seems to be a common problem with this hardware, see for instance:

[https://bugs.launchpad.net/alsa-driver/+bug/107232](https://bugs.launchpad.net/alsa-driver/+bug/107232)

In the end I pulled an ancient sound card (some no name board, with a I think a Realtek chip) out of an even more ancient machine (dual 286 processors) that had (luckily) not yet been sent to e-waste, installed that card, and disabled the on board sound.  The new sound card came up fine, alsamixer saw it, and sound was at a useful level in Mythtv.  Completely painless.

Sigh.  I bought the ECS 690G board specifically for DVR use because it had built in graphics and sound.  In the end, neither one of these was up to the task:  the video could not do component out (ATI hardware - 'nuf said) and the sound had insufficient volume.

---

### Post by mathog on 2009-01-24
The ALC883 sound device is working now - I'm not sure why though, and
don't have a huge confidence that it will continue to do so.

Here are the current settings:

Added

options snd-hda-intel model=3stack-6ch

as the last line of

/etc/modprobe.d/alsa-base

Then installed one package:

Applicatins -> system -> add/remove
  enable all
  add  gnome-alsa-mixer

Before doing so, there was only a faint sound, after doing so, there was a usable (although still not super loud) volume.  Dragging the volumes for Master, PCM, and Front all the way up (they were all at 100
or above 70). made it a bit louder still.

Finally, in mythtv, did:

Utilities/Setup -> Setup -> General, advance to the 3rd page, and set the Master and PCM volumes to 100%.  This fixed mythtv resetting the volume DOWN from what the mixers said, because one of these, I think Master, was only at 70%.

Now the odd part is that the only thing I did today inside Mythbuntu that seems to have resulted in a working ALC883 (analog) is
to add gnome-alsa-mixer.  Previous use of the terminal program "alsamixer", with similarly high settings, had not resulted in more than a whisper.

One thing I did do differently today was to boot Mandriva 2009 live to
get to a full Gnome desktop, and then used gnome-sound-property and gnome-volume to test various drivers with the ALC883.  Of these, the only one which worked was OSS, none of the ALSA modes would emit a peep.
And Mandriva 2009.0 uses a newer ALSA than does Mythbuntu 8.10.  After that booted into Mythbuntu, made the single change noted in the previous paragraph, and suddenly the sound worked.  

Here's hoping this success survives a few power cycles...

---

