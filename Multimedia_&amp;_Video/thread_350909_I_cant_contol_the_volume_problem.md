---
title: "I cant contol the volume problem"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by Mba7eth on 2007-02-01
Hi guys, On my box i have VLC, mplayer, xmms and i can play them as i really wish with no problem at all. But once i start the realplayer i have to : 
1. stop everyother sound application currently using the sound card. 
2. i can't control the volume at all in the system, even from realplayer itself. If i mute the sound from realyplayer and from the os, i still can hear sounds and music playing ?

---

### Post by pseudonym on 2007-02-01
It could be that the ALSA [dmix]("http://alsa.opensrc.org/Dmix") plugin (to enable multiple sound streams) doesn't work well for your soundcard. I know it doesn't on mine. Since overriding the default ALSA configuration with an ~/.asoundrc file I haven't had any problems. The one I use is this excellent version from the [Myth TV Howto]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly") .

Also, any application which has an option to set the volume control from within it (as opposed to using just the ALSA mixer) should be set to do so. If not, some apps can mute your PCM unexpectedly (like xine and xmms).

---

### Post by Mba7eth on 2007-02-01
once i got home i'll check ...... Thanks anyway :)

---

