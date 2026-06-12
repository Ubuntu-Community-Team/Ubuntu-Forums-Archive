---
title: "Need Hardware Suggestions"
date: 2013-06-24
forum: Mythbuntu
---

### Post by toddk111 on 2013-06-24
I'm looking to replace my frontend/backend machine.  I want to be able to playback a recording while simultaneously recording up to 6 HD channels at once (ATSC OTA Antenna and possibly QAM in the future).  I want a machine that is powerful enough to do these things but is fairly slim and quiet so that I can keep it in my living and sleeping areas.  I have built machines in the past but I'd rather buy something prebuilt (mini-itx?).  Here are some questions:

Can anyone recommend a good machine at the lowest cost that would satisfy my requirements stated above?
For tuners, should I use two HDHomerun Prime boxes?
If the machine has USB 3.0, could I do those simultaneous recordings to an external hard drive?
I saw a Lenovo Q190-57316188 at [Fry's]("http://www.frys.com/product/7706888?site=sr:SEARCH:MAIN_RSLT_PG"), it looks like the size I want but would it work for what I'm trying to do?

Any suggestions would be greatly appreciated.
Thanks,
Todd

---

### Post by klc5555 on 2013-06-24
The frontend for playback and the backend for simultaneous recording have two fairly divergent sets of requirements. 

The frontend for playback is mostly all about CPU power/speed and quality of hardware-accelerating video card. Sound too, of course. 

The backend for simultaneous HD recording is not particularly CPU sensitive, doesn't need sound, doesn't need X or a graphics card at all except possibly to configure the backend with mythtv-setup, but requires robust I/O and, with multiple simultaneous HD recording, each of which recordings consume over 6 GB/hr, several large fast SATA disks. (For my own use, over the years I've usually preferred 1 disk per HD stream I expect to record simultaneously --in practice this has usually amounted to 2-3 tuners and 2-3 drives per backend. Allowing myth to spread its simultaneous recording over multiple drives to avoid degradation, particularly if a recording is being watched at the same time as HD stuff is recording.)

So maybe some kind of a hairy beast of a single machine can be found to do acceptably all of the simultaneous heavy lifting you intend for it. I don't believe the Lenovo is such a machine. But it would very likely be better to separate the job into more modest specialized machines: 1 backend machine and 1 frontend machine, connected by ethernet. You could buy/build a graphics-display-heavy, surround-sound, super fast CPU frontend machine with just enough hard disk to hold the OS and mythtv to run mythfrontend. That role might be a good fit for the Lenovo.

Your current machine could be transitioned to backend-only status. It could live in a closet, if necessary; it could certainly handle all foreseeable disk and I/O requirements for recording, since it obviously does so already, and would not have to waste resources and CPU cycles running an unnecessary frontend. It doesn't take much CPU to pump HD recordings over a cat 5 cable to a frontend --until recently I did much of my HD recording on a backend with 2 tuners, built on a 12-year-old Athlon +2100 motherboard,  with a PCI SATA card added to provide SATA capability to the motherboard, and an old s3 video card with 128K of video RAM to allow the MB to boot. Kept the whole piece of junk in the basement because it was noisy as hell. And uncovered because it ran hot. But it had no trouble piping the recordings over ethernet to my much quieter and completely modern frontend upstairs.

So you have a lot of flexibility, particularly with the backend specs, when you split the frontend/backend jobs across a pair of machines. You may want to consider it, since you already have a capable combo machine that can be transitioned to the backend.

---

