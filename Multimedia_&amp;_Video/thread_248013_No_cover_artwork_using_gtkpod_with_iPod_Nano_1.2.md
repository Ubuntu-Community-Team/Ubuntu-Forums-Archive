---
title: "No cover artwork using gtkpod with iPod Nano 1.2"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by pertti on 2006-08-31
Hi! I've been using gtkpod for transfering music to my iPod Nano. So far it has worked pretty well, with the exception of album artwork.

Since I updated the firmware of my iPod to v1.2, gtkpod fails to write the album artwork with this warning:

```
Failed to save /media/ipod/iPod_Control/Artwork/ArtworkDB
```

Still, gtkpod shows the cover art in the track details, even after disconnecting and reconnecting the iPod.As far as I remember, this worked properly before updating the firmware (I had to update it on day two since I messed it using Rhythmbox from CVS :rolleyes:).

I've also tried Amarok 1.4.1 and 1.4.2, but this doesn't work either.

Any ideas on this? Is there any problem with firmware 1.2? Should I/is possible to go back to 1.1?

Thanks in advance!

---

### Post by OmahaVike on 2007-12-08
i just ran into that problem as well.  here's how i got around it:

(with ipod unplugged)
```

sudo mkdir /media/ipod

```

pointed gtkpod to this directory (edit -> edit preferences -> iPod mount point : /media/ipod)

hit the sync button and let it work its magic.  no errors.

then, plugged in the ipod and saw that it mounted automatically at /media/ipod-1.   manually copied over the files.
```

sudo cp -R /media/ipod/iPod_Control/* /media/ipod-1/iPod_Control/ 

```

voila!

hope this helps sombody out.  pease post here if you find alternative approaches.  thanks!

---

