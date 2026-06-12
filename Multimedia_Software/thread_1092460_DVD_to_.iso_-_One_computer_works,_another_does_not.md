---
title: "DVD to .iso - One computer works, another does not"
date: 2009-03-10
forum: Multimedia Software
---

### Post by jrj127 on 2009-03-10
I am trying to take my DVD collection and rip them to my home media server.  I am running into situations where my fast desktop has encryption errors using Brasero and K3b on some DVDs (it works on other DVDs).  However, my ThinkPad can successfully rip the problematic DVDs.  Both systems run Ubuntu-8.10 and seem to have the same packages installed.

Below is the system configuration and debugging output from both Brasero and K3b.  Does anyone have any suggestions?  Yes, I have libdvdcss2 installed.  Could I be missing some package?


Ubuntu 8.10 Intrepid Ibex
Kernel:  2.6.27-13-generic
libdvdread3 0.9.7-11ubuntu2
libdvdcss2 1.2.10-0.2medibuntu1
Sony DRX-830U
TSST SH-S203N

Brasero-0.8.2
GUI error:
```
Error while burning: Error reading video DVD (fatal error in vts css key).

```

View log:
```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_output_size_for_current_track
BraseroDvdcss stopping
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss output set (IMAGE) image = /home/jared/brasero.iso toc = nil
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_set_use_average_rate
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_start_progress
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_error
BraseroDvdcss finished with an error
BraseroDvdcss asked to stop because of an error
error = 1
message = "Error reading video DVD (fatal error in vts css key)"
BraseroDvdcss stopping
Session error : Error reading video DVD (fatal error in vts css key) (brasero_burn_record burn.c:2524)

```


K3b-1.0.5 (Using KDE 3.5.10)
GUI Window:
```
Found encrypted DVD.
Writing image file to /home/jared/k3b.iso.
Unmounting source medium
Retrieving all CSS keys. This might take a while.
Failed to retrieve all CSS keys.
Video DVD decryption failed.
Removed image file /home/jared/k3b.iso

```

Show Debugging Output:
```
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-13-generic
Devices
-----------------------
TSSTcorp CDDVDW SH-S203N SB01 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

SONY DVD RW DRU-830A SS22 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]


```

---

### Post by cariboo on 2009-03-10
It looks like you don't have libdvdcss2 isntalled. To install libdvdcss2 you need to enable the [Medibuntu]("http://help.ubuntu.com/community/Medibuntu#Adding the Repositories") repositories. Once the repositories are enabled, open Synaptic and search for libdvdcss2 and install it.

Jim

---

### Post by jrj127 on 2009-03-10
As I said in my post, libdvdcss2 is installed already, version 1.2.10-0.2medibuntu1.

I removed the package and reinstalled.  There was no change in the error.

---

### Post by jrj127 on 2009-03-16
Bump...

How could I not be able to copy a DVD to .iso if I have libdvdcss2 (version 1.2.10-0.2medibuntu1) installed?

---

### Post by inobe on 2009-03-16
that is some weird stuff

you said "some" do work ?



> I am running into situations where my fast desktop has encryption errors using Brasero and K3b on some DVDs (it works on other DVDs). However, my ThinkPad can successfully rip the problematic DVDs


hmm........

let's give k9copy a try !

i really don't understand this' but i will assume one or both of those apps being the culprit .

i hope my suggestion help's, i would hate to deal with a confusing situation like that.

edit: please shoot me a pm if that works' i would really like know, thanks

---

### Post by jrj127 on 2009-03-17
k9copy seems to have done the trick, thanks for the tip!

It seems very peculiar that the same two programs do not work on one machine but do work on another machine.  And why do some DVDs work and some do not work at all on the "bad" machine?

---

### Post by clancymf on 2009-03-17
I had the same problems with k9copy too.  I have switched to handbrakecli.  Its command line but is so easy to use and the options for ripping are great.  Now I rip my movies without any titles, xvid, and only the longest chapter.

---

