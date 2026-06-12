---
title: "vsound not working in Dapper 64-bit"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by huckleberry on 2006-11-04
[FONT="Arial"][SIZE="2"]I am trying to rip some streaming audio from the internet using vsound.

I have an AMD-64bit computer running Dapper

Here is the command I am trying to run.[/SIZE][/FONT]
[FONT="Courier New"][SIZE="1"]
jlparker@Ubuntu-Linux:~/Desktop$ sudo vsound -f phc09022006.wav -v -k -d -t -a 30 /opt/realplayer/realplay rtsp://a754.v5559f.c5559.g.vr.akamaistream.net/ondemand/7/754/5559/v001/mpr.download.akamai.com/5559/phc/2006/09/02_phc.rm
Password:
Output file:   phc09022006.wav
Temp AU file:  ./vsound6255.au
About to start the application. The output will not be available
until the application exits.
Warning: LD_PRELOAD="/usr/lib/vsound/libvsound.so"
ERROR: ld.so: object '/usr/lib/vsound/libvsound.so' from LD_PRELOAD cannot be preloaded: ignored.[/SIZE][/FONT]

[FONT="Arial"][SIZE="2"]The vsound6255.au is never created.  I have tried numerous combinations of vsound options, but I just can't seem to get it to work.  Does any one have any suggestions?  I searched the forums, but was unable to find any helpful post on this topic.

Thanks,

[/SIZE][/FONT]

---

