---
title: "Sound"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by Cattie on 2007-05-21
OK, I have no sound.  But only in Ubuntu.  In Vista, I have sound.  It just sucks.  I'm running a Toshiba Satellite A105-s2236 with a 1.6 gHz Celeron M processor, and the only name for a sound card I've found is "Sound Volume Control Dial".  In grepAud it says it's "Audio device: ATI Technologies Inc SB450 HDA Audio (rev01)".  Any help would be so appreciated.

---

### Post by renzokuken on 2007-05-21
firstly, try running

```
alsamixer
``` in the terminal and check all the volumes are correct (i.e. not muted or anything)

then it may be worth compiling the latest alsa-driver since it has much better support for a wider range of soundcards than the default version installed. thats how i solved my sound issues.

i think alsa-driver 0.1.0.12 is the default version in ubuntu and the latest version i used to get sound working was 0.1.0.14rc4

---

### Post by Cattie on 2007-05-21
OK, if I open Alsamixer in the terminal, the left MM box is "Caller 1".  The Right is "Off Hook".

Any ideas?

I know that at one point, there was something that needed to be enabled, but I can't find it now, and I'm not too good at remembering what it is.

---

### Post by renzokuken on 2007-05-22
when alsamixer is opened, use the Tab key to move between "playback", "capture" and "all". make sure everything is unmuted (use left and right to select and press "M" to unmute. if you see "MM" below it means that channel is muted.

failing that it may be worth trying a newer version of alsa

---

