---
title: "Jerky video playback"
date: 2008-09-15
forum: Mythbuntu
---

### Post by Markus72 on 2008-09-15
Hi,

any ideas why I might expect jerky video playback using MythBuntu 8.04?

HW: Athlon64 3000+, 2GB RAM, Gforce 5600 (or so)...
(using the default nvidia driver)

It's only PAL videos, stereo sound, nothing special.
I had similar problems on my manually installed "old" ubuntu/mythtv installation but I could track it down to PCI timings...
But these do not affect the problem (made the same setup).

Using the top command I only see 40-60% CPU load (maximum quality settings), no iowait... 

Don't know where to dig deeper...

Any idea?

Help is highly appreciated

Thanks in advance.

Markus

PS: the vids were recorded using dvbt, so they should be mpeg2

---

### Post by Markus72 on 2008-09-18
Hi,

no idea?

M

---

### Post by anonymousdog on 2008-09-18
Is playback the same (jerkyness) using vlc or another media player?  Are files local or remote?  Do you have frontend and backend logs during playback?  Are you using the nv driver or the proprietary nvidia driver?

---

