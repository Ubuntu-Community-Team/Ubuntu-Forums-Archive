---
title: "DVD Playback problem (libdvdcss2 installed)"
date: 2008-12-07
forum: Multimedia Software
---

### Post by rybl on 2008-12-07
I am having problems playing DVD using tomtem-xine or any other media player for that matter.  I have libdvdcss2 libdvdread3 and libdvdnav4 and w32codecs installed from the mediabuntu repository.  When I try to play a DVD it gives me the following error.

> The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

I have the same setup on my desktop and everything works fine.  My laptop is a dell x1330 and I found another thread that said I should set the region code using regionset I did this and this is now the output of regionset.

```

regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE
```

Thanks in advance for the help

---

