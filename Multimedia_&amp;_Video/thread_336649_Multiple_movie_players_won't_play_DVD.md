---
title: "Multiple movie players won't play DVD"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by tripwire45 on 2007-01-11
I've tried totem, gxine, xine, mplayer kaffeine and xfmedia. All of them except mplayer and xfmedia think that the movie is only 14 seconds long and only play the intro (sony pictures). No other items are on the playlist. I've tried installing the latest codecs to no avail. Mplayer locks up when trying to play and xfmedia acts like nothing is there. 

I've Googled myself out but have yet to find an answer. Running Ubuntu 6.06. Any ideas?

Thanks.

---

### Post by ciscosurfer on 2007-01-11
> **tripwire45 said:**
> I've tried totem, gxine, xine, mplayer kaffeine and xfmedia. All of them except mplayer and xfmedia think that the movie is only 14 seconds long and only play the intro (sony pictures). No other items are on the playlist. I've tried installing the latest codecs to no avail. Mplayer locks up when trying to play and xfmedia acts like nothing is there. 

I've Googled myself out but have yet to find an answer. Running Ubuntu 6.06. Any ideas?

Thanks.If the DVDs are encrypted, to watch them you'll need to install libdvdcss2 (for other types of files, not DVD related, w32codecs are needed).

[Automatix2]("http://getautomatix.com") will take care of these both for you.

If you'd rather not bother with Automatix2, you can grab them both [here]("http://debian-mirrors.sdinet.de/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb") and [here]("http://debian-mirrors.sdinet.de/debian-multimedia/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb").  (DISCLAIMER: keep in mind the legality of these links before downloading).

---

### Post by tripwire45 on 2007-01-12
Thanks. I'll give it a shot. :)

---

### Post by tripwire45 on 2007-01-12
Worked like a charm, Ciscosurfer. Thanks. :)

-Trip

---

