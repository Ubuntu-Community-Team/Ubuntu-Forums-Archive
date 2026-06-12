---
title: "cannot unmute microphone from volume control"
date: 2009-02-18
forum: Multimedia Software
---

### Post by lenards on 2009-02-18
OS: Ubuntu 8.10 Intrepid Ibex (laptop)

Sound card: HDA Intel
chip: Realtek ALC880

I have sound, that's all okay.  I open volume control, go to the recording tab. I click to get rid of the "red x", indicating mute, and then when I reopen the volume control the "red x"'s are back.  

[volume control, recording tab]("http://gigism.com/volume_control_recording_tab.png")

Any ideas way I wouldn't be able to get the capture tracks unmuted?  Is there a particular log file I should check out?  I have a headset plugged and have verified that the headset is not muted and works on my WinXP install.

---

### Post by lenards on 2009-02-18
It looks like this is, in fact, a bug: 

[Bug #290121]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/290121")

---

