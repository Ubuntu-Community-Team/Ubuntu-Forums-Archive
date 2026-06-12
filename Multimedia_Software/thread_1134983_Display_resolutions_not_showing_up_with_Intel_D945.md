---
title: "Display resolutions not showing up with Intel D945GCLF2"
date: 2009-04-24
forum: Multimedia Software
---

### Post by PatrikG on 2009-04-24
After upgrading to 9.04 from 8.10 I can no longer set my screen resolution to 1280x1024, the only value possible to use is 1024x768 and some other weird resolutions like 1152x864 and 1360x768.

Any ideas out there?

Updated:
- Detect monitors does not work, so it says "Monitor: Unknown". it's an HP L1925 monitor.
- I have tried to start in recovery mode and do the XFIX option, but to no avail

More updates:
I burned a CD with 9.04 and started that, same problem. so clearly an issue with the display drivers (or something) bundled in 9.04. How do I make a bug report?

---

### Post by PatrikG on 2009-04-24
Thanks to this information:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I went back to the old driver and now everything works fine again!

---

### Post by PatrikG on 2009-05-08
An update in case anyone else has the same problem.

I have now went to the 2.7.0 driver (google it to find how to do). the display modes disappeared as expected.

I then ran xrand to see that 1280x1024 was missing, so I added that. I had to make a "modeline" for my monitor, which I also googled up how to do, and then added the resolution to xrand. the display is now correct, all I need to do now is to find out how to make it stick after a reboot...

---

