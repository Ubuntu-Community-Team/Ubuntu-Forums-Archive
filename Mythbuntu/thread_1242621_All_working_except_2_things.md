---
title: "All working except 2 things"
date: 2009-08-17
forum: Mythbuntu
---

### Post by bcg30506 on 2009-08-17
I've now mostly got a good stable and HD-capable mythtv 0.21vdpau system but for 2 issues I'm hoping someone can help with:

1. Since updating last week with the latest weekly and getting vdpau working again for low CPU usage and HD playback, I now lose lip sync with the audio/video when watching LiveTV after a while.  It seems to start off ok, but the longer you watch, the more they appear to get out.  This was never an issue before, so I don't know if it is the latest mythtv build or the fact that I now use the VDPAU playback profile.

2. MythWeather still gets errors and displays a blank screen for current conditions.  All other screens look fine, like 3/6-day forecasts, satellite, and radars.  I see this in mythfrontend.log:

2009-08-17 10:27:16.909 nice /usr/share/mythtv/mythweather/scripts/us_nws/nwsxml.pl -u ENG -d /home/me/.mythtv/MythWeather/NWS-XML KGVL has exited
2009-08-17 10:27:16.909 heat_index_string::
2009-08-17 10:27:16.909 nrecoverable error parsing script output 

But no fixes I've found in this or any other forum have worked.  Again, it used to work until several updates ago and my location has not changed.

Thanks to everyone who has helped thus far and I hope someone can help solve these last 2 items.  :)

---

### Post by bcg30506 on 2009-08-19
Update:

The mythweather current conditions is mostly working now.  Only the "Feels Like" shows NA, but everything else now displays on the first screen.  I used newlinux's hacked nwsxml.pl script (search the other thread on this) and had to change my location in setup as my previously set one must have gone away.

As or VDPAU LiveTV playback, lip sync between audio and video is still getting way out over time.  It starts off ok but the longer it plays, the more it gets out of sync.  I just discovered this morning that pausing or Rew/FF a for a bit then resuming playback will correct it and sync things back up for a while.  But it eventually goes out again.  This is new after either the last mythtv update or since setting up the VDPAU profile.  It was way worse with the "extra audio buffering" setup option enabled.  I disabled this option and VDPAU still plays HD videos and the A/V sync takes longer to break.

---

### Post by mitchell2345 on 2009-08-19
for number 1 please post a sample of your mythfrontend logs with the '-v playback' option used.

This should give more info on what is happening.

~Mitchell

---

### Post by bcg30506 on 2009-08-19
Thanks, Mitchell.  I've added the -v playback option and attached the logs to this message.  I must explain them and what I did.  The attached file is bzipped tar and contains 2 log files:

mythfrontend.log.advanced : This is the 1st one and used my existing setting of the Advanced 2x deinterlacer.  It played for a while then the sync got out.  I jumped back and forward using the remote and this resynced it for a time but then it always goes back out.  This file is rather long (13K lines) since the problem only shows up after watching for a bit.

mythfrontend.log.temporal : This log was created after I changed my playback profile to use VDPAU's Temporal 2x deinterlacer based upon a hint on the nvnews forum that interlacers can cause sync issues with the vdpau driver.  It was the suggested one.  I left all other settings unchanged originally.  When I started Watching Live TV the sound was all crackly and the sync was WAY out immediately.  Then I remembered reading about the "Extra audio buffering" setting in Playback options.  It was disabled, so I turned it on.  Then went back to Live TV.  This time it started with no sound quirks and stayed in sync for the entire time I left it playing. Woo hoo!  So the log shows both attempts.  The first without the extra audio buffering and the last one with that option enabled and everything working better.

Hope this helps someone and helps the dev team debug something.  I tried to be thorough but not overload with too much useless info.

---

### Post by bcg30506 on 2009-08-21
Actually, now that I've been using Temporal 2X for a bit, I've noticed some horizontal tearing during fast pans when watching either SD or HD content.  It's not horrible, but the wife did notice and ask what it was.  I've tried all other deinterlacer options.  The only one that didn't have other artifacts or didn't lose A/V sync and did not seem to tear was Advanced 1X.  However, my HD content would not play without stuttering with it.  So Temporal 2X is the only deinterlacer that plays both HD and SD content in sync using VDPAU, but I have to deal with the slight tearing in motion scenes.

I do already have the Composite disabled in xorg.conf.  Is there anything else I can try or is this something that needs a code fix first?

Also, the current conditions for mythweather have not updated since I originally posted it was working now.  The screen still displays info, but it is from Tuesday 3 days ago.  All other screens are up to date.  I see no errors in the frontend log.

---

### Post by bcg30506 on 2009-08-26
I just added the avenard repository and did a dist-upgrade.  This brought me to the 190 beta version of nvidia, the latest mythtv and mplayer with vdpau support, and the 2.6.28-15-generic kernel.

I'm happy to report that all video tearing issues using vdpau profile with temporal 2x deinterlacer are gone!  Both HD and SD videos and recordings play perfectly with no motion pan tears, jumpiness, and for the most part, in sync.  Every once in a while especially after FF/Rew an HD mts video, the audio sync gets out by about 50 or 60ms.  The CPU usage while watching either live SD TV or an HD MTS recording with the internal player is about 3%.  Using mplayer to watch HD videos the CPU runs about 48% - still not bad and I can even watch 1080p Apple trailers now too.

---

