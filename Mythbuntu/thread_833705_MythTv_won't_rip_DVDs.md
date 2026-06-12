---
title: "MythTv won't rip DVDs"
date: 2008-06-18
forum: Mythbuntu
---

### Post by maynard001 on 2008-06-18
I get the following message when I try to use the "Import DVD" menu option within the MythTV Frontend:

Error: DVDPerfectThread read failed for 319 blocks at 1844
Job failed

I'm able to play the DVD fine...it just won't rip.  

Any ideas?

---

### Post by maynard001 on 2008-06-19
no ideas huh?

---

### Post by jlagrone on 2008-06-19
Check to make sure that you have the folders for ripping and videos and that the mythtv user can write to them.  If you are using the default settings, that'd be /var/lib/mythtv/vidoes and /var/lib/mythtv/videos/temp I believe (you can find where they are set in setup >> media settings >> video settings >> general settings and setup >> media settings >> video settings >> rip settings, respectively.

Make sure you have the lastest updates, in particular libdvdcss* (but since you can watch it, you should be fine)

If none of that works, look in /var/lib/mythdvd/temp/mtd.log and /var/log/mythtv/mythbackend.log and see if there are any other error messages

---

### Post by maynard001 on 2008-06-20
Thanks for the reply.  I'm pretty sure it's not a rights problem because I was able to rip one DVD out of about 10 that I've tried.

The only error message in the mtd log is that "DVDPerfectthread unable to read" error message.  I've installed libdvdcss and the w32 codecs.  I checked my /usr/lib directory and see them both in there.

---

### Post by jlagrone on 2008-06-20
It's probably just that particular disk then.  Check it for scratches and such.  Otherwise, myth seems to not like certain disks, but I've never had one that would play and not also rip.  Often removing and reinserting the disk helps.

---

### Post by uopjohnson on 2008-06-20
Are you sure you are able to play the disk just fine?  I'm not being sarcastic, there are lots of features, menus, and credits, and many other portions of a DVD that are included in a copy that you may not have watched.  There could be a problem there that is causng the rip to fail.  In my experience this error seems to come from new copy protection schemes on DVDs that are designed to prevent copying of the DVD and also cause problems with playing the DVD in myth, however if you can watch the DVD from start to finish in myth and you can't copy it then you have another problem.

---

### Post by Trollslayer on 2008-06-22
Some copy protection schemes corrupt certain sectors in a way that only commercial DVD players can handle them, I've had this a few times.

---

