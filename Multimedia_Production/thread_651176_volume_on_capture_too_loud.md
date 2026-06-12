---
title: "volume on capture too loud"
date: 2007-12-27
forum: Multimedia Production
---

### Post by blutz on 2007-12-27
hey,

I am trying to record some music from a dat-recorder using ardour and actually everything is working fine, but the input-signal is too loud and I cannot reduce it any further with alsa mixer (it is already at the lowest point).
is there a way to reduce the volume with ardour or with alsa, it is not possible to do so at the recorder!?

i am using gutsy

best regards
blutz

---

### Post by Mblackwell on 2007-12-27
Look for a setting in the ALSA Mixer (you might have to enable it for it to be visible) called AC97 Capture. Make sure this is lowered a few notches from the top, and not maxed out.

---

### Post by theorganloft on 2007-12-28
> **blutz said:**
> hey,

I am trying to record some music from a dat-recorder using ardour and actually everything is working fine, but the input-signal is too loud and I cannot reduce it any further with alsa mixer (it is already at the lowest point).
is there a way to reduce the volume with ardour or with alsa, it is not possible to do so at the recorder!?

i am using gutsy

best regards
blutz

Where do you have it coming in?  If you are using your Mic port, you will have to adjust the mic input slider. For the Line, use the liner slider.

It is important to point out that we are talking about the ALSAMIXER from the terminal command line.

open a terminal and type alsamixer then press enter.  It is there that you can control your mix.  

If you have more than one sound interface in your machine, you may be adjusting the wrong one.  You can switch interfaces in the mixer.  :guitar:

---

### Post by blutz on 2007-12-28
hey,

i am using the line-in and i am working with the gui-version of alsa mixer. with this tool you can choose which input-signal you will use as capture ('switches'). first i tried it with line-in capture, so i could record in the background and listen to some other music at the same time. but after setting the volume-control under 'recording' to null the signal was still too loud for ardour.
i solved this problem by setting the capture to 'mix' and so i can regulate the incoming signal under the play-back tab.

thx for the help!!

---

### Post by theorganloft on 2007-12-28
Very good.  You did it right.  

I use an external mixer with a Compressor/Limiter.  This way I get a constant +6db signal to my Delta Revolution.  I monitor through the mixer.  I can also send signals, using Jack, through the surround sound ports.  I like jack.  It works just like a pro-studio with sends, returns, auxiliaries, etc.

If I hook up a guitar or external synthesizer this keeps my signal from damaging the audio input and keeps distortion at bay.  

Good Luck!:guitar:

---

