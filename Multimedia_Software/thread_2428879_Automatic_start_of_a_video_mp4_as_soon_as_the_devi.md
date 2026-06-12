---
title: "Automatic start of a video mp4 as soon as the device is switched on"
date: 2019-10-10
forum: Multimedia Software
---

### Post by formadigimar on 2019-10-10
Hello, I want to perform an automatic start of a video mp4 from power on the device.

This video must be in full screen, in infinite repeat mode and also in kiosk mode

My Ubuntu is version Ubuntu 18.04 LTS.

Best regards,

---

### Post by TheFu on 2019-10-10
I've never done this, but I wouldn't use Ubuntu for a 1-trick pony like this.  I'd use a custom variant of TinyCore with mpv loaded, then setup autologin and have mp4 load the video and run it over and over and over in a loop.  TinyCore is 16MB, not 800MB and doesn't come with hacker-friendly tools like any Ubuntu would.

With mpv, you can disable all keyboard input, except a specific 1 that you control to quit.  All other attempts to interrupt the process can be caught to avoid the <cntl>-c breakout to a prompt.

And if you wanted cheaper hardware, a Raspberry Pi v3 would make a much cheaper solution and easily handles 1080i. If you need 4K, a pi-v4 does that.  About $45.

---

