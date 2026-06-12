---
title: "Playback issues (Pixellation/Audio Jumping) - ABC TV Melbourne Only"
date: 2011-03-10
forum: Mythbuntu
---

### Post by mr_luksom on 2011-03-10
Hi,

I'm having issues with files recorded/live tv, although only for one station (ABC TV Melbourne - ABC1/2/24). It is something that has changes recently - over the last month or se.

I am getting large amounts of pixellation on the screen, and audio jumping. I have tried different playback profiles (currently using Normal, have tried CPU--, no VDPAU support), but there is no change in the symptoms. I don't think it is a hardware issue as I get the same picture on my remote frontend as well as the backend machine.

I am getting the following errors showing up in the logs, any ideas?

```

2011-03-11 02:02:51.114 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 27 27
2011-03-11 02:02:51.114 [mpeg2video @ 0x7fcc7d076380]invalid cbp at 0 1
2011-03-11 02:02:51.114 [mpeg2video @ 0x7fcc7d076380]ac-tex damaged at 25 2
2011-03-11 02:02:51.115 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 4 3
2011-03-11 02:02:51.115 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 4 6
2011-03-11 02:02:51.115 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 15 7
2011-03-11 02:02:51.115 [mpeg2video @ 0x7fcc7d076380]mb incr damaged
2011-03-11 02:02:51.115 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 19 16
2011-03-11 02:02:51.116 [mpeg2video @ 0x7fcc7d076380]invalid mb type in B Frame at 5 19
2011-03-11 02:02:51.116 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 5 20
2011-03-11 02:02:51.116 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 6 26
2011-03-11 02:02:51.116 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 7 27
2011-03-11 02:02:51.116 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 7 28
2011-03-11 02:02:51.116 [mpeg2video @ 0x7fcc7d076380]ac-tex damaged at 18 31
2011-03-11 02:02:51.116 [mpeg2video @ 0x7fcc7d076380]invalid mb type in B Frame at 5 32
2011-03-11 02:02:51.117 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 40 7
2011-03-11 02:02:51.118 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 23 16
2011-03-11 02:02:51.118 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 33 27
2011-03-11 02:02:51.122 [mpeg2video @ 0x7fcc7d076380]ac-tex damaged at 14 28
2011-03-11 02:02:51.195 [mpeg2video @ 0x7fcc7d076380]invalid mb type in B Frame at 30 18
2011-03-11 02:02:51.196 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 23 30
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 12 33
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 8 1
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]mb incr damaged
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 2 3
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 3 10
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 5 11
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 1 15
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 8 16
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 1 20
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]mb incr damaged
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 1 25
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 15 26
2011-03-11 02:02:51.197 [mpeg2video @ 0x7fcc7d076380]invalid mb type in B Frame at 5 33
2011-03-11 02:02:51.198 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 14 7
2011-03-11 02:02:51.199 [mpeg2video @ 0x7fcc7d076380]00 motion_type at 24 19

```

---

### Post by LowSky on 2011-03-10
rescan channels... im betting your feed is a bit off. 

If it is still an issue look into getting a amp for the antenna/cable feed.

---

