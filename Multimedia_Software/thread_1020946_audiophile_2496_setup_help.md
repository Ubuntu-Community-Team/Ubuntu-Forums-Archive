---
title: "audiophile 2496 setup help"
date: 2008-12-24
forum: Multimedia Software
---

### Post by regote on 2008-12-24
Hello,

I just upgraded to 8.10, with a GNOME 2.24.1 desktop. Trying to make my M Audio Audiophile 2496 sound card work, I installed OSS, following the steps indicated in [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound). Now the mixer ossxmix sees that sound card, as well as an ICH AC97 Mixer (ALC850).

Afterwards, in System -> Preferences -> Sound I chose

"M Audio Audiophile 2496 (OSS v4 Audio Mixer)" for the Default Mixer Tracks,

and "OSS4 - M Audio AudioPhile 2496 out 1/2" for Sound Events, Music and Movies, and Audio Conferencing Sound playback.

When testing these 3 sounds, indeed they come out of the audiophile. However, although the "out 1/2" panel of the ossxmix gets illuminated, the volume doesn't change no matter if I raise or lower the "out 1/2" control.

The rest of sounds (vlc, for instance) come out of the standard sound card. In the ossxmix, AC97 mixer section, there is an illuminated panel when vlc plays, and raising and lowering the control does change the volume, as expected.

Now, how can I manage to make all the sounds come out of the audiophile? Although it is probably a very dumb question, I hope you can help me.

Many thanks in advance.

---

### Post by Matthiacon on 2008-12-30
It's not a dumb question.  I also love my M-audio 2496 and am having trouble getting it to work properly under Ubuntu 8.10 (amd64).  Until I can figure it out, I've removed it from my main machine and have decided to use the onboard audio.  :(

---

### Post by Greg314 on 2009-01-06
Personally, I turned off the chipset on the mainboard and then it switched on the M2496, it works perfectly. It's a bit dirty but it works.

If you need the chipset, I guess that you can check in the configuration what the settings are with the chipset turned off and try to put the same after turning on the chipset again.

---

### Post by markbuntu on 2009-01-06
This is not for OSS but it is a solution for getting the ICE1712 chipset working with  pulseaudio

[http://ubuntuforums.org/showpost.php?p=6449370&postcount=989](http://ubuntuforums.org/showpost.php?p=6449370&postcount=989)

---

