---
title: "play hd content like h264 with hardware accelaration, ati or nvidia?"
date: 2008-07-15
forum: Multimedia Software
---

### Post by Jean__ on 2008-07-15
Hi,

I probably need to buy a new system because I can hardly play hd content on this one. It's a pentium 2.4 ghz, 1 gb memory and nvidia Geforce 7600 Gt. 

I have a samsung 22" syncmaster as well as a samsung 40" hd ready tv attached to the card, both work well.

I can play some 720p content but often it's too choppy, and 1080i is mostly out of the question. However I do see people reporting that they can play hd content with a system like mine.

So what should I buy to get me smooth hd content playback. Obviously a new faster pc like a dual core, but what about video cards and hardware accelaration on linux?? What is the situation on driver support for this? I read a lot but there is hardly hands on experience and a lot of wishing.

I hope to hear something from people with experience on this, are there people out there enjoying hd content on their big lcd screens? What are your experiences?

---

### Post by steefjeqv on 2008-07-16
Hi,

There's no hardware accelerated meg4/h.264 possible for linux at the moment.

It's being worked on by AMD/ATI who hope to have some support by the end of the year (most certainly only for their future graphic cards), but perhaps also for the most recent designs.
[http://www.phoronix.com/forums/showthread.php?t=10392&page=8]("http://www.phoronix.com/forums/showthread.php?t=10392&page=8")

There's also Broadcom who've released a chipset to do mpeg4/h.264 decoding. And they mention it will also be supported for linux.
[http://www.mail-archive.com/vdr@linuxtv.org/msg06796.html]("http://www.mail-archive.com/vdr@linuxtv.org/msg06796.html")

There's one thing out there that can do hardware meg4/h.264. It's called Reel eHD PCI card and it works together with a special development version of VDR (linux Video Disk Recorder). Quite expensive though (about 179 euro).
And a lot of work to set it up. Support is good by the VDR Portal, but mostly in German.  

There's also CoreAVC for linux but that's software decoding.
[http://ubuntuforums.org/showthread.php?t=839295]("http://ubuntuforums.org/showthread.php?t=839295")

Personally, I'm going to wait 'till the end of the year and hopefully some new options will have emerged by then.

Greetings,
Steven

---

### Post by Jean__ on 2008-07-16
Thanks Steven.
The options are not too overwhelming at the moment no.
I looked at CoreAvc but it seems a lot of hassle to setup and even then there are quite some limitations, so I'll pass for now.
I too will wait some time and probably buy a brand new pc in a half year or so and hope untill then the situation has improved. It's strange with so many hd tv's sold at the moment that support for playback hd movies from pc is so weak, even in windows.

Greets, Jean.

---

### Post by markbuntu on 2008-07-16
I think it is an issue of IP rights. That is why everything is moving so slowly. Because once HD gets on a pc, people can, and will, do anything with it.

The newer video cards have HD support built in to the hardware and firmware, it is only a matter of getting the drivers up to snuff to use them. My ATI Radeon HD 3650 1GB claims to have built in support HD.

I can play the HD from Hulu but it lags because my poor single cpu can't keep up with the downloading and playing at the same time. I have better luck with downloaded HD and Miro. Full screen playback is awesome on my 24 inch monitor which has native 1920x1080 resolution. The card is handling the playback and keeping my other monitor up. CPU usage does not max out.

If I had a tv, I would try it with one. Anyone want to give me a 40" tv?
Or maybe a blue-ray dvd recorder for my computer?

---

