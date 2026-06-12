---
title: "[SOLVED] Odd video error"
date: 2008-10-21
forum: Multimedia Software
---

### Post by RJWEcology on 2008-10-21
I'm not sure why, but when I try to watch any video on my desktop (or system) the video player loads (I've used VLC, Totem, MPlayer, SMPlayer etc) and then crashes to this screen:

[http://i472.photobucket.com/albums/rr83/RJWEcology/error.jpg](http://i472.photobucket.com/albums/rr83/RJWEcology/error.jpg)

Can anyone help me with this? It's never happened before and it's really irritating. 

Thanks,

Rich

---

### Post by rvm4000 on 2008-10-21
It seems your X session is closed (crashed maybe). Probably because of a bug in your graphic card driver.

You could try to set the video output to "x11" in the players, I don't think that could cause any crash, although it won't have any kind of hardware acceleration, so it will be slow.

---

### Post by RJWEcology on 2008-10-22
I've upgraded to the beta 8.10 and it's fixed now.

---

