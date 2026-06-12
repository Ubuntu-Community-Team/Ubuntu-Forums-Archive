---
title: "Hearing Sound Twice with old Capture Card"
date: 2009-11-07
forum: Mythbuntu
---

### Post by wincen on 2009-11-07
I'm using Mythbuntu 9.04 and I nearly have it all setup.  The problem is tha when I Watch TV i hear the sound twice, once from the line in and then again delayed from Mythtv actually saving the sound.

I use an old card that requires a jumper form the capture card to the soundcard.  I followed this link [http://www.mythtv.org/docs/mythtv-HOWTO-7.html]("http://www.mythtv.org/docs/mythtv-HOWTO-7.html") to get sound working (originally there was no sound at all) but now the sound is played twice!

Here's what the link tells you to do to get sound working:
```
$ amixer set Master,0 100%,100% unmute
$ amixer set PCM,0 100%,100% unmute
$ amixer set Line,0 75%,75% mute captur
$ amixer set Capture,0 100%,100% captur
$ su
# alsactl store
# exit
```

If I just use a client to connect to my backend watching tv does not play the sound twice.

---

