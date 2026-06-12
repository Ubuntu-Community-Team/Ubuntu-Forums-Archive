---
title: "No Sound with SB Live Value Card"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by jjr2527 on 2006-08-07
Hello:

I am having issues getting my SB Live Value sound card to produce any sound.  I am certain that the card physically works because it worked in Breezy and XP.  I have followed the comprehensive guide and tried the other suggestions I found related to this card.  The alsa number that I believe is most important to know is: 

emu10k1

Has anyone been able to get this to work?  What steps did you take to fix it?

---

### Post by Sutekh on 2006-08-08
Just some simple diagnosing that you can try using the Terminal (Applications -> Accessories menu)

Can we start by checking that the card is detected
```
lspci | grep audio
```
And then move on to check that appropriate modules are loaded for the card (emu10k1)
```
lsmod | grep snd
```
If you card is listed using the **lspci** command, and there are snd_emu10k1 modules present using the **lsmod** command, then you should try mucking around with all the channel volume settings in the alsamixer
```
alsamixer
```
Make sure that you are playing something for which you have support for.  By this I mean, don't try playing an mp3 without the mp3 decoders, etc.

Best bet is to try play a .wav file or .ogg in Rhythbox (if you are using Ubuntu) and see how it goes playing with the volume.

---

### Post by rjpeter2 on 2007-01-31
"If you card is listed using the lspci command, and there are snd_emu10k1 modules present using the lsmod command"

I have this same problem...my card is listed with the lspci command, but there is no snd_emu10k1 module listed with the lsmod command. how do i get the modules? I'm very green with linux so detailed explanations would help a lot. :)

---

### Post by duouk2000 on 2007-01-31
Do you have an onboard sound card? I have an SB Live! as well and had to manualy make it the default sound card in system/preferences/sound before it would work.

---

### Post by Rezn on 2007-02-01
Try turning off your on board sound card in the bio's. I had the same problem where I kept losing sound. Turning on board off seems to have worked so far.

---

