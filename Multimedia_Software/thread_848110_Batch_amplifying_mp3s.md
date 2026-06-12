---
title: "Batch amplifying mp3s"
date: 2008-07-03
forum: Multimedia Software
---

### Post by kyozo on 2008-07-03
Hi,

I have a bunch of mp3 podcasts which I listen to on my phone using a bluetooth ear thingie.

The problem is that the sound level is too low when driving my car (yeah it's noisy as hell :)).

I need to amplify the mp3s, I have tried this in audacity, but I don't want to do it manually, and besides that, audacity uses diskspace like a lunatic (a 20mb mp3 file ends up using several gb of diskspace), so using audcitys macro stuff on multiple files will not do either.

Are there any tools to amplify an mp3 file that can be run from the shell (so I can script my way out of this in combination with wget and mp3splt).

Thanks

Kyozo

---

### Post by Stochastic on 2008-07-03
Take a look at mp3gain, it can be set to normalize to a specified volume.

---

### Post by Bungo Pony on 2008-07-03
> **Stochastic said:**
> Take a look at mp3gain, it can be set to normalize to a specified volume.

I use MP3Gain in WINE, and it does a fantastic job for batch 'normalizing' MP3s. And until now, I never knew there was a Linux version!

sudo apt-get install mp3gain

---

### Post by Giantics on 2008-07-06
> **Bungo Pony said:**
> I use MP3Gain in WINE, and it does a fantastic job for batch 'normalizing' MP3s. And until now, I never knew there was a Linux version!

sudo apt-get install mp3gain

Have a look at this:
[http://sourceforge.net/projects/easymp3gain/](http://sourceforge.net/projects/easymp3gain/)

---

