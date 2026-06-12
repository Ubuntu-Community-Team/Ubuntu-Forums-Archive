---
title: "How do you get ordered chapters + segment linking in mkv files to work?"
date: 2012-07-18
forum: Multimedia Software
---

### Post by kill o matic on 2012-07-18
Recently converted from Windows 7 and I can't get any mkv files with ordered  chapters to play reliably using the most suggested SMplayer + mplayer2 setup.  The timeline loads correctly, but when it attempts to switch to the  external segments playback will stall in most cases (except when it  feels like cooperating, which is rarely). I can still seek into the  external segments or play them from the chapters menu. The same files played fine in MPC-HC under Windows, so I don't think they have anything wrong with them. Anyone encountered this before?

Edit: It's an audio issue apparently. Switching the audio output option in SMplayer  from "pulse" to "alsa" or "sdl" fixes it (the others give me no sound  but still transition correctly). Don't know if this has any downsides  yet and I only tested it with AAC (LC) 2 channel audio. VLC Player however  works correctly even with its pulse module selected, so either they use  different versions or its a mplayer2 bug.


Edit2: "alsa" seems to cause hanging when quickly pausing/unpausing or flipping frame by frame, so switched to "sdl" instead.

---

