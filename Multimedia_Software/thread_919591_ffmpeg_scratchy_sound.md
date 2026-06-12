---
title: "ffmpeg scratchy sound"
date: 2008-09-14
forum: Multimedia Software
---

### Post by aws910 on 2008-09-14
I use mplayer with a streamdump/dumpfile command to record internet radio.  This gives me wmv files, which, in ffmpeg, show as an "asf" file type.  They play fine in all players and the quality is acceptable.  My final goal is to edit these audio files.  Audacity tells me I have to convert it to wav or aiff, so I use ffmpeg to do so - it generates wav(or aiff, I've tried both) files, but the output file has a scratchy sound.

My ideas/questions are:
Maybe ffmpeg isn't getting all the resources(cpu/ram) it needs?  Is there a way I could tell this?  Is there a switch that I could use on ffmpeg to detect this, or alternatively, a switch that would tell ffmpeg to be more aggressive in its consumption of resources?

Is mencoder better?  I've never used it, and I'm not sure my mplayer/mencoder build can even make an uncompressed audio file.

Is there a better-suited program for the audio conversion(wmv/asf to wav) task? 

Is there a better-suited program for my overall objective?  I want to record blocks of Sirius radio, review them, extract songs I like, and encode them as MP3 files.  Currently I'm using Sipie with the recordsirius.py script.

Any help or ideas would be greatly appreciated.

---

### Post by aws910 on 2008-09-16
bump. Might be a memory issue.  Some more info, taken while processing the file:
cat /proc/meminfo:
```
MemTotal:      3088280 kB
MemFree:        127016 kB
Buffers:         17540 kB
Cached:        2189716 kB
SwapCached:          0 kB
Active:         852128 kB
Inactive:      2010580 kB
HighTotal:     2208588 kB
HighFree:         7200 kB
LowTotal:       879692 kB
LowFree:        119816 kB
SwapTotal:     8193140 kB
SwapFree:      8193140 kB
Dirty:           81128 kB
Writeback:          56 kB
AnonPages:      655452 kB
Mapped:         133900 kB
Slab:            59136 kB
SReclaimable:    42752 kB
SUnreclaim:      16384 kB
PageTables:       3580 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   9737280 kB
Committed_AS:  1529576 kB
VmallocTotal:   114680 kB
VmallocUsed:     50452 kB
VmallocChunk:    61428 kB

``` 

free:
```
             total       used       free     shared    buffers     cached
Mem:       3088280    2965400     122880          0      17664    2193132
-/+ buffers/cache:     754604    2333676
Swap:      8193140          0    8193140

```

Should I be concerned that it's not using the swapfile?  It still says it has 122880 ram free.  My machine has 4gb ram, but it seems that the process to enable the last 1gb of ram is pretty hairy - I've never recompiled my kernel before, and this is my dev machine for work... All my coworkers use osx on their mac, and I know they're just waiting for me to mess up my system so they can laugh at me!

---

