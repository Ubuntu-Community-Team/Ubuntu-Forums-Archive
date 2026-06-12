---
title: "&quot;Sound Juicer could not find any CD-ROM drives to read&quot;"
date: 2008-08-12
forum: Multimedia Software
---

### Post by stephen67 on 2008-08-12
I have 7.10 running on a PS3.

But I can't play CDs or DVDs.

I have been through all the low level stuff.

file -s /dev/scd0 

deals with a data disk just fine, and identifies a DVD as UDF and reports the label correctly.

But inserting a CD or DVD gives no response.

Launching Sound juicer gives the subject error message.

Can anyone suggest what I should try?

Thanks
Stephen

---

### Post by qwertzqwertz on 2008-11-01
Hi Stephen,
a late answer, but also for anyone else having the same problem. I have Fedora 8 running. There you need to start the haldaemon in order to get sound-juicer working fine.
Start a console as Root, go to /etc/init.d  and type:
  ./haldaemon status
--> this will tell you whether haldaemon is running or not.
If it is not running, you may type:
  ./haldaemon start
to get it running.
Then restart sound-juicer, and it should find your CDROM drive.
If it solves the problem, you might want to add haldaemon to the services started automatically with system start. The "checkconfig" package is a nice tool to do this.

Once again - this is for Fedora. Dont know how it is with Ubuntu.

Hope that helps.

regards -

---

