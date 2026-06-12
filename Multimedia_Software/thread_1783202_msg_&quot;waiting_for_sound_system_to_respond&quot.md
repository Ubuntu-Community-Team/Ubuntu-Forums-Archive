---
title: "msg &quot;waiting for sound system to respond&quot;"
date: 2011-06-15
forum: Multimedia Software
---

### Post by clappr on 2011-06-15
main.c: Failed to acquire autospawn lock

waiting for sound system to respond




I have been seeing the first message repeatedly in my Log.  The second message I see on startup. 

Solution: In a terminal window type: ls -l $HOME/.pulse

The output should look like this: lrwxrwxrwx 1 richard richard 23 2011-06-15 12:15 b647ecedc67a8542ee56121f4becac6d-runtime -> /tmp/pulse-YKmNCtFkmWYU

if your permission does not reflect your ownership then type:
sudo chown -R richard:richard /home/richard/.pulse
T
o make this change please replace richard with your username.

---

