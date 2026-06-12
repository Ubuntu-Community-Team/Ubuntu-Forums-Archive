---
title: "Sound output from SoundBlaster AudigyHD 24bit is terrible... Suggestions Please?"
date: 2008-10-06
forum: Multimedia Software
---

### Post by AFarris01 on 2008-10-06
ey everybody...im not really having a *problem*, more of a growing annoyance.  After upgrading to Ubuntu 8.04, and gaining pulseaudio, i was finally able to successfully set up my 5.1 surround system in a workable manner, however i've had an issue with my sound quality ever since.

As soon as i set it up, i noticed that the sound from my speakers was a bit scratchy, but i was so happy that all the speakers actually worked that i just kinda resolved to live with it until i figured out how to fix it.  now here i am, 6 months and endless tinkering later, and it still sounds horridly scratchy and tinny.

I've looked around the net a lot for guides on trying to make the sound output from pulseaudio better quality, but i've never been able to turn up much info.  the main things i've tried changing have been the sample format and resample method.  so far, i'm using the following:
default-sample-format = float32be
resample-method = src-sinc-best-quality
and the qualioty is still poor at best.

When I turn off/mute the sub-woofer, and listen to the satellite speakers individually, it sounds very much like bass is being piped through them, which shouldn't be happening if the mixer was working properly, so it seems that theres something wrong here, and i have no idea what.

I know its not the speakers themselves, because I've hooked them up to my brother's computer, and they work fine there, and i dont suspect it's the sound card itself, because when i still had windows it worked fine on there, but still sounded scratchy/tinny on ubuntu.

is there a way i can refine the way that the software mixer does the routing to the sub by configuration?  anything else i can try to help improve sound quality?  thanks for any suggestions!

Andrew

---

