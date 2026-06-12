---
title: "Updated 17-03-11 - Black screen on boot. (Intel i915)"
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Arabica Bean on 2011-03-18
Okay, I realised that I failed hard here. A few weeks back I got the  black screen on the live cd, so I left it alone until last week, where the daily live worked fine, so I upgraded to natty on my machine without any issues.

Last night I ran a dist-upgrade (I know, I know, shoot me!) and now I'm getting the black screen on boot. What's weird is, the screen is coming up fine, just the back-light is not powered on. (I can barely make out the login screen).  I know that this is not a hardware issue on my lappy as I've been booted into this live CD for a while now with no problems.

The only package that dist-upgrade removed was "simple-ccsm" so I'm at a loss as to why it's no longer showing.

I'll happily provide any necessary info if requested.

BTW, skimming the logs didn't yield that much. dmesg didn't report any errors that I could see.

I realise that there are issues with Nvidia cards, but I couldn't see much relevant info on the forum relating to Intel GPUs
Any steering in the general direction is greatly appreciated.

---

### Post by mfecteau on 2011-03-29
You may have a solution in this thread :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515246/comments/55](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515246/comments/55)
(check post #55)

Good luck

---

### Post by mfecteau on 2011-03-29
In fact, I had the same problem and the fix for me was to edit the grub file (/etc/defaults/grub), remove the "quiet" and the "splash" word, save the file, execute "update-grub" and restarting ...

---

