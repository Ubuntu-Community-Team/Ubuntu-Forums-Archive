---
title: "DVD Playback on 7.10"
date: 2008-04-23
forum: Multimedia Software
---

### Post by Milambar on 2008-04-23
I have dvd playback working, but...

apt-get upgrade wants to upgrade libdvdcss2, I currently have version 1.2.5-1 installed. 

The upgraded version breaks my dvd playback for some reason. So every time I do an update, I have to manually downgrade libdvdcss2 back to version 1.2.5-1.

Is there any way I can instruct apt-get to ignore the updates to libdvdcss2?

---

### Post by wolfen69 on 2008-04-23
if you just let update manager handle it for you, you would have the choice of unchecking it.

---

### Post by mc4man on 2008-04-23
Open up synaptic, search libdvdcss2, highlight the package, and under the package tab choose lock version. It will still be listed in updates but won't be updated. In hardy you'll never see it again

---

### Post by Milambar on 2008-04-23
> **mc4man said:**
> Open up synaptic, search libdvdcss2, highlight the package, and under the package tab choose lock version. It will still be listed in updates but won't be updated. In hardy you'll never see it again

I don't use synaptic. I find it slow and clunky, and not very well laid out. Too windowsish. Anyway, Ubuntu forced the update somehow, and now it won't downgrade again.. Im guessing something was marked as dependant on it.

Now I can't play dvd's at all. Heres the output I got from the shell:

> 
libdvdread: Invalid title IFO (VTS_17_0.IFO).
*** Zero check failed in ifo_read.c:1756
    for pgcit->zero_1 = 0xd5b7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1760 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***

*** Zero check failed in ifo_read.c:761
    for pgc->zero_1 = 0xc0e3

*** libdvdread: CHECK_VALUE failed in ifo_read.c:762 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:604 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:605 ***
*** for total <= 255 ***

libdvdread: Invalid title IFO (VTS_17_0.BUP).
[00000292] dvdread demuxer error: fatal error in vts ifo
[00000292] dvdread demuxer error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000294] vcd access error: no movie tracks found
[00000294] vcdx access error: unknown ID encountered -- maybe not a proper (S)VCD?
[00000294] access_file access error: file /dev/scd0 is empty, aborting
[00000301] main private error: cannot pre fill buffer
[00000281] main playlist: stopping playback


Note, the dvd USED to play perfectly before the update, and still plays perfectly under windows.

---

### Post by mc4man on 2008-04-23
Well go ahead and uninstall from cli (or however you remove packages and then go here and pick your version
[http://download.videolan.org/pub/libdvdcss/](http://download.videolan.org/pub/libdvdcss/)
If you want to post title maybe it's one that will benefit from dvdnav patch
[http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html)

---

### Post by Milambar on 2008-04-23
Bleh, why is DVD playback so hard to get working under linux? None of those libdvdcss files work. Looks like I need to keep my windows dualboot partition solely for dvd playback.

On a sidenote, My USB digital tv decoder works flawlessly under Ubuntu. Its very glitchy under windows.

---

### Post by mc4man on 2008-04-23
for the heck of it go into home dir. find .dvdcss folder and delete the folder associated with the title your trying to play, then try again with the .25 ver. if you want to mention title I'll see if it has structure protection

Edit: if your using totem this works sometimes
[http://ubuntuforums.org/showthread.php?t=747326](http://ubuntuforums.org/showthread.php?t=747326)  #4

---

