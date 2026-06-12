---
title: "usb card reader not working; excessive error messages logged to syslog"
date: 2010-10-15
forum: Multimedia Software
---

### Post by stephanecharette on 2010-10-15
I have a USB card reader that works fine on one of my older computers running 10.04.  But when I bring that same card reader to my new computer running 10.10, it fails to work and the following error messages are logged to /var/log/syslog four times per second:

Oct 15 02:55:35 stephane-desktop kernel: [  432.740628] hub 2-1.3:1.0: unable to enumerate USB device on port 3
Oct 15 02:55:35 stephane-desktop kernel: [  432.990392] hub 2-1.3:1.0: unable to enumerate USB device on port 3
Oct 15 02:55:35 stephane-desktop kernel: [  433.239468] hub 2-1.3:1.0: unable to enumerate USB device on port 3
Oct 15 02:55:35 stephane-desktop kernel: [  433.498865] hub 2-1.3:1.0: unable to enumerate USB device on port 3

This happens whether or not the card reader has an SD card inserted in it.  The other slots are all empty since I don't own any XS, CF, or MS cards.

Googling showed me lots of threads with this message, but no solution.  Anyone know what I can do?

---

