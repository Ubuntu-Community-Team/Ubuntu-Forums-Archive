---
title: "MP3 lags at beginning of playback (JLayer API)"
date: 2010-02-25
forum: Multimedia Software
---

### Post by Tronman on 2010-02-25
Hi everybody,

I've been trying to use the code sample here:

[http://www.cs.princeton.edu/introcs/faq/mp3/mp3.html](http://www.cs.princeton.edu/introcs/faq/mp3/mp3.html)

To get a basic (lightweight) MP3 player up and running using the JLayer API from Javazoom.

I noticed that when the MP3 file first starts to play, there's a bit of a "lag" where the song plays almost in slow motion for a second or two until it plays properly. Note that my OS is Ubuntu 9.10 64 bit, the MP3 itself is fine (e.g. plays in VLC with no lag), the lag length seems to be a bit different depending on the song. It doesn't seem to happen at all with the same code in Windows (Vista HP 64). I tried turning up the thread priority, but no luck.

Does anyone have any suggestions on how to fix this?

I've also noticed that on occasion the song won't play at all, the sample code simply spits out it's result and quits. It seems to happen if I just had another player open, and I have to wait a moment or two to work, maybe a blocked resource or something?

I've tried posting on the JLayer forums, but they appear to be broken. Hopefully my question is appropriate here as it might be an Ubuntu issue (not Java or JLayer itself).

Thanks!

---

### Post by jazarine on 2011-05-14
bump!
I am facing a similar problem with a product that uses jlayer. However, during the lag, there is no sound coming at all.
The mp3 is started after around 3-4 seconds. No problem with windows.
Is it related with Ubuntu?

---

