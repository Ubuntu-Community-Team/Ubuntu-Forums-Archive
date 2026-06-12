---
title: "w32 codec seems to have killed my audio"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by tokyo on 2006-12-09
i was searching around for a fix for playing .wmv files when i stumbled upon this

[https://help.ubuntu.com/community/RestrictedFormats#w32codecs](https://help.ubuntu.com/community/RestrictedFormats#w32codecs)

after following the directions:

> 
wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb


everything was working fine for about 5 minutes, then i noticed that the audio track to the video i was viewing cut out.  i thought it was just the file, so i went to a few audio players to see if the rest of the sound was out, turns out, any mp3 i attempted to play came out as silence.

i rebooted my computer, hoping it was a fluke, but no start up jingle, and still no audio playback.

when i adjust the volume very quickly up and down, i can hear the static in the line from it adjusting, so i know it's not my speakers.

if anyone has help or can point me in a better direction, it would be appreciated.

-cheers

---

### Post by tokyo on 2006-12-10
i found a fix for this, just in case anyone else has tried to install w32 drivers and run into the same issue i'll tell you what happened.

turns out the PCM volume was muted (by default PCM does not show in the volume control, you have to enable it in the preferences) when i installed the w32 drivers and started watching .wmv files.  

i have no idea how or why this came about as an issue, but if you run into this, make sure you check ALL the volume levels.

---

