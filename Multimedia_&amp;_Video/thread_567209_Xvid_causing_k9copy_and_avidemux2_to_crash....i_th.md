---
title: "Xvid causing k9copy and avidemux2 to crash....i think..."
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by porphiron on 2007-10-04
Lo folks, here again with another odd problem.....which is more than likely my fault!!....


I've set up a machine to do all my ripping and encoding, and so far everything has worked fine......xubuntu rawkz!....

until....

fired up k9copy, which i have on another machine and  (which works fine ) started to encode a dvd to avi (XviD x2 pass avi) i ripped the contents of the dvd to my harddrive, via dvd shrink (please, dont shout.....i like it and it works well in wine!), within 20mins, k9copy segfaulted, fiddled around, tried it in root, to no avail. tried various different dvds but every time k9copy would seg fault within the first twenty mins of the firstr pass, sometimes longer, I've now reinstalled all the various files required for k9copy, dvdauthor e.t.c. and reinstalled xubuntu twice now, and could never get to the bottom of why the bloomin thing would seg fault....

To save my sanity I decided to try somthing else, in the shape of avidemux2, lo behold, first pass carried off ok, as soon as the second pass starts.......avidemux2 crashes....BUT, having run it within a terminal, i got the message that libxvidcore.so.4 had caused the crash!, reinstalled the xvid package, but still no joy....so.....any ideas what i can do now?

I have installed xubuntu twice on this machine, once from a backup I made from the machine that will run K9copy / avidemux2 fine, they worked fine on the newley installed machine, but had many hardware problems like sound and video problems plus other spurious crashes, so in the end had to go back to a proper install (all machines run xubuntu 7.04) and back to the k9copy/avidemux crashes.

I did initially think that it might be a hardware problem, but as the above states, k9copy worked fine from an install cloned from another machine.

Apart from the machine i cloned a working install from, I also have a latop that runs k9copy fine and have checked the none working install against both machines, and have made sure that all installs have the same files, and still no joy...

Sorry for the lengthy post, but am trying to get as many details down as possible...

system details:

ASUS Nforce2 mobo
Sempron 2600 o/c to 2800 ish
Nec DVD/rw/Ram
Sony DVD/rw
Philips DVD/rw
Maxtor 120GB Hdd
2GB kingston pair in dual channel mode
External 320GB Hdd

Running Xubuntu 7.04

have tried encoding the files from within both the internal and external hdd, it crashes which ever drive I use (i did think it was a usb problem initially)

Any help in this matter would be very very very VERY appreciated.

sorry again for the lengthy post

Porph!

---

### Post by porphiron on 2007-10-04
update, this is output from avidemux...

*********** BACKTRACK **************
Frame  0: avidemux(ADM_backTrack+0x4b) [0x864aadb] 
Frame  1: avidemux(_Z20sig_segfault_handleri+0x2d) [0x864aedd] 
        <sig_segfault_handler>()
Frame  2: [0xffffe420] 
Frame  3: /usr/lib/libxvidcore.so.4 [0xb7223c48] 
*********** BACKTRACK **************

---

### Post by porphiron on 2007-10-05
update:

have found that for some reason this machine does not like the two updates above the original install version of xvid/libxvidcore.so.0.4

and have moved over to trying dvdrip instead of dvd shrink and k9copy

dvdrip crashed with both newer packages and am now trying as above

---

### Post by brazso on 2007-11-23
I had absolutely the same problem described by you with avidemux. I had been using an overclocked athlon xp processor, and the permanent crashes in the libxvdcore.so were due the the exaggerated overclocking. I just decreased the fsb speed by 1 mhz and the problem vanished. Check the stability of your computer with some diagnostic program (memtest86, gimps/mprime, etc...).

---

