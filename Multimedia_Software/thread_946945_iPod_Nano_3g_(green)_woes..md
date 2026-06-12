---
title: "iPod Nano 3g (green) woes."
date: 2008-10-13
forum: Multimedia Software
---

### Post by goofyheadedpunk on 2008-10-13
I have been unable to create a proper iTunesDB for my green iPod nano with banshee 1.2.1, gnupod 0.98.3 or hipo 0.6.1, either through completely rebuilding the database or by incremental adding. I'm using Ubuntu 8.04.

Here's the situation: I recently bought a third generation, green iPod nano for my wife. A single album was loaded onto the device with iTunes as part of the gift. After a few days she used banshee to upload more music. No errors were reported and the ejection process worked correctly. After this point, however, the iPod reported that it had "No Music". I assume this is because banshee failed to cryptographically sign the iTunesDB appropriately?

Anyway, I reformatted the iPod with iTunes (which noted that iTunes was unable to read the device's database) and re-loaded the music running banshee --debug. No errors were presented and I still recieved "No Music". Forcing banshee to rebuild the database by deleting it from the device did not fix the issue.

Moving on to gnupod, I attempted the procedure in section 4.11 of the manual, recovering lost files. No errors were given during the process and all went well, seemingly. However, "No Music" still plagued me. Attempts to use Floola and Yumipod failed, both sigsegv.

This sucks, of course. I've been given no errors, nothing hard and fast to latch onto, but still something is amiss. Does anyone have ideas or suggestions?

---

### Post by rinzy20 on 2008-10-13
[http://ubuntuforums.org/showthread.php?t=906217&highlight=ipod+hack](http://ubuntuforums.org/showthread.php?t=906217&highlight=ipod+hack)

this might be of use........

---

