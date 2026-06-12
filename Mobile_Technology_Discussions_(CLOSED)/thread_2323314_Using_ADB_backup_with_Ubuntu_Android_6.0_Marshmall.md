---
title: "Using ADB backup with Ubuntu Android 6.0 Marshmallow"
date: 2016-05-04
forum: Mobile Technology Discussions (CLOSED)
---

### Post by superkid333 on 2016-05-04
Hello,

I am having difficulties using ADB to backup my phone to my computer. I use Ubuntu 15.10 and ADB version 1.0.31 (should be the latest). I have a Samsung Galaxy S6 with Marshmallow 6.0

The problem is when I use the command line, no backup of the phone happens. Here is my command:

$: adb backup -all 

sometimes I use just "adb backup" and with the same result. 

The result is a 0 KB file called "backup.ab" being created. Which is useless. I've tried different tags like -system -apk -all, all with the same results.

After typing it in on the command line, it prompts me by saying "Now unlock your device and confirm the backup operation." After 2-3 seconds, it goes back to a regular prompt ready to accept input. 

On my phone, nothing happens. There is no prompt to confirm backup. This also happened with the previous version of android, Lollipop. 

Please help!

---

