---
title: "Issues with playing DVD to completion"
date: 2008-05-20
forum: Multimedia Software
---

### Post by richardjones on 2008-05-20
I'm using Hardy on a Home Theatre PC with a Lite-On or Sony ATA DVD drive. I use kaffeine with the xine back-end to actually play media.

Most DVDs play fine.

I have a couple of DVDs that don't play at all (but I was able to rip and transcode them so we can still play the content).

Then there's the third category, the reason for this post. Some DVDs play until about 1/2 to 3/4 of the way through when they just stop, and kaffeine throws up an error:

[INDENT][B]The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (Expected NAV packet but none found.)[/B][/INDENT]

Sometimes the error is "Invalid NAV packet", IIRC.

I've tried replacing the DVD drive (as mentioned above, two manufacturers), and I've tried playing the DVDs in other computers, and the error still happens.

I even tried playing the DVD under Windows using VLC (which uses the same low-level libdvdread etc. libraries). Same error.

The disks play fine in an off-the-shelf DVD player.

There doesn't seem to have been any traffic in the Ogle mailing lists (the source of the libdvdread library) for a couple of years, so I can only assume that this is a ... somewhat isolated problem, even though I get the same error wherever I try to play the disk.

Any thoughts?

---

