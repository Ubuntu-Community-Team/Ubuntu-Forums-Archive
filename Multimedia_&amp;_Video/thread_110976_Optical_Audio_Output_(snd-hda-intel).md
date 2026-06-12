---
title: "Optical Audio Output (snd-hda-intel)"
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by polt on 2006-01-01
The digital optical output supplied on many newer Intel motherboards, including the Intel 945PVS, is not yet supported by the ALSA driver available with "Breezy Badger" or its recent updates. Also not supported is Dolby Digital output. The optical output is also know as IEC958 or S/PDIF or TosLink.

If you are using the snd-hda-intel driver, then you probably do not have support for any kind of digital output. This means you cannot hear the Dolby 7.1 or 5.1 sound coming out of your DVDs.

If you are planning on using any kind of optical or digital output with Ubuntu and ALSA, then check carefully to see if it is supported. You can get lots of authoritative information at [alsa-project.org]("http://alsa-project.org").

---

### Post by adrianhensler on 2006-01-10
Hi,

Thanks for that snd-hda-intel. That helped me get my Abit ic7-G's optical out working... mostly. 

Hopefully someone can help with this one; mplayer song.mp3 pipes the audio through the optical out; I can't figure out how to get Mythtv (or the music plugin) to work through the optical output.

One gigantic virtual ham to whoever has any valid suggestions.

ps: don't think I'm beyond even the most basic suggestions.

Thanks.....

---

