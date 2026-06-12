---
title: "Adobe Flash Plugin works, then quits"
date: 2012-01-23
forum: Multimedia Software
---

### Post by ratcheer on 2012-01-23
I have been using Ubuntu for about three years and I have a new problem. I use Adobe Flash 11.1r102 with Firefox 9.0.1 on 11.10 64-bit.

Flash had quit working as of 1/9/12, because I needed it to watch the BCS Championship that evening. I reinstalled it and it worked just fine.

But, sometime after that, it stopped working, again. Firefox still recognizes it as an installed plugin, but anytime I need to use it, an image is displayed that shows it to be non-operational. Sometimes the image looks like a black-and-white clapboard that they use for movie scenes, sometimes it is a color image with a red dash or a red X.

Here is the currently installed plugin: -rw-r--r-- 1 root root 18782360 2012-01-10 08:49 /usr/lib/mozilla/plugins/libflashplayer.so

Why does it stop working when it is clearly installed? What can I do to keep it working?

---

### Post by ratcheer on 2012-01-23
New info: I tried changing the mode of the file from 644 to 755, but that made no difference. I am sure it was 644 when I installed it, and it worked then.

Tim

---

### Post by ratcheer on 2012-01-23
This is so stupid, I don't even know why I tried it. But it worked.

I deleted /usr/lib/mozilla/plugins/libflashplayer.so, then re-copied the exact same file I had copied on Jan 10. 

-rw-r--r-- 1 root root 18782360 2012-01-23 12:58 libflashplayer.so

??????

Tim

---

### Post by ratcheer on 2012-01-25
I am beginning to believe, but have not proven, that enabling videos to play as HTML5 is what is "killing" the Flash functionality. The reason I think this is that, now that I have gotten Flash working again, even videos that were playing as HTML5 are back to playing as Flash, again. I am guessing that if I make the changes to allow them to play as HTML5, again, then Flash plugin would be dead again. Right now, I don't feel like messing with it.

Can Flash plugin and HTML5 coexist? Are they supposed to?

Tim

---

### Post by wolfen69 on 2012-01-26
Just for future reference, you can also put libflashplayer.so into ~/.mozilla/plugins. That way, when I do a new install, I just use my backed up .mozilla file, and flash works straight away.

---

### Post by ratcheer on 2012-01-26
Thanks, @wolfen69

Tim

---

