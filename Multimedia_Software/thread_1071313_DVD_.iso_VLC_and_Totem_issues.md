---
title: "DVD .iso VLC and Totem issues"
date: 2009-02-16
forum: Multimedia Software
---

### Post by xigen on 2009-02-16
We rented Purple Rain from the local video store and tried to play it on our Ubuntu box.

VLC would not play the .iso file.
I copied the file to the hard drive to see if that would help - no luck.

Totem played the file -- however, only the concert portion of the audio would play... all dialogue was absent.  It was the strangest thing to only have one portion of the audio track.  I tried to find an option under audio settings to get the dialogue back -- no luck.

VLC (round 2)
I reinstalled VLC, ubuntu restricted codecs and libdcss 2 and 3.   VLC did not recognize or play the disk or saved .iso.

Also, navigation of the dvd is irritating.  It would not let me fast forward, skip intros, or move to a new scene.

... 

I just tried playing the 'bonus disc'/DVD -- it works just fine.  UGH!

...

any suggestions regarding what I could try next?

AMD64, M-Audio Delta 66, Ubuntu 8.10

Cheers,
MW

---

### Post by sanderj on 2009-02-16
Huh? You see an .iso when you put in the video-DVD?! Strange; I would expect VIDEO_TS and AUDIO_TS.
And VLC playing an .iso? Does that work at all? Will try that myself on an unecrypted DVD-iso.

Anyway, have you followed this: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

EDIT: I checked, and VLC can indeed play an .iso with a video-dvd inside. Cool. Thanks.

---

### Post by xigen on 2009-02-19
I used handbrake to rip the dvd to .mp4 and everything works.

MW

---

