---
title: "Gnome programs do not display video on GMA 950"
date: 2010-08-07
forum: Multimedia Software
---

### Post by ojas on 2010-08-07
I have Ubuntu 10.04 on a FujitsuSiemens Amilo 1520 Si, that uses the GMA 950 graphics chipset.

Totem does not display the video when playing video files. The audio plays fine.

VLC  did not use to display the video either. It does so since I switched  its video output from "Default" (whatever that might be) to "X11 video  output".

Cheese does not display the camera picture. Recording works fine, though.

Flash videos in Firefox run fine as well.

How can I get video displayed in Totem and Cheese?
What is this "Default" output method that VLC talks about?

Thank you for your attention.

---

### Post by Yellow Pasque on 2010-08-07
Totem and Cheese are gstreamer programs, so try the different options under the video tab of:
```
gstreamer-properties
```

---

### Post by ojas on 2010-08-07
That worked. I switched the "Default Output" from "Autodetect" to "X Window System (No Xv)".

Thank you.

---

### Post by Yellow Pasque on 2010-08-07
You're welcome, please mark thread solved.

---

### Post by ojas on 2010-08-08
I tried to when writing my reply. But I cannot edit the Prefix of the title. How do I mark the thread solved?

EDIT: I found it. It's in the Thread Tools.

---

