---
title: "Intel 865G - 1440x900 Widescreen Problems"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by pearzoo on 2006-07-01
For the last few weeks I have been searching these forums looking for somebody  who is running 1440x900 on an Intel 865G (64MB Shared) on Dapper.

I can get this resolution on my HP notebbok which uses the 855G graphics Card. Using 915resolution was dead easy - I re-wrote a mode to "1440x900" and specified in the xorg.conf. Worked first time no problem.

BUT then I tried to do the same on the HP dx 2000 desktop that uses the 865G video chipset. I do the 

915resolution 38 1440 900 24

This returns happy and listing using 915resolution -l show the new mode.

I add the mode to xorg.conf and restart X.

Well - depending on which mode I overwrite I have one of two outcomes:

1. The monitor displays an out of range error.
2. X starts beautifully at 1280x1024 - running 1440x900 "Virtually".

Now I've tried Modelines, With and without DDC enabled. I've tried ForceBIOS options, I have done many dpkg-reconfigure xserver-xorgs.  The worst is there is no specific error in the X log.

All that it reports is that it will be using built in mode 1440x900 . And mentions doing so virtually.

Please let me know if you have any further ideas on this. I will post the X log files and xorg.confs if required, but I have followed every thread to do with widescreen, and I have made it work easily on another card (855). I am convinced that the 865G can not be made to use this Resolution using the current 915resolution and i810 X drivers.

For the record, the card and monitor work on that ugly thing called XP so I know it must be possible.

---

### Post by pearzoo on 2006-07-04
I have it working!

There is  a problem with the 865G and this resolution. I have hard-coded the correct 1440x900 modeline setting into the 915resolution source and ... Hey I'm typing this from my new display.

If any of you have this probem - let me know - I know how to sort it - even if it's just a temp workaround. I will take a longer look at the code. My feeling is that one needs to be able to specify the clock speed with your mode setting. But more about that when I've had a decent chance to play with it. 

I'm catching up work at the moment!!!

---

### Post by george.aprozeanu on 2007-02-06
I have the same problem. How did you do it anyway?

---

