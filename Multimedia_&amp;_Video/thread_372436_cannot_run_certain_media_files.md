---
title: "cannot run certain media files"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by zumbi77 on 2007-02-28
Hi

I've installed the codecs, following the advice given at ubuntuguide.org. Mostly it works fine, but there are some files that just won't play. For example the videos at viftv.no

Can't figure this out, but I'm wondering if I have to adjust some settings in firefox so the mplayer plugin is set to play these files (I'm guessing they are wmv9).

Advice would be much appreciated.

---

### Post by Daveth on 2007-03-01
try playing them using Totem. version 2.16.2 claims to have sorted playback of this media type. See

[http://pkgsrc.se/multimedia/totem](http://pkgsrc.se/multimedia/totem)

for the changelog.

---

### Post by panch0 on 2007-03-02
MPlayer needs a -playlist option to play .asx files. In KPlayer, open File Properties and set Playlist to Yes in the General section.

---

