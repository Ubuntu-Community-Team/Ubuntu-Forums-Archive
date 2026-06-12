---
title: "Force Rhythmbox to use SPDIF"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Kjeldgaard on 2009-11-19
Hi

I recently upgrade to Karmic and now I don't get any sound when playing MP3s in Rhythmbox. My PC (Asrock ION 330) is connected to my receiver via SPDIF (optical). I have removed Pulsa Audio and only using ALSA. In Alsamixer all the channels are unmuted and set to max volume. And the sound works great in XBMC and Amarok. I won't use Amarok as this doesn't not recognise the shortcuts on my keyboard (Logitech DiNovo Edge).

My asound config file looks like
```
pcm.!default {

   type plug
   slave {
       pcm "iec958"
   }

}
```Does anybody know how to force Rhythmbox to use the SPDIF output or know a music player where you can use the SPDIF output and also recognise the shortcuts on my keyboard?
I prefer using Rhythmbox.

---

