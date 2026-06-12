---
title: "Brasero doesn't recognize my empty cd"
date: 2008-05-03
forum: Multimedia Software
---

### Post by ubuntu_jazzbach on 2008-05-03
Hi !!!

Exactly as the title of this thread: Brasero doesn't detect my empty cd, although it's correctly mounted !!! Does it have happened to anyone of you ??

Please help !! And thanks in advance :eek:

---

### Post by f37u5g0d on 2008-05-03
I have the same problem.  I have tried simple 700MB CD-RW's but IDK about regular CD-R's

---

### Post by neilevan814 on 2008-05-22
When I try to burn an iso image of a verbatim 700mb cd-r my empty disc is only getting recognized as 480mb?????  I checked on another cd drive on another computer in windows and my cd is not corrupted all 700mb available.
Neil

---

### Post by ERSchrager on 2008-05-24
Greetings all.  Same problem here.  New install of 8.04 using WUBI.  Rthymbox will create a Audio CD from a blank CD.  Nautilus wrote files to a blank CD, but Brasero would not write to those original blank CD's.  Said the cd's were full.

Here is the last few lines of the log file, if it can help anyone.

```
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_6RMHBU
	-exclude-list
	/tmp/brasero_tmp_YTMHBU
	-quiet
	-print-size
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 185233
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroWodim called brasero_job_get_action
BraseroGenisoimage stopping
BraseroMd5sum stopping
BraseroWodim stopping
Session error : Insufficient space on media (0 available for 185233) (brasero_burn_record burn.c:2270)
```

Roger

---

### Post by brnetonboy on 2009-01-02
I am having this trouble as well, hopefully somebody knows the solution by now? As soon as I "add" some files, it tells me it is oversized, and it seems to think the empty disc has a size of 0. 

Oversized (687 MiB / 0 in Data CD-R: "Blank CD-R Disc")

---

### Post by eagleton on 2009-01-02
There is a [bug]("https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/181703/") with the version of Brasero in Intrepid.

You can try to 1st burn a CD with Rhythmbox and then try again with Brasero. This seems to have done the trick for some people.

---

### Post by habtool on 2009-01-02
not the most elegant solution, but K3b worked for me.

sudo apt-get install k3b

---

### Post by martimcfly on 2009-03-16
Another quick solution slightly more elegant :) that worked for me:

sudo apt-get install gnomebaker

---

### Post by Chasalin on 2009-03-19
Have the same problems here after I installed VMWare... seems like some conflict. I tried brasero and K3B and both fail to detect an empty disc, although the system pops up with a 'Empty CD found! would you like to start brasero?'
Haven't tried GnomeBaker yet, but I always create an ISO before burning (habit from the good old days with no buffer underrun protection) so I just entered ```
$ cdrecord myfile.iso
``` and it works like a charm.
Can imagine that GnomeBaker uses *cdrecord* directly and will work just as well.

---

### Post by strfish7 on 2009-03-26
Gnomebaker worked for me...:)

---

### Post by sachinaxn on 2010-02-23
> **Chasalin said:**
> Have the same problems here after I installed VMWare... seems like some conflict. I tried brasero and K3B and both fail to detect an empty disc, although the system pops up with a 'Empty CD found! would you like to start brasero?'
Haven't tried GnomeBaker yet, but I always create an ISO before burning (habit from the good old days with no buffer underrun protection) so I just entered ```
$ cdrecord myfile.iso
``` and it works like a charm.
Can imagine that GnomeBaker uses *cdrecord* directly and will work just as well.


Really It is Working Very fine

Thakns 

sachin

---

