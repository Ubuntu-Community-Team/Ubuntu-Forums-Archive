---
title: "Mplayer error video_out (-vo) device"
date: 2010-04-26
forum: Multimedia Software
---

### Post by herojig on 2010-04-26
First time caller here with mplayer "error opening/initializing the selected video_out (-vo) device" and wondering where to start. all the codecs have been installed that I can think of. trying to smooth out DVD play but it's getting worse the more that add to the initial install of ubuntu 9. but i can't get smooth play in winxp which is also on this box as a dual boot, so perhaps my logic that linux was lighter and will work is wrong in this case. thx!

---

### Post by andrew.46 on 2010-04-26
Hi herojig,

> **herojig said:**
> First time caller here with mplayer "error opening/initializing the selected video_out (-vo) device" and wondering where to start.

An excellent start is to install a decent front-end for MPLayer by running the following in a terminal:

```
sudo apt-get install smplayer
```

and then changing the video out device in the SMPlayer preferences:

Options --> Preferences --> General --> Video --> Output Driver

When you are there select something like gl or x11 and see if this gets around the problem.

All the best,

Andrew

---

