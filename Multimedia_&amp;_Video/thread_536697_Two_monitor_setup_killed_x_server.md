---
title: "Two monitor setup killed x server"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by expertninja on 2007-08-28
I booted up ubuntu with a second monitor attached to the VGA out on my laptop (nvidia card). I had the second monitor off when I started it up, but the login screen was on the second monitor. I figured I would reboot without the monitor attached, but when I did X wouldn't start because of an "internal error"

What I have tried:
1. Starting X with the monitor attached
2. Using a backup xorg.conf that had previously worked
3. sudo dpkg-reconfigure -phigh xserver-xorg to go back to the original settings
None of these worked. Any ideas?

---

