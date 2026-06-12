---
title: "Berkeley Lectures"
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by ThrashJazzAssassin on 2007-07-30
Can anyone get any of the real media lectures to work consistently? The odd one or two work fine but most of them are missing sound for me. The only success I've had was with Totem. I've had no success with Helix player. Cheers

EDIT: and the link [http://webcast.berkeley.edu/index.php]("http://webcast.berkeley.edu/index.php")

---

### Post by ThrashJazzAssassin on 2007-07-31
bump

---

### Post by david_2001 on 2007-07-31
I'm no expert on streaming media but, just out of curiousity, I thought I'd have a play to get an idea of what's changed in biology in the 27 years since I graduated...

Anyway, I don't use realplayer but rely instead on the mozilla-mplayer plugin for firefox to play real media streams from the Internet.  That didn't work.  The plugin didn't load when I clicked on one of the archived lecture icons.  So, I downloaded the .rm file linked from the lecture icon and tried running the rtsp address in the .rm file with mplayer and then totem at the command line.  No joy.  So I edited the rtsp address to remove the end time and, tada, mplayer (but not totem) was able to play the lecture with sound and it continued to work for two more randomly chosen biology lectures.

If you have mplayer and w32codecs (w64codecs for x86_64 ubuntu) installed then try the following:
```
mplayer rtsp://169.229.131.16:554//classes/s2007/bio1a/20070117.rm?start=00:02:50
```
```
mplayer rtsp://169.229.131.16:554//classes/s2007/bio1a/20070323.rm?start=00:03:51
```

---

