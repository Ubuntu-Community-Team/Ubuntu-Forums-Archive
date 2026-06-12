---
title: "Hardware demands!"
date: 2008-10-17
forum: Mythbuntu
---

### Post by thusgaard on 2008-10-17
Hi 

I need to build 2 backends for family and one frontend. I'm thinking mini ITX to keep them low powered (green). My own back/frontend is a media PC from HP so there is no way to compare there. 

I need the following: 
Backend1
- Record one analog and one digital channel at the same time.
- Play and timeshift one of the channels being recorded. 

Backend2
- Record two digital channels at the same time.
- Play and timeshift one of the channels being recorded. 

Frontend
- Play recorded channels in full HD and to standart TV-out.

My questions are the following. 
- Which tuners should I use (PAL b/g for the analog, Denmark)?
- Which processors would be able to do this, could an Intel Atom dual core do the job?
- Will DVI deliver full HD or do I need HDMI?
- Has any one any experience?

BTW. when I build these I will post all of my findings on my homepage and in any WIKI that would have them.

Kind regards J;-)

---

### Post by ian dobson on 2008-10-17
Hi,

I would recommend looking at a PVR-150 for analoge tuner. They have MPEG encoding onboard so you don't need a fast CPU for encoding.

An Atom dual core might be enough. Using a NVIDIA 7300 my frontend needs about 8% CPU to watch a SD recording on a CORE2 1.6GHz. At the moment Atoms are abit too new, maybe wait abit for the Linux Kernel to catch up. As said a bottom of the range CORE2Duo should be enough and some are really cheap (I just picked up a E5200 - 2.5GHz,2Mb cache Dual Core for about 60Euro). 

I'm still using an old analog TV so I can't say much about the DVI question apart from the fact that HD takes alot of CPU to decode/display. SD/MPEG2 is no problem with NVIDIA cards as they support hardware decoding.

Regards
Ian Dobson

---

