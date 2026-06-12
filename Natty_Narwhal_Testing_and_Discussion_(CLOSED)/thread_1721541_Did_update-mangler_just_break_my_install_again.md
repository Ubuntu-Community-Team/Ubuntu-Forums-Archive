---
title: "Did update-mangler just break my install again?"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-04
Check for updates, it finds a ton.
Try to install them, it crashes. The crash report system freezes, so much for that.

So I fired up apt-get upgrade, only to see there are no updates to install. An apt-get clean && apt-get check && apt-get update later, there are still "no updates to install".

What do?

---

### Post by macroshaft on 2011-04-04
What does sudo dpkg --configure -a do? That usually works for me.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-04
It supposedly does something, but doesn't print anything in the terminal. Afterwards, apt-get still doesn't see any updates.

---

### Post by macroshaft on 2011-04-04
Is your system obviously broken at all? Or are you just presuming it didn't complete the updates?

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-04
> **macroshaft said:**
> Is your system obviously broken at all? Or are you just presuming it didn't complete the updates?

It couldn't have. update-manager crashed right after I clicked install, it didn't even start downloading. The desktop seems to work as good as usually otherwise.

---

### Post by macroshaft on 2011-04-04
I have experienced numerous problems in Natty where update manager appears to have crashed, or even crashed the entire system, but is actually still working away in the background and if left will complete the upgrades.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2011-04-04
I checked the processes, it crashed completely.

---

### Post by macroshaft on 2011-04-04
Sounds like a bit of a mystery then, I was half way through updates when you posted and it went ok. I guess wait and see if new updates appear tomorrow or if the system is now blind to them.

---

### Post by VMC on 2011-04-04
aG93IGRvIGkgdWJ1bnR1Pw==, is your install new or from an upgrade?
I never use update manager. First thing I do is turn it off at Startup options.

Have you tried the "apt-get -f " option?

I had to laugh at the title "update-mangler", made me laugh.

[Also, off-topic, what does "aG93IGRvIGkgdWJ1bnR1Pw==" mean? Was that just a random key input?]

---

### Post by jerrylamos on 2011-04-04
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Check for updates, it finds a ton.
Try to install them, it crashes. The crash report system freezes, so much for that.

So I fired up apt-get upgrade, only to see there are no updates to install. An apt-get clean && apt-get check && apt-get update later, there are still "no updates to install".

What do?

I get update screw ups from time to time during Alpha, and even Beta.  I re-install.....and always have a Maverick partition around to recover the mess that Natty may have made.

If running Alpha's & Beta's expect to re-install from time to time.

Jerry

---

### Post by Mr. Picklesworth on 2011-04-04
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> It couldn't have. update-manager crashed right after I clicked install, it didn't even start downloading. The desktop seems to work as good as usually otherwise.

Update Manager uses aptdaemon, which is a separate process. (That's why it doesn't need to run as root any more). So, it can crash and your updates will keep installing :)

---

