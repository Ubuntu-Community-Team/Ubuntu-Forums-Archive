---
title: "mythfilldatabase with xmltv on 10.04"
date: 2010-07-15
forum: Mythbuntu
---

### Post by JasonEde on 2010-07-15
I've just upgraded (fresh install keeping db) from 9.10 to 10.04 and so far it was all looking good.

I then tried to run a mythfilldatabase. I first received an error about date manipulation and followed [http://ubuntuforums.org/showthread.php?t=1381171](http://ubuntuforums.org/showthread.php?t=1381171) to install a new copy of xmltv from sourceforge.

However, now I get the error below.


2010-07-15 22:41:28.375 Connected to database 'mythconverg' at host: localhost
2010-07-15 22:41:28.784 Updating source #1 (uk_rt) with grabber tv_grab_uk_rt
2010-07-15 22:41:28.784 Found 40 channels for source 1 which use grabber
2010-07-15 22:41:29.086 Grabber has capabilities:
2010-07-15 22:41:29.086 Grabbing XMLTV data using tv_grab_uk_rt is not supported. You may need to upgrade to the latest version of XMLTV.
2010-07-15 22:41:30.383 Updating source #6 (SAT_uktv) with grabber tv_grab_uk_rt
2010-07-15 22:41:30.383 Found 76 channels for source 6 which use grabber
2010-07-15 22:41:30.748 Grabber has capabilities:
2010-07-15 22:41:30.748 Grabbing XMLTV data using tv_grab_uk_rt is not supported. You may need to upgrade to the latest version of XMLTV.
2010-07-15 22:41:31.104 Data fetching complete.


If I try running tv_grab_uk_rt --configure I get...

Unknown capability lineups (known: all apiconfig baseline cache manualconfig preferredmethod share tkconfig) at /usr/bin/tv_grab_uk_rt line 140

Any suggestions on how to get past this? I can switch back to eit temporarily, but prefer the 14day nature of xmltv

---

### Post by ian dobson on 2010-07-15
Hi,

Maybe try using the manualconfig option.

Regards
Ian Dobson

---

### Post by JasonEde on 2010-07-16
Ok... I think I've got it working now...

I got started from [http://www.opensource-archive.org/showthread.php?t=190727](http://www.opensource-archive.org/showthread.php?t=190727)

By going to [http://packages.debian.org/sid/xmltv](http://packages.debian.org/sid/xmltv) and following dependencies I managed to install it and it all seems to be working.

I needed to install in order:

libparse-recdescent-perl_1.965001+dfsg-1_all.deb
libxmltv-perl_0.5.57-3_all.deb
xmltv-util_0.5.57-3_all.deb
xmltv-gui_0.5.57-3_all.deb
xmltv_0.5.57-3_all.deb

All seems to be good now.

---

