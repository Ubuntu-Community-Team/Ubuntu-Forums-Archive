---
title: "totem segmentation fault on real media files"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by Nikusan on 2007-05-05
Hi all,

Totem is segfaulting when I try to play .rm files. These very same videos have played fine in totem in previous Ubuntu versions (dapper was the last that could play them if I recall correctly).

I have w32codecs and all the gstreamer plugins installed fine (including gstreamer0.10-pitfdll). VLC also chokes on the same files. Mplayer plays them fine. This is strange because mplayer and gstreamer use the same binary real video codecs from w32codecs? Correct me on that if I'm wrong.

I'm not keen on installing real player, and I'm not a huge fan of mplayer's user interface. Does anyone know what's going on?

---

### Post by Martin Aulbach on 2007-05-06
Are you using SCIM as the default input method? (If you don't know SCIM, you probably don't) RealPlayer aborts with a segmentation fault if I don't deactivate SCIM by means of an environment variable before launching.

---

