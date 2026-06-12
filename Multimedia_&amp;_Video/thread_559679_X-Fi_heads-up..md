---
title: "X-Fi heads-up."
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by Silent Warrior on 2007-09-25
Creative recently released some beta drivers (64-bit ONLY) for X-Fi. Hooray!

... Only, it won't install/compile. There are a number of problems with the installation (!) that I, for one, have been unable to get around. You're probably better off scanning the Creative-forums for clues.

Problem 1: The installer-file needs not one, but TWO modifications before it works like it should.
Problem 2: It's a bunch of source-code that needs to be compiled, and that, well, doesn't seem to work for a variety of reasons. I see a ton of what looks like 'divide by zero'-warnings/errors, and some jiffies.h hates me for some reason. ALSO, the show-stopper seems to be a problem related to asm/rcesm or something quite like it. Someone suggested it had to do with not including autoconf. I'm buggered if I know what to make of it.

Well, just doing the holler. Perhaps some of you have some idea on how to successfully compile this... well, code? (Short of switching to Red Hat, that is.)

---

### Post by spartan777 on 2007-09-25
i really hope they resolve things soon, i've been waiting to get an x-fi card, but wouldn't have any use for it the 50% of the time I'm on my pc (in ubuntu... not playing games).

why would they release the driver only in 64 bit? i can't imagine them not release a 32 bit version.

---

### Post by Silent Warrior on 2007-09-26
Perhaps it's easier to work out the kinks on just one architecture instead of... two? *Shrug* Programming isn't my backyard, and that's that.

[Edit] Oi! Have a glance at [http://olausson.de/x-fi](http://olausson.de/x-fi) ! I successfully 'make'-erised the driver, but I didn't manage to get it installed with those tweaks. Or custom-patches... or illegal modifications, whatever... The point is, they work better than what Creative provides. :)

Edit again... Hm... It fails because there's a reference to /sbin/chkconfig, very much a Red Hat-utility, it seems. I'm a little short on time, so I can't try it myself just now, but... what would happen if you change that reference (in the .diffs) to point at modprobe?

---

