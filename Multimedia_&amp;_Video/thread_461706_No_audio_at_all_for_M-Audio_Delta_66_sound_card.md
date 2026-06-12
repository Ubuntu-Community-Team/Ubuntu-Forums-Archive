---
title: "No audio at all for M-Audio Delta 66 sound card"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by drumjunky on 2007-06-02
Like many others, I am very new at this. I just switched to Ubuntu a week ago and so far it's ok. Not great, but ok.

My main problem is that I can't get sound. 

_Here is the *aplay -l* report:_

**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: M66 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: M66_1 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I can't get anything to play back. I havn't even begun to try to record audio, but I'll cross that bridge later.  I've tried a few things on [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and I ended up having to reinstall Ubuntu. 

Anybody out there that can help? Please don't make me go back to Microsoft!

Thanks
Drumjunky

---

### Post by tgalati4 on 2007-06-02
sudo apt-get install envy24control
envy24control

Be sure to edit preferences and activate all of the channels, unmute them, and set the sliders to 70%.

Welcome to the community.

---

### Post by drumjunky on 2007-06-02
I opened the control utility which looks like the one from Windows, but still no sound coming out. I tried configuring the patchbay/router but nothing. Any suggestions?

---

### Post by tgalati4 on 2007-06-02
Do you see any green signals in the control panel?  If so, then the card is working.  It's a matter of getting the patch set up correctly.  Unfortunately, you need to be a mix engineer to get it set up correctly.  I'm not near my music station so I can't suggest the correct patch right now.  Perhaps tomorrow.

If no green signals, then there may be an interrupt issue with the card.  Windows is plug-n-play, Linux is not, so you have to make sure that there is not an interrupt conflict with the sound card.

I assume that the card was working fine in Windows.  

In BIOS, turn off PNP OS under PCI/Interrupts.  Also, temporarily turn off the parallel port and serial ports, this will free up interrupts so that Linux can use them.  Once you get it working, then you can turn things back on one at a time.

I like the M-Audio Delta 66 card, it's sweet.  I use it in a PII, 300 MHz wihitebox for recording church concerts.  I have it set up as dual boot:  Dynebolic 2.4.2 and Dapper Drake.  I use Dynebolic for real-time recording.

Good luck.

---

### Post by drumjunky on 2007-06-02
It worked! Wow, loud and clear. I love you guys.:D

---

### Post by tgalati4 on 2007-06-02
What exactly did you do to get your card working?

---

### Post by drumjunky on 2007-06-03
All I ended up doing was turning off PNP in the bios. I couldn't figure out how to turn off serial or parallel ports but turning the PNP off did the trick.

---

