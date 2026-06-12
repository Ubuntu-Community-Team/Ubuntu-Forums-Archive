---
title: "mplayer plays TS files, but not Live Satellite TV"
date: 2011-10-21
forum: Multimedia Software
---

### Post by wrxguy on 2011-10-21
Hi everyone,
Finally after installing Ubuntu 11.10 I got my DVB-S2 card working.Here is the model: [http://linuxtv.org/wiki/index.php/Azurewave_AD_SP400_CI_(VP-1041)](http://linuxtv.org/wiki/index.php/Azurewave_AD_SP400_CI_(VP-1041)))

So, I wanted to test it. I followed these instructions:
[http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php)

Everything went fine, but when I try to watch a channel, I got the following

================================================================
[B]user@desktop:~$ mplayer dvb://'The Voice'
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team

Playing dvb://The Voice.
dvb_tune Freq: 12524000
TS file format detected.[/B]
================================================================

That's it, it doesn't go any further. It's stays like that (I waited 15 min) and nothing happens.
FYI, I can play .TS files with Mplayer, no problems at all, but not Live TV.

Any idea what the problem could be?
Thanks

---

