---
title: "nMedia pro-lcd, lcdproc and the lis driver."
date: 2011-04-23
forum: Mythbuntu
---

### Post by miststlkr on 2011-04-23
I know there have been a few threads about this in the past, but none recently.  I can not, for the life of me, get this working.  I even read that it worked out of the box in 9.10 so I reformatted/reinstalled down to 9.10 to try it and no good.  Tried the two or three tutorials I have been able to find, went through downloading the CVS and building/compiling it from scratch.  No luck.   Has there been any headway made on this and why the lis.so can't "see" the ftdi.h for some reason and build normally on newer distros?  Has anyone actually gotten the LCD to work correctly, and is willing to give me some of their time to try to figure out what is going wrong on my end?  As far as I can tell, the 9.10 install built the lis.so just fine, but when I try to run LCDd from the terminal I get the error

===

Could not open driver module server/drivers/lis.so: server/drivers/lis.so: cannot open shared object file: No such file or directory
Driver [lis] binding failed
Could not load driver lis
There is no output driver
Critical error while initializing, abort.

===

I tried moving the driver path in the ./lcdproc-0.5.3/LCDd.conf file, but it still gives the same path in the error message, despite restarting through init.d and system reboots, even tried changing the Driver=lis to Driver=curses in he .conf just to see if the error would change, and it didn't... still looking for the lis driver.  

I thought perhaps I have the wrong "copy" of LCDd.conf, maybe there is one in /usr/bin/something but *find -name lcdproc -print* comes up with only that directory as a hit, so i don't think there is another hidden away somewhere.

Clearly I'm doing something stupid here, and any help would be greatly appreciated.

---

