---
title: "Backend crashing every day."
date: 2009-11-09
forum: Mythbuntu
---

### Post by sydneysuder on 2009-11-09
I am having to re-initialize my backend every day.  At first I thought it was autoexpire issues (I had a thread for that) but after changing some settings it seemed to have gone away.

But now it is back.  It seems that sometimes it stops working when it starts recording a program. I have a program (junkyard wars) scheduled for 6:30 pm everyday and it pretty much craps out recording that program every day.  Some days it doesn't (every now and then).

I have looked at the logs and see nothing that tells me what is going on. I'd appreciate if someone can shed a light on the situation.

[http://mythbuntu.pastebin.com/m73fe5b36](http://mythbuntu.pastebin.com/m73fe5b36)

BTW the logs show the frontend started on 10/27... I don't usually run the frontend on that machine so you can ignore it.

CONFIGURATION
Machine:  Virtual Machine running with 512MB Ram and assigned one of four cores on a Q9400 Intel CPU
HDD:       Two drives. System drive is 9 GB and data drive is 500GB (mounted on /video/videos

---

### Post by azmyth on 2009-11-09
Are you using 0.21 or 0.22?

---

### Post by sydneysuder on 2009-11-09
0.21 with myth repos enabled (Not ppa) because I have the hdhr dbvt version.

---

### Post by Skybolt83JL on 2009-11-09
That sounds like the fun I had with 0.21 and the pcHDTV HD5500 cards. Upgrading to trunk daily builds (0.22) helped greatly.

YMMV caveat emptor no warranty is implied or expressed.

---

### Post by OffAxis on 2009-11-09
> 512MB Ram and assigned one of four cores on a Q9400 Intel CPU
Is that enough processor power? I thought 3 GHz was the minimum recommended for HD recording...(myth website's down right now, otherwise I'd check)

---

### Post by nickrout on 2009-11-09
> **OffAxis said:**
> Is that enough processor power? I thought 3 GHz was the minimum recommended for HD recording...(myth website's down right now, otherwise I'd check)

There is no real minimum CPU for recording HD. Most HD comes as a digital stream requiring no processing, it is just dumped to disk.

Commflagging, transcoding or watching on the other hand...

---

### Post by sydneysuder on 2009-11-10
> **OffAxis said:**
> Is that enough processor power? I thought 3 GHz was the minimum recommended for HD recording...(myth website's down right now, otherwise I'd check)

Apart from crapping out once a day (and only once a day) it runs fine. I have had 3 frontends (two on livetv and one on playback) running at the same time whilst recording a program without any performance issues.

---

### Post by sydneysuder on 2009-11-10
> **Skybolt83JL said:**
> That sounds like the fun I had with 0.21 and the pcHDTV HD5500 cards. Upgrading to trunk daily builds (0.22) helped greatly.

YMMV caveat emptor no warranty is implied or expressed.


I have the mythrepos installed, how is that different? or is it the ppa one that I need to enable to go to .22.

I check for updates every day and there is nothing. The only time that there were any available was when I first installed (and the HRHD tuners wouldn't work)

---

