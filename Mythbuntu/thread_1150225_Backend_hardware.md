---
title: "Backend hardware"
date: 2009-05-05
forum: Mythbuntu
---

### Post by WrathofthePenguin on 2009-05-05
I'm planning a setup in which I'll have backend recording with firewire and a tuner card to record clear qam via coax. In case you're wondering, this is to allow me to record two channels at the same time while avoiding the extra monthly cost of another set top box. I'll also have two additional frontends.

My question is how powerful a box will I need for the backend? At worst I'll be recording HD (via firewire), recording clear qam, watching a recorded program and serving a another recorded program to another television's frontend at the same time. If I'm recording HD via firewire I believe it's not as taxing on the processor because it's in mpeg format, but I'm not sure how taxing the rest of it is.

I'd like to keep the frontends low-power/low-noise, which is why I'm not considering a couple of "mini" backends.

I'm thinking of a phenom II X4 940 (I'm actually drooling as I type this) with 4GB of 1066 RAM.

---

### Post by newlinux on 2009-05-06
your backend CPU doesn't need to be very powerful at all. Capturing clear QAM and firewire are both of minimal impact (just capturing a digital file, no encoding involved). Serving content doesn't require much CPU either. Just make sure you get a good disk and consider using XFS or JFS for your media filesystem, and storing your recordings on a different partition from your system files. If you do commercial flagging or transcoding, that will take up more CPU than anything you mentioned. Any modern CPU can do what you want. Backends don't need to be very powerful at all, unless you want really fast commercial detection and transcoding.

your frontends need to have enough power to decode HDTV content, which requires more CPU than your usual backend tasks do, unless you get a VDPAU capable GPU and use VDPAU enabled myth and mplayer. Is this machine to be a combined backend/frontend?

That Phenom is way overkill for your a backend, and not necessary for combined/frontend backend, but certainly nothing wrong with getting it unless you are looking to save money - in which case you could get away with less. All the HD capable machines in my hardware link in my sig can easily do what you are looking to do (and most of them do).

---

### Post by WrathofthePenguin on 2009-05-06
> **newlinux said:**
> your backend CPU doesn't need to be very powerful at all. Capturing clear QAM and firewire are both of minimal impact (just capturing a digital file, no encoding involved). Serving content doesn't require much CPU either. Just make sure you get a good disk and consider using XFS or JFS for your media filesystem, and storing your recordings on a different partition from your system files. If you do commercial flagging or transcoding, that will take up more CPU than anything you mentioned. Any modern CPU can do what you want. Backends don't need to be very powerful at all, unless you want really fast commercial detection and transcoding.

your frontends need to have enough power to decode HDTV content, which requires more CPU than your usual backend tasks do, unless you get a VDPAU capable GPU and use VDPAU enabled myth and mplayer. Is this machine to be a combined backend/frontend?

That Phenom is way overkill for your a backend, and not necessary for combined/frontend backend, but certainly nothing wrong with getting it unless you are looking to save money - in which case you could get away with less. All the HD capable machines in my hardware link in my sig can easily do what you are looking to do (and most of them do).

newlinux - this was seriously helpful (except for the part where you undercut all my reasons for getting a monstrous phenom!) Thank you!

---

### Post by ian dobson on 2009-05-06
hi,

The backend doesn't need any real processing power (except for transcoding/comm flagging). I've put together a low power backend for a friend using a passive cooled,underclocked Pentium3 850MHz, which runs at only 500MHz with 750MB ram and a 120GB harddisk. I've installed 2 tuners (One PVR-150 and a DVB-C card) and even when recording 2 programs at the same time to CPU load doesn't go much over about 25-35%.

Regards
Ian Dobson

---

