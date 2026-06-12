---
title: "Extremely slow CD write speed"
date: 2008-06-08
forum: Multimedia Software
---

### Post by mirzmaster on 2008-06-08
For the last little while I've been experiencing some extremely slow CD write speeds that affect me whether I'm burning an audio CD or a data CD.  The problem also exists with both Gnomebaker and Brasero as well.

When a burn session starts, it appears to be going well until all of a sudden the write speed drops to be about 2X.  As you may know, this means it takes about 30 mins to burn an 80 min CD.  :(

For starters, hdparm does report that DMA is enabled for the burner in question, so I know that isn't the issue:

```
/dev/hdb:
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

While performing a burn in Brasero this evening, I managed to save the log output, which I've attached to this post.  Here is the interesting snippet:

```
...
...
...
BraseroWodim stdout: Track 01:   34 of  700 MB written (fifo   9%) [buf 100%]  12.7x.
BraseroWodim called brasero_job_set_rate
BraseroWodim called brasero_job_set_written_session
BraseroWodim called brasero_job_set_current_action
BraseroWodim called brasero_job_start_progress
BraseroWodim stdout: Track 01:   35 of  700 MB written (fifo   7%) [buf  93%]  12.2x.
BraseroWodim called brasero_job_set_rate
BraseroWodim called brasero_job_set_written_session
BraseroWodim called brasero_job_set_current_action
BraseroWodim called brasero_job_start_progress
BraseroWodim stdout: Track 01:   36 of  700 MB written (fifo   4%) [buf  99%]  12.8x.
BraseroWodim called brasero_job_set_rate
BraseroWodim called brasero_job_set_written_session
BraseroWodim called brasero_job_set_current_action
BraseroWodim called brasero_job_start_progress
BraseroWodim stdout: Track 01:   37 of  700 MB written (fifo   1%) [buf 100%]  12.3x.
BraseroWodim called brasero_job_set_rate
BraseroWodim called brasero_job_set_written_session
BraseroWodim called brasero_job_set_current_action
BraseroWodim called brasero_job_start_progress
BraseroGenisoimage stderr:   5.58% done, estimate finish Sun Jun  8 01:15:33 2008
BraseroGenisoimage called brasero_job_set_progress
BraseroGenisoimage called brasero_job_start_progress
BraseroWodim stdout: Track 01:   38 of  700 MB written (fifo   0%) [buf  19%]   4.7x.
BraseroWodim called brasero_job_set_rate
BraseroWodim called brasero_job_set_written_session
BraseroWodim called brasero_job_set_current_action
BraseroWodim called brasero_job_start_progress
BraseroWodim stdout: Track 01:   39 of  700 MB written (fifo   0%) [buf   6%]   1.8x.
BraseroWodim called brasero_job_set_rate
BraseroWodim called brasero_job_set_written_session
BraseroWodim called brasero_job_set_current_action
BraseroWodim called brasero_job_start_progress
...
...
...
```

From the very get-go, the fifo buffer -- which starts at 100% -- dwindles down until it's empty, at which point the burn speed drops drastically as the fifo buffer remains at 0% for the remainder of the write session.

Does anyone know how I can prevent this zero-percent fifo buffer issue?  I'm not very keen on dropping the CD write speed in order to get this working.  :\

Another interesting note:  When trying to burn an ISO using Nautilus' "Write to Disc..." option does not result in any slowdown.  Does that mean my problem could be a cdrecord problem?  What is the root cause though?

---

### Post by Bubba64 on 2008-06-08
Why are you using those when you have the cd dvd creator in places it will burn a cd in about 30 seconds, faster then you can write down the songs. Those media devices are horrible in my opinion.

---

### Post by mirzmaster on 2008-06-08
> **Bubba64 said:**
> Why are you using those when you have the cd dvd creator in places it will burn a cd in about 30 seconds, faster then you can write down the songs. Those media devices are horrible in my opinion.

Thanks for the feedback, Bubba, however I prefer to use more advanced tools like GnomeBaker, and especially Brasero.  Brasero gives me the option of burning CDs without the 2 second gap in between tracks, which is a feature I rely upon.

---

### Post by mirzmaster on 2008-06-10
Another data-point:  It appears that the Nautilus built-in CD/DVD writing utility works just fine.  This is looking more and more like a cdrecord issue.

---

### Post by baggos123 on 2008-06-21
I have exactly the same problem however even in the Nautilus built in burning utility.

---

### Post by diskotek on 2008-06-22
i have a big problem with Brasero: it uses whole processor and i can not do anything while i'm burning cd's. dma is enabled and i'm using amd athlon 64 +3000, with 1 gigs of ram. is there any known issue?

---

### Post by mirzmaster on 2008-06-24
* bump *

---

### Post by medic2000 on 2008-07-02
Bump again

---

### Post by johndoe20081026 on 2009-03-27
(Bump)

I have this same issue. Only difference is that the Gnome defualt burner is slow, too, along with Brasero and K3b. It's really killing me.... Takes 1~4 hours to burn a 4 Gig DVD...

Can we *please* fix this?

---

