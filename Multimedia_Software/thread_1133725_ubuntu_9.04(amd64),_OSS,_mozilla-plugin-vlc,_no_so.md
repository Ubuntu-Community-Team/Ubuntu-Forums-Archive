---
title: "ubuntu 9.04(amd64), OSS, mozilla-plugin-vlc, no sound"
date: 2009-04-23
forum: Multimedia Software
---

### Post by monkman on 2009-04-23
hello, i just updated from 8.10 to 9.04. sound works fine when using rhythmbox or playing files with the vlc player. but when i open a website with mulitmedia like 

[http://www.zdf.de/ZDFmediathek/100sec]("http://www.zdf.de/ZDFmediathek/100sec") 

and i choose vlc and dsl2000 and klick on "übernehmen", there is no sound. in 8.10 it worked fine. what can this be? thx!

---

### Post by monkman on 2009-04-23
on my notebook which is 32bit, everything is fine...

---

### Post by monkman on 2009-04-23
after switching to 32bit on my desktop, where i have to use oss, still the same. so i don't think, this depends on 32/64bit...

---

### Post by redenex on 2009-04-23
Any of [these discussions ]("http://ubuntuforums.org/search.php?searchid=58363192")might help you?!

---

### Post by monkman on 2009-04-23
switched from oss back to alsa. this works. but now i have to find a way to avoid resampling, which was very easy with oss...

---

### Post by psyke83 on 2009-04-23
Please check the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

---

### Post by monkman on 2009-04-23
thanks, but i continue using oss from now on... serves my purpose best.

---

### Post by psyke83 on 2009-04-23
> **monkman said:**
> thanks, but i continue using oss from now on... serves my purpose best.

Ok, but you realize that OSS* doesn't support software mixing, right? You won't be able to play sound in two applications simultaneously.

*Note that when you select OSS output, it's actually OSS output emulated by the ALSA kernel modules. To get "true" OSS output, you need to install OSSv4, which isn't supported officially in Ubuntu.

---

### Post by monkman on 2009-04-23
actually it does support simultaneously sound. but only with resampling to 48khz, like alsa, which i don't want. the mixer has a switch which can turn it off and on again. for hifi-tasks it's much better. i have audio in 44,1, 48 and 96khz and i don't want it resampled. oss puts it through without changing it. by the way: i got the maudio revolution 5.1. shure you have to close the application if you want sound from another in this situation, but i can live with it. at least better than with bad quality sound ;)

---

### Post by semano on 2009-11-04
Dear All,
I am having trouble with playing music with VLC player. I cant hear any sound while watching movies with VLC player.

But, I can listen music and watch movie with Rhythmbox media player and Movie Player.

I would really appreciate any kind of help to sort out this problem.

regards,
semano

---

### Post by corjuela on 2010-01-31
> **semano said:**
> Dear All,
I am having trouble with playing music with VLC player. I cant hear any sound while watching movies with VLC player.

But, I can listen music and watch movie with Rhythmbox media player and Movie Player.

I would really appreciate any kind of help to sort out this problem.

regards,
semano

It happened to me too, i need to configure the alsa device properly to make it work...go to the advance settings and on the audio options go to audio output modules, you can find it. Hope it works for you ;)

---

