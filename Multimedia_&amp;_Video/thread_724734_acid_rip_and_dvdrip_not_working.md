---
title: "acid rip and dvd:rip not working"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by mohnkern on 2008-03-14
I read through the forms, and I'm seeing something no one else has reported.

Acidrip -- I put the DVD in read in DVD, select the Track I want to rip, and click on Start, and it immediately says "done" with no warning message, and no errors.

DVD:rip -- It seems to start okay, gets up to 70%, and then says its done.  The last thing in the log file is:

Fri Mar 14 22:14:26 2008 Executing command: execflow tcprobe -H 25 -i /home/mohnkern/dvdrip-data/fellowship/vob/001/ && echo EXECFLOW_OK
Fri Mar 14 22:14:28 2008 DVD TOC reported wrong framerate 29.97, adjusted frame rate to 23.976 and frame count to 145456
Fri Mar 14 22:14:30 2008 Program stream units calculated
Fri Mar 14 22:14:30 2008 Not enabling PSU core, because this movie has only one PSU.
Fri Mar 14 22:14:30 2008 Job 'Process title #1' finished
Fri Mar 14 22:14:30 2008 Job 'Rip - title #1' finished


However when I go to the directory there's an avi directory, but no avi, and the vobs are there.

Any ideas?

---

### Post by xc3RnbFO8P on 2008-03-16
Install this:

> wget -c [http://packages.medibuntu.org/pool/f...ntu4_amd64.deb](http://packages.medibuntu.org/pool/f...ntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
sudo /usr/share/doc/libdvdread3/install-css.sh 

Edit: do you have a 64 bit computer? If so did you install w64codec?
> sudo apt-get install w64codecs

---

