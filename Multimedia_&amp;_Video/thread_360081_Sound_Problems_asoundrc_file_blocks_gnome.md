---
title: "Sound Problems: asoundrc file blocks gnome"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by MikeG12 on 2007-02-12
Hi,

i have a problem with my sound setup, when i create the .asoundrc with the following content:

pcm.!default {
    type plug
    slave.pcm "surround41"
    slave.channels 4
    route_policy duplicate
}

mpg321 stops working (giving me this error: "ALSA: underrun, at least 0ms.") and i can't login into gnome, it freezes, living me only the mouse pointer. I have to delete the .asoundrc file to login in gnome again.

With all other programs (totem, mplayer, xmms) the sound is fine and all my speakers work.

I have a soundblaster Audigy LE using the CA0106 driver.

Can anyone help me?

Thanks

---

