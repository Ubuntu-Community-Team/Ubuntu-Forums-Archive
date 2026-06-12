---
title: "Is Framebuffer being used by Xserver?"
date: 2008-05-15
forum: Multimedia Software
---

### Post by vicky.irobot on 2008-05-15
Hi,

Is Framebuffer being used by X-Server for display or framebuffer is something that is only used for embedded targets?

If not using framebuffer then how does the graphics driver communicates with the kernel? Does it use any other subsystem?

I did a cat /proc/devices and I find fb is to be registered. In lsmod I see fbcon, video. 

Can any one explain the connection between the graphics and the fb subsystem. Currently I have not enabled the nvidia proprietary graphics card on my system and so I am guessing that it is using a generic driver.

---

