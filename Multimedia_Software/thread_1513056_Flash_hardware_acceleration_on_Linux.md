---
title: "Flash hardware acceleration on Linux?"
date: 2010-06-18
forum: Multimedia Software
---

### Post by gophergun on 2010-06-18
As I understand, Flash 10.1 does not support hardware acceleration on Linux. I've heard Gnash does, but I can't get it to work on much of anything. Flash video is absolutely abysmal on my netbook without handing things off to the integrated graphics. Is there either some kind of trick to get Gnash working more reliably, or perhaps another option supporting this feature?

---

### Post by kerry_s on 2010-06-18
adobe flash is the best option, you'll just waste your time on the others.

> Flash video is absolutely abysmal on my netbook

flash for me is only as good as the internet connection, slow internet, slow flash, other then that works perfect here.

mines a atom 230 1.6ghz 1gb-ram b43 wireless intel 950g vid nettop.

---

### Post by gophergun on 2010-06-18
Personally, I can't even do 480p on my Eee PC 1000HE (Atom N280, I believe) without stuttering on Firefox, whereas I would normally be able to push 720p, and don't get me started on fullscreen. I don't think Internet connection is my issue, as I'm on cable, and I don't think wireless G is a big enough hindrance to that. What should I be doing differently?

---

### Post by kerry_s on 2010-06-19
> **gophergun said:**
> Personally, I can't even do 480p on my Eee PC 1000HE (Atom N280, I believe) without stuttering on Firefox, whereas I would normally be able to push 720p, and don't get me started on fullscreen. I don't think Internet connection is my issue, as I'm on cable, and I don't think wireless G is a big enough hindrance to that. What should I be doing differently?

have you tried reinstalling flash in synaptic? mark it for complete removal, then install it again.

i can run full screen just fine, it's how i watch most vids. my monitors 14 inch lcd 1024x768.

---

### Post by gophergun on 2010-06-19
Just tried, still noticeably stuttering in 480p. It's rather frustrating, considering I switched over to the Windows partition for the first time in a long while, installed 10.1, and watched some TV on the internet, and it was just flowing beautifully. Just wish I could get it working that well in Linux, or really even close - instead I'm sort of stuck with a 4-5 fps slideshow with audio. /whine

---

### Post by Naggobot on 2010-06-19
With previous Flash version 10.(something) performance was adequate on most videos/sites. Now that flash updated to 10.1 sites/videos that worked previously OK are now stuttering or total slide shows. 

With previous version it was possible to force HW acceleration in full screen mode by adding a file /etc/adobe/mm.cfg with a key OverrideGPUValidation=True. I suspect that this does not work with 10.1 or something else has happened.

---

### Post by snowpine on 2010-06-19
I have two Atom 270 netbooks and an Atom 330 nettop, all with Intel 950 integrated graphics. I dual boot with Windows XP specifically for flash video watching. Flash is not open source software, therefore there is nothing Canonical can do to make it run better in Ubuntu. It just works better in Windows and always will until Adobe supports Linux equally. :(

That being said, I usually get adequate performance if I download the video first and watch it from my hard drive, rather than streaming. There are lots of "Youtube downloaders" out there but I just copy it from /tmp. ;)

---

### Post by Linuxforall on 2010-06-19
You can also use minitube which is in the Ubuntu repos to watch all flash streaming minus Adobe flash.

---

### Post by gophergun on 2010-06-19
> **snowpine said:**
> I have two Atom 270 netbooks and an Atom 330 nettop, all with Intel 950 integrated graphics. I dual boot with Windows XP specifically for flash video watching. Flash is not open source software, therefore there is nothing Canonical can do to make it run better in Ubuntu. It just works better in Windows and always will until Adobe supports Linux equally. :(

That being said, I usually get adequate performance if I download the video first and watch it from my hard drive, rather than streaming. There are lots of "Youtube downloaders" out there but I just copy it from /tmp. ;)

Absolutely, I'm not blaming Canonical at all, it's Adobe's fault for not supporting, say, VA-API. Regardless, it leaves people with an unfortunate choice of good online video or a good operating system.

As for Minitube: is there a browser plugin for that? Is it available automatically, or do you have to open the program and type in the URL any time you want to watch a video? Is it available just for Youtube, or any Flash video (e.g. ABC, Comedy Central, etc.)? Finally, I suppose the big question is: is it actually hardware accelerated?

---

