---
title: "Watching Flash movies"
date: 2009-02-11
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-11
Hi All

I have just tried to watch a TV programme from Channel 5's website via their on demand service. This seems to make use of Flash player to work.

I managed to install Flash successfully, although I'm using 64 bit Mythbuntu and the 64 bit Flash for Linux seems to be an alpha version, which is probably worth noting.

I did all this in the Ubuntu desktop, not in MythTV.

I was able to watch the picture, but there was no sound. I don't think this is a Flash player problem, because I can't get any sound in Mplayer opened through the Ubuntu desktop either.

The sound works just fine through the MythTV front end. However, it initially didn't work. My speakers are connected via a S/PDIF connection, and to get the sound to work with MythTV I found a setting somewhere in the setup screens where I had to change the sound option from whatever it had originally been to "alsa-spdif", and then it worked.

Presumably somewhere there is an equivalent setting that tells the rest of the system, not just MythTV, to use the S/PDIF connection. Any idea where I might find it?

Or alternatively, is it possible to watch TV programmes from a website using Flash player through the MythTV front end (which would probably be more convenient anyway)?

Thanks
NM

---

### Post by nickrout on 2009-02-11
mplayer -ao alsa:device=spdif ...etc

But as for the general system, I dunno.

---

