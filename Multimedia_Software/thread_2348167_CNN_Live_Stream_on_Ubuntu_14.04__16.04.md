---
title: "CNN Live Stream on Ubuntu 14.04 / 16.04"
date: 2017-01-01
forum: Multimedia Software
---

### Post by stevefdriscoll on 2017-01-01
Boy this problem just doesn't seem to stay resolved. I've been viewing CNN Live Streaming for a few years and every once in a while, something gets broken. This time, I just can't figure out what occurred a few weeks ago to break it. I was running the latest Firefox on 14.04 and had long since used these instructions to install HAL - [https://ubuntuforums.org/showthread.php?t=2221366](https://ubuntuforums.org/showthread.php?t=2221366) . Then something broke.

I've since upgraded to 16.04 and have tried libhal1-flash via the instructions here - [http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up](http://www.omgubuntu.co.uk/2015/09/how-to-watch-hulu-on-ubuntu-1404-up) .

I've tried to narrow the problem using the Flash Player site here - [https://helpx.adobe.com/flash-player/kb/flash-player-11-problems-playing.html](https://helpx.adobe.com/flash-player/kb/flash-player-11-problems-playing.html) .

The suggested test site is simply stuck on the "Loading Flash Access license" pop-up window.

Any thoughts please?

p.s. CNN Live Streaming has never worked with Chrome either.

SOLVED (kind of):

I went to [https://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](https://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) and installed an older version (Released 11/8/2016) Flash Player 11.2.202.644 (32 MB). I opened the archive and copied libflashplayer.so to the /usr/lib/flashplugin-installer directory overwriting the current one. Close and reopen Firefox. You will get a warning saying that the plugin is an old version. And the file may get overwritten in the future so this is a hack but I'm sick of researching.

If anyone has a better solution then please post.

Good luck!

---

