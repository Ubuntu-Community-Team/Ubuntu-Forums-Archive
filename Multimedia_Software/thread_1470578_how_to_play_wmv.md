---
title: "how to play wmv"
date: 2010-05-03
forum: Multimedia Software
---

### Post by Dhanjal on 2010-05-03
Hi how can i play wmv (container) files in ubuntu, i have unsuccessfully tried mplayer, totem and vlc.

VLC gives the following error

No suitable decoder module:
VLC does not support the audio or video format "wmas". Unfortunately there is no way for you to fix this.
No suitable decoder module:
VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this.

---

### Post by nitstorm on 2010-05-03
ubuntuforums.orgubuntuforums.org/newreply.php
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by mc4man on 2010-05-03
Just asked the other day (decoding of mss2
see here
[http://ubuntuforums.org/showthread.php?t=1468678](http://ubuntuforums.org/showthread.php?t=1468678)

wmas (voice) can be decoded by gstreamer 
vlc will need to be built off of a recent ffmpeg - repo and ppa vlc's aren't.
mplayer usually can

---

### Post by Dhanjal on 2010-05-03
Thanks for the link, i downloaded w32 codecs and those videos work in kmplayer and smplayer now

---

### Post by lenca.flenca on 2010-05-06
hey!

i've been searching and trying out all the possibilities i could find, but i still cannot play wmv files...

i've installed extras, i've installed w32codecs, i've installed everything i've been asked to install in the process... and still can't play the files, not in vlc or mplayer.

i'm starting to lose it, here.

some help, please?

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-30
> **lenca.flenca said:**
> hey!

i've been searching and trying out all the possibilities i could find, but i still cannot play wmv files...

i've installed extras, i've installed w32codecs, i've installed everything i've been asked to install in the process... and still can't play the files, not in vlc or mplayer.

i'm starting to lose it, here.

some help, please?

i installed ubuntu 11.04 32bit and i got the same problem after intalling extra and all codecs !!

---

### Post by andrew.46 on 2011-04-30
> **&#1581 said:**
> i installed ubuntu 11.04 32bit and i got the same problem after intalling extra and all codecs !!

Hmmm.... 32bit MPlayer should not have any troubles.... can you post the problem file somewhere?

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-30
> **andrew.46 said:**
> Hmmm.... 32bit MPlayer should not have any troubles.... can you post the problem file somewhere?

i tried this one 
[http://samples.multimedia.cx/V-codecs/MSS2/intro_windows.wmv](http://samples.multimedia.cx/V-codecs/MSS2/intro_windows.wmv)

[IMG]http://img851.imageshack.us/img851/9696/screenshotzwr.png[/IMG]

---

### Post by andrew.46 on 2011-04-30
Perhaps you could try SMPlayer and the w32codecs from Medibuntu? Looks like you might be using the Totem media player. This particular file plays on a 32bit system, I attach a screenshot demonstrating this.

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-04-30
> **andrew.46 said:**
> Perhaps you could try SMPlayer and the w32codecs from Medibuntu? Looks like you might be using the Totem media player. This particular file plays on a 32bit system, I attach a screenshot demonstrating this.

Thank you very much
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

that was very useful :) thanks

---

### Post by danieee on 2011-06-15
> **andrew.46 said:**
> Perhaps you could try SMPlayer and the w32codecs from Medibuntu? Looks like you might be using the Totem media player. This particular file plays on a 32bit system, I attach a screenshot demonstrating this.

This worked for me very well, Thanks a lot

---

### Post by andrew.46 on 2011-06-15
> **danieee said:**
> This worked for me very well, Thanks a lot

No problems :).

---

