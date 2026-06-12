---
title: "VLC shutdown problem"
date: 2020-11-05
forum: Multimedia Software
---

### Post by dagring on 2020-11-05
I run Ubuntu on Raspberry Pi 4 B. The program runs smoothly, but when I try to shut it down either by closing the player window or use the quit command, an instance of vlc are still running and I cannot open a new window of VLC. I have to run ```
killall -9 vlc
``` to shut it down.

I have tried to reinstall VLC, but the same pattern.

Have anybody experienced this, and how can it be fixed?

Dag R

---

### Post by hk42 on 2020-11-07
Same thing on Ubuntu +Intel PC. 
Partial solution is to pause or stop video playback before closing VLC.
Kaffeine is also affected.

---

### Post by dagring on 2020-11-07
OK. Good to hear it's not only me experiencing this. Hopeful an update will fix this.

Dag R

---

