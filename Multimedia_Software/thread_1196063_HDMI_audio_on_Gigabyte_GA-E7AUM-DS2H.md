---
title: "HDMI audio on Gigabyte GA-E7AUM-DS2H?"
date: 2009-06-24
forum: Multimedia Software
---

### Post by klato on 2009-06-24
Has anyone had any success getting audio over hdmi to work on this motherboard? I just did a fresh install of Ubuntu 9.04 and I have no audio over HDMI. Nothing is muted or anything like that...unsure what to do at this point. I've done some searching but have not come up with a solution. Any ideas?

Thanks!

---

### Post by klato on 2009-06-25
Well, I partially fixed it. Under System->Preferences->Sound, I chose the hdmi piece and I can now hear sounds.

However, I still get no sound in Firefox and I also don't hear anything when I login. (it sounds like it gets cut off). Might play around with asound.conf tonight.

---

### Post by klato on 2009-06-25
I was able to get sound working in Firefox now, by putting the following in asound.conf:

pcm.!default {
     type plug
     slave.pcm "hdmi"
}

However, some sounds (i.e. system sounds) still go through the green jack on the front of my PC. Any ideas how I can make ALL sounds in Ubuntu go through HDMI on this board?

---

### Post by eskomorko on 2009-07-14
Have you fixed your problem yet? Just interested because I ordered the same motherboard.

---

### Post by klato on 2009-07-14
Unfortunately I could never get it going. I threw in the towel and ended up installing Windows XP SP3...works like a charm. I'll probably revisit Ubuntu in the future.

If you find a way to make it work please make a post here if you can =)

---

