---
title: "Media loads but won't play"
date: 2009-10-23
forum: Multimedia Software
---

### Post by lingenfr on 2009-10-23
This is a fresh install of Karmic amd64. I have tried .mpg and .avi (video) and .flac, .mp3 and .ogg (audio) and all do the same thing. Totem, Rythmbox and mplayer/smplayer all queue up the file but won't start playing. I have tried running them from the command but don't get any useful feedback. I ran totem with the --debug option and got nothing. Smplayer/gmplayer must be killed as they won't close correctly once I try and play a file. When I first attempted the .mpg file it asked to install codecs and I installed gstreamer bad and ugly. When that didn't work, I also installed ubuntu-restricted-extras. I installed VLC and had a little better results. The audio files seemed to play, but no audio. The video played with no audio. I am not sure what to try next. I've looked through similar posts and googled and can't find any answers. I did try closing FF to see if that made a difference. It didn't. I don't have a problem filing a bug report but would like to at least narrow it down. I don"t really want to crap up my system by continuing to install players. My hardware info is shown below. Thanks.

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller

**UPDATE: A reboot seems to have fixed this. I was ESCing past one or more slow loading partitions which seems to have created this problem.

---

