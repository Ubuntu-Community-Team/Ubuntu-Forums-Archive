---
title: "Microsoft Digital Sound System?"
date: 2006-07-29
forum: Multimedia &amp; Video
---

### Post by kevmacmills on 2006-07-29
Greetings, all!

After spending many years working on UNIX systems (FreeBSD, AIX, Solaris, etc.) for a living, I decided to take the plunge at home and spent the day today setting up Ubuntu.  Great stuff!

So far, everything as pretty much Just Worked and I find that very encouraging.  One thing that is giving me trouble, however, is my sound system.  I have the Microsoft Digital Sound System which is a USB-driven set of speakers and a subwoofer.  The sound system was detected correctly and I do get sound (so, why am I complaining?), but the volume control is what is giving me trouble.

First, the volume level is amazingly high.  Now, I certainly enjoy working out the subwoofer, but my neighbors don't ;)  After a bit of fiddling with the alsamixer, I found out what is going on:  When I attempt to adjust the volume (either with the volume control applet or with the volume buttons on the speaker) I'm actually adjusting the bass volume!  I can see this when I run alsamixer - the Desktop volume is pegged at 100% and the Bass volume is what moves when I adjust the volume.  Strange, eh?

Can anyone point me in the right direction here?  

Thanks for any help!

---

