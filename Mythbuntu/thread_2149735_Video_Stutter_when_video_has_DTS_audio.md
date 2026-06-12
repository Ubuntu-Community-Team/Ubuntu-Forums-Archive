---
title: "Video Stutter when video has DTS audio"
date: 2013-05-29
forum: Mythbuntu
---

### Post by DiGiTGOD on 2013-05-29
I had a completely working setup until some point in the last couple of months, Movies with DTS stopping playing flawlessly and started stuttering, giving the following in the frontend log.

```
May 29 22:05:57 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 722ms for video buffers AAAAAAAAAAAAAAAA
May 29 22:05:58 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 825ms for video buffers AAAAAAAAAAAAAAAA
May 29 22:05:58 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 929ms for video buffers AAAAAAAAAAAAAAAA
May 29 22:06:11 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 103ms for video buffers ffAAALfALAAAAAAA
May 29 22:06:12 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 103ms for video buffers AAAALAAffAfAALAA
May 29 22:06:12 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 206ms for video buffers AAAALAAffAfAALAA
May 29 22:06:13 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 103ms for video buffers fAAAALAAAAAAfALf
May 29 22:06:13 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 207ms for video buffers fAAAALAAAAAAfALf
May 29 22:06:13 mythfrontend1 mythfrontend[1536]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 310ms for video buffers fAAAALAAAAAAfALf

```

Nothing has changed, no OS/Myth updates (that I can remember doing), no config changes (that I can remember doing, so I doubt it).  I've since done a complete reinstall of 12.04.1 from the Mythbuntu disc and that didn't fix it.

The machine is an Emachines ER1401, GF 9200, 2GB RAM, dedicated Frontend, stereo audio over HDMI.  I have a dedicated backend, a separate dedicated backend for the Tuners, and another separate dedicated frontend.

I'm running 12.04.1/0.25-fixes, I'm loathed to move up to 0.26 unless I absolutely have to, as this setup has been working for a fair while.

I've gone through the VDPAU stuff in wiki for Myth, and applied everything from CPU frequency stuff to Xorg config, nothing has fixed it.  I've also increased the audio buffer in the prealloc thing to 32764.

What's annoying is my separate frontend is running a PCI (not express) GF 8400GS with a 2.8GHz intel processor, and this still runs the same videos fine.

I have narrowed it down to any video that contains a DTS audio track (don't have any that have more than one track to see if it is only when one is selected).

Pulling my hair out now as most of the stuff we watch I encoded with AC3 so there is no issue, it's just the stuff I did with DTS that's the issue.

I'll post any logs requested.

Thanks,
Martin

---

### Post by nickrout on 2013-05-30
What are you playing into? TV or amplifier? It is unlikely your TV supports DTS.

What are your audio settings?

---

