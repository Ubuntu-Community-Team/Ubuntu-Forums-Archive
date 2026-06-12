---
title: "kernal options"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by andyp11 on 2006-06-29
Have I got this right?

I can set up the rt kernal as per the wiki, then simply decide which one to boot into from grub, the rt kernal for music stuff and the standard ubuntu one for a (slightly) more stable OS for normal stuff. No harm done even if the rt kernal updrade goes belly up.

Then all applications, music and otherwise, are available to both OS's albeit with differing performance efficiencies, or perhaps some apps have specific kernal dependencies?

What do folk think?

---

### Post by lunatic77 on 2006-06-29
Yes......I use different kernels from time to time without changing anything else in the system.  And it's always a good idea to keep previous, known-to-be-working kernels available in GRUB just in case...

---

### Post by dolson on 2006-06-30
That is absolutely correct. You're only changing the kernel, and the only apps that might not work with the -RT kernel are likely known and have specific kernel option or module requirements (VMware is one example).

I generally use the -RT kernel because I'm too lazy to reboot and pick the other ones, but you certainly can. GRUB will list all kernels installed by default on Ubuntu.

---

### Post by andyp11 on 2006-06-30
OK. Thanks to all. That's my next todo then.

---

