---
title: "Copying a DVD"
date: 2009-07-09
forum: Multimedia Software
---

### Post by billybag on 2009-07-09
I am having a lotof problems trying to copy DVDs. I have tried Brasero:
```

Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_output_size_for_current_track
BraseroDvdcss stopping
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss output set (IMAGE) image = /tmp/brasero_tmp_J03PWU.bin toc = none
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_set_use_average_rate
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_fd_out
BraseroDvdcss called brasero_job_get_image_output
BraseroDvdcss called brasero_job_error
BraseroDvdcss finished with an error
BraseroDvdcss asked to stop because of an error
	error		= 1
	message	= "Error while reading video DVD (read error)"
BraseroDvdcss stopping
Session error : Error while reading video DVD (read error) (brasero_burn_record burn.c:2599)


```

xDVDShrink:
```

   BATCH ERRORS REPORTED
   There were 8 failures in the rip of this multi-
   episode DVD. The titles numbered 1 2 3 4 5 6 7 8 were not ripped.
   A 'fail' file has been written. You may now check the
   source DVD; pehaps trying to singly rip the titles listed
   above. If you can fix the problem re-start 'xdvdshrink'
   and click the 'Restart' button in the TV Show/Episode mode
   to try to re-process the failed rips.

   See the episode logs in your home directory!

   Hit any key to exit xdvdshrink    

```

and K3B:
```

System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-13-generic
Devices
-----------------------
TEAC DVD+-RW DVW28SLC A.06 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, SAO/R96P, SAO/R96R, Restricted Overwrite, Layer Jump]

K3bDataTrackReader
-----------------------
reading sectors 0 to 2172415 with sector size 2048. Length: 2172416 sectors, 4449107968 bytes.
using buffer size of 128 blocks.
Problem while reading. Retrying from sector 2110638.
Read error in sector 2110638.
Read a total of 2110638 sectors (4322586624 bytes)

```

all speeds set to lowest. 

Are their any other methods?

---

### Post by HappyFeet on 2009-07-09
Do you have libdvdcss2 installed?

You can also try K9Copy, it works for me.

---

### Post by billybag on 2009-07-10
Hey, thank you for the advice, I downloaded K9Copy. In an effort to waste as more blank cds, Should i create an iso or rip the dvd?

thanks

---

### Post by dE_logics on 2009-07-10
It's clearly a CD problem...that CD is bad, that's what I think...and all the software logs say.

---

### Post by e24ohm on 2009-07-10
> **billybag said:**
> Hey, thank you for the advice, I downloaded K9Copy. In an effort to waste as more blank cds, Should i create an iso or rip the dvd?

thanks
I create .iso; however, i have not been able to create an .iso from a few of my DVDs.

---

### Post by billybag on 2009-07-10
K9Copy **appears** to be working. It is taking a while (decided to choose the option of backing up as .iso)

---

### Post by billybag on 2009-07-10
K9Copy worked! Thank you!!!

---

