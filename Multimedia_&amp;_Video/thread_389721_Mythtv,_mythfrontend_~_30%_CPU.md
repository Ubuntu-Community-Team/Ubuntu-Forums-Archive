---
title: "Mythtv, mythfrontend ~ 30% CPU"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by ebike on 2007-03-21
Hi All,

On my recent install of mythtv for Ubuntu Edgy, I have noticed that mythfrontend is using about 25..30% CPU, which is pretty much the total cpu usage.

I remember when I ran mythtv on my gentoo box it was about 17%, anyone have any idea's why it is higher?

I do get "prebuffer" pauses showing up in the log, which I wouldn't expect for a machine that was running nowhere near 100% cpu., and I do get the occasional pause in watching TV.

The only thing I can think off, is that I am running a different version of the nVidia binary drivers that was I was before ....  anyone?

I am running on a 2.8Ghz Athlon XP box.

---

### Post by electronikjunkie on 2007-03-21
Are you watching HD or SDTV? I used to get tons of prebuffering pauses/stuttering when HD content was being displayed. The only way for me to get rid of it was to install MythTV SVN and I still get the stuttering when the OSD is displayed. I'm using XvMC only with HDTV, so I don't have any stuttering on SDTV when the OSD is displayed. I disabled all my unused devices in my BIOS to help free up some IRQs, but it didn't change anything. I know if I disable "extra audio buffering" the prebuffering/stuttering comes back. I was thinking it my be something to do with my on board audio. I'm going to disable the on board sound in the BIOS, drop in a PCI audio card, and boost the latency up. Hopefully this will completely fix the stuttering.

Oh yeah, Mythfrontend is around 12% with SDTV and around 15%-20% with HDTV.

---

### Post by ebike on 2007-03-21
Hi, am using SDTV with a Haupauge PVR500 twin tuner hardware accelerated card.
I am not using XvMc .. I have extra audio buffereing enabled. 

How fast is your cpu ?

---

