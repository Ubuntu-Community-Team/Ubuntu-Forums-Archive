---
title: "DLNA (Upnp) with MythVideo using wrong MIME"
date: 2011-08-03
forum: Mythbuntu
---

### Post by Adamal on 2011-08-03
I've been using mythbuntu now for 6 months.  I used it for recording OTA broadcasts.  I then watch them on my PS3, using the UPNP/DLNA built into mythtv .24.

I recently attempted to get it working with Videos.  I drop a couple, mp4 files I made with handbrake and scanned them in.  They show up fine in mythtv.  It was even able to grab the meta data from IMDB.  However when I tried to play them on my PS3 I received a corrupt video error.

I installed upnp inspector and it appears that the protocolInfo for these two videos is coming up as http-get:*:text/plain:DLNA.ORG_OP=01;DLNA.ORG_CI=0;DLNA.ORG_FLAGS=01500000000000000000000000000000.

Note the MIME type of "text/plain".  That should be "video/mp4".  It looks fine for all my recordings which are all in mpeg2 format.  Does anyone know how to force mythtv to set to correct MIME type?

---

