---
title: "Making M-Audio MobilePre USB work"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by isaacj87 on 2007-05-16
Hi, I have an M-Audio MobilePre USB I/O device and I read in another thread that it should automatically be usable upon plugging in. I can't seem to get it to work...I read that it's a class compliant USB Audio device so do I need a certain package?? Thanks!

---

### Post by isaacj87 on 2007-05-25
is there no one that can help me?

---

### Post by paulg on 2007-06-07
isaacj87, just went through this myself so I put together a howto [here](http://ubuntuforums.org/showthread.php?t=466667). If you have any questions post them there and I will respond.

~pAul.

---

### Post by isaacj87 on 2007-06-07
THANK YOU! I tried those drivers before but did not realize that you needed to modify the udev rules. All I did was copy and replace the line under MobilePre...I see that it is recognized now...is that all I have to do to get it to work?

---

### Post by paulg on 2007-06-07
That should do it. Try unplugging and replugging it in. Should work no problem now.

~pAul.

---

### Post by isaacj87 on 2007-06-07
does this alter anything else related to udev? or is it just modifying the mobilepre udev rules only?

how did figure out the fix to this bug?

haha. sorry about all the questions..you just made my day though

---

### Post by paulg on 2007-06-07
Just modifies the MobilePre udev rule. Everything else should work as it was before.

How did I figure this out? Well days! I read every post on the MobilePre in this forum then read them all again and started to piece it together. I narrowed it down to a udev problem but had no idea the format for the rules had changed so spent days trying to imitate other rules on this forum from USB phones, to hard drives and other audio devices. I don't know where I got the idea to check for a bug report but I'm glad I did. Probably just because I tried everything else. 

Anyway, enjoy and spread the fix if you see someone else asking!

~pAul.

---

