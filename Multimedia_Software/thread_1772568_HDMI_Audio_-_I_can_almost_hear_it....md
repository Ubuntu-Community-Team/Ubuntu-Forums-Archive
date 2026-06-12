---
title: "HDMI Audio - I can almost hear it..."
date: 2011-05-31
forum: Multimedia Software
---

### Post by RMOP on 2011-05-31
but not quite.

I've scoured this and other websites, and have made substantial progress, but still have no audio output.

I installed a Zotac nVidia GeForce GT220 card yesterday. The video is working just great with Ubuntu 2.6.32-32-generic, and both video and audio are working when I boot to Windows XP.

When I first installed, Ubuntu was still seeing the on-board VIA sound chip, but I disabled that, modified my sound.conf file, and now my nVidia card is recognized. But it still doesn't work. I've updated everything I can think of.

Here's some relevant output:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Here's my sound.conf file:

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

AlsaMixer v1.0.24.2 shows my nVidia card, as does the Sound Preferences applet. The selectable items in AlsaMixer is S/PDIF. Also listed but not selectable are S/PDIF1 - 3. These are shown as "OFF" when I arrow over them. The boxes above them say "MM" whereas the box over S/PDIF says "OO."

The only thing which seemed to get the nVidia sound card recognized was the creation of the sound.conf file. I'm sure that I've either added something wrong there or omitted something crucial.

Pointers, please? Thanks.

---

### Post by hvc123 on 2011-05-31
MM means mute i think, have you tried pressing M to unmute them ?

---

### Post by ghostborg on 2011-05-31
M toggles the mute and the up and down arrows adjust the volume.

If you make changes don't forget to save them after you exit alsamixer.
alsactl store


Make sure the correct hardware is selected in Hardware and Output tabs in the sound preferences. Test it out in sound effects by clicking on Bark, Drip etc

I had an audio problem with 11.04 for about two weeks until an update came down and fixed the bug which also seemed to cause people in 10.10 problems too.

---

### Post by lidex on 2011-05-31
reference this:
[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

---

### Post by RMOP on 2011-06-01
Thanks, all.

It's sorted. As I find so often to be the case, the solution is a bit obscure. When looking at the link you sent, I found references to PulseAudio. That led to a bit of quick research, and the use of gstreamer-properties. When set to PulseAudio, my HDMI card was not selectable, but when I changed to ALSA, I could select my card from gstreamer-properties, and I now have SOUND.

---

