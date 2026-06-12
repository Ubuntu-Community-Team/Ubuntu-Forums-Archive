---
title: "Rhythmbox on Karmic does not save podcast feeds"
date: 2009-12-28
forum: Multimedia Software
---

### Post by Mike Schafir on 2009-12-28
I just upgraded to Karmic from Hardy and Rhythmbox will not save my
podcast feeds.  The feed loads when added, but is not there the next time
rhythmbox is started.  Any ideas on how to fix?

thanks.

---

### Post by Mike Schafir on 2010-01-03
Does anyone have any insight into this problem. Is it a configuration issue or a problem with Karmic?

---

### Post by Mike Schafir on 2010-01-03
I figured out the solution myself by removing the "rhythmbox" directory in ~/.local/share, then completely uninstalling and reinstalling rhythmbox.

Rhythmbox created a new rhythmdb.xml file and all is well.

Hopefully this will help others who run into this problem.

---

