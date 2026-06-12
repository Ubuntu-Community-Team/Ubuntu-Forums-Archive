---
title: "A64/NV6800gs display issues"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by InThane on 2006-01-04
I recently picked up a [nice little box]("http://z.iwethey.org/forums/render/content/show?contentid=239669").  Windows runs on it just fine; thought I'd throw Ubuntu on it and see how that runs.  **I should also mention that there is a PCHDTV 3000 card in there as well.**

The following is using Breezy Badger, 5.10.

After figuring out which network port was actually supported out of the box, the installation proceeded without any difficulties.  Machine finishes installing packages, then reboots for first startup.  Initializes the display and...

Garbage.  I'm not talking "refresh rate is broken" - I'm talking the display has the x and the y down, but all I'm getting is a bizzare patterned bitmap.

Take a look at the disk I'm using, and notice that it's the i86 version.  Go grab the AMD64 version, install that, exact same behavior occurs again.  Boot into recovery mode, apt-get update, apt-get upgrade.  Reboot, same thing all over again.  Unfortunately, this is the end of my Linux knowledge as far as troubleshooting goes. :P

I'm going to take a Debian disk home with me today and see if that works, but just wanted to see if anybody had any immediate insights, or if a specific logfile might help diagnose what is going on.  Note: I haven't installed NVidia's proprietary drivers yet.  Might try that.

---

### Post by InThane on 2006-01-05
And installing the NVidia proprietary drivers fixed the issue.

---

