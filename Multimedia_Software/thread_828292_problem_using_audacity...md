---
title: "problem using audacity.."
date: 2008-06-13
forum: Multimedia Software
---

### Post by karan mangat on 2008-06-13
on importing and playing a music file, i'm getting this error:

Error while opening sound device. Please check the output device settings and the project sample rate.

---

### Post by xc3RnbFO8P on 2008-06-13
Did you install Audacity from Add/Remove?

---

### Post by xc3RnbFO8P on 2008-06-13
You can try the [beta source]("http://audacity.sourceforge.net/beta/audacity-src/audacity-src-1.3.5.tar.bz2")
When you ./configure it will ask for wx-config
search **[COLOR="SeaGreen"]wx[/COLOR]** in Synaptic Package Manager
I think I installel about 20 files before it stop complaining.
Install **.dev** also.

---

### Post by ajgreeny on 2008-06-13
It doesn't like having any other sound using app open at the same time, or at least if it does, it seems it must be opened first.  Also check in audacity's preferences the input and output sound systems that are set up.  By default I think OSS is used but ALSA is better

---

### Post by xc3RnbFO8P on 2008-06-13
If I use other than OSS it gets extremely slow and it doesnt work.
With this beta I can record (only through mic)
and save it as mp3, wav or ogg (using export)

---

### Post by karan mangat on 2008-06-13
i installed it using apt-get.
well, now its working alright.

thanks

---

### Post by ajgreeny on 2008-06-13
Just out of interest, what input sources have you got available in the mixer bar?  In Gutsy I had mic, line in, mix, and several others which I can't remember, but in Hardy I only have mic available.  Annoying but not disastrous.

---

