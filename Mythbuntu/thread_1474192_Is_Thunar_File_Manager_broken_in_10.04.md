---
title: "Is Thunar File Manager broken in 10.04?"
date: 2010-05-05
forum: Mythbuntu
---

### Post by neutron68 on 2010-05-05
Since upgradeing from 9.10 to 10.04, I noticed that Thunar File Manager doesn't work right.

I can click on File System and see the list of folders.  If I click on 'etc' I am shown the contents of that folder, and then I can't do anything:
- can't activate any of the files, 
- can't look into any folders.  
All I can do is go back a level to File System.

I even went to Synaptic and reloaded Thunar.  It's still broken.

Is anyone else seeing this broken behavior?

Eric

---

### Post by slamhound on 2010-05-05
I think there is a bug out there on this.  I think there are a couple workarounds.  One is to not use detailed list to view files.  I think using icon-view works (but try some different options to see which works).  I also think I read that hitting enter once you select a file rather than double clicking might prevent this problem.

---

### Post by neutron68 on 2010-05-05
Can we roll back to an older version of Thunar?

---

### Post by straxus on 2010-05-06
The bug is in GTK, so an older Thunar would not help.  I've found the best solution for now is to change to single click mode in Thunar.  Only double clicks are bugged.

---

### Post by neutron68 on 2010-05-06
That's good information to know!

Also, thanks for the workaround!

Eric

---

### Post by 2DC on 2010-05-10
Thats great! Thanks for the tip. Changing to "Compact List View" also work by the way. :)

---

### Post by zagor on 2010-06-18
Also, if you change to single click mode instead of double click it works.
It's annoying, but works....
PCManFM has the same issues (and the same workaround...).

---

