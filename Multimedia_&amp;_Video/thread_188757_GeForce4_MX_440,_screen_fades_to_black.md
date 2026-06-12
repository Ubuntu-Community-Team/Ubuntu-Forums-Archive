---
title: "GeForce4 MX 440, screen fades to black"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by dotMatt on 2006-06-04
Using the nvidia driver (from the "restricted modules") for my GeForce4 MX 440 on  Dapper, 2.6.15-23-k7.

When playing games that use 3D acceleration (X-moto, Tux Racer, Globulation, etc), my screen will occasionally fade to black (gradual fade, takes about 10 seconds from start to complete black).  Pressing ctl-alt-F1 to switch to a VT, then ctl-alt-f7 to come back, brings the game back at full brightness.

Any thoughts?

Thanks all,
dotMatt

---

### Post by disturbed1 on 2006-06-04
Adjust your screen saver settings. Somewhere between the game and your desktop manager there is a mis communication. The game took over the screen, but the manager doesn't know that the mouse is still moving.

---

### Post by dotMatt on 2006-06-04
As opposed to simply disabling the screensaver, how do I fix the problem?

---

### Post by KillerBOB on 2006-08-29
I have the same problem with xmoto. Does anyone have a solution for this?

---

### Post by tseliot on 2006-08-29
> **dotMatt said:**
> Using the nvidia driver (from the "restricted modules") for my GeForce4 MX 440 on  Dapper, 2.6.15-23-k7.

When playing games that use 3D acceleration (X-moto, Tux Racer, Globulation, etc), my screen will occasionally fade to black (gradual fade, takes about 10 seconds from start to complete black).  Pressing ctl-alt-F1 to switch to a VT, then ctl-alt-f7 to come back, brings the game back at full brightness.

Any thoughts?

Thanks all,
dotMatt
Does the display go into standby too? Or does it just become black?

---

### Post by KillerBOB on 2006-08-29
For me it is the screensaver that kicks in (it's set to 10 min, which is default I think). Obviously I can disable the screensaver each time I plan to play xmoto, but it's a hassle to remember to enable it.

---

