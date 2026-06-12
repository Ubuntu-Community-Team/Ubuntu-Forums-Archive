---
title: "Sound only works on my guest account"
date: 2013-11-23
forum: Multimedia Software
---

### Post by Tyler_Aschenbrenner on 2013-11-23
I am running Ubuntu 13.10.  My sound has always been hit or miss but I can always fix it by running:
```

killall pulseaudio
sudo alsa force-reload
pulseaudio --start
```
That has worked fine until today. My battery ran out and shut the laptop down, I plugged it in and turned it back on but now sound will not come back on.

Sound settings shows that it is detecting my speakers, and alsa mixer shows that nothing is muted but still no sound. When I log out I hear the drum sound and sound works fine in my guest account.

Any idea how to fix this?

---

### Post by Tyler_Aschenbrenner on 2013-11-23
Well I fixed it by doing the thing that I should have tried in the first place. I turned it off and back on again.

---

