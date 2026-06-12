---
title: "Devede &amp; Disk Space"
date: 2009-12-06
forum: Multimedia Software
---

### Post by lizandeen on 2009-12-06
I have a 500g xp and ubuntu 8.10 dual boot system (169g and 328g respectively) with 2g of ram. The problem is that when I try to create an iso with Devede I'm told "Conversion failed Maybe you ran out of disk space?". Any ideas? Thanks in advance

---

### Post by mc4man on 2009-12-06
Far removed from 8.10 but if you get a chance search mencoder and devede in synaptic and post what versions are installed ( r. click on packages -> properties will show full name

Sorta seems like  out of sync mencoder and devede versions, does the error occur right after the encoding is finished?

---

### Post by lizandeen on 2009-12-07
It's Mencoder 2:1.0~rc2-Oubuntu17+medibuntu1 and Devede 3.11-Oubuntu1 (both installed at the same time using Add/Remove...).The error does seem to occur right after the encoding is finished and if it isn't then it's right before. I should also point out that when I used this version of Devede on an Ubuntu only 500g I had no problems. Could it be that I need to change the size of the swap partition?

---

### Post by mc4man on 2009-12-07
assuming you do have plenty of available space ( min. 2x the expected .iso size) I'd try this first.

Replace your medibuntu mencoder with the intrepid repo version

2 ways

Search mencoder in synaptic, highlight mencoder -> package tab and see if a 'force version' is availabe. If so, then expand and chosse the repo ver. ( mencoder (2:1.0~rc2-0ubuntu17) and then click apply.

Or in System -> Software Sources -> Third party disable medibuntu, close and reload.
Then search mencoder, mark for removal, apply. After done re-search and install mencoder

Then give devede a try again

---

### Post by lizandeen on 2009-12-08
Afraid no luck with that-any other ideas?

---

### Post by mc4man on 2009-12-08
> Afraid no luck with that-any other ideas? 
Not without loading up an intrepid live cd and seeing if the error can be reproduced
If nothing positive comes up , ck. back tommorow night.

The above was based on that the exact error/behavior was happening in karmic's devede when a mencoder other than the repo version was used. 

(though due to some changes in mplayer/mencoder in karmic, libavcodec also came into play which isn't the case in Intrepid.

---

### Post by eddier on 2009-12-08
Hey ho!  I,ve just run into the same problem with DeVeDe-3.14.0-0ubuntu5 and mencoder 2:1.0~(rc3)+svn2009.

It (devede) suggested"'maybe a bug with mencoder?"

Creation of an Mpeg from an avi works fine-creation of the iso image is the choker.

eddie

---

### Post by SuperSonic4 on 2009-12-08
What are your partitions formatted as?

---

### Post by eddier on 2009-12-08
Installing  the latest version (3.15.2) from Rastersoft seems to have solved the problem for me.

eddie

---

### Post by lizandeen on 2009-12-10
sorry for delay in replying , xmas nonsense etc, will download live cd now and try again. (But in reference to other posts, I have to point out I didn't have this problem until I started using dual boot)

---

### Post by KevNice on 2010-02-09
I had this problem, and I can say that it probably has nothing to due with dual-boot. I got this exact same error, right after I successfully made an .iso with similar files. No idea what's causing it as I've got plenty of disk space.

---

