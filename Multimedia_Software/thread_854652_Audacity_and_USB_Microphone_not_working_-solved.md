---
title: "Audacity and USB Microphone not working -solved"
date: 2008-07-09
forum: Multimedia Software
---

### Post by drjoewebb on 2008-07-09
I just loaded Kubuntu 8.04.1 and my biggest problem was getting Audacity and other audio programs to recognize my USB microphone.

This was solved by entering this command in terminal
AUDIODEV=/dev/dsp1 audacity

The details were on the Audacity wiki
[http://www.audacityteam.org/wiki/index.php?title=USB_mic_on_Linux](http://www.audacityteam.org/wiki/index.php?title=USB_mic_on_Linux)

---

