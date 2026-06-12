---
title: "State of HD decoding in Maverick?"
date: 2010-06-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by warnec on 2010-06-24
Hi. I'm planning to buy a laptop with Intel X4500MHD card, and I enjoy watching HD content a lot. So, I was curious if it could help decode HD content and work alongside the CPU. 

Here's what I found:

[http://intellinuxgraphics.org/h264.html](http://intellinuxgraphics.org/h264.html)

Seems like an awful lot of work. 

Patching libva, libdrm and mplayer wouldn't be that hard (but still pain in the ***), but it's kernel recompiling that makes it much harder.

My question is - as that patch for kernel is written against the rc5 of 2.6.34,. which Maverick will use, is there any chance to see out-of-the-box support in the final version? The same question goes to libva, libdrm and mplayer,

---

### Post by xens on 2010-06-24
also waiting for an answer. One friend bought an HP laptop with an "HD READY" intel GPU (dont have the model yet), and he asked me if somthing was possible under linux.

Cheers Romain

---

### Post by cariboo on 2010-06-24
it's pretty hard to answer your question, as most of the content that says its HD isn't. Youtube's claimed 720p is nowhere even close to be being 720p, and most other HD media isn't either. About the only way you are assured of watching HD media is to create it yourself.

---

### Post by Starks on 2010-06-24
that wasn't very helpful. the topic creator was asking about out-of-the-box support for hardware-accelerated decoding like vdpau, xvba, and vaapi.

---

### Post by cariboo on 2010-06-24
> **Starks said:**
> that wasn't very helpful. the topic creator was asking about out-of-the-box support for hardware-accelerated decoding like vdpau, xvba, and vaapi.

I understand that, but it's pretty hard to test it out if you don't have the proper media. Most claimed HD media will work out of the box.

Try [Big Buck Bunny]("http://www.bigbuckbunny.org/index.php/download/")

I've been able to view it the last several versions without any added extras.

---

### Post by mc4man on 2010-06-24
Don't have a tester install available atm (computer room is being boarded out) but the ffmpeg in maverick does dep on libva1
[https://launchpad.net/ubuntu/maverick/i386/libavcodec52/4:0.6-1ubuntu1](https://launchpad.net/ubuntu/maverick/i386/libavcodec52/4:0.6-1ubuntu1)

so that's part of the equation.

Whether they build vaapi into some players is to be seen - vlc 1.1 is a candidate. - am expecting that to be the vlc used
(don't know the state of affairs with gstreamer atm.

Mplayer will likely not support - the release being used is quite old (16 months.) Though that should be easy to test.

Edit: as far as codec support it seems to be good as far as gstreamer, when vlc is re-built should be excellent there, xine=libs is a question mark and mplayer will be left wanting...

---

### Post by warnec on 2010-06-24
well, I mainly want to watch Movies/TV Shows in .mkv or .mp4 format which are reported to be HD.

to say something like this:
> 
I understand that, but it's pretty hard to test it out if you don't have the proper media. Most claimed HD media will work out of the box.

(...)

I've been able to view it the last several versions without any added extras.


doesn't seem very helpful to me. I don't want the media to **play**, because it's kind of obvious it would (with proper codecs). The big question is, if it will use GPU acceleration to make the process faster and reduce CPU's stress.

I'm planning to use VLC, but the main question I don't know an answer about is whether it will work on _Maverick_. _**I am mainly concerned about the 2.6.34 kernel, as I don't know if this "enable-multiple-ring-buffer.patch" made it to the official 2.6.34 stable tree, which will be used by 10.10.**_

Of course the same goes to libdrm and libva, but I guess this is just a matter of time when they get it integrated,or they could already have, i think libdrm 2.6.41 has already done that, see:

[http://permalink.gmane.org/gmane.comp.video.dri.devel/46855](http://permalink.gmane.org/gmane.comp.video.dri.devel/46855)

> 
1) media ring support on kernel 2.6.35 for doing media decode on G45+


---

### Post by cariboo on 2010-06-24
I've just been doing some really inaccurate testing. Watching [Elephants Dream 1920]("http://orange.blender.org/download") using vlc, cpu usage averages about 32%, see elephants dream screenshot.

While my freshly ripped dvd collection, using handbrake at the highest quality settings, the cpu usage is around 22% average, see galaxy_quest screenshot.

The system I'm using has an old AMD 3800+, 2Gib ram and an Nvidia 9400GT. with the 195.36.24 drivers

As a side note, Totem shows 70-80% with elephants dream and around 22% watching galaxy quest.

---

### Post by cariboo on 2010-06-24
I've done a little more playing around, on my netbook with Intel 945i chipset, using the xorg-edgers Intel drivers and mplayer, elephants dream 1920 is quite watchable with about 35% average cpu usage. I'm using the latest kerenl:

```
Linux redstone-maverick 2.6.35-5-generic #6-Ubuntu SMP Mon Jun 21 21:33:48 UTC 2010 i686 GNU/Linux
```

---

### Post by Longinus00 on 2010-06-24
So long as you have a dual-core (or better) cpu you'll be able to play back most anything. The caveat is you'll have to use a multithreaded decoding player like the mt branch of mplayer but you should be using that anyway.

---

### Post by Starks on 2010-06-24
If we ask Leanna and Andy nicely, we should be able to get the ring buffer kernel patch backported into Maverick.

---

### Post by warnec on 2010-06-25
Please do :D Where should I post/where to write at?

---

### Post by warnec on 2010-06-25
cariboo:

nvidia propably already has hardware hd decoding available already, what concerns me, is intel. It would be great to test elephant's dream with some intel hd-decoding-capable gpu like x4500 with vlc 1.1, mplayer vanilla and kernel 2.6.35 to test how big are the differences between CPU stress with VLC (w/ GPU decode) and mplayer (w/o GPU decode)

---

### Post by eyelessfade on 2010-06-25
[http://mirror05.x264.nl/Dark/force.php?file=./LosslessTouhou.mkv](http://mirror05.x264.nl/Dark/force.php?file=./LosslessTouhou.mkv) (fast mirror I got 12MB/s peak from it)
Try that one. It's lossless and really hard on any system.
It's only 640x480, but you should really feel it.

On my office computer: Elephants Dream 1920 ca 15% cpu.
LosslessTouhou.mkv -> 68% cpu

---

### Post by warnec on 2010-06-25
please note that **I don't have the laptop yet.** I want to make sure it will run HD fast and without great CPU usage, and I'm planning to buy one with Intel's GPU. I have nowhere to test it on.

---

### Post by Starks on 2010-06-25
The kernel patch is in the Maverick kernel.

Not sure about the drm or other component patches. I'll ask around.

BTW, Eyeless, I haven't seen that video in a while. It's meant to bring computers to their knees. coreavc-for-linux can't even handle it.

---

### Post by Longinus00 on 2010-06-25
> **warnec said:**
> please note that **I don't have the laptop yet.** I want to make sure it will run HD fast and without great CPU usage, and I'm planning to buy one with Intel's GPU. I have nowhere to test it on.

My 1.6ghz core duo can decode 720p.the resolution of its screen. just fine. It can even do 1080p at bitrates lower than 30mbps or so. So long as your cpu is ~2.0ghz it should handle most any regular video file, don't even worry about your gpu (especially if you're getting an intel one).

> **eyelessfade said:**
> [http://mirror05.x264.nl/Dark/force.php?file=./LosslessTouhou.mkv](http://mirror05.x264.nl/Dark/force.php?file=./LosslessTouhou.mkv) (fast mirror I got 12MB/s peak from it)
Try that one. It's lossless and really hard on any system.
It's only 640x480, but you should really feel it.

On my office computer: Elephants Dream 1920 ca 15% cpu.
LosslessTouhou.mkv -> 68% cpu

Elephants Dream 1920 < 10Mbps
LosslessTouhou ~ 40Mbps

Bitrate, not resolution is the limiting factor for decoding compressed streams. If you look around you can find 1080p 5.1 profile >40Mpbs  samples to test out your decoding hardware.

---

### Post by warnec on 2010-06-25
@Starks:

as long as the patch enters Maverick's kernel (and, as You say, it already has) everything should be easy-peasy. Maybe a very little compilation here and there, nothing major. Possibly out-of-the box by the time Maverick arrives.

@Longinus00:

Good to hear CPU can handle HD nicely. But it's not only about performance, but also about the comfort of mind - I want to make sure that my new laptop's hardware would do tasks on Ubuntu the same way as it would do on Windows, hadn't I already decided to purge Windows entirely ;)

---

### Post by hugmenot on 2010-06-26
> **warnec said:**
> @Starks:

as long as the patch enters Maverick's kernel (and, as You say, it already has) everything should be easy-peasy. Maybe a very little compilation here and there, nothing major. Possibly out-of-the box by the time Maverick arrives.


The Intel page you cited with the patches explicitly mentions that this is for Ironlake, not Eaglelake like your GM45.

The patches they mention are in already, and you can get them built into packages at least from xorg-edgers (not sure about main).

But it doesn&#8217;t work on my GM45. I took xorg-edgers and got libva from git here: [http://cgit.freedesktop.org/libva](http://cgit.freedesktop.org/libva). And then I compiled ffmpeg, mplayer and gstreamer with libva enabled. It fails on all of them.

I summarized my findings here:
[http://www.phoronix.com/forums/showthread.php?t=21126&page=5](http://www.phoronix.com/forums/showthread.php?t=21126&page=5)

Not sure, if it&#8217;s supposed to work yet. I&#8217;m afraid it just isn&#8217;t ready for GM45. At least it isn&#8217;t mentioned here as supporting H264: [http://www.freedesktop.org/wiki/Software/vaapi](http://www.freedesktop.org/wiki/Software/vaapi)

Ironlake is the new generation of graphics that come with i5, i7 processors. Maybe you should consider buying a laptop with i5 or i7. The G45/GM45 is 1-2 year old tech. [The new Intel chips can even decode two HD H.264 stream at the same time]("http://www.phoronix.com/forums/showpost.php?p=133661&postcount=36").

> 
Good to hear CPU can handle HD nicely. But it's not only about performance, but also about the comfort of mind - I want to make sure that my new laptop's hardware would do tasks on Ubuntu the same way as it would do on Windows, hadn't I already decided to purge Windows entirely ;)

You will get H264 acceleration support in video players sooner or later. Probably this year. But it&#8217;s still too early.

Surprised how much misinformation is present in this thread. These forums can be so noisy.

---

### Post by hugmenot on 2010-06-28
Word from the developer:

> No, GM45 support will schedule for Q3 this year.

Thanks
Zou Nan hai

---

