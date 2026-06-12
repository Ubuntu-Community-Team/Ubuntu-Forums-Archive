---
title: "Problems with NI Audio4dj and recording"
date: 2009-10-06
forum: Multimedia Software
---

### Post by Monomer on 2009-10-06
I ave an Audio4dj here that's giving me some problems. It works well with programs such as xwax.

Any audio recording problem, I cant get it to work with. Audacity crashes after I select it as a A/I and click ok.

It shows up as a Pulseaudio mixer under volume control. I've removed pulse and switch to esound with no luck.




Anyone? I'm a fairly new linux user here - a solution in laymen's terms would be nice.

---

### Post by Monomer on 2009-10-06
The kernel necessary for xwax to work was also installed:



Native Instruments' Audio 4 DJ

    * Uses snd-usb-caiaq module
          o Developed by Native Instruments
          o Kernel >= 2.6.30 required
    * The device presents two stereo pairs by default; use the following ALSA devices:
          o plughw:DJ,0,0
          o plughw:DJ,0,1

---

### Post by Vigh on 2009-11-01
how did you manage to set up your soundcard to work in ubuntu? I have a audio kontrol 1 but ive been struggling to set it up, good luck with fixing ur recording issues, have u tried using JACK? and then recording

---

