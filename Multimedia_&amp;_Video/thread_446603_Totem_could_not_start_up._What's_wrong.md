---
title: "Totem could not start up. What's wrong?"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by sri1025 on 2007-05-17
I login and play a few songs. I exit Totem and if I try after some time, say 2 hours or so, I get the following error message:-

Totem could not start up.
Could not establish connection to sound server

But if I log off and login again, it works. What could be possibly wrong?

These are the console log messages when I tried to start totem:-
```
ALSA lib pcm_direct.c:222:(make_local_socket) connect failed: /tmp/alsa-dmix-8412-1179145085-47233: No such file or directory
ALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client
ALSA lib pcm_direct.c:222:(make_local_socket) connect failed: /tmp/alsa-dmix-8412-1179145085-47233: No such file or directory
ALSA lib pcm_dmix.c:851:(snd_pcm_dmix_open) unable to connect client

```

Any solution?

Thanks,
Srikanth

---

### Post by Jadd on 2007-05-30
I have exactly the same problem. The problem doesn't lie with Totem though, it lies with esd, Ubuntu's sound system. Type esd in a terminal and you'll get the same message.

---

### Post by sri1025 on 2007-05-30
So,

What's the solution? Please let us know.

---

