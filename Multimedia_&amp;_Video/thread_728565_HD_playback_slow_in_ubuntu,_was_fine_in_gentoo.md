---
title: "HD playback slow in ubuntu, was fine in gentoo"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by powderific on 2008-03-18
After getting sick of compile times, kernel configuration, and generally having to put more work into just using my pc than I felt like, I switched from Gentoo to Ubuntu. For the most part, I'm happy with the switch. But I'm having a lot of trouble with 720p video. With Gentoo I could play pretty much anything 720p with mplayer from the console even if I was running Azureus in the background. My pc is pretty slow with an Athlon 3000+, 1 gig of RAM, and Geforce4 MX 440, but even when I had a slower Athlon 2400+ I could play HD files from the console if I just turned off any background programs. Is Gentoo really that much faster than Ubuntu? Is there anything I can do to bump up the speed a little?

My biggest problems come from the sound de-syncing from the video, though occasionally the video gets choppy too. I've tried things like -autosync 30 and lavdopts stuff, but nothing seems to improve it much.

I'd appreciate any help. I really don't want to go through the rather arduous process of reinstalling Gentoo, so I'd like to hear any suggestions.

---

### Post by shirilover on 2008-03-19
You could try compiling mplayer from svn to take advantage of the decoding improvements as well as optimization for your hardware.

[This thread]("http://ubuntuforums.org/showthread.php?t=558538") should make that much easier.

---

### Post by powderific on 2008-03-19
I don't know if it'll fix the problem, but it certainly looks worth a try. Thanks!

---

