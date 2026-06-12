---
title: "Re: Sticky &quot;Comprehensive Multimedia...&quot;"
date: 2013-10-14
forum: Multimedia Software
---

### Post by Ed W. on 2013-10-14
The Sticky at the top of this section was last edited almost two years ago and Medibuntu doesn't appear to be supported anymore.  Is it all still good?  Sorry if it's a dumb question, maybe I should have posted this in the beginners section.

Specifically, I'm trying to watch "Firstrowsports" and it won't load in 12.04 and the system wants to open it with Archive Manager.  Also, I can't figgure out how to find k3b on the hard drive so I can add it to "open files with" list.

I did several searches, but no luck.  I guess my search fu is weak.

---

### Post by oldos2er on 2013-10-15
I'm guessing the app firstrowsports wants to install is Windows-only, and won't work on Linux. 

k3b is in /usr/bin/k3b

---

### Post by doug-ravennasprings on 2013-10-16
Complete waste of time

---

### Post by deadflowr on 2013-10-16
medibuntu has been closed.
But it shouldn't matter as far as running and watching DVDs is concerned.
The libdvdcss(2) has been moved to videolan and the install script has been updated to reflect that.

If you paid any attention to the updates which have been made in the last week, you might have noticed one for libdvdread4, that update changed the 
/usr/share/doc/libdvdread4/install-css.sh script.

I take it that the firstrowsports is a movie of some kind?

No clue as to why archive manager wants to open it. Try right clicking it and choose other application.

---

