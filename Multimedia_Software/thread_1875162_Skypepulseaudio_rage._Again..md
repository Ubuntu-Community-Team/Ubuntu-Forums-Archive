---
title: "Skype/pulseaudio rage. Again."
date: 2011-11-04
forum: Multimedia Software
---

### Post by K1251 on 2011-11-04
So, once again this stupid little Acer netbook is giving me hell. After getting sick to death of KDE, I replaced it with Xubuntu 11.10, which was great so far, until I tried to get Skype to work. Now, I had problems getting skype to hear the microphone in Kubuntu 11.04, but I solved it by removing pulseaudio.

That actually worked in Xubuntu too, but now I have no volume indicator on the panel. I tried installing indicator-sound, but that just sets up pulseaudio all over again. Also, even with pulseaudio installed I can now no longer get the indicator back: "Indicator Plugin" just gives me mail and network, and Mixer just puts a button there which opens alsamixer.

So basically, is there a way I can get the indicator back without installing pulseaudio? Or can I install it but just disable it? Or if I have to have pulseaudio, how the hell do I a) get the indicator back and b) get the mic to work in skype??

- K

---

### Post by LewisTM on 2011-11-04
You should install indicator-sound-gtk2 to enable the indicator for XFCE.
I had the same kind of problem wrt Pulse vs ALSA on an old eeePC and was considering getting a more recent Acer netbook for Skype, so I really hope you can solve that.

Did you try the old trick of muting the mic's left channel in the Pulseaudio mixer?

---

### Post by K1251 on 2011-11-04
> **LewisTM said:**
> You should install indicator-sound-gtk2 to enable the indicator for XFCE.
I had the same kind of problem wrt Pulse vs ALSA on an old eeePC and was considering getting a more recent Acer netbook for Skype, so I really hope you can solve that.

Did you try the old trick of muting the mic's left channel in the Pulseaudio mixer?

Ah thanks, didn't realise it was indicator-sound-gtk2 and not indicator-sound; XFCE is new to me. And muting the left channel worked, which is odd because I thought I tried that earlier, must've muted the wrong thing though I guess.

Everything works now though: solved! Thanks.

---

