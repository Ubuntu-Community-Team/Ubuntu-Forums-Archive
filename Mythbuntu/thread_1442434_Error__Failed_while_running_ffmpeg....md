---
title: "Error : Failed while running ffmpeg..."
date: 2010-03-30
forum: Mythbuntu
---

### Post by waldick on 2010-03-30
I'm running 9.10
trying to burn a dvd with mytharchive...and i keep getting this error: "Error: Failed while running ffmpeg to re-encode video" 

I get this error if i try to burn either videos or recorded shows.

Other than this problem i have been able to get my mythbox up and running with the help of the posts in this forum, however, i have not been able to find a solution...

help please....

---

### Post by klc5555 on 2010-03-30
You will need to have installed/enabled all the usual dvd support and proprietary codecs, etc. in myth control center.

Sometimes this sort of ffmpeg thing is a missing library or codec that ffmpeg is looking for to do the particular encode. If it is in this case, then typing "ffmpeg" from a prompt may, in addition to listing all the options ffmpeg is compiled for, list one or another library it can't find for one of its compiled-in options. If this happens, then you'll need to find the package that contains the missing library and install that package. 

The search function at packages.ubuntu.com is valuable for researching what package owns a pesky missing library, if this turns out to be the problem, and then the package may be installed using the usual methods, apt-get or synaptic.

---

