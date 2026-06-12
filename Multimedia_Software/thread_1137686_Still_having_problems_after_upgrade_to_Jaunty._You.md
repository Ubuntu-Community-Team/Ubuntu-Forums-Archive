---
title: "Still having problems after upgrade to Jaunty. Youtube and ECT."
date: 2009-04-25
forum: Multimedia Software
---

### Post by The_Real_Anna on 2009-04-25
I upgraded to Jaunty today from Intrepid.

I must say, I feel like throwing in the towel. It has been over 5 hours. I have looked through every, and tried everything, and still:

YouTube is very choppy. I have sound but VIEWING online videos in Youtube goes in and out.

On other sites I cannot view videos as all.

I feel like crying. :(

I have:

Jaunty installed
Adobe Flashplayer
Mediabuntu
Shockwave
Intel Celeron D

And just about everything else I'm supposed to have on here. I searched through the forum for a few hours and followed the tutorials.

---

### Post by unf on 2009-04-27
Same here.. you can watch youtube from opera. Still it was better in intrepid. I had font problem with firefox, sans > Waree I did get much higher performance.  

With interpid it was much better. 64bit + E6420 + 8400GS(HDMI/SeperateX)/8600GT Twinview 2x17" + 40"  

I dont know if the twinview defect my performance. Metacity does not understand twinview at all.. with compiz it have "virtual screens" but menu panel is 2560 pixel long... not 1280 like it was in intrepid.

Something todo with pulseaudio?

---

### Post by VMC on 2009-04-27
> **The_Real_Anna said:**
> I upgraded to Jaunty ...
YouTube is very choppy. ...
I have:

Jaunty installed
Adobe Flashplayer
Mediabuntu
Shockwave
Intel Celeron D

...That "very choppy" sounds very suspicious. May very well be your video chip. Bring back the output of this:

```
lspci | grep VGA 
```

---

### Post by unf on 2009-04-27
When I am watching youtube, sometimes pulseaudio cpu usage hits 110-140% (core2 100% + 100%) = choppy

I noticed that no sound sometimes. PulseAudio to blame?

[https://launchpad.net/~crimsun/+archive/ppa](https://launchpad.net/~crimsun/+archive/ppa) < did not solve anything.

---

### Post by CerialPhreak on 2009-04-29
I'm having similar issues with an ATI card. For me, problem carries over from youtube ect to saved videos in a variety of formats (AVI, WMV, FLV).

---

### Post by kafkaian on 2009-05-08
I never learn. Should've stayed with Intrepid. Youtube choppy - even after today's kernel update. BBC videos just don't play and hang on startup. Really fed up, but take responsibility for entrusting yet another Ubuntu upgrade.

---

### Post by lelamal on 2009-05-24
I've been having the same problems with videos described in this thread. My output to VMC's command is:
> 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
I'm using a Thinkpad laptop (R50e), and everything was fine until last upgrade to Jaunty. I hope someone finds a solution as soon as possible.

---

### Post by brianfactors on 2009-07-07
You might want to try getting rid of pulseaudio if your problem is sound. That worked when I had problems multitasking sound.
```
sudo apt-get purge pulseaudio
```
Or you can just find it in Synaptic.

---

