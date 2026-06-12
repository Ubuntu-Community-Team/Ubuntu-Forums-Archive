---
title: "Constant static sound"
date: 2008-08-31
forum: Multimedia Software
---

### Post by joey_breizh on 2008-08-31
I was having some issues with Skype (it gives me a "problem with audio playback" whenever I try to call someone) and a friend tried to look around on the Terminal to see what was up... he didn't find anything but now my speakers are constantly making static sound.

The only way I can turn them off is by going into the Volume Control and muting either the Master output or the Front output.

Alsamixer is not being very helpful because for some reasons it's only been displaying the Master output instead of all the outputs like it used to do before. (I think that particular change occurred when I followed the directions [here]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") in order to fix a sound bug with Flash.)

Here is info on my hardware:
>        description: Audio device
       product: SBx00 Azalia
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel


Help would be greatly appreciated because the problem is awfully annoying.

---

### Post by joey_breizh on 2008-08-31
Solved. The microphone output was doing the static sound and I could see it in alsamixer or Volume Control so I couldn't bring the volume down.

I would still like to know how to visualize all the outputs in alsamixer again though.

---

### Post by minky311 on 2008-08-31
If you are talking about alsamixer in the terminal pressing the tab key changes the view.

---

### Post by joey_breizh on 2008-08-31
I've figured that out but whatever view I'm in I can only see Master and/or Capture. PCM, MIC, all the other stuff is never there.

---

### Post by minky311 on 2008-08-31
What about right clicking the speaker icon in the upper right hand corner and going to volume control then clicking edit preferences.

---

### Post by joey_breizh on 2008-08-31
I have a number of outputs selected there, but none of them are in alsamixer...

---

