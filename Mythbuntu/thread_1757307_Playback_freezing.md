---
title: "Playback freezing"
date: 2011-05-13
forum: Mythbuntu
---

### Post by OxleyDave on 2011-05-13
I am experiencing freezing during playback. I have these messages in mythfrontend.log:
```

2011-05-13 19:37:53.550 ALSA, Error: Setting hardware audio buffer size to 6016
2011-05-13 19:37:53.550 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied.
2011-05-13 19:37:53.550 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2011-05-13 19:37:53.550 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely

```

Following the instructions and running 'echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc' does fix the playback freezing issues. However after reboot the prealloc value has gone back to 4096.

How do I persist this change across reboots or give mythfrontend permission to modify this file?

Cheers,
Dave.

---

### Post by klc5555 on 2011-05-13
Easiest way would seem to be adding the command to the /etc/rc.local file, which I believe runs after alsa has loaded, as it starts up as @S99 in /etc/rc5.d

In this case you'd presumably omit the word "sudo", since rc.local runs as root.

---

### Post by OxleyDave on 2011-05-13
I tried this yesterday and it didn't work. I've worked on it a bit more this morning and found that I needed to put a 'sleep 5' before the command in rc.local. Is there no alsa config file for initialising this setting? However it is now working so this can be considered solved. Thanks for the help :D

Cheers,
Dave.

---

