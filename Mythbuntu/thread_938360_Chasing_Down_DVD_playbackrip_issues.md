---
title: "Chasing Down DVD playback/rip issues"
date: 2008-10-04
forum: Mythbuntu
---

### Post by dsbw on 2008-10-04
OK, I've got Myth installed on my new box, thanks to folks here.

Now it's time to hunt down all the issues. [sigh]

I've noticed that DVD playback goes for a bit, then stops for a few seconds, then goes for a bit. I figured a bad DVD, so I tried ripping it.

The rip seemed to work but the DVD was not to be found in the video library. So I checked some settings and tried again with another DVD.

Same issue of the playback going for a bit, then hanging, then going for a bit. (The only continuous video I've gotten going is from MythStream.) So I decide to rip this one and see if there's data anywhere.

I flip to the command line, but don't find anything in the temp directory, but do find a file in the /var/lib/mythtv/videos$ directory: DVD_VR_001of.

But while this is going on, I'm getting errors every 10 seconds or so:

[ 1712.3489 ] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x28000000 action 0x2 frozen
[ 1712.#### ] ata3.00: irq_stat 0x08000000, interface fatal error
[ 1712.#### ] ataa3: SError: { Dispar BadCRC }
[ 1712.#### ] ata3.00 : cmd a0/01:00:00:00:fc/00:00:00:00:00/a0 tag 0 dma 12902 in
[ 1712.#### ] ata3.00: status { DRDY }

Crap. Bad hard drive? It's weird, though: All these parts worked before I switched to this new Abit mobo. (I've run the RAM check for days without turning up anything there.)

Now what?

---

### Post by dsbw on 2008-10-05
Bump. I've got rips working, though I'm still getting these errors while ripping.

SATA error?

Possibly related, a rip that I did yesterday tht worked is not working now. It shows up in the library, and before where I'd select it once to open and once to play move, when I select it to open, the screen just goes black. I can play it in VLC outside of MythTV.

---

### Post by dsbw on 2008-10-07
No. This error seems pretty serious. Anyone?

---

