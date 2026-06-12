---
title: "Microphone + Acer + Pulse = White Noise"
date: 2009-07-06
forum: Multimedia Software
---

### Post by Soapy.Illusions on 2009-07-06
Hi everyone,
 
When I first installed ubuntu two months ago, sound was a big issue on my Acer Aspire 6920 laptop, everything was fixed with Pulse Audio and a lot of tweaking, but my microphone is still unusable. 
 
When I try to record something, it says it's picking up sound from my mic (even if there is no sound in the room) and no matter what sound level I make it remains at about the same level according to the recorder
 
When I play it back, all I hear is white noise...
 
It's an HDA audio card, and I have tried messing with every single volume control and have tried ALSA and Pulse... 
 
Does anyone have any light they can shed on this problem?

---

### Post by dlmarti on 2009-07-06
Honestly, this could be electrical in nature.  Does it still occur under a different OS?

I've also seen this if you have extra gain turned on, did you check all the available switches in the mixer (even the hidden ones).

---

### Post by Soapy.Illusions on 2009-07-06
It works perfectly in my Vista partition but I hate going back to Windows to use my mic
 
And I have tried moving the boosts up and down with no change

---

### Post by Xlost on 2009-07-06
I have that issue to, but just described it a little different in this thread.

[http://ubuntuforums.org/showthread.php?t=1205740](http://ubuntuforums.org/showthread.php?t=1205740)

---

### Post by Soapy.Illusions on 2009-07-06
Well the difference with my problem is I have never gotten any sort of sound to be recorded, it's not white noise on top of my recording it is just simply white noise. No matter if I am silent, or yell at the mic, pulse audio and the voice recorded show a constant recording volume.

---

### Post by JonUK on 2009-12-02
I have exactly the same problem on Ubuntu 9.10, ASUS motherboard P7P55D with VIA® VT1828S chipset.

Did you find a solution?

---

### Post by BubbaBlues on 2009-12-24
Same here. I have never gotten a single sound to record in any linux distro I've tried (except for white noise)  I've tried Audacity, gnome recorder, sound recorder, Nothing works.  In fact, the inconsistent cobbled up mess that Linux uses for audio is the only drawback I've found with Ubuntu.  BTW, I'm using Realtek HD onboard sound.

---

### Post by BubbaBlues on 2010-01-16
I have to eat a little crow here.  I went to Staples and bought a 30 dollar Diamond sound card and now everything is working. I guess it was just the onboard sound that wasn't working. Still, Linux is lacking in audio, when you have to use a jumper wire from headphones out to line in on your sound card just to record streaming audio. But at least it's something. :cool:

---

### Post by Gannin on 2012-01-07
You don't need to do that to record streaming audio.  And that's not a limitation of Linux, that's a limitation of the hardware.

For instance, I had an old SoundBlaster card that had a built-in hardware mixer onboard.  This meant the soundcard could natively record a stream of any audio passing through it.  Most soundcards no longer include this feature because of the expense.  Just how many dial-up modems went from hardware controlled to software controlled, to save on the expense.

However, such monitoring is still possible through software.  You just have to jump through more hoops to do it than when the soundcard has the feature built-in into its hardware.

Pulse does provide a feature to monitor the audio stream of a device.  It's set through the Pulse settings.

---

