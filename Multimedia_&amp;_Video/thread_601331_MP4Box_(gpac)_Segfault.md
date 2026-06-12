---
title: "MP4Box (gpac) Segfault"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by igb on 2007-11-03
I have been encoding mpeg files recorded on my MythTV box (feisty) to MP4 files for use on my iPod for some time. Suddenly, I am getting segfaults from MP4Box. The command that's causing the problem looks like:

```
/usr/bin/MP4Box -add /tmp/1-Torchwood-10_19_2007-Countrycid-21.mp4 /mnt/sda3/mythtv/pda/Torchwood-10_19_2007-Countrycid-21.mp4
```

Here is the back trace:
```

[mpeg2video @ 0x2b28163206d0]ac-tex damaged at 27 29
frame=87560 q=6.2 Lsize=  149656kB time=2921.5 bitrate= 419.6kbits/s
video:107294kB audio:19659kB global headers:0kB muxing overhead 17.883024%
Executing command #2 of 3  in job 'ipod'...
IsoMedia import - track ID 1 - Video (size 320 x 240)
IsoMedia import - track ID 2 - Audio (SR 32000 - 1 channels)
Converting to ISMA Audio-Video MP4 file...
Saving to /mnt/sda3/mythtv/pda/Torchwood-10_05_2007-Cyberwoman-21.mp4: 0.500 secs Interleaving
*** glibc detected *** /usr/bin/MP4Box: double free or corruption (!prev): 0x00000000006250c0 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b0564f48b23]
/lib/libc.so.6(cfree+0x8c)[0x2b0564f4c26c]

```

Any ideas as why this might suddenly start happening?

Ian.

---

