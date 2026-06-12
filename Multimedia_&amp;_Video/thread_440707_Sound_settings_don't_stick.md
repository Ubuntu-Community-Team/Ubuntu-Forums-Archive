---
title: "Sound settings don't stick"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by feffer on 2007-05-11
After upgrading to Fiesty, sound was not working. In Alsamixer, I muted the analog channel, and then sound worked normally. I also did ```
sudo alsactl store
``` to save my settings, but this didn't survive rebooting. This has always worked in the past on earlier Kubuntu and other distros. Anyone know why the settings don't stick?

I did search and read other Fiesty sound posts. There was one ( [http://ubuntuforums.org/showthread.php?t=418360&highlight=sound+muted](http://ubuntuforums.org/showthread.php?t=418360&highlight=sound+muted) ) concerning the .asoundrc file, but like one other poster, I don't have this file in my /home dir. My soundcard is a SoundBlaster and the alsa driver works fine once I mute the analog channel. Anyone know how I can get my settings to stick?

Thanks,
feffer

---

