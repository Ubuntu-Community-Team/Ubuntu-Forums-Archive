---
title: "Mplayer 5.1 (ac3, a/52) sound with pulseaudio workaround"
date: 2008-05-21
forum: Multimedia Software
---

### Post by vprasaj on 2008-05-21
Current version in hardy won't play 5.1 sound. 
The problem is with the application, not the sound server.
Mplayer is a little faster for *.mkv files then totem. On older machines the difference is noticed.

What you have to do is to run mplayer like this:
```

gmplayer -ao pulse -channels 6
```

[**LINK**]("http://forums.fedoraforum.org/showthread.php?t=183339")

You can put a script in "/home/user/.gnome2/nautilus-scripts" for easy use.

Script:
```
#!/bin/bash
gmplayer -ao pulse -channels 6 $NAUTILUS_SCRIPT_SELECTED_URIS
```

It will open files that have names without spaces. (Rename properly if needed.)

BTW
For stuttering sound and other fixes with pulseaudio look at the link below.

[**LINK**]("http://ubuntuforums.org/showthread.php?t=789578")

I hope this helps to someone.

---

