---
title: "mp3blaster &quot;Failed to open sound device&quot;"
date: 2010-11-09
forum: Multimedia Software
---

### Post by Kyentei on 2010-11-09
Hello everyone,

The last few days I have been having issues with using mp3blaster on Ubuntu 10.10. If I recall correctly, it always used to work.
When I was using Debian on my desktop, mp3blaster worked fine. I have recently installed Ubuntu 10.10, and now it does not. Same issue goes for my laptop.

The issue is: Whenever I want to play a song, it says "Failed to open sound device".

All other media applications work just fine, and my user is in the desired groups too. I have no clue where to look anymore, as all topics I have found on this issue are from 2006 or earlier. (without providing a solution)

I hope you guys can help me out here.

- Kyentei

**EDIT:**
Hm, nevermind I suppose. Mp3blaster depends on /dev/dsp which was removed since Ubuntu 10.10.

More info here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/634211)

**EDIT2:**
**Solution!**
If you run mp3blaster within padsp, it will work!
```
padsp mp3blaster
```

---

### Post by stratos001 on 2011-04-26
Thank you so much for this solution.  I have been looking for this for a while :)

---

### Post by mister-el on 2011-06-02
Hello,

it works also for me. In my opinion, this hint belongs to the documentation under /usr/share/doc/mp3blaster

cu el

---

### Post by riderplus on 2012-03-17
There's still a problem. I can't control the volume. Pressing "t" does nothing, no mixer shows up. That's after solving the previous problem, thank you for the solution. I don't have any /dev/mixer files, so...how can I use ">" and "<" to control the volume if there's no mixer??

---

### Post by Yellow Pasque on 2012-03-17
Instead of using the OSS output (and emulating oss with padsp), you can use SDL (works in Oneiric or later).
[https://bugs.launchpad.net/bugs/752091](https://bugs.launchpad.net/bugs/752091)

---

### Post by riderplus on 2012-03-18
Thanks for the answer, but I've no idea how to use that one :(

---

### Post by Yellow Pasque on 2012-03-18
```
echo "AudioDriver=sdl" > ~/.mp3blasterrc
```

---

### Post by riderplus on 2012-03-18
Ok, now I upgraded to 11.04 and mp3blaster uses SDL out of the box. But I still have no mixer and no possibility to decrease/increase the volume! That's really weird, is there any way I could make it *see* the mixer?

**EDIT: **I upgraded to 11.10, but the only way I could make it see the mixer was by passing options to padsp like this: ```
padsp mp3blaster -s /dev/dsp
``` There's no way I could make it see the mixer with SDL.

---

