---
title: "Sound Blaster Live! 24 Bit Only plays front OR rear"
date: 2009-09-23
forum: Multimedia Software
---

### Post by Mindbleed on 2009-09-23
I have been having troubles with my Sound Blaster Live! 24-Bit sound card since I installed Ubuntu.  I have a 5.1 Surround sound setup.

It has only been playing on the Front L + R speakers and the subwoofer.

Today I entered the Sound Preferences (which i have checked before) and today there were new options.  There were 4 options Labeled
Live! 7.1 24bit [SB0413] CA0106 (ALSA)
and 3 for OSA

Some of these options play in the front speakers, some do not work, but one actually plays ONLY in the rear, which has never happened before.

I am wondering if anyone has had this problem before, or if there is any way to use BOTH sound settings to get it to play in both.

I do not really know how to edit ALSA other than in this dialogue, but maybe this will be my key to success

---

### Post by mr.interested on 2011-10-15
Have you fixed the problem?

I have very similar issue in the latest Ubuntu (11.10): [http://ubuntuforums.org/showthread.php?t=1860273](http://ubuntuforums.org/showthread.php?t=1860273)

PS This is how it looks:

[[IMG]http://img266.imageshack.us/img266/2705/screenshotat20111015085.th.png[/IMG]](http://imageshack.us/photo/my-images/266/screenshotat20111015085.png/)

---

### Post by mr.interested on 2011-10-18
Does anyone have any suggestions? The sound card was correctly recognized in Ubuntu 10.04, 10.10, and 11.04. I'm surprised that it doesn't work properly in 11.10.

---

### Post by Shazaam on 2011-10-18
```
alsamixer
```
(in terminal) still works. Have you checked to make sure that what you need is unmuted? To unmute use the left-right keyboard keys and hit m.

---

### Post by mr.interested on 2011-10-18
I've just plugged the card and... magic happened:

[[IMG]http://img338.imageshack.us/img338/3450/screenshotat20111018222.th.png[/IMG]]("http://imageshack.us/photo/my-images/338/screenshotat20111018222.png/")

Compare it with the latest one:

[[IMG]http://img266.imageshack.us/img266/2705/screenshotat20111015085.th.png[/IMG]]("http://imageshack.us/photo/my-images/266/screenshotat20111015085.png/")

The additional options somehow appeared, but I haven't done anything, just plugged the speakers to the same USB slot after a few days.

Perhaps some Ubuntu upgrade?

PS One of the major things that I've changed was "Languages for menus and windows". I've changed English US to other language, and then switched back to English US after restart.

---

### Post by mr.interested on 2011-10-19
I can now confirm that the problem is with "Languages for menus and windows".

The card works only with the following order:
English (UK)
English (US)
English

It doesn't work with:
English (UK)
English

My guess is that the "Languages for menus and windows" isn't available for "English (UK)", and so Ubuntu always skips to the next language. So it looks as the correct settings are available only for "English (US)".

---

### Post by mr.interested on 2011-12-01
Just an update. The problem still occurs whenever I connect the card when system is running, or before I wake it up. In other words, the card is detected properly (ie, with 5.1 settings) only when I connect it before I boot Ubuntu. Otherwise, it doesn't work (I have only 2 speakers active as per the earlier images attached).

Any ideas what is going on? I didn't have this problem with previous versions of Ubuntu.

Best

---

