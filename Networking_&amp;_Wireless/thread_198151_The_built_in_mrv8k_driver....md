---
title: "The built in mrv8k driver..."
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by Mr. Picklesworth on 2006-06-16
I'm curious: Does the built-in mrv8k driver work for most people?
I was a bit annoyed after the last update to find out that my wireless had been broken because it put back the mrv8k.ko file which I had deleted from /lib/modules/blah/net/wireless , and it was a real pain having to set it up again.

So I guess two questions, actually:
-The above question of how well that driver works (it doesn't work for Asus WL-138g). Are built in drivers worth it if, when they don't work, they make things more difficult?
-Is there a more clean, permanent way to stop that driver from being used other than deleting it?


Edit:
Come to think of it, my wireless is still broken... I'll post the errors here if I give up fixing it myself. Ndiswrapper still works, but modprobe does not, so the interface does not even show up. (The setup worked flawlessly before, and I am using the newest version of ndiswrapper installed from source).
I recently installed Kubuntu-desktop, but I had wireless internet working through there and the problem is definietly caused by an update downloaded later on.
It doesn't work through Gnome, either.

---

### Post by noname101 on 2006-06-17
The kernel was probably updated. So you'll have to recompile ndiswrapper. Also before doing that make sure you run sudo make uninstall in the ndiswrapper folder.

---

### Post by Mr. Picklesworth on 2006-06-17
Hey thanks!
Of course :)

---

