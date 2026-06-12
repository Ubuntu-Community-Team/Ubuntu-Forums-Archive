---
title: "Video fixed now audio broken"
date: 2009-09-23
forum: Mythbuntu
---

### Post by trevs.bronco on 2009-09-23
I managed to get my video issue in a[ previous post]("http://ubuntuforums.org/showthread.php?t=1271865") fixed. now my audio that was fully functional before is not working during video playback through my myth frontend. Live TV works, recorded TV works, music player works, I have audio when playing streams in firefox and I have audio in Mplayer outside of myth.When I look at the frontend log there is nothing that is obvious to me, but I am sure it is something simple. Could someone please look at this log entry and tell me if I am missing something. 

```
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 1280 x 544 (preferred colorspace: H.264 VDPAU acceleration)
VDec: using H.264 VDPAU acceleration as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x544 => 1280x544 H.264 VDPAU acceleration  [fs] [zoom]
[Mixer] No hardware mixing, inserting volume filter.
```Thanks,

Trev

---

### Post by trevs.bronco on 2009-09-23
Does any one know why is has [OSS] listed in AO? my settings are all set to ALSA. could this be my problem and if so how would I get that to ALSA?

Trev

---

### Post by trevs.bronco on 2009-09-25
Is there anyone who can help? I have been working on this for three months and my wife is getting very disappointed that she can't just lay in bed and watch a movie at night. Anyone? Please.

Trev

---

### Post by trevs.bronco on 2009-09-28
Well after reading way too many how to's and old posts and trying way too many things that didn't work I finally figured out myself the simple solution I was looking for. The answer was to ad -ao alsa to the list of commands in the default video player in mediautilities/setup>setup>settings>video settings>player settings.

Trev

---

