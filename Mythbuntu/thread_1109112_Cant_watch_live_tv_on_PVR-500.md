---
title: "Cant watch live tv on PVR-500"
date: 2009-03-28
forum: Mythbuntu
---

### Post by ukulele_ninja on 2009-03-28
Ive been trying every whichway to get this to work on my mythsystem. I have the Hauppauge PVR-500 dual tuner card and when i select 'watch tv' the screen flickers but then goes back to the menu. I have also gone into the backend setup and everything looks as it should but still no avail.

Im thinking that the system may not be finding the tuners right. The output of -ls /dev/vi* -l shows only three devices: /dev/video0, /dev/video24, and /dev/video32. I think there should be more but im not sure. Any ideas?

---

### Post by 4dognight on 2009-03-30
Have you checked your backend and frontend logs?
How about dmesg too?
More than likely some useful info will be in there.

---

