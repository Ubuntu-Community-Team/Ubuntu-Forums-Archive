---
title: "Remote frontend stutters during playback..."
date: 2012-05-15
forum: Mythbuntu
---

### Post by toddk111 on 2012-05-15
I just set up a remote frontend in another room using a 100mb wired connection.  When I try to playback my recordings (all are HDTV), the video is "jerky"...in other words, it pauses briefly or stutters.  

Is there a buffer setting on the frontend that I can adjust so that it will cache the recording locally on my machine?  Could something else be causing the stuttering?  Here is my configuration on my remote frontend:

Acer Aspire 5100-5764 Laptop
AMD 64x2 TK-53 1.7ghz, 2xL2 cache
256MB ATI Radeon Xpress 1100 HyperMemory
Ubuntu x64 10.04LTS

When I play these recordings on the frontend located on my backend machine, they have smooth playback so I'm sure the recordings are good.  Also, I've watch videos and DVDs on my laptop before, so I don't think it's a codec problem.  Please let me know if you have any ideas for making my remote frontend have smooth playback.

Thanks!

---

### Post by klc5555 on 2012-05-15
You have a bottleneck somewhere. You need to examine your frontend log to begin to determine where this bottleneck is.

Fast ethernet is easily fast enough; it is recommended to assure that it is running in full duplex mode.

Although ATI video is not supported by VDPAU, it should still be fast enough. I have no trouble with HD recordings on an old T43 Thinkpad with ATI graphics. Try resetting your frontend playback profile from the default "normal" (or on 10.04 maybe "CPU+") to "slim" --"slim" helps on remote frontends whose hardware may be a bit marginal. However, if your remote frontend laptop is running something hoggish like Gnome (which, as vanilla Ubuntu it must be), it's wasting resources that, on a marginal machine, could be used for mythfrontend.  XFCE or even one of the pure window managers like Fluxbox, Blackbox, or FvWM would cut down on the wastage. The above-mentioned T43 Thinkpad started out with a molasses-like Ubuntu 10.04 installation, then over time slimmed down to Xubuntu 11.04 and now runs XFCE over a minimalized Slackware 13.37 on a custom 3.2.8 kernel. It could do HD even while running Xubuntu, but could not do so reliably on vanilla Ubuntu 10.04.

I'm not familiar with the AMD processor you use, or how well its "1.7Ghz" rating stacks up against similarly rated Intel processors. I know that a 1.8 Ghz or 2.0 Ghz Intel Pentium M laptop processor can display HD recordings if not too much else is going on on the machine. It may be that a 1.7 Ghz AMD simply doesn't have the processing juice on a machine that can't offload some of the processing using VDPAU or even XvMC  But someone else who actually runs one of these processors would have to weigh in on that.

At one time there was a document on the wiki in diagnosing HD playback bottlenecks that I can't seem to find now. However there is a second document on "optimizing" that may provide you some useful tips: [http://www.mythtv.org/wiki/Optimizing_Performance](http://www.mythtv.org/wiki/Optimizing_Performance)

Maybe some of the others here will have additional ideas.

---

