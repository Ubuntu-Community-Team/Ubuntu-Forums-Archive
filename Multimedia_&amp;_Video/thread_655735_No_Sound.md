---
title: "No Sound"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by jsop on 2008-01-01
I just finished installing Ubuntu for the first time.
I cannot hear any sound when I try to play music saved on my HDD or streamed online content. I Have already installed the extras package to enable playback of mp3's.

As I am not quite familiar with Ubuntu, I'll need some instructions to find and post the information needed to resolve my problem.
Thanks!

---

### Post by taurus on 2008-01-01
Do you have an onboard soundcard or do you have to install a PCI soundcard?  Not a whole lot of info to go on here.

---

### Post by jsop on 2008-01-01
I have a PCI soundcard. I think the name might be snd-cmipci, however I am not sure how to install drivers in linux.

---

### Post by taurus on 2008-01-01
Is there an onboard soundcard too or it doesn't come with one?

```
lspci
```

---

### Post by jsop on 2008-01-01
There is an on-board soundcard, I have never used it as it does not support my 5.1 speakers.

---

### Post by taurus on 2008-01-01
Then, you must go into your BIOS to turn it off.  

You can do a quick test right now.  Unplug the speakers from the PCI soundcard and plug it into your onboard soundcard.  Do you hear sound coming out of your speakers when you play an mp3?

---

### Post by Casual Fan on 2008-01-01
Once you get the on-board sound card turned off, if you still don't have sound, follow the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[SIZE="1"]*This is about the only useful thing I do around here...point people to this thread. :)*[/SIZE]

---

