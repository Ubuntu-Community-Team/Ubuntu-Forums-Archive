---
title: "No Sound after updates - Ubuntu 9.04"
date: 2009-07-03
forum: Multimedia Software
---

### Post by edantes on 2009-07-03
Problem solved after the series of remove/reinstalls described here:

[http://ubuntuforums.org/showpost.php?p=7553674&postcount=1501](http://ubuntuforums.org/showpost.php?p=7553674&postcount=1501)


Original post follows, preserved for posterity:
-----
After installing a few updates, my sound system stopped working. Not sure of the exact cause or chain of events, but the result is that all I get are clicking noises when System->Preferences->Sound selects "Autodetect" or "ALSA". I still get the correct test tone when I select the "OSS Analog" interface.

Question for our kind hearted readers: How can I restore the default sound infrastructure I was using before? Everything still works if I boot from the Ubuntu 9.04 CD. I tried reinstalling packages from ALSA and PulseAudio without success.

Thanks in advance for your suggestions.

A bit of extra information:

lspci | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

