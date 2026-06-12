---
title: "Rane Serato SL-1 Doesn't Function Properly"
date: 2011-09-28
forum: Multimedia Software
---

### Post by Thedjatclubrock on 2011-09-28
Hey guys! :)

My friend gave me his Rane SL-1 USB audio interface when he purchased the newer SL-2. I've used it before successfully on this computer (I don't remember how long ago), but it no longer functions properly. The unit seems fine, as it works in OS X and Windows. It shows up in alsamixer, and when I cat the sound card listing in /proc , but I can't use aplay, mixxx or xwax to successfully listen to or play audio from the unit. 

From Proc:
 1 [SL1            ]: USB-Audio - SL-1                           &#9474;      &#9474;
&#9474;     &#9474;                      Rane SL-1 at usb-0000:00:04.0-1, full speed
From dmesg:
[33210.070040] usb 3-1: new full speed USB device number 4 using ohci_hcd
[33210.426119] cannot find UAC_HEADER
[33210.426126] snd-usb-audio: probe of 3-1:1.8 failed with error -5

Any ideas? Thank you so much

---

