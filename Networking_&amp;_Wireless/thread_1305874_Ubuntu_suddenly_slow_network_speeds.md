---
title: "Ubuntu suddenly slow network speeds"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by Jaesin on 2009-10-30
I use both Win 7RC, 9.04 and now 9.10 and it used to be that I could get the same speeds on 9.04 and win 7, but when I went to download the iso for 9.10 from 9.04 it told me that it would take 3 days to complete.  I tried another mirror, and it said that it would take 4 hours.  So I rebooted into 7 and it took me 30 mins.  The speeds in Linux were at best 56 kbs.  Under 7 they were 300+.   Was there an update to 9.04 that carried over into 9.1 and if so how do I fix it, also Synaptic has the same problem with speed.

my connection is dsl 6mb speed, though i normaly get 4mb
a month ago everything was normal.

---

### Post by dj-toonz on 2009-10-30
No nothings wrong with your connection or mine, as Karmic has only been out for just over 24 hours, the servers are still being hammered, so everything what's being used i.e software / center or the repos are going to be slow for a few days :(, right now i'm downloading adobe reader & getting 4 kb/s under jaunty 600 kb/s+

---

### Post by Jaesin on 2009-10-30
if thats the case, why did it only take windows 30 min. to download, aren't they all the same servers?  why would it make a difference what OS is used to dl?

bye the bye, i HOPE thats all it is, as i much perfer 9.* to 7

---

### Post by Jaesin on 2009-12-03
After a series of updates, 9.10 works fine.

---

### Post by Zenith88 on 2009-12-05
Does not work fine for me.

I just migrated from F12 to Ubuntu Studio 9.10 and noticed that transfer from Windows share dropped from 6.2 MB/s to 4.6 MB/s on 1.5 GB files.

$ uname -a
Linux host 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux
$ smbd -V
Version 3.4.0

---

