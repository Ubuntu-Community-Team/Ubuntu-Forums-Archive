---
title: "[B]snd-hda-intel[/B] - Very Low Volume"
date: 2009-02-07
forum: Mythbuntu
---

### Post by bryanf2009 on 2009-02-07
The sound on my Motherboard - Intel DG965OT is very low.  I have to turn up my Speakers all the way to hear anything (this is not loud at all)

Does anyone have a fix for this?

Thanks
Bryan

---

### Post by movieman on 2009-02-07
Have you checked the volume control in the ALSA configuration?

---

### Post by bryanf2009 on 2009-02-08
Yes - this was the first thing I did.  Unmuted everything in Playback.  But the sound was not there

It seems alsa has a newer version which fixes this 1.0.19 (releases 19 Jan 2009) - for some reason Mythbuntu is still on 1.0.18

I did however, manage to get the volume somewhat working.
[LIST=1]
[*]Removed Module snd-hda-intel
[*]Reinstalled Module snd-hda-intel
[*]Went into xine and configured the Audio to be 7.1 Sourround
[*]Went to Package Manager and search "alsa" and reinstalled the items already installed (be careful NOT to install items which were not already installed, and do not Uninstall them.  There is an option to "Re-Install")
[*]Went to Package Manager and search for "sound" - reinstalled all the packages which were already installed (be careful NOT to install items which were not already installed, and do not Uninstall them.  There is an option to "Re-Install")
[*]Wen to the Mixer and enabled all the items
[*]Then I adjusted Master and the PCM until the sound was at a nice enough level.
[/LIST]

I am now getting 7.1 Surround Sound from the on Board Intel DG965OT.  It is pretty Loud... And it sounds awesome!

Hopefully Mythbuntu will release 1.0.19 soon! 

Bryan

---

### Post by bryanf2009 on 2009-02-08
I wanted to detemine what actually enabled the soudn to play.

[LIST]
[*]Removed Module snd-hda-intel
[*]Install Module snd-hda-intel
[/LIST]

Thus if one is having problems with their sound:  Determine which Sound Module is being used.

In saying I got my sound to work; there seems to be issues with the volume having to be very high tp get any sound (better than having the volume all the way up and only a little bit of sound); however, I still think there is an issue here.

Note:  Mythbuntu is using ALSA 1.0.18; where as an update has come out; not sure when this will be included.

Bryan

---

