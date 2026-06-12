---
title: "VLC record limit for [TO] separate partition?"
date: 2010-08-31
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-08-31
I've started recording TV tuner input TO a separate partition, with this CLI command:

vlc pvr:// : pvr-device="/dev/video0" : pvr-radio-device="/dev/radio0" : pvr-norm=0 : pvr-frequency=-1 : pvr-bitrate=-1 ***--sout '#duplicate{dst=display,dst=std{access=file,mux=ts ,dst="/media/disk-1/output.mpg"}}'***

When I recorded to the 'Home' directory, it recorded up to 8.3G for an MPEG file. Now however, it is stopping at 4G record length.

Is this a default record length for recording TO a separate partition?


I found the [VLC CLI page](http://wiki.videolan.org/VLC_command-line_help), and I cannot find record limitation syntax of any sort. 
HELP?

---

### Post by Moozillaaa on 2010-08-31
Saving to FAT32 partition. DUH. 

 #-o

---

