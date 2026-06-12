---
title: "ShockWave Flash always crashes in Chrome - 14.04 LTS"
date: 2015-01-20
forum: Multimedia Software
---

### Post by sylva-feyth on 2015-01-20
Hello All... relatively new to linux and brand new to the forums. I did a pretty comprehensive Google to try and solve my issue and am hoping someone else knows what to do.

Anytime I go to twitch.tv in Chrome an error pops up saying flash crashes. I came across the common solution of disabling one of the flash plugins in the browser, but I believe that only works for older versions as I currently only see one file (not two) and saw other posts of more recent dates saying the same thing. 

It works just fine in firefox, but the reason I want it in Chrome is so I can cast the feed from twitch to my TV.

EDIT: I am willing to provide info / log files required, I just don't know which ones may be needed - as mentioned, pretty new.

---

### Post by kerry_s on 2015-01-20
google chrome has there own flash, it's built in.
check "chrome:gpu" see if your hardware acceleration is working, they black listed a lot of machines. if it's not all green, go into "chrome:flags" & enable the very top 1 composting i think.
sorry on details, bad memory, i switched to firefox currently.

---

### Post by dwpbike on 2015-12-13
i seem to be getting some relief by going to about:plugins and unclicking  "Adobe Flash Player - Version: 20.0.0.228
Shockwave Flash 20 always allowed to run".  sadly, chromium is still dead.

the forums seem to want to edit my colon in "about(colon)plugins.

---

### Post by howefield on 2015-12-13
> **dwpbike said:**
> the forums seem to want to edit my colon in "about(colon)plugins.

Below the posting window select "Disable smilies in text"... (not available with the quick reply option)

---

