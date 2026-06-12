---
title: "Sound fix for those having trouble after update to 9.04"
date: 2009-09-23
forum: Multimedia Software
---

### Post by thirtysixbelow on 2009-09-23
I recently updated to 9.04 (not a fresh install) and I lost audio. When trying to diagnose the problem it seemed it could no longer detect my soundcard or any devices related to sound. For some reason though if I ran commands such as aplay as sudo it would detect my soundcard devices. Being that it seemed to be permissions related I was able to track down the simple fix of adding myself to the audio group. I was looking through very complicated solutions and it ended up being the easiest one that fixed it. I just wanted this to be out there again for others. If aplay -l doesn't detect your soundcard but sudo aplay -l does just sudo addgroup [username] audio and reboot.

---

