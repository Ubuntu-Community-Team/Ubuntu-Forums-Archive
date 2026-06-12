---
title: "Sansa 260 and Ubuntu?"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by rondamato on 2007-11-18
Hello again,

I have read the past posts regarding the Sansa MP3 players and Ubuntu and they are all very informative...I have a weird problem that isn't really addressed though... :icon_frown:

*Sometimes* (and not that often) the Sansa will automount on my desktop as a "Sansa 260" with an Ubuntu HDD icon and everything.  I can then see its folder structures, add music, etc.  MOST of the time, though, it never shows up--even though it autolaunches Rhythmbox (??) on plug-in almost every time.  Sysinfo does not "see" it on these occasions.

The machine will [I]always[/l] charge the player thru USB, but hardly ever "sees" it (meaning it almost never automounts and I cannot manually mount it either.)  Whoops, guess I just said that, but bear with me...the coffee's just kicking in.

I am running Firmware 1.03 on the Sansa (the newest stuff) which is slightly buggy (tracks drop out sometimes or sometimes power just drops...but only 1x or 2x per month).  This firmware is known in the Sansa world as the "Hebrew Firmware."  Some people on the Sansa forums have had problems with this firmware, but the few Ubuntu users I've found on there say that it works fine with Fawn and Gibbon.

OK, now get this: yesterday a friend comes over with his laptop running XP Pro.  I plug in the Sansa...Windoze searches for a driver...finds it (???!!!)...then my player mounted right up, but all of my album/artist folders were gone but for about 30 Beatles tracks (this is toooo weird).  I disconnect, look at my music thru the Sansa's interface...and my music is all there and playable--except now almost every track has a duplicate  They can't be "real" dupes(prob just symlinks) because I'd be out of space, but HOW did Windows screw my player up THAT fast???  GRRRR!!!!  Hmmm, and WinExplorer had all the "hidden" files turned on also and stuff was still missing AND there were no dupe files...what the heck is happening???  :confused:  

I have a Mac to plug it into also, but I've tried this 3 or 4x and it just corrupted the firmware.

Any suggestions?  Should I downgrade the firmware, format, and reload the songs (they are backed up on DLT)?  Or does someone know a better/faster way?  I guess if no one has seen this I'm going to just try my suggestion above and let you all know what happens.

Oh yeah, should Ubuntu "read" an MTP USB device without trouble usually?  My gut says "yes" but experience is trying to prove my gut wrong!  I only have one MTP device to try it on.

Thank you SOOOO much for your help friends!  Sorry for the N00B questions!  

DoctorRon
Chicago, IL
<rondamato@gmail.com>
------------
v7.10 Gutsy Gibbon 32-bit/Gnome
HP Pavillion (something)
AMD Sempron 3100 w/2GB DDR 533

---

### Post by barry_vancouver on 2007-11-19
my Sansa e280 had no problems being instantly recognized and mounted on my laptop with Feisty Fawn. 

My Desktop PC with Gutsy 7.10, however, refused to mount the device...unitl I typed the following command into Terminal:
 sudo modprobe -r ehci_hcd


I found this command trolling Google and ubuntu forums on and off the last few days for any advice relating to Sansa usb drives and mp3 players...

Give it a go!  Worked beautifuuly for me on Gutsy!! :d

Now I can sleep!!

---

