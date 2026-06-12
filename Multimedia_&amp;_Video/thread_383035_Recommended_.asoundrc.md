---
title: "Recommended .asoundrc?"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by Megatog615 on 2007-03-12
Hi. I am having minor problems with my Ensoniq 5880 AudioPCI sound card. I believe it may be due to my .asoundrc file. If I try to play certain sound files through mplayer(in Firefox), I will get nothing but static. It seems to happen only with mp3 files, but I might be wrong.

Right now, this is my .asoundrc:
```
pcm.card0 {
        type hw
        card 0
        mmap_emulation true
}

pcm.!playback {
        type dmix       # dmix plugin for mixing the output
        ipc_key 1234    # a unique number
        slave {
                pcm "card0"
                period_time 0
                period_size 1024
                buffer_size 8192
                rate 44100
        }
bindings {
        0 0
        1 1
        }
}

pcm.!capture {
        type dsnoop     # dsnoop plugin for input
        ipc_key 5678    # another uniqe number
        slave {
                pcm "card0"
                period_time 0
                period_size 1024
                rate 44100
        }
}

#
# combined playback/capture device
#
pcm.!duplex {
        type asym
        playback.pcm "playback"
        capture.pcm "capture"
}

#
# making the playback/capture device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# for oss compatibility
#
pcm.!dsp {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

```
dmixing works perfectly well, among other things. I may have something wrong here.
If anyone else has the same sound card as me, would you care to post your .asoundrc(or /etc/asound.conf)?

---

### Post by panch0 on 2007-03-13
I do have an Ensoniq AudioPCI:

```
$ cat /proc/asound/cards
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xd400, irq 225
```

Here's my .asoundrc:

```
$ cat .asoundrc
pcm.dmixer
{
   type dmix
   ipc_key 1234
   slave.pcm "hw:AudioPCI"
}

pcm.!default
{
   type plug
   slave.pcm "dmixer"
}
```

And KPlayer/MPlayer work fine here, never heard any "static", not even sure what you mean by that. Maybe you just have too many parameters set, try keeping it real simple like the above and see if that works.

---

