---
title: "LMMS Warning"
date: 2011-03-09
forum: Multimedia Software
---

### Post by usalabs on 2011-03-09
First off, my system is a duel core AMD Athlon x64x2, I'm running Ubuntu 10.10 64bit, with 4GB RAM, and a Sound Blaster X-Fi PCI-e sound card, I installed LMMS, along with Jack, everything works fine, but,,,, and yes there is always a but,,,,,,my duel core is no match for LMMS and its LADSPA plugins, even with the jack latency set to above default 42ms, the cpu is still no match for LMMS, it seems (after careful testing on various other ubuntu setups), LMMS will ONLY work on a quad core (or higher), 16GB system, with no interruption in audio quality.

ALSA is even worse.

I thought I would mention this before anyone else posts problems with LMMS.

---

### Post by Yellow Pasque on 2011-03-10
Did you try the Ubuntu Studio kernel? Actually, the RT kernel is in a sad state right now for Ubuntu: [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)
You should probably try another distro with a real-time kernel and/or use this helpful site: [https://rt.wiki.kernel.org/index.php/Main_Page](https://rt.wiki.kernel.org/index.php/Main_Page)

---

### Post by cchhrriiss121212 on 2011-03-10
The rt kernel is fine, it is just a little behind in version numbers. Ubuntu will be switching to the low-latency kernel, which is just as good as the rt, on the next release. Get one from here:
[https://launchpad.net/~abogani/+archive/ppa]("https://launchpad.net/%7Eabogani/+archive/ppa")

As for LMMS, it has never worked well with jack. How many tracks/plugins are you trying to use?

---

### Post by usalabs on 2011-03-10
Up to 5 tracks, and 2 plugins just about runs with my duel core, but any more than that, the cpu reaches to 95% and the sound starts to splutter.

I tested LMMS on a quad core system with 12GB memory, using jack at default latency of 42ms,  and I could create 12 tracks with 14 plugins, before the system starts to reach about 90%, then audio starts to splutter.

UPDATE.......
I just now finished a comparison between Musix (a knoppix based distro specifically for audio/video production), Ubuntu Studio and Windows XP, on 3 separate computers, each having an AMD Athlon x64x2, and 4GB ram, and a sound blaster X-Fi Pci-e card, each one (except windows) running jack and LMMS, and 15 tracks, using 3 effects plugins each track, and a limiter on the master track,, windows was running Cakewalk Pro Audio 8, with 15 tracks of audio, and about as many effects plugins.

The findings are:-

Ubuntu Studio = Completely useless on a duel core system.
Musix = ditto
Windows XP, excellent, the latency was not noticeable, and I still had room for a lot more tracks.

Conclusion.
I'll be installing windows XP Pro SP3, specifically for my audio productions.

---

