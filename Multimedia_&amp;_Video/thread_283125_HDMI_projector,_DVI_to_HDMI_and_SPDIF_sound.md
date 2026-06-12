---
title: "HDMI projector, DVI to HDMI and SPDIF sound"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by rklauco on 2006-10-23
Hello to everyone.

I am using Ubuntu with Freevo as my home TV/recording/audio station.
Everything works just fine.

I would like to extend the quality/functionality.
I would like to buy a new projector (preferably Acer PH530 as it have 1280x720 px native resolution - 720p) and I would also extend the sound experience by Logitech Z-5500 digital speaker set.

My question is:
I have no experience in connecting the speakers using SPDIF connection. There are more options - optical link and coaxial link. Is there any difference?
Will this set work with linux and deliver the sound also for stereo MP3 files?
Will there be some sync issues with digital connection?

Next question:
I read a lot these days about problems with Xorg regarding the DVItoHDMI connection and the correct setup of the mode.
Will the projector work with this connection? Have anyone some experience in connecting HDTV capable projector to Ubuntu and get it to work?

Any help/advice will be greatly appreciated.

---

### Post by gundog on 2007-10-03
Audio
=====
It depends on what type of connection you have on your motherboard. Most seem to be SPDIF (which is coaxial digital connector, or, if you are really sad, Sony Phillips Digital Interconnect Format) though I have heard of some that use TOSLINK (an fibre optical cable with an irregular hexagonal connector). The Z-5500 speakers have both TOSLINK and SPDIF (i.e. both optical and coaxial connectors). All you need to do is hook the pc up to the Z-5500's and it should work natively. There is some fiddling to be done with ALSA but there is some help here:

[http://ubuntuforums.org/archive/index.php/t-509438.html](http://ubuntuforums.org/archive/index.php/t-509438.html)

In practical terms there is no difference in sound quality between TOSLINK and SPDIF.

Video
=====
I cant help you there. Theoretically you should just be able to plug your DVI-D out into the HDMI in (with the correct cable) and it *should* work. I dont own any HD kit so I cannot help you there.

---

### Post by rklauco on 2007-10-03
Thanks for the reply.
In the meantime, I modified the mainboard and boucht an AV receiver, so the sound works already.
But the HDMI connection is still untested and I am a bit affraid to buy an expansive projector and find out it's not working outside the windows world :-(

---

### Post by mojoman on 2007-10-03
I've got a Hitachi HD-projector connected with DVI-HDMI. I set it up as a dual-monitor using twinview (I got a nVidia-card) with the projector as my second monitor. Took some tweaking in my xorg.conf to get it working properly but it wasn't that hard. And the effect? In three words. Quality of Life! Man, I watch a lot of movies these days! :biggrin:

I'll be happy to let you have a look at my xorg.conf if you decide to go for the twinview solution.

/mojoman

---

