---
title: "Sound does not work without headphones"
date: 2008-07-31
forum: Multimedia Software
---

### Post by itsjareds on 2008-07-31
My sound doesn't work without headphones. I don't use speakers, I just use the basic in-the-computer speakers. The sound doesn't work with nothing plugged in, but when I plug in my headphones, I can hear music.

But there's also another problem -- when I have the headphones in and turn the volume to "mute", it doesn't mute.

Any help?

---

### Post by Yellow Pasque on 2008-07-31
Sounds like a jack sensing problem. This could be caused by a bug in ALSA or just not having alsa-base configured correctly. See [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by itsjareds on 2008-08-01
I found out why it was going through the headphones: seems to be a bug where I mute it using the system tray icon, but it doesn't mute the master volume. I double clicked the icon and it brought up the manager, and Master wasn't muted. Also, if I do mute it, then try to scroll up the Master, it stays muted.

---

