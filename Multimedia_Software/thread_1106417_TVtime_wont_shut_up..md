---
title: "TVtime wont shut up."
date: 2009-03-25
forum: Multimedia Software
---

### Post by ant2ne on 2009-03-25
I closed TVtime, but I can still hear it. I cant shut it up.

---

### Post by lovinglinux on 2009-03-25
I'm not sure if this a solution, but you could try the command:

```
killall tvtime
```

If this  doesn't work, you could use this script to start tvtime:

```

#!/bin/bash

#raise the Line In volume
amixer -q set "Line" 80% unmute

#open the TV application and mute the Line In after closing it
tvtime && amixer -q set "Line" 0% mute
```

Presuming you get the tv card sound from "line in" input.

This is just a workaround, but will avoid the annoyance.

---

### Post by ant2ne on 2009-03-25
Actually, my overall goal is to use this computer as a myth back end. If the TV tuner needs the line in functional at all times then this maybe a constant annoyance.

---

### Post by lovinglinux on 2009-03-25
> **ant2ne said:**
> Actually, my overall goal is to use this computer as a myth back end. If the TV tuner needs the line in functional at all times then this maybe a constant annoyance.

Maybe you could try using alsa instead of pulseaudio in the sound preferences: System >> Preferences >> Sound

TVTime works great for me and it doesn't keep the audio running when closed. But this happened to me after playing flash videos, until I changed the sound preferences.

---

