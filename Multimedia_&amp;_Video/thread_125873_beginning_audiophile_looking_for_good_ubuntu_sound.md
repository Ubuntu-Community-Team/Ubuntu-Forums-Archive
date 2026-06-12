---
title: "beginning audiophile looking for good ubuntu sound card"
date: 2006-02-05
forum: Multimedia &amp; Video
---

### Post by GTroy on 2006-02-05
title says it most!!
anything that I can get at a good price, and isn't too crazy/hard to get working.

I'm wondering what others are using with good audio success.

---

### Post by darkpark on 2006-02-05
Soundcards based on the VIA Envy24 chip are pretty good and they work with ubuntu (any linux distro that has alsa drivers version 1.0 or newer )  
Good examples would be the M-Audio Revolution 7.1 or 5.1  and the Chaintech AV-710.

---

### Post by hw-tph on 2006-02-05
ICE1712-based cards are nice too, like the STAudio/Hoontech DSP24 and the M-Audio Maya series.


Håkan

---

### Post by GTroy on 2006-02-05
thanks Darkpark:  I bought the chaintech AV-710 for $24.  I coudn't believe the price compared to m-audios.  now I've gotta look for threads on getting it to work right.

---

### Post by dolson on 2006-02-16
Hey, that is a great price! What is the difference between this card and a Creative card? I currently have a SoundBlaster Live! 5.1 and an Audigy2 ZS. My main concern is making music... If this card is better in some way, I'd snag one or two.

---

### Post by pioni on 2006-02-17
I have M-Audio Delta Audiophile 2496 (with ICE1712 chip) and it doesn't work properly with Ubuntu 5.10. At least Gnome sounds are played in mono from left speaker and at wrong speed, maybe half or 1/4 of what it should be. I've managed to solve the playback speed problem by toying around with Envy24control and alsa-mixer, but at least the system sounds are still played in mono from the left speaker only. Volume controls also do not work.

I'm not sure if it's the card's fault or Ubuntu's fault, as this card has been recommended for Linux use and even Ubuntu seems to have drivers for it. Shame that it simply doesn't work. I've done several fresh installs and tried this and that, but the same problems still exist. :confused: 

Anyway, this is a problem that is probably easily fixed if I only knew HOW. M-Audio Audiophile 2496 is not that exotic or new device and using it in Linux should NOT be this hard! :evil:

---

### Post by GTroy on 2006-02-17
buy the chaintech av-710.  I first found out about them at head-fi.org (headphone audiophiles) & they LOVE the chaintech.  I had mine working without any configuration.  totally plug, and play.  the only thing is I've heard is the midi might cause some issues.   for the price you can't beat it.

---

### Post by jadugarr on 2006-02-19
[QUOTE=GTroy]buy the chaintech av-710.  I first found out about them at head-fi.org (headphone audiophiles) & they LOVE the chaintech.  I had mine working without any configuration.  totally plug, and play.  the only thing is I've heard is the midi might cause some issues.   for the price you can't beat it.[/QUOTE]

I'm looking at perhaps replacing my audigy with something more suited for audiophile quality, but was concerned about what would easily work w/ ubuntu.  I have been looking back and forth between these forums and head-fi.org (member there as well), and just picked up some alessandro ms-1s ... so now I have to make sure I'm getting the best sound possible out of them :D

---

### Post by pioni on 2006-02-19
I just installed Fedora Core 4 and after installing all updates the M-Audio Delta Audiophile 2496 finally works perfectly in Linux! Now I just have to find out what is going wrong in Ubuntu, so that we all can enjoy this card in Ubuntu as well.

---

### Post by Teroedni on 2006-02-19
Here is a list of Alsa preffered soundcards

[http://alsa.opensrc.org/Alsa+Preferred+Soundcards](http://alsa.opensrc.org/Alsa+Preferred+Soundcards)

---

### Post by Kuprin on 2006-02-19
I personally like my Soundblaster Live - it's an old card, and is very slow in ALSA, but OSS sounds BEAUTIFULLY with it and I can even get a MIDI synth reasonably well. I need to figure out some better MIDI integration, but I think I'll wait for Dapper before I do any more serious tinkering.

---

### Post by pioni on 2006-02-19
If the original poster wasn't a "beginning audiophile" and looking for "good sound", I'd give my vote to SB Live too. It's supported that well mainly because it's very old card.

SB Live is always locked at 48kHz, so 44.1kHz mp3's and CD's get resampled. Not that it's a huge problem, since the card is very noisy and sounds muffled as well. SB Live has its uses, but I don't think that words audiophile and SB Live fit into same sentence.

---

