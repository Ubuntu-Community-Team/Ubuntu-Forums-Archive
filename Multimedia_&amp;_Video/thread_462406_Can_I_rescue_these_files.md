---
title: "Can I rescue these files?"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by tinker123 on 2007-06-02
Hi;
About a week ago I was Unbuntu 6.10 with the latest K3B installed because I think it is the best cd/dvd maker for linux around.

For various reasons I decided to to a clean install of Unbuntu 7.04, so I used K3B to make a mixed DVD that held all of my data.  I did not test the DVD before I blew away my system and my data.

Whenever I try to open a file from this DVD I get this error message
=============================================================
 The filename "20061017_rae_sikora_1.mp3" indicates that this file is
of type "MP3 audio". The contents of the file indicate that the file
is of type "plain text document". If you open this file, the file
might present a security risk to your system.

Do not open the file unless you created the file yourself, or received
the file from a trusted source. To open the file, rename the file to
the correct extension for "plain text document", then open the file
normally. Alternatively, use the Open With menu to choose a specific
application for the file.
===============================================================






If I try to copy any file off of the DVD it comes out at zero size ( the proper size is on the DVD ) and I get this error message:

===========================================================
 Error "I/O error" while copying "/media/200...ora_1.mp3".
==========================================================




I get this output when running dd on it

=========================================================
root@Wisdom:/dev# dd if=/dev/dvd of=temp.isobs=32k
211328+0 records in
211328+0 records out
108199936 bytes (108 MB) copied, 18.4958 seconds, 5.8 MB/s
root@Wisdom:/dev#
========================================================== 


Even though it says there is only 108 MB on the disc running du tells me  I have 2.6 gigs worth of information on the dvd:

This is the command I used:
du -ch /media/2007May27_Backup/

I got a LONG list of files and directories that ended in these
entries:

1.1M    /media/2007May27_Backup/steve/locale
2.6G    /media/2007May27_Backup/steve
2.6G    /media/2007May27_Backup/
2.6G    total


Is there any chance of recovering these files or should I give up the data as lost?

Thanks in advance for any info

Steve

---

