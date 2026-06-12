---
title: "Where to configure X86Audio* signals?"
date: 2009-04-28
forum: Multimedia Software
---

### Post by Hichhiker on 2009-04-28
I have a keyboard with built in mute/volume control.

The buttons/control are bound to X86AudioMute, X86AudioRaiseVolume, X86AudioLowerVolume signals.

End result is that this controls the PCM input on the mixer. Unfortunately PCM input is buggy in Ubuntu+Intel audio (nasty crackling noise when you mute, other bugs). I want to remap it to control master volume instead. Any idea where to look for this mapping? Everywhere I look all I find is how to bing the key to the signal. This is NOT what I am looking for.


Thanks.

---

### Post by markbuntu on 2009-04-28
You need to change the setting in the panel volume control (the little speaker icon)from pcm to master. Right click on the little speaker choose preferences and click on master. Then 

Open System/Preferences/Sound and check that the Default Mixer Tracks is set to your sound card and in the box it says Master. This is where the device to be controlled is set and the volume control preferences is where you set what part of the device is controlled.

There is an update on the way to fix that crackling but keeping the PCM volume up all the way seems to fix it for many people and now you should be able to do that.

---

### Post by Hichhiker on 2009-04-28
> **markbuntu said:**
> You need to change the setting in the panel volume control (the little speaker icon)from pcm to master. Right click on the little speaker choose preferences and click on master. Then 

Open System/Preferences/Sound and check that the Default Mixer Tracks is set to your sound card and in the box it says Master. This is where the device to be controlled is set and the volume control preferences is where you set what part of the device is controlled.

There is an update on the way to fix that crackling but keeping the PCM volume up all the way seems to fix it for many people and now you should be able to do that.

Thanks. The second part (System/Preferences/Sound) did it. I am a much happier user.

-HH

---

