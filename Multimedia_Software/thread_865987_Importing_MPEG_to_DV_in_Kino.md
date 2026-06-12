---
title: "Importing MPEG to DV in Kino"
date: 2008-07-21
forum: Multimedia Software
---

### Post by p221072 on 2008-07-21
Hello,
I bought a new videocamera Sony DCR SR72 and found out this model save clips in MPEG2 format.
Kino allows only to work on DV format, so I have 2 questions:
1) Is there any way to import many clips at the same time from MPG to DV in Kino?
2) Does converting from MPG to DV bring to any quality loss?
Thanks,
Paolo

---

### Post by Robstarusa on 2008-07-21
> **p221072 said:**
> Hello,
I bought a new videocamera Sony DCR SR72 and found out this model save clips in MPEG2 format.
Kino allows only to work on DV format, so I have 2 questions:
1) Is there any way to import many clips at the same time from MPG to DV in Kino?
2) Does converting from MPG to DV bring to any quality loss?
Thanks,
Paolo

I have a Canon HV20 and started playing with this yesterday.

First, Kino in the packages is outdated.  I can't do captures with it for some reason.  However "dvgrab" seems to work for me capturing directly from the camcorder.  Actually, once it's hooked up, I can run dvgrab, and it will start/stop the playback, etc.  It also picks up the date, time, etc and displays it if you run "dvgrab -showstatus".  The only thing that did not work was the raw format.  I had to try "dvgrab -f hdv -showstatus /path/to/outpufile".

Rob

---

