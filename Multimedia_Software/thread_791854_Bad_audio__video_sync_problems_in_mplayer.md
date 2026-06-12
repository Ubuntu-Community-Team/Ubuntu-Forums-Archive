---
title: "Bad audio / video sync problems in mplayer"
date: 2008-05-12
forum: Multimedia Software
---

### Post by bryan.taylor on 2008-05-12
When I watch a video in mplayer the video lags behind the audio by 3-4 seconds.  This problem appeared only after upgrading to hardy.

I've tried H.264, XviD, Divx, and dvd vob files all with the same sync problems.  I've tried the mplayer distributed with hardy, and I've tried compiling my own.  Both have the same sync problems.  I've tried the "-autosync 30" option with no result.

I'm out of ideas to try, and I would really like to have mplayer working because it's my favorite player.  Vlc just isn't a good enough substitute.

I'm not sure what else I should include, but if anyone has a suggestion i'd be more than happy to post additional information.

Thanks for your help. :)

---

### Post by blom on 2008-05-12
I had a similar problem with Gutsy, and now with Hardy, except in my case it got slowly more and more out of sync.  I found that pause/play got it back in sync again.

vlc doesn't have the same problems at all (for me), but half the hotkeys don't work and none of the media keys on my laptop work - in vlc, so I'm shot either way I go :-)

---

### Post by bryan.taylor on 2008-05-12
Well, I solved my problem.  Previously I had followed the instructions [here](https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/188567) on how to fix the zsnes audio.  I guessed that mplayer could be having audio issues because of pulseaudio as well.  So, since I already had the ability to bypass pulseaudio via sdl, I selected sdl for my audio output in mplayer.

It works fine now. :)

I guess pulseaudio just needs some more work?

---

### Post by shamrock_uk on 2008-05-14
Glad you got it working! 

You may be aware of this, but the - and + keys will adjust the audit/video delay in increments of 100ms in case you stumble across a video file that exhibits a similar problem in the future.

---

