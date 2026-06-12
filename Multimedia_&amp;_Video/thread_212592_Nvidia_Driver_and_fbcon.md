---
title: "Nvidia Driver and fbcon"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by MITService on 2006-07-10
Hi everybody!

I just installed Ubuntu on the laptop of my girlfriend. Everything worked fine until I installed the closed-source nvidia drivers.

When it boots up and starts gdm the display is totally disorted. Looks like a projection of one line to the whole screen - totally weird.

The problem is fbcon I think. The fbcon module gets automatically loaded.
xorg.conf is fine - the nvidia module too.
When I start up in recovery mode (single user) and start gdm by the init script X comes up just fine with hardware acceleration and all.
fbcon is not present here.

But when I do a normal startup fbcon is there and gdm freaks out. I tried to remove the splash parameter from the grub config file. No use - fbcon is still there.

Any pointers on where and why this gets loaded - and how I can prevent it from loading?
Thanks...

---

### Post by tseliot on 2006-07-10
Try this:

add "blacklist fbcon" to "/etc/modprobe.d/blacklist"

```
sudo echo "blacklist fbcon" >> /etc/modprobe.d/blacklist
```

WARNING: make sure you use ">>" and NOT only a single ">"

then reboot

---

### Post by MITService on 2006-07-15
Sorry for replying so slow.

Blacklisting the fbcon module did not work. I also blacklisted all modules depending on fbcon.

It is still loaded on startup and the x server's display is warped when using nvidia driver.

---

### Post by MITService on 2006-07-15
Ok, ignore my statement!
fbcon gets also loaded in single user mode (recovery).

Strange thing is: X works with nvidia closed source driver in single user mode - but it doesn't in normal bootup.
The only difference in the grub line is that normal bootup uses "quiet" instead of "single". But that should cause no problem.

So any idea what causes this to fail?
Should be some init script that doesn't get loaded in single user mode - right?
Any idea which one this might be?

---

