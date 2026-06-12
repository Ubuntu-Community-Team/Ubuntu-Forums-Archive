---
title: "Why don't I see /dev/video0 (a webcam) in remote sessions."
date: 2010-03-17
forum: Multimedia Software
---

### Post by sadohert on 2010-03-17
I'm happy to poke around and find the answers that I need but I'm at a bit of a loss for what to look for next.  20 minutes ago I was at home in a local session and I could work with my webcam through /dev/video0 device node.  Now I'm at work in a remote session and that device node file isn't listed.  I *think* this is a udev or sysfs related thing, but I can't seem to find any information to draw a connection between those subsystems and the whole "local session" angle to my problem.

Does anyone have any tips on whats going on here?  I can see why we might not want remote users to just monkey around with a webcam willy nilly, but there MUST be a way to circumvent that restriction.

Thanks

Stu

---

### Post by no2498 on 2010-03-18
not sure this will help
do you have gstreamer installed on both computers
you can find it in add/remove
hope it helps

---

### Post by sadohert on 2010-03-19
So, it turned out the issue was my webcam is  built into my monitor, and my monitor is set to suspend after 10 minutes. When the monitor suspends it also shuts the webcam down, which was making the device disappear.

Sneaky bugger.

---

