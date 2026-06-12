---
title: "Poor audio support - the death of Ubuntu"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by bep on 2006-10-27
Sorry for the dramatic title, I just had to do so to draw some attention.

I love Linux, I love Ubuntu - a 3 month convert as such.

But I'm almost on the verge of going back to Windows. Almost. 

You can do the search yourself: "distorted audio".

You can do a lot of fancy GUI-magic, like fancy themes with rounded corners, but they do not mean a lot if the foundation is crappy.

And this is the fact:

I (and many others) can boot into Windows XP, and it SOUNDS great. In Ubuntu, it sounds distorted and crappy.

Yes, there may be some hidden tweaks (I have looked, I have looked), but this should just work. Some basic resampling from 48 Khz should not be magic.

I have done Ubuntu for 3 months now. I would really like to continue, but the audio is just the bit that is going to make the final argument.

---

### Post by charles_elwood on 2006-10-27
Ah, I get this regularly on Intel sound cards, try turning the PCM volume down untill the distortion stops. About 90% ussually works for me. It's one of those times where ALSA is happy to let you shoot yourself in the foot. Windows assumes you are a fool and won't let you have too much gain there as the natural instinct is to turn things all the way up.

---

### Post by bep on 2006-10-28
The reduction of PCM volume does not help with the resampling/distorted sound problem. As I said, I've tried a lot of things.

---

### Post by rustybronco on 2007-10-04
Have you tried another distro perhaps? 
sometimes if hardware does not work with one distro, I try others first.
perhaps I could mail you a bunch to try?

---

### Post by tgalati4 on 2007-10-05
Last resort:

>sudo apt-get install powertweak
>gpowertweak

Play around with latency settings between the video card, sound card, and any other devices that have a "0" for latency.  0 means that the device can instantly demand the PCI bus can that can interfere with decoding sound streams.

Sometimes the default PCI latency settings won't work well with certain hardware.  It's worth the time to try it and it's simpler than reinstalling Windows.

---

### Post by jfdill_2 on 2007-10-05
Hmm this rings a bell I had a similar problem with ALSA some time ago.  I think it had to do with the size of the sound buffer and priority, especially since it was on a slower Sempron system on a cheapo Biostar mobo.  I'm playing around with Kubuntu Gutsy at the moment, in there the setting is in System Settings -> Sound System -> Skip Prevention check the box for "Run with the highest possible priority (realtime priority)" and move the slider for "Sound buffer" to the right.

Other things to check is that you are using the best driver for your sound card, the default one may not work the best with your hardware, or there may be a "proprietary" driver that works better, have seen that with cheapo AC97 / Intel / SiS chipsets on the motherboard.

If I can find the specifics of the problem and what I did to fix it, I'll post more details.

---

### Post by daviemcc on 2008-01-21
Bep, I'm in complete agreement, Linux would be absolute awesome if there was only some decent audio sounds coming from my speaker. It's not that it's unlistenable to, it's just really annoying, Windows is perfect! IT'S SO FRUSTRATING!

---

