---
title: "Gnome mplayer freezes system"
date: 2011-07-12
forum: Multimedia Software
---

### Post by LenK on 2011-07-12
Lubuntu 11.04 on laptop (PIII ATI Rage Mobility). Playing a WMV or MPEG file, system freezes when playback ends. I have not tried any other formats.

I looked at mplayer Preferences

In the Player tab, "Video Output" was blank - I set it to "x11"

This corrected the freeze problem, at least the first time that I tried it. However, it did not seem to persist through multiple plays of the MPEG file, whether or not accompanied by an mplayer quit and rerun or a reboot, even though I did not change the parameters. I tried setting vo=x11 in the etc/mplayer/config file, but that did not help. It is sporadic. It will work a few times with the MPEG file, then hang, for no apparent reason. One thing it does seem to do consistently is hang on the WMV file, regardless of the vo setting, and on both files, when vo is not specified (what I started with). This is a time-consuming task, with a reboot on every failure, and I have run out of ideas on what to try next. When it hangs on the MPEG file I noticed that the elapsed time ends up at 20 sec, even though the video total time is 16 sec. When it doesn't hang, the elpased time goes to 20 sec, then returns to 16 sec.

---

### Post by DHAines56 on 2011-07-12
Have you tried any other media players to see if the problem persists. I like to use VLC Media Player. It has a clean, easy to use interface and can play most known media formats without the need to install codecs. If it still freezes there is a possibility that a codec has been corrupted and probably needs to be reinstalled

---

### Post by LenK on 2011-07-13
> **DHAines56 said:**
> Have you tried any other media players to see if the problem persists. I like to use VLC Media Player. It has a clean, easy to use interface and can play most known media formats without the need to install codecs. If it still freezes there is a possibility that a codec has been corrupted and probably needs to be reinstalled

I saw one post in which a few people expressed a preference for VLC. With yours added, I installed it. No freezes, but no sound either, for the MPEG or the WMV file. Found a post that suggested setting audio output to ALSA - that worked.:D

Thanks for your help.

---

