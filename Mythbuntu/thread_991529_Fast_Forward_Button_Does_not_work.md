---
title: "Fast Forward Button Does not work"
date: 2008-11-23
forum: Mythbuntu
---

### Post by shanep00 on 2008-11-23
I have a widows media center USB remote that stopped working today.  The remote seems to be dead because it no longer lights up and is not sending any signal (even with new batteries).  Anyway, I ended up getting my old REPLAYTV remote to work with the USB ir receiver. Everything seems to work except for fast forward.  It is clearly sending the FF signal.  When I put LIRC in test mode the   replaytv remote sends the correct code as defined in the replaytv config file I got from the LIRC site.  

Any ideas why fast forward would not work?  When viewing a recording, hitting FF does nothing.  I can use rewind but no FF.

Thanks,
paul

---

### Post by shanep00 on 2008-11-23
I just fixed my own problem.  I had to add a Forward section to the mythtv file in the .lirc folder in my home directory.  I don't know why one got created without Forward.

---

