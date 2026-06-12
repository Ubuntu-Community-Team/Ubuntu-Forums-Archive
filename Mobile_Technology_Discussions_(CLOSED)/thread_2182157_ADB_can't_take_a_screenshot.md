---
title: "ADB can't take a screenshot"
date: 2013-10-20
forum: Mobile Technology Discussions (CLOSED)
---

### Post by robman79 on 2013-10-20
Hello everyone.

I'm trying to take a screenshot of Ubuntu Touch (build r100) via ADB according to [this manual on wiki]("https://wiki.ubuntu.com/Touch/CoreApps/Dogfooding#Getting_a_screenshot").

Here's what i got:

```
roman@roman-ubuntu-test:~$ adb root
adbd is already running as root
roman@roman-ubuntu-test:~$ adb shell /system/bin/screencap -p /tmp/screenshot.png

```

And then it just hangs and create empty file. Any idea? Thanks!

---

