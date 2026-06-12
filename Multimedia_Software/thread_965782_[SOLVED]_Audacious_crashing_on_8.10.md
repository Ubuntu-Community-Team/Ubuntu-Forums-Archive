---
title: "[SOLVED] Audacious crashing on 8.10"
date: 2008-10-31
forum: Multimedia Software
---

### Post by johnnybirdman on 2008-10-31
When i try to open some .pls or .m3u streams I get the following error using Audacious.  I'm running ubuntu 8.10 on one machine and xubutnu 8.10 on another and get the errors.  Here is a sample of the error:
```
ERROR: neon: neon.c:1084 (neon_aud_vfs_fread_impl): <0x1a15ec0> Buffer still underrun, fatal.
ERROR: neon: neon.c:1300 (neon_aud_vfs_fseek_impl): <0x1a15ec0> Can not seek before start of stream
ERROR: neon: neon.c:1084 (neon_aud_vfs_fread_impl): <0x1a15ec0> Buffer still underrun, fatal.
ERROR: neon: neon.c:1084 (neon_aud_vfs_fread_impl): <0x1a15ec0> Buffer still underrun, fatal.
ERROR: neon: neon.c:1084 (neon_aud_vfs_fread_impl): <0x1a15ec0> Buffer still underrun, fatal.
ERROR: neon: neon.c:1084 (neon_aud_vfs_fread_impl): <0x1be6800> Buffer still underrun, fatal.

```
Anyone else have this or know of a fix?  
Should I post a bug?

Thanks,
J.

EDIT: solved by using something other than Audacious...

---

### Post by JvdS45 on 2008-11-04
audacious
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
id3_file_vfsopen: file failed
id3_file_vfsopen: file failed
id3_file_vfsopen: file failed

so thats mine :| what happend with this in 8.10 :|

---

### Post by johnnybirdman on 2008-11-04
I don't know what happened with this in 8.10, but I have to admit I was also having issues (not necessarily the same issues) in 8.04 and just resorted to VLC as a temporary fix.  

However, after posting this I found this [[COLOR="DarkOrange"]post here[/COLOR]]("http://ampache.org/forums/t2117-Easy-question-want-Audacious.html") where it is recommended not to use audacious.

My error in the OP came about as I was trying to play music from my [COLOR="DarkOrange"][ampache ]("http://www.ampache.org")[/COLOR]server (awesome software by the by), but if it's 'harmful/disruptive' I'm going to move to something else.  Maybe have to finally figure out how xmms2 works.  Always liked xmms anyway.
J.

---

