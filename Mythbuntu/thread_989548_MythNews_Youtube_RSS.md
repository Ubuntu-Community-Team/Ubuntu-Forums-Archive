---
title: "MythNews Youtube RSS"
date: 2008-11-21
forum: Mythbuntu
---

### Post by amlino on 2008-11-21
Hi. I have installed  mythbuntu 8.10 and cannot get mythnews youtube to work. The same was not working with 8.04.

I can see all videos available from the front end, click on the video and see the "downloading media..." msg on the screen.

The frontend log shows the following:


2008-11-21 18:37:32.795 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/news-ui.xml
[B]2008-11-21 18:38:07.957 MythNews: VideoURL http://youtube.com/get_video.php?video_id=d>
[/B]                <title>OpenDNS</title>
        </head>
        <body id=&t=>
        <head>
                <title>OpenDNS</title>
        </head>
        <body id=
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.

Playing /home/marcello/.mythtv/MythNews/newstempfile.
Exiting... (End of file)

This does not seem the parser is doing a good job since the URL [http://youtube.com/get_video.php?video_id=d](http://youtube.com/get_video.php?video_id=d) does not exist. And does not matter which video I click, I get the same highlighted URL above.

I updated the mythstream youtube parser based on this bug -> [https://bugs.launchpad.net/mythbuntu/+bug/223781](https://bugs.launchpad.net/mythbuntu/+bug/223781) but did not help.

Any idea?

Thanks,
Marcello

---

### Post by amlino on 2008-11-21
I should have mentioned... that I also tested youtube mythstream on mythbuntu and it is currently not working...

I updated the mythstream youtube parser based on this bug -> [https://bugs.launchpad.net/mythbuntu/+bug/223781](https://bugs.launchpad.net/mythbuntu/+bug/223781) but did not help.

---

### Post by amlino on 2008-11-21
Managed to get mythstream working with youtube by installing the updated parser, removing the $HOME/.mythtv/mythstream/streams.res and creating a streams.res with just a test entry. Maybe something was not getting properly updated via the frontend...

example:

[item]
Video
YouTube top viewed today
[http://youtube.com/rss/global/top_viewed_today.rss](http://youtube.com/rss/global/top_viewed_today.rss)
yt
youtube/feed


Could not get MythNews to work with youtube

---

### Post by jdeslip on 2009-01-28
I cannot seem to get any video/audio working in mythnews.  I'd like to get the Onion Videos Working...

---

