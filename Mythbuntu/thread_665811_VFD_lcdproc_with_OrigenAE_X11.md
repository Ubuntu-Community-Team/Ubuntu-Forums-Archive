---
title: "VFD lcdproc with OrigenAE X11"
date: 2008-01-12
forum: Mythbuntu
---

### Post by endymon on 2008-01-12
Hi,
I keep getting garbled text on my LCD display using the VFD included with the OrigenAE X11 case (same as Zalman HD160).

I'm using the Irtrans LCD driver from [http://www.irtrans.de/en/download/linux.php](http://www.irtrans.de/en/download/linux.php) which seems to be version 0.4.3

I get the same error messages with Mythlcd as described on their Wiki:
[http://www.mythtv.org/wiki/index.php/Mythlcdserver](http://www.mythtv.org/wiki/index.php/Mythlcdserver)

**I keep getting: **
"LCDProcClient: WARNING: Something is gettingpassed to LCDd that it doesn't understand" & "llast command: widget_set Time timeWidget 5 2 "11 41 PM""

It says that Mythtv has been compiled with a different version of lcdproc protocol.

I'm using Mythbuntu 7.10. How do I go about solving this ? My setup is at this moment very stable and I would like to avoid reinstall / rebuilding all of Mythtv. 

Is it possible to just rebuild the mythlcdserver ?

Any help would be greatly appreciated as I'm not really well versed in the compiling / building things ;-)

---

### Post by endymon on 2008-01-17
Okay this has been solved.

I pulled out the power for a long time to have the VFD completely reset itself. 

Then I booted, started LCDd again and display works perfectly.

Apparently when I did my first install of Mythbuntu I used the default driver for lcdproc. That garbled up my display and the only way back was to cut the power for some time for it to reset.

On a side note though is that I am still getting these errors. I'm pretty sure that everyone with my setup will be getting them if they increase the debug logging. 

But they are not really an issue as long as the display works fine !

---

