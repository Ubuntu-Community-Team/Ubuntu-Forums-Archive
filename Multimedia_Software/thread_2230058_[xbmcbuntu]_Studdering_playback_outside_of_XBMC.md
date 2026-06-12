---
title: "[xbmcbuntu] Studdering playback outside of XBMC"
date: 2014-06-17
forum: Multimedia Software
---

### Post by junkyhlm on 2014-06-17
I have some problems with audio outside of XBMC.
I have a simple script that starts Spotify that i have as a shoutcut in XBMC.
```
#!/bin/bashopenbox &
spotify
#$1
killall -9 openbox
```

Now when listening to music after some time the audio starts to studder really bad. It returns to normal when pausing/playing again but only for a short while.
Could someone give me some pointers on this?

I really dont know what logs to check. I have done "tail -f /var/log/*.log" when running spotify but i cant see anything.

---

