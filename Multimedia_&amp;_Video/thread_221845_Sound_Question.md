---
title: "Sound Question"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by Sidhy on 2006-07-24
I was wondering what is the best sound driver for linux. And is it possible to have sound without such high delays ? I know it is with a better sound card, but why dont I have such delay with Windows and yet with linux its awfull. I want to go to linux instead of Windows but if I have such a high delay with sound I just can't do all the things in linux the way I want to. 

I try to play CounterStrike .. but the sound keeps way behind with jack2oss, artsdsp, and all the other ways I try (also set snd_mixahead to lower the delay but without any suc6)

---

### Post by Sidhy on 2006-07-25
.. Looks like this forum is dead. asked 2 questions already one about esdlib0 and this one but no one even send me a reply or what so ever bad support for ubuntu if you ask me :(

---

### Post by Lord Illidan on 2006-07-25
[LEFT]Alsa should be the best sound driver in Linux.

What is your soundcard, and do XMMS and Amarok play music correctly from it?

Also, it could be unrelated to sound, do you have DMA enabled? Do a ```
sudo hdparm /dev/hd*
``` and post the output here.

Also, does Counter Strike play under Wine? If so, then that might be a reason for the sound delays.
[/LEFT]

---

### Post by Sidhy on 2006-07-25
Well I am using ALSA and I got just a simple on board sound card. And yes CS is playing under Wine what else should I use? .. I tried cvscedega but it wont even run counterstrike right. 

and I cant do the command right now not at home sry ..

---

