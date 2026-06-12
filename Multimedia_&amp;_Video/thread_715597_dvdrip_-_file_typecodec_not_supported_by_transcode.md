---
title: "dvdrip - file type/codec not supported by transcode"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by Crash90 on 2008-03-05
I have run into a bit of a snag with Dvd Rip (it looks more specifically transcode). I have tried ripping the two movies:

Animal House
Transformers

Both times, when trying to rip a terminal pops up and reads

```
Catched Callbacks Exception: Error executing command execflow tcprobe  -i /home/peter/dvdrip-data/AH/vob/004/ && echo EXECFLOW_OK:
EXEC_FLOW_JOB_PID=28215
[fileinfo.c:118] file read error: No such file or directory
[tcprobe] unknown file type
[tcprobe] filetype/codec not yet supported by 'transcode'
 at /usr/share/perl5/Video/DVDRip/JobPlanner.pm line 378

```

Things I have tried:

Updating transcode - Did not solve 
Updating libdvd - Did not solve

Now I am stuck.

---

### Post by xc3RnbFO8P on 2008-03-05
Try this:

> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
> sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb



> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
> sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by Crash90 on 2008-03-05
> **Ringi said:**
> Try this:

Jackpot! Thanks given!

I will do my best to forward this knowledge onto others!

---

