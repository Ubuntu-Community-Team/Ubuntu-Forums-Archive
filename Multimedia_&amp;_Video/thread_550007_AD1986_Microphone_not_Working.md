---
title: "AD1986 Microphone not Working"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by curatola on 2007-09-13
Hi everyone, I'd like some help here, I have a asus P5SD2-X motherboard with AD1986A onboard sound card. The problem is, playback works fine but I can't get to hear my own voice on speakers neither can I have conversations on Skype. I have played with mixer levels and options and still nothing. I see that alsa has corrected some issues on that AD1986A after release 14 of Alsa. any help here would be appreciated. This is what's been holding me to migrate completely to Linux. 

**UPDATE:** From Alsa project page I found this: 

Changes v1.0.14rc3 v1.0.14rc4 (65,964 bytes)
107: - hda-codec - Add missing Mic Boost for AD1986A codec
122: - hda-codec - Fix front/rear mic inputs on AD1986A codec
127: - hda-codec - Fix surround output on AD1986A 

Now the question is: How can I install latest version of alsa on 7.04(Feisty), from my research Feisty is using version 13. Any help??

Thanks:)

---

### Post by linuxwizard on 2007-09-13
Have you tried this
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

See if this will help installing the new Alsa
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

