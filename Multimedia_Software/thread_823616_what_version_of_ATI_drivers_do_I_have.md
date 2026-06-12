---
title: "what version of ATI drivers do I have?"
date: 2008-06-09
forum: Multimedia Software
---

### Post by Barky on 2008-06-09
hey all,

I've been trying to see what version of my ati driver I have to see if I should update. Most games have run like garbage so far (low, low fps on any close to recent game like nexuiz, ET:QW, savage 2, say 5-15 fps, but fine on older games like warsow and tremulous). using fglrxinfo, I've been told that the version should be next to the number after "OpenGL version String: " (like this: OpenGL version string: x.xx.xxx (xx.xx.xx)) in parenthesis. On mine though, there is nothing after the OpenGL version string number so I can't tell what version drivers I'm running (like this: OpenGL version string: x.xx.xxx). If anybody could help me out I would appreciate it. Just for the record: I do have the proprietary drivers enabled through the hardware drivers setting. running ubuntu 8.04.

system specs:

Athlon xp x2 3800+, ati radeon 1800xt 256mb, 1 gig pc3200 ram

---

### Post by sim-value on 2008-06-09
The version in the repotaire is 8.3 the recent one is 8.5

---

### Post by frekja on 2008-06-10
I have this problem as well - fglrxinfo doesn't give the driver version, just the OpenGL version. I used EnvyNG to install newer ATI drivers (I have a Mobility Radeon 9700) and it installed the ATI catalyst control panel into my applications menu, which shows the driver number (8.47.3). I checked the launcher, and you can apparently use **amdcccle** to get to it. Hope this helps.

---

