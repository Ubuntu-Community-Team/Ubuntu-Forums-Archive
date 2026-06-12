---
title: "playing two audio files simultaneously with Mplayer"
date: 2008-11-12
forum: Multimedia Software
---

### Post by v_suresh74 on 2008-11-12
Hi,
     I want to know if it is possible to play two audio files simultaneously  with mplayer such that one is directed exclusively to the 'left channel' and the other one exclusively to the 'right channel' and if so the command line options to do so.

regards
suresh

---

### Post by aeiah on 2008-11-12
anything's possible with mplayer ;)

check the manual. it looks like something like this will work, although perhaps it plays the left channel through both speakers. i cant test right now:

```
mplayer -stereo 1 file.ext
```
or
```
mplayer -stereo 2 file.ext
```
for right channel.


what is it you're trying to achieve though? do they need to be synchronised? does this need to be automated? is this a video file or audio only? something like audacity might be better depending on what you really want. you could load both tracks in there, make them both mono, and then set one for left channel and one for right.

---

### Post by v_suresh74 on 2008-11-12
> **aeiah said:**
> anything's possible with mplayer ;)

check the manual. it looks like something like this will work, although perhaps it plays the left channel through both speakers. i cant test right now:

```
mplayer -stereo 1 file.ext
```
or
```
mplayer -stereo 2 file.ext
```
for right channel.


what is it you're trying to achieve though? do they need to be synchronised? does this need to be automated? is this a video file or audio only? something like audacity might be better depending on what you really want. you could load both tracks in there, make them both mono, and then set one for left channel and one for right.


thanks. i need to do this for audio files and yes synchronized. i have gone through the man page quite a few times. no avail.
the reason to tease this capability out of mplayer is to do a 'dichotic listening experiment' where in a subject is made to listen two different audio streams simultaneously -- one from the left ear and one from the right ear. based on the subject's ability to answer questions based on the audio stream contents one could infer about the mechanism of attention in subjects. we are planning one such experiement and thought would avoid the unwieldy setup of taking audio output from two different pc's. if nothing else work will need to fall back on this.

regards
suresh

---

