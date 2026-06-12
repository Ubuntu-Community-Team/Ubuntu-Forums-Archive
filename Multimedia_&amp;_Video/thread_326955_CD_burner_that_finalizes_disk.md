---
title: "CD burner that finalizes disk?"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by Coburn on 2006-12-28
I'm trying to burn CD's that I can run on the Windows computer at work.  The burners I've tried so far have a quirk.  They just move files to the disk.  They don't "finalize" the burn.

I've tried the burn utility in Nautilus, Gnomebaker, and a couple others.

It seems older CD players don't recognize content on a disk that has not undergone this final step.  And that's what we have at work.

The paradigm I'm up against here seems to be that advancing technology leaves older approaches in the dust.  It's the same thing I ran into when I tried to install the Dapper CD on a computer with 228 M of RAM.

Before I try any new approaches (e.g. mkisofs from term)  I'd like to hear back if anyone's solved this for themselves.

Thanks

---

### Post by 900i on 2006-12-28
Have you tried K3B!

---

### Post by deadgobby on 2006-12-28
Yep secound that one. K3B is good. :)

---

### Post by Coburn on 2006-12-29
OK, I admit.  I took the word of the IT at work on this one.

After reading the info on mkisofs, I think my trouble might be that Nautilus and Gnomebaker are burning in plain ISO9660 or Joliet mode, and not writing files that Windows can read.  There are options for this kind of thing, and maybe the utilities are not using them.

So, maybe I have to learn to use mkisofs.

I'd appreciate a cheat here.  What might be the format to build an ISO readable by Mac and Windows from a single directory?

Thanks

PS-- I prefer not to use KDE utilities.  Sometimes they conflict with my Gnome stuff.  Just a personal preference.

---

### Post by Coburn on 2007-01-05
But, hey, it works.

Thanks, guys

---

