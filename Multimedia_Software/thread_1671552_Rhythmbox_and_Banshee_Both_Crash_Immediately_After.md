---
title: "Rhythmbox and Banshee Both Crash Immediately After Playing Song"
date: 2011-01-20
forum: Multimedia Software
---

### Post by spuzzdawg on 2011-01-20
Both Banshee and Rhythmbox crash, leaving a segmentation fault in the terminal, after playing a song for less than a second. I do manage to get some sound before they crash. This problem seems to have begun only a couple of days ago after doing an update. Unfortunately I was playing playing around with moving my music collection to an NFS share around the same time as the update so I can't be sure which action it was that broke music playback.

Because both Banshee and Rhythymbox are affected and showing identical behaviour I think the problem is gstreamer. Reinstalling everything I could find in synaptic related to gstreamer had no effect. 

Some general information:
- My music collection is in FLAC but other formats seem to cause the same behaviour.
- Music from an NFS share or my external USB drive causes the same behaviour
- VLC plays music from my NFS share without any problems
- Removing ubuntu-one (as suggested in some posts) did not help
- I'm using Ubuntu Desktop 10.10 x86

I've had no luck searching the interwebs for help thus far. Does anyone have any ideas?

---

### Post by spuzzdawg on 2011-01-21
I got Rhythmbox to play music without crashing by disabling certain plugins. I'm not sure exactly which plugin is responsible because disabling all plugins will cause rythymbox to play reliably but enabling individual plugins will not cause rythymbox to crash reliably. I suspect that there may be a bug relating to how multiple plugins interact.

Banshee continued to crash after rythymbox plugins were disabled. As I never use banshee anyway I just uninstalled it.

---

### Post by spuzzdawg on 2011-01-23
I think I partially solved this one by following this thread [http://ubuntuforums.org/showthread.php?t=1513987](http://ubuntuforums.org/showthread.php?t=1513987).

I did a complete uninstall including config files using synaptic. With the find grep rhythm command from the mentioned thread I found all rythymbox files still remaining and deleted them. Rythymbox plays music from NFS share without crashing whilst default plugins are on. 

Rhythmbox still crashes with a CD in the drive or when selecting an internet radio station. Maybe one day I'll get rhythmbox working 100%

---

