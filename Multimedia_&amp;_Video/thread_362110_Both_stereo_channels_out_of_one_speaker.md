---
title: "Both stereo channels out of one speaker"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by BenHines on 2007-02-15
Hi,

Has anyone had this problem?  It seems that both stereo channels of sound are coming out of the left speaker and nothing is coming out of the right speaker.  I'm pretty new to linux, so I'm not sure how to go about fixing this.  When I do 'aplay -l' I get this:

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm using the on-board sound on a PCChips P23G (V3.0) motherboard.  

I went into the volume control and manipulated the left and right volume sliders separately.  Only the left slider had any effect.  

Any ideas on what to do next?  Thanks!

---

### Post by Daveth on 2007-02-15
asides from the very obvious checking and cleaning of your connections, have you tried loading alsamixer? Worked wonders for my 5.1 sound.
Find it in Synaptic under gnome -alsamixer.

---

### Post by BenHines on 2007-02-17
Hello,

This issue is now fixed.  In and attempt to fix a different issue with the motherboard, I flashed the BIOS with the latest from PCChips and when I rebooted I had full stereo sound coming from botht he left and right channels.

---

