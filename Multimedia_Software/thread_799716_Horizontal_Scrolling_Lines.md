---
title: "Horizontal Scrolling Lines"
date: 2008-05-19
forum: Multimedia Software
---

### Post by gedreosan on 2008-05-19
I installed Hardy on one of my desktops today and it's giving me a bit of a video issue.  I've got horizontal lines that are constantly scrolling rapidly down the screen.  If there's a big spot of one colour they're hard to notice, but when they pass along contrasting areas, say at the edge of a window they're really noticeable.  I've tried adjusting the refresh rate on the monitor, an HP w19e 19" widescreen LCD.  I've also tried using the nvidia restricted drivers and tried not using them.  The motherboard has a built-in nvidia GeForce 6150SE nForce 430.

---

### Post by hermes0710 on 2008-05-19
Enable sync2vblank through nvidia-settings (run as root)

---

### Post by gedreosan on 2008-05-19
I found "sync to vblank" and "sync to vblank on display device" under x server xvideo settings and "sync to vblank" under opengl settings.  Sync to vblank under x server was already checked so I checked the other two and it takes that change.  I can close and reopen nvidia settings and it shows all three checked.  But the lines are still there and if I log out or reboot, it goes back to just having sync to vblank under x server checked.

---

### Post by hermes0710 on 2008-05-19
You should set these settings with root privileges:
 Open a terminal and execute:
  ```
gksudo nvidia-settings
```

---

### Post by gedreosan on 2008-05-19
Okay, so the settings did stay this time:), but the horizontal lines are still there scrolling away:(.

---

