---
title: "Sound problems again"
date: 2008-04-26
forum: Multimedia Software
---

### Post by shoeshrimp on 2008-04-26
Hey Guys, I've just upgraded from Ubuntu 7.10 to 8.04 in the hope that they might have fixed the problems with the AC97 soundcards, but to no avail - they haven't. My problem is as follows, and I'd really appreciate it if anyone has any ideas as to what I can do.

1) The only time I get any sound is the bongos sound as the log-in screen appears. After I've put my password in, I get no sound at all.
2) When playing mp3 tracks (I have the codecs installed) using any program, the track never proceeds past 0:00 secs and will not play. Occasionally the program crashes
3) The output of aplay -l is:
```
tom@tom-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
4) I have blacklisted the atiixp modem drivers, as I wondered if that might be why I have sound before it's logged in (perhaps the modem isn't loaded until that point), but it doesn't seem to have done anything.

Thanks in advance,

Tom

---

