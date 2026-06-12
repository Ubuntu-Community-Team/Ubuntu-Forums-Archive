---
title: "formatting a DVD+-RW disc"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by finite9 on 2006-11-22
Gnomebake and Graveman seem buggy in Dapper:

I cannot format a DVD+RW disc despite the man page for growisofs saying that I can.

If I do

```
growisofs -Z /dev/dvd=/dev/zero
```

in Terminal, then it formats the disc correctly.  If I try this in the GUI utilities, I get errors (graveman) and a seemingly successful operation (Gnomebaker) that in fact does nothing but read the disc.  Is this a known bug with Gnomebaker/Graveman?  Is it fixed in the version available in Edgy?

I tried to go through the Gnomebaker forums, but it's *all* spam in the forums...complete waste of time!

UPDATE:  Dagnabit!!  I wrote too soon...growisofs gives these errors at end of format.  Does nothing work???

4671373312/4700372992 (99.4%) @3.9x, remaining 0:05
4686970880/4700372992 (99.7%) @3.3x, remaining 0:02
:-[ WRITE@LBA=230540h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
builtin_dd: 2295104*2KB out @ average 3.6x1385KBps
:-( write failed: Invalid argument
/dev/dvd: flushing cache
/dev/dvd: stopping de-icing
/dev/dvd: writing lead-out
/dev/dvd: reloading tray

---

### Post by DOD1951 on 2006-11-22
Have you tried K3B? It has the function but I have not tried it.

---

### Post by finite9 on 2006-11-22
No, I don't want to use Qt apps on my Gnome system. Have you tried it?  They all use the same back end anyway...growisofs...so there shouldn't be any difference between gnomebaker/graveman/k3b.  NeroLinux might be different as it uses proprietary backend writer afaik.

---

### Post by finite9 on 2006-11-23
I read the manual for dvd+rw-format which is supplied as part of dvd+rw-tools and that does not work either:

finite9@redwood:~$ dvd+rw-format -force  /dev/dvdrw
* DVD&#65533;RW/-RAM format utility by <appro@fy.chalmers.se>, version 4.10.
* 4.7GB DVD+RW media detected.
* formatting 0.8/

...the "/" after 0.8 on the last line is a progress indicator that rotates, and it stopped after 0.8% and returned to the prompt.

I have checked in NeroExpress for Windows and the same Samsung DVD+RW 4x disc can be formatted, and a multisession disc can be created.  If I create the first session in Gnomebaker, then try to add more sessions in NeroExpress in WinXP, the Nero will not recognise the existing session nor try to import it.

Seems like the only function available for DVD+-RW users in Linux is to 'burn a disc'.  No formatting and no multisession.

I have not tried cdrecord-dvdpro or NeroLinux, so maybe there is more luck with those tools?

---

