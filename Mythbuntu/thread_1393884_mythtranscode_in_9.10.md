---
title: "mythtranscode in 9.10"
date: 2010-01-29
forum: Mythbuntu
---

### Post by 4dognight on 2010-01-29
I have some recordings I wanted to save off and make a bit smaller in size. They are approx 5-6 gb each(mpeg2 HD recordings). I tried to use the transcode in the mythweb page. It changed the file from 5.2 gb to 11.4 gb in size! I thought the transcode feature was to shrink the file in size?
Only thing I changed was the setting in autodetect from rtjpeg to mpeg4.

I cant find any good info on transcoding in mythtv. Anyone got a decent howto on it?

---

### Post by hemimaniac on 2010-01-29
personally i use handbrake or acid rip, to make them smaller just pick an avi container and set the destination size, basically recode them to xvid if it is an option, or you can transcode it to a smaller final size

---

### Post by movieman on 2010-01-30
Sadly, MythTV seems to treat the specified bit-rate as a vague hint rather than a hard limit; if I record MPEG-2 off a station with some interference and then tell MythTV to transcode to H.264 at half the bit rate it's quite likely to double the size of the file instead.

---

### Post by CaveMole on 2011-06-25
> **4dognight said:**
> I have some recordings I wanted to save off and make a bit smaller in size. They are approx 5-6 gb each(mpeg2 HD recordings). I tried to use the transcode in the mythweb page. It changed the file from 5.2 gb to 11.4 gb in size! I thought the transcode feature was to shrink the file in size?
Only thing I changed was the setting in autodetect from rtjpeg to mpeg4.

I cant find any good info on transcoding in mythtv. Anyone got a decent howto on it?

I have similar concerns.
Seems odd that this is not a common issue.

For me, I want some shows compressed for easier streaming over the network to low-powered machines like netbooks.

---

