---
title: "Firefox Flash Sound Breaks after a while"
date: 2009-04-17
forum: Multimedia Software
---

### Post by rold50 on 2009-04-17
Hi All,


My firefox flash sounds works but then after a while it breaks (either I don't hear sound or after a few seconds I hear sounds like CD skipping or scratch,etc). I have to restart my firefox for the sounds to work. It only happens in flash. Even if the sounds of my flash breaks, my other application's sound still works fine.

I tried installing flash-plugin-nonfree-extrasound but it still doesn't work.

I also tried changing 
system->preferences->sound to ALSA and it still doesn't work.

---

### Post by Speed8 on 2009-04-17
I'm having the same problem. I have tried a couple things (basically what you have tried) and no success. Anyone have an answer or ideas?

---

### Post by rold50 on 2009-04-17
Any ideas?

---

### Post by Speed8 on 2009-04-17
[http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

check this thread out, the beginning isnt relevant but the last pages are. Going to try them and hope they work.

---

### Post by rold50 on 2009-04-20
> **Speed8 said:**
> [http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

check this thread out, the beginning isnt relevant but the last pages are. Going to try them and hope they work.

Did it work for you? I tried creating the firefoxrc file and adding 
FIREFOX_DSP=”aoss” but it still doesn't fix my problem.

---

### Post by abbot on 2009-05-06
this happens to me as well.  i have to restart firefox to get sound working without doing the skipping thing.  when i restart it though i have to wait a minute because it will give me a message saying it's still open and i have to wait.  this was happening before i updated to jaunty.

since upgrading to jaunty sometimes it will drop the sound out of my whole system as well and i think i have to resort to restarting my whole computer before it will come back.

---

### Post by abbot on 2009-05-07
I checked around and found that I didn't have pulse audio installed.  I used this thread to install it.  Today I got home from work and everything's working fine so this may be the fix.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

