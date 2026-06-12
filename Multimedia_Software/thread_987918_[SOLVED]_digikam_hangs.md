---
title: "[SOLVED] digikam hangs"
date: 2008-11-20
forum: Multimedia Software
---

### Post by Petermet on 2008-11-20
Briefly, it seems that if you try to point Digikam to a location other than one in the home folder (as, in my case, a portable drive where my images are), it hangs on the splash screen before opening, with a pop-up error message to the effect that "Failed to update the old database to the new database format. This error can happen if the album path does not exist or is write protected"..(neither of which is true).."you need to adjust the Album Path in digikam's configuration file". 

BUT as the app has hung before loading, there is no way to access the configuration window by means of which I unwittingly mis-pointed it in the first place. When closing the pop-up, the splash-screen also closes and the entire app shuts down.

---

### Post by Petermet on 2008-11-20
Sorry to have posted - I have managed to find the configuration file and remove it, by searching via "find" in the terminal, rather than using the search in nautilus.

---

