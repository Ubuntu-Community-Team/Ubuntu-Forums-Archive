---
title: "Copy VCD's (copy the file AVSEQ.DAT)"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by krussell on 2007-05-02
Hello :-)
I can right-click and copy DVD movie files (*.VOB), but i cannot copy VCD files (commonly named AVSEQ.DAT).
How can i directly copy VCD files in to Hard disk??

---

### Post by disturbed1 on 2007-05-02
Install vcdimager from synaptic. In a terminal type vcdxrip.

---

### Post by krussell on 2007-05-14
Thanks for your reply. Yes, i got vcdxrip working fine. It copies the whole movie, can i also choose a portion of the vcd?

---

### Post by disturbed1 on 2007-05-14
One way to do this is, once vcdxrip copies your movie to the hard drive you could open it with Avidemux and use the mark in/mark out features. As long as you choose copy as the video and audio codec in Avidemux there will be no re-encoding.

Avidemux is also in Synaptic.

---

### Post by manmath on 2007-11-27
Here is the fix, in multiple ways. Do whichever suits you the best.

I copy the disc to the hard disk as a raw/iso (dd if=/dev/cdrom of=/tmp/image.iso) then I use vcdgear to extract the dat to mpg:

vcdgear -raw2mpg /tmp/image.iso movie.mpg


This is pretty much the method I would recommend as well, the one change I would add is that I use readcd as it handles copying from the CD medium much better than dd, IMHO.

"vcdgear -fix -cue2mpg" has been reliable in extracting a working mpg from a standard image file set.

Just tried with DD and had an issue. readcd is a good tool, I prefer cdrdao myself and this command line should get you a lovelly bin/cue to use vcdgear on:

cdrdao read-cd --device ATA:1,1,0 --driver generic-mmc-raw --read-raw image.cue

Change the device for whatever is your reader!

OR

install readvcd and then 

# readvcd 2 > mv.mpg

OR

Install vcdimager
# vcdxrip

OR

install cdfs
mount -t cdfs /dev/cdrom (or whatever your drive is) /home/movie (or whatever your destination)

---

### Post by krussell on 2007-11-28
D' disturbed1 and manmath :-)
Thanks a lot for the solution, it works great!

---

### Post by rykel on 2008-02-07
Hi pals,

May I know where/how I can find/install cdfs?

Also, where is the output of vcdxrip?

Thanks for clarifying! I cannot believe that no Linux distro has made copying .dat files as invisible to the user as Windows after all these years...   :confused:

---

