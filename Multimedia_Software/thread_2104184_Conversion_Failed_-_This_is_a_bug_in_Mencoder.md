---
title: "Conversion Failed - This is a bug in Mencoder"
date: 2013-01-12
forum: Multimedia Software
---

### Post by cottfcfan on 2013-01-12
Using Devede to convert .avi files to iso, everything works fine.
But converting .mp4 files to iso, I get the above message everytime.
Ironically using Devede in windows 7 works fine.
Anyone know of a fix?
Thanks.

---

### Post by cottfcfan on 2013-01-13
Problem solved. All has to do with "Dual pass encoding". I always use this in Devede, to improve the conversion quality.
While this works with .avi files, with .mp4 files on the second pass, it throws out the above error. Leaving as single pass works without error.
Hope this helps someone else with the same issue.

---

### Post by Journeyman1962 on 2013-05-06
This didn't work for me. But something else did. In edit > preferences, "use ffmeg instead of mencoder" was checked. I unchecked it - it worked. 
Hope it helps someone else.
T

---

