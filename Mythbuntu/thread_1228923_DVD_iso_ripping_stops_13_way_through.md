---
title: "DVD iso ripping stops 1/3 way through"
date: 2009-08-01
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-08-01
I had been ripping dvds fine with no problems in mythbuntu, I have the restricted extras and css lib installed and can play back all of the discs i am trying rip.  

The ripping process starts ine, and for no reason about 5-10mins in it just drops me back to the "No jobs and nothing else to do" screen.

What could be causing this problem?  I have restarted the machine but the fault is still present and is occuring with all my dvds (including ones i had succesfully ripped before).

Any help well is welcome!

Edit:  I have checked that my temp directory drive is not full and the destination drive has about 350gb free!  I have also tried adjusting the speed of my drive within the settings but with no change. 

One thing that has occured to me is VLC lists my dvd drive as /dev/sr0 but myth has it as /dev/dvd.  I dont think this can be the issue as myth as ripped 12dvds fine using the /dev/dvd setting and likewise plays the discs aswell.



EDIT:: I changed the drive to /dev/sr0 and managed to rip one dvd fine.  PLaced the next disc and and the same as above happened again.  Very confused as to what is going on now!  HELP!

---

### Post by mathog on 2009-08-01
> **geekyhawkes said:**
> 

The ripping process starts ine, and for no reason about 5-10mins in it just drops me back to the "No jobs and nothing else to do" screen.


Look at the log files and see what it says happened at that point.  Otherwise just do it manually with something like:

umount /media/cdrom
nice -15 dd if=/dev/dvd of=$TARGET_DIR/$NAME.iso bs=16384

That should work for any DVD, since it is just a binary image of the entire disk.

The one that can break this is a bad disk.  If there is a read error on the optical disk the dd will abort.  Probably the same thing will happen with any other ripper unless it has code to let it skip bad blocks.

---

### Post by mathog on 2009-08-01
> **mathog said:**
> 
The one that can break this is a bad disk.  If there is a read error on the optical disk the dd will abort.  Probably the same thing will happen with any other ripper unless it has code to let it skip bad blocks.

There are tools to get around this, but you will most likely end up with a hole in your tv show or movie.  Try, for instance dd_rescue and dd_rhelp.  They aren't part of any distro that I know if, but if you google for them you can download and build them easily enough.  Handy to have around for bad disk partitions too.

---

### Post by klc5555 on 2009-08-02
> **geekyhawkes said:**
> I had been ripping dvds fine with no problems in mythbuntu, I have the restricted extras and css lib installed and can play back all of the discs i am trying rip.  

The ripping process starts ine, and for no reason about 5-10mins in it just drops me back to the "No jobs and nothing else to do" screen.

What could be causing this problem?  I have restarted the machine but the fault is still present and is occuring with all my dvds (including ones i had succesfully ripped before).

Any help well is welcome!

Edit:  I have checked that my temp directory drive is not full and the destination drive has about 350gb free!  I have also tried adjusting the speed of my drive within the settings but with no change. 

One thing that has occured to me is VLC lists my dvd drive as /dev/sr0 but myth has it as /dev/dvd.  I dont think this can be the issue as myth as ripped 12dvds fine using the /dev/dvd setting and likewise plays the discs aswell.



EDIT:: I changed the drive to /dev/sr0 and managed to rip one dvd fine.  PLaced the next disc and and the same as above happened again.  Very confused as to what is going on now!  HELP!

Some discs just won't do iso rips in Myth. Many of these discs will do a "perfect" rip of the actual show from the DVD without any problem.

A few discs simply won't rip in Myth at all. For these, you'll need to rely on other Linux ripping tools. 

Occasionally frustrating, but that's just the way it is.

---

### Post by geekyhawkes on 2009-08-03
Thanks very much.  Im new to myth, and if all i have to put up with is occasional rip from the desktop i can live with that!

---

