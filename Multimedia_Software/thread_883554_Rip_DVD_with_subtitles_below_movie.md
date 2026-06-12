---
title: "Rip DVD with subtitles below movie"
date: 2008-08-08
forum: Multimedia Software
---

### Post by PerJensen on 2008-08-08
All,

Here is a script which rips a DVD with subtitles below movie. It uses mencoder.

Main features:
--------------
1. Automatic cropping
2. Add 60 pixels high bar below movie
3. Add subtitle to 60 pixel bar

Assumptions:
------------
Your dvd drive is /dev/dvd

The script is hardcoded, but easily changed, for danish audio with fallback to english audio and danish subtitles.

For cropdetection a little Python script is used, it is included in the script comments. Uncomment the python script and save it as ~/bin/mencoder-crop.py

Also some mencoder config settings are included in the script comments. Save them as ~/.mplayer/mencoder.conf

Usage:
1. Put DVD in dvdreader
2. ~/bin/rip-dvd.sh the-filename-you-wish.avi

Hope it is of use for someone, I used a fair bit of time getting the settings right for my tastes.

Regards
Per

---

