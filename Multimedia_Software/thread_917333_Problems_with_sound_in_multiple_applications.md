---
title: "Problems with sound in multiple applications"
date: 2008-09-11
forum: Multimedia Software
---

### Post by benjick on 2008-09-11
Okey, I've tried to narrow down my problems but without any luck so I'm turning to you. I can't play sound in  multiple application.

e.g. firefox (flash like youtube etc) and rhythmbox (or any media application) won't work good together. If I play a video at youtube and then start up rhythmbox it wont play the file. VLC will play the file but silent. The other way around I will see the video at youtube but it will be silent. I can use VLC + rhythmbox without any problems so I thought for myself "Yeah, let's blame flash" and that would be all fine.

I went on with my life; closing applications to use another until I started playing World of Warcraft (WoW) using the app Voicechatter (VC) to communicate with other player via the voicechat it provides. I can hear the in-game sounds in WoW while i speak to my friends thru VC. We were killing this boss which took some time so i fired up some music through Rhythmbox but NO - no sound here. I located the source for this to VC and thought "Okey, i should listen to my friends anyways". I then loaded up firefox and went to youtube - voila, i can hear music without any problems.

I tried a lot of things to fix this, can't remember them all. But; i fired up gstreamer-properties and picked ALSA instead of auto-detect - no result (restarted X just to be sure). I switched back to auto-detect for pulseaudio and i activated the support for simultaneous output under Pulseaudio Prefs - still no help.

I've googled my *** out and I have no clue. It's getting really annoying to have to close down Rhythmbox every time someone links a youtube/break/whatever-link. Any help is welcome.

I'm running Ubuntu 8.04 and the latest version of Firefox. I run the beta 10 of flash but i have tried with 9 (which made firefox crash almost every time i watched a flashthingy) with the same result.

Thanks in advance,
benjick

-----
Solved by installing libflashsupport

---

### Post by benjick on 2008-09-12
bump

---

### Post by waygamit on 2008-09-12
Have you tried another threads? Maybe they will be able to help you somewhere.

---

### Post by benjick on 2008-09-12
Solved this by installing libflashsupport. Thanks #ubuntu :>

---

### Post by eye208 on 2008-09-12
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

