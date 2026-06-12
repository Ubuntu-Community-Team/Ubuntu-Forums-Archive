---
title: "[SOLVED] Can't record new shows"
date: 2007-10-17
forum: Mythbuntu
---

### Post by packet on 2007-10-17
I just moved from my old mythdora backend to a the new mythbuntu and everything looks good but it doesn't actually record new shows!  I get this log in my mythbackend.log:

2007-10-17 12:38:53.678 TVRec(2): Changing from None to RecordingOnly
2007-10-17 12:38:53.686 TVRec(2): HW Tuner: 2->2
2007-10-17 12:38:53.863 Unknown video codec
2007-10-17 12:38:53.864 Please go into the TV Settings, Recording Profiles and
2007-10-17 12:38:53.864 setup the four 'Software Encoders' profiles.
2007-10-17 12:38:53.865 Assuming RTjpeg for now.
2007-10-17 12:38:53.865 NVR: Error, unknown audio codec
2007-10-17 12:38:53.895 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2007-10-17 12:38:53.898 Started recording: Yes, Dear "Jimmy Has Changed": channel 1007 on cardid 2, sourceid 1

And it looks like it is recording but it isn't, I've got a PVR250 so it should be using the hardware encoder, I've never actually had to go futz with the encoding settings as it has always just worked.

Any ideas?

---

### Post by superm1 on 2007-10-17
Sounds to me like you chose the wrong type of tuner in mythtv-setup.  Make sure you chose MPEG2 Encoders (PVR-xxx)

---

### Post by packet on 2007-10-17
Ok, sorry, figured it out.  Somehow I selected the wrong card in the mythtvsetup, it was listed as V4L instead of MPEG-2.  Not sure how I could have missed that, other than the fact that I was doing it at 2am.

Looks like a successful conversion from mythdora to mythbuntu!

---

