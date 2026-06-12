---
title: "PulseAudio jumpy on system start"
date: 2009-06-26
forum: Multimedia Software
---

### Post by CatKiller on 2009-06-26
When I first start the computer, sound through PulseAudio is jumpy. It skips every couple of seconds using Amarok. But if I use ```
pulseaudio --start &
``` to stop the running daemon and start another, it's fine. I haven't been able to find where PulseAudio gets started from to check whether the command-line parameters there are different from those specified in pulse-daemon.conf. Any pointers would be really helpful.

I'm using Jaunty. The pulseaudio process in top doesn't go above 12% whether it's started automatically or manually.

---

### Post by CatKiller on 2009-06-27
Any thoughts?

---

### Post by CatKiller on 2009-07-05
Oh well. For the time being, I've put ```
pulseaudio -k && pulseaudio -D
``` in my Startup settings. It's a hideous hack, though. I'd much rather get this configured properly.

---

### Post by CatKiller on 2009-07-07
Removing

pactl load-module module-x11-xsmp

from the startup applications seems to have helped. I have no idea what it's for.

Thanks for the help guys.

---

