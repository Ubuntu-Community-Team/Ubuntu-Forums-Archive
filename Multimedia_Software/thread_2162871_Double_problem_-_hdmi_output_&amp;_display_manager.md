---
title: "Double problem - hdmi output &amp; display manager"
date: 2013-07-16
forum: Multimedia Software
---

### Post by piotrbb1 on 2013-07-16
Hello,

I know this is not a new problem in Ubuntu but nothing seems to work for me. After installing Ubuntu 12.04 64bit I can't switch the sound to hdmi (TV). The icon is not in there. In the Ubuntu 12.04 32bit everything worked fine, I think I have tried everything: unmuting everything in alsamixer, installing proprietary drivers, installing pulse audio volume control. Nothing.

Another problem is that after connecting to TV the computer switched to 1024x768 display (4:3) and now I can't change it because it is not active anymore. My resolution is 1366x768.

Thank you for any advice because I don't know what to do with it.

---

### Post by piotrbb1 on 2013-07-16
By the way it's Acer Aspire AO722 - sound card - ATI Radeon

---

### Post by piotrbb1 on 2013-07-16
As it is freshly set up system I can even change distro provided it helps.

---

### Post by piotrbb1 on 2013-07-16
Any advice is welcome :-)

I have tried so many different ways of solving the problems that I am open to any hints:-)

---

### Post by piotrbb1 on 2013-07-18
Hi, it's me again. Maybe some of you had a similar hdmi output- no icon problem or know how to unlock the screen resolution. The forum people have always been very helpful to me. I know this time someone will also think of something:-)

---

### Post by Mark Phelps on 2013-07-18
What specific version Radeon card do you have?  IF you don't know, open a terminal, enter "lspci" -- and look for the line containing "VGA".  Post that information back here.

Ubuntu changed the X-server version between 12.04.1 and 12.04.2.  The AMD Radeon HD 2x/3x/4x-series cards would work with the first, but not the second.

---

### Post by feardotcom on 2013-07-19
I run hdmi sound. After install i did ALL the updates and installed the correct drivers ( i use nvidia though) and rebooted and it worked fine for me. I just went to the sound and selected hdmi sound for output. I dont know if you did all of your updates or not, but try that if you haven't.

---

