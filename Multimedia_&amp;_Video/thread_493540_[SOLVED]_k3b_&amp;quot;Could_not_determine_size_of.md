---
title: "[SOLVED] k3b &amp;quot;Could not determine size of resulting image file&amp;quot;"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by Motorhead Kaze on 2007-07-05
Any idea what to do with this error and how to fix it?   I've seen another post online, but it didn't help me.  Using Feisty BTW.

I find it strange that K3B has the little green bar at the bottom which clearly reads "4.4Gb" but can't tell itself the size.  

:(

---

### Post by Motorhead Kaze on 2007-07-06
Wow, 7 hours, and no one knows the answer.  Does this help?

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
BENQ DVD DC DW1670 100 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, SAO/R96P, SAO/R96R, Restricted Overwrite, Layer Jump]

K3bIsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

Used versions
-----------------------
mkisofs: 1.1.2

mkisofs
-----------------------
Unknown file type (unallocated) /tmp/kde-kaze/k3bVideoDvd0/.. - ignoring and continuing.
Unknown file type (unallocated) /tmp/kde-kaze/k3bVideoDvd0/.. - ignoring and continuing.
/usr/bin/genisoimage: 
Implementation botch. Video pad for file VTS_12_0.BUP is -2292636
/usr/bin/genisoimage: Implementation botch. Video pad for file VTS_12_0.BUP is -2292636
/usr/bin/genisoimage: 
Either the *.IFO file is bad or you found a genisoimage bug.
/usr/bin/genisoimage: Either the *.IFO file is bad or you found a genisoimage bug.

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid VIDEO_TS -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-kaze/k3bm40TIb.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-kaze/k3bm8Lmsc.tmp -dvd-video -f /tmp/kde-kaze/k3bVideoDvd0

---

### Post by brianbarry on 2007-07-06
I've the same message before when trying to use a media file not multiplexed into DVD format, i.e. vob files and such.  I use avidemux to convert to *.mpg, then use QDVDAuthor to create the DVD structure, then use kb3 or Nero to burn to disk.  A really convoluted method compared to windows solutions, but I refuse to use windows and this is the best solution in Linux I've found to date.  Maybe someone else can provide a more direct solution.

Brian

---

### Post by Motorhead Kaze on 2007-07-09
Thanks Brian, I'm going to give that a try.  

Nero...I had been using Nero 6 when still using Windows, and I liked it very much, what the heck is up with Nero 3?  So far I've only seen that it burns from .iso files.  Oh well.  Anyway, thanks for the info.:)

---

### Post by Motorhead Kaze on 2007-07-10
:-s  
'Fraid I still don't have the solution to the K3B error message, but in fact I did have all the .bup/.vob pieces already (a full, decoded DVD movie) but K3B was just being annoying and not helping me.  I was however able to use Nero3 to burn the DVD the way it was without any problem at all.  So, the solution was:  Try another program.  Oh well, whatever works.

Wish that there were 1 program that would "Do it all" but then it would require lots of pros to make it, and it wouldn't be free.

---

### Post by phillywize on 2008-01-26
This thread is ancient history, but for those who search/google their way onto it, a PARTIAL workaround to this apparent issue with k3b (or one of the programs it invokes) is here:

[http://ubuntuforums.org/showthread.php?t=642825](http://ubuntuforums.org/showthread.php?t=642825)

Essentially what you should do is use makeisofs at the command line to produce an iso, THEN go to k3b and burn it (or burn it from the command line).  Whatever works for you.  But k3b seems not to like some vob/bup/ifo sets.  Sometimes I get the same error using mkisofs directly, but it seems to possibly be slightly more reliable.  The above link is to the commandline foo for building the iso.  It's VERY easy.

Edit:  if you're still getting errors from mkisofs, and are willing to do some work with a windows freeware app, this will give further help:

[http://www.coujo.de/ib2/index.php?showtopic=1707](http://www.coujo.de/ib2/index.php?showtopic=1707)

If anyone knows of an equivalent app for linux that will allow you to maipulate .ifo's, chime in!

---

### Post by Motorhead Kaze on 2008-01-26
HI!

Yes, it's an old post, but I never labelled it "Solved".  Thanks for posting.  I will look into this.  Currently, my K3b problem is here:  [http://ubuntuforums.org/showthread.php?t=676848](http://ubuntuforums.org/showthread.php?t=676848)

---

### Post by phillywize on 2008-02-02
> **Motorhead Kaze said:**
> HI!

Yes, it's an old post, but I never labelled it "Solved".  Thanks for posting.  I will look into this.  Currently, my K3b problem is here:  [http://ubuntuforums.org/showthread.php?t=676848](http://ubuntuforums.org/showthread.php?t=676848)

Bah, sorry, took a look and can't help you there.

Sounds like you found a fix for your DVD burning issue posted here, but just in case, and also for posterity and future seekers of an answer...here's a link to ifoedit, which, for me, runs perfectly well under wine, so no need to bemoan the lack of a corresponding linux tool.

[http://www.afterdawn.com/software/video_software/dvd-r_tools/ifoedit.cfm](http://www.afterdawn.com/software/video_software/dvd-r_tools/ifoedit.cfm)

Good luck with your other k3b/cd/dvd burning issues.

---

### Post by Motorhead Kaze on 2008-02-03
Ah hello again!

Yes all my K3b problems are solved. Sorry I never marked this solved only because I never solved THAT problem.  After reformatting my disc and putting Gutsy in fresh THAT problem was gone...and I got a new one. I'll go ahead and mark this puppy solved because the issue is over.

It's not relevant here, but heck, since I'm typing... I had a problem with "Wodim" in K3b and fixed it by going to settings/configurek3b/programs/user parameters/ and under cdrecord I typed in usr/bin/cdrecord .

---

