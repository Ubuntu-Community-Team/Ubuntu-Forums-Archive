---
title: "Problem with playback - Audacious"
date: 2009-01-02
forum: Multimedia Software
---

### Post by OinkOink2 on 2009-01-02
Hi all,

I get the following message at terminal after running Audacious and trying to play a song that I've added to my playlist. The song is on my Windows partition, but the partition is mounted at boot and Exaile played the files fine. I suspect the line in green is the issue, but as I've never used Audacious before I don't know how to solve it.

```
:~$ audacious
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
[COLOR="Green"]MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin[/COLOR]
```


Any ideas?

Thanks.

EDIT: I'm also seeing this line too -
[CODE][COLOR="Green"](audacious:23139): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed[/COLOR][CODE]

---

### Post by elitenoobboy on 2009-01-03
Can it play other songs? What about other songs that are the ubuntu partition? From your post, it sounds like audacious can still play other songs.

---

### Post by OinkOink2 on 2009-01-03
> **elitenoobboy said:**
> Can it play other songs? What about other songs that are the ubuntu partition? From your post, it sounds like audacious can still play other songs.

What gave you that idea? I was hoping you were right...

Anybody else?

---

