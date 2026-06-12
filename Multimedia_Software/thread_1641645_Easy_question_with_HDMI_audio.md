---
title: "Easy question with HDMI audio"
date: 2010-12-09
forum: Multimedia Software
---

### Post by McManCSU on 2010-12-09
If I have HDMI properly configured for surround sound, when I go into the Volume settings and choose the Hardware, should I have an option for Surround (HDMI)?  All I see is Stereo over HDMI but for Analog I see the Surround options.

Thanks!

---

### Post by sydbat on 2010-12-09
> **McManCSU said:**
> If I have HDMI properly configured for surround sound, when I go into the Volume settings and choose the Hardware, should I have an option for Surround (HDMI)?  All I see is Stereo over HDMI but for Analog I see the Surround options.

Thanks!If you are getting sound, that is good!! As for "surround"...I have found VLC to be the best for that. Change the settings in VLC (Tools > Preferences > Show Settings "All" (at the bottom) > Audio). When you have "All" clicked, you get a new menu on the left side that allows you to change tons of settings.

In the Audio settings, open Output Modules > ALSA and choose the correct HDMI sink (mine is the second one which = hw:0,7...although that does not seem to be explicitly stated there). Save. Exit VLC (just incase), then start it up again. Play a DVD with full 5.1 or 7.1 Surround Dolby Digital or DTS through HDMI.

I hope that helps.

---

