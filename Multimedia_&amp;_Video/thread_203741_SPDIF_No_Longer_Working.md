---
title: "SPDIF No Longer Working"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by Shigun on 2006-06-25
Ok, I recently went to a friends house this weekend, so I could not take my speakers with me.  No biggie, I plugged in my headset into my second soundcard, and set it as the default in my asound.conf

During the time, I also installed a new kernel set which supports my dual core processor, as the default kernel did not have SMP support.

I get home, hook up my sound system, set my asound.conf back to normal, and I get....nothing.  Ok, thinking something might be up, I move the asound.conf to a backup location, try again.  Nothing.  I dont know whats up.  Yet, my second soundcard still works fine.

I've tried booting to the older kernel, but that doesnt work either.  Help please?

---

### Post by LordRaiden on 2006-06-26
Does sound without SPDIF work? If it does, then do this in a shell

```
alsamixer
```

Navigate to the right with the right arrow key, and look for settings under SPDIF or IEC958. Make sure they are not muted (with M) and try setting the volumesto max (with up).

If that does not work, try setting the volume all the way down (don't ask me why, sometimes it works).

If you get an error about alsamixer not finding something, then something is wrong with your alsa drivers. Post back if this is the case.

---

