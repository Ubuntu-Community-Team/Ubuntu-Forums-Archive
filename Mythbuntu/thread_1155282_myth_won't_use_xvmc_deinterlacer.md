---
title: "myth won't use xvmc deinterlacer"
date: 2009-05-10
forum: Mythbuntu
---

### Post by ctcarroll on 2009-05-10
This one has got me stumped.  I'm using an Nvidia 7300GS on an AMD X2 system with 2GB of RAM, and the nvidia proprietary driver version 180.44 in Jaunty.
To start out clean, I recreated my xorg.conf (attached) and added just the minimum options specified in the Wiki ([http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC).)  My  /var/log/Xorg.0.log (attached)  looks pretty good.   No error messages that lead me to believe that XVMC shouldn't work.

My /etc/X11/XvMCConfig contains the line:
libXvMCNVIDIA_dynamic.so.1

I created a separate playback profile to use just XvMC at all resolutions. Using standard xvmc decoder and xvmc-blit, 1CPU, bob 2x deinterlacer, and one field fallback deinterlacer.
When I start playback I get the OSD to come up (with blue, not greyscale), a black screen for a few secs, then maybe playback starts, but locks up a few seconds later.  I notice many prebuffering pauses in the log before it crashes.

I created a log of the output using mythfrontend -v playback > myth3.log (attached).    I'm getting an error about using the xvmc-blit deinterlacer, but I can't figure out why.   It seems like XVMC should be working.    Could anyone suggest what I might be doing wrong?
Thanks!!!

---

