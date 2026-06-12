---
title: "Multiple backends - proper HDHomeRun tuner setup?"
date: 2011-10-01
forum: Mythbuntu
---

### Post by AbMagFab on 2011-10-01
I've been banging my head against a wall all day today.

I started with a standard setup:
- One backend
- 3 front ends
- 2 HD Home Run (OTA only)
- 1 HD Home Run Prime (FIOS)
- Full gigabit network

It all works great, but I wanted to spread the load across a couple of back ends, and I had a spare machine lying around.

So, first thing I did:
- Make it a secondary back end
- See what happens

And basically nothing happened, except commercial skip jobs started spreading across the two back ends.  Nothing was being stored in the new storage space, although MythWeb reported it as being available (and empty).

I let that all run for a couple days, and today decided to try something else, and ended up with (after lots of other failed tries):
- I put one HD Home Run tuner and one HD Home Run Prime tuner on the second back end
- I cross-mounted (NFS) the media directories across both backends
- I defined both directory sets on the main backend

The end result is that everything pre-recorded works, and new recordings work (at least the ones on the primary back-end), but I can't watch LiveTV on any FE, or even a FE running on the BE.  On the dedicated FEs, I get an error saying the IP might be wrong, on the FE/BE it just flashes the menu really quickly.

So I have:
BE-Primary, /media/myth1, nfs:/media/myth2, HDHR1-0, 1-1, 2-0, 3-0, 3-1
BE-Secondary, /media/myth2, nfs:/media/myth1, HDHR2-1, 3-2

Storage Directories defined only on primary, and all with 2 entries of /media/myth1/* and /media/myth2/* (one for each type, e.g. recordings, coverart, etc.)

As soon as I put all the HDHR tuners on the primary backend and remove them from the secondary backend, everything works again and I can watch LiveTV from anywhere.

Any thoughts?

---

