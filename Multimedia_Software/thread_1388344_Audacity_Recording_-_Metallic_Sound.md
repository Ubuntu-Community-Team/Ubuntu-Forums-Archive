---
title: "Audacity Recording - Metallic Sound"
date: 2010-01-23
forum: Multimedia Software
---

### Post by tom-japan on 2010-01-23
I decided to post this thread due to my experience recording my own voice and some steaming audio (kids stories).

Recording streaming audio with Audacity gives a strange metallic sound mixed into the recording. This came up several releases ago and again in Hardy. (I can't remember if I worked out a solution or got around it some other way a few years ago)

At the same time, I had trouble finding a way to record playback. The 'Mix/Mix Mono' thing gave me input in Hardy, but also the metallic sound mixed in.  Upgrade to Karmic and I couldn't figure out how to get past Pulse without fiddling with the alsa mixers directly (resulted in metallic sound again)

Solution- Go to Pulse Volume controls, Input Devices tab. at the bottom of the box, choose 'All Input Devices' NOT 'All Except Monitors', then mute any mics and unmute the Monitor input.

This gave me perfect sound recording in Audacity in 9.10.

I hope this helps anyone who has had similar problems.

---

