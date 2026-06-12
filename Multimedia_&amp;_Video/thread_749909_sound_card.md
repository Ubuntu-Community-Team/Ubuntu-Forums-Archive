---
title: "sound card"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by hashi856 on 2008-04-08
I'm running ubuntu 7.10, and have a sound blaster x-fi audio. The volume control gives me this message "No volume control GStreamer plugins and/or devices found". I dont get sound on firefox or DVDs or anything on my computer, except for pidgin. For some reason I get sound from pidgin. Is there a reason Pidgin would give me sound when nothing else will? Doesn't this mean that Linux recognizes my sound card? I've made a few other threads relating to this problem:

[http://ubuntuforums.org/showthread.php?t=747825](http://ubuntuforums.org/showthread.php?t=747825)
[http://ubuntuforums.org/showthread.php?t=747932](http://ubuntuforums.org/showthread.php?t=747932)
[http://ubuntuforums.org/showthread.php?t=745824](http://ubuntuforums.org/showthread.php?t=745824)

---

### Post by Metaljaz on 2008-04-11
Creative has linux drivers for 64bit systems. Read here:

[http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)

This thread may provide useful information:

[http://ubuntuforums.org/showthread.php?t=239981](http://ubuntuforums.org/showthread.php?t=239981)

---

### Post by deadgobby on 2008-04-11
if you have a sound card you may want to go into BIOS and disable on board sound devices. all sound should pump through the sound card. Or if you can go into the terminal and type in this command and post the reply back here.
aplay --list-devices 
Gobby

---

### Post by WoosterB on 2008-04-12
I have the same card.  Try this thread as it got mine to work:

[http://ubuntuforums.org/showthread.php?t=732512&highlight=Soundblaster](http://ubuntuforums.org/showthread.php?t=732512&highlight=Soundblaster)

-S

---

