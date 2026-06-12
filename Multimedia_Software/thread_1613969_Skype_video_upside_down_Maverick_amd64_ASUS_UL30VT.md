---
title: "Skype video upside down Maverick amd64 ASUS UL30VT"
date: 2010-11-05
forum: Multimedia Software
---

### Post by Vermind on 2010-11-05
Hi,
I have an ASUS UL30VT laptop with
```
Bus 001 Device 003: ID 064e:a136 Suyin Corp.
``` webcam.
I am running Ubuntu Maverick 64-bit. The Cheese webcam application shows my camera picture correctly, but Skype shows it upside down. I have tried installing modified/updated libv4l from [https://launchpad.net/~libv4l/+archive/ppa/+packages](https://launchpad.net/~libv4l/+archive/ppa/+packages) and manually extracting the 32-bit maverick libv4l into /usr/lib32, with no luck. Skype keeps showing the picture upside down. Also the V4l Control Panel seems not to affect the picture in Skype.

The camera uses the uvcvideo driver.
Any ideas?

---

### Post by mavrek on 2011-04-15
I have the exact same setup (as far as I can tell) and I used this solution:

[http://ubuntuforums.org/showpost.php?p=8925031&postcount=225](http://ubuntuforums.org/showpost.php?p=8925031&postcount=225)

I'm running the latest (2.2beta) Skype version too.

---

