---
title: "Trouble with Zoom H2 USB microphone"
date: 2010-09-23
forum: Multimedia Software
---

### Post by jaaf64 on 2010-09-23
I have a zoom H2 and I intend to use its usb microphone function.
I connected it and it seems to work with xvidcap if I declare /dev/audio1 as the input device. Well.

I want to go further and use it for other purposes and before installing jack and other applications I would like to understand why it does no longer appear in the "Sound preferences" under  the 'input" and "hardware" tabs as it was the case the day before.

---

### Post by cchhrriiss121212 on 2010-09-23
So it used to show up and now it does not?
Try plugging it into a port with no other USB devices present, then open a terminal and put "arecord -l".

---

