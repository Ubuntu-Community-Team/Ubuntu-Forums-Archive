---
title: "Skipping on VLC cancels video playback"
date: 2009-07-27
forum: Multimedia Software
---

### Post by themusicalduck on 2009-07-27
For some reason when I skip on the seeker on VLC my video playback will be interrupted and will close. VLC will stay running, but I will have to restart the video playing. Trying to skip it again usually causes it to crash. It doesn't always happen, but about half the time it does.

This is the output when it happens

```
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0xb7601580] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1


```

I included everything after skipping the video.

VLC version is 1.0 and I'm running Ubuntu 9.04.

---

### Post by themusicalduck on 2009-07-28
bump

---

### Post by igorzwx on 2009-07-28
I solved all my multi-media problems with this:

[http://shibuvarkala.blogspot.com/200...jackalope.html]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

But this solution is not universal:
OSS4 does not support some modern hardware.

---

### Post by themusicalduck on 2009-07-29
Thanks for the links. Installing all of the codecs from medibuntu seems to have fixed it!

---

### Post by igorzwx on 2009-07-29
NOTE: It seems that if a person install css codec from the wrong place, he
may get something wrong to the hidden folder  ~/.dvdcss
In this case, it might be enough to clean that hidden folder.
Such things are not likely to happen when you use Medibuntu repositories.

---

### Post by MichealH on 2009-07-29
> **themusicalduck said:**
> For some reason when I skip on the seeker on VLC my video playback will be interrupted and will close. VLC will stay running, but I will have to restart the video playing. Trying to skip it again usually causes it to crash. It doesn't always happen, but about half the time it does.

This is the output when it happens

```
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0xb7601580] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1


```I included everything after skipping the video.

VLC version is 1.0 and I'm running Ubuntu 9.04.

Is there VLC for linux?

---

### Post by themusicalduck on 2009-07-29
Yeah, it's under add/remove programs or installable by typing ```
sudo apt-get install vlc
``` into a terminal.

---

