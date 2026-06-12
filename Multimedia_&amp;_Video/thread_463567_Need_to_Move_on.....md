---
title: "Need to Move on...."
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by gatoruss on 2007-06-03
Well I am sorry to say that I think that I need to give up my Ubuntu experiment.  I just cannot solve the wireless problem.

I originally loaded 6.10, and after struggling for a week or so, was able to get wireless set up and working.  Then I upgraded to 7.04, and I lost wireless.  I struggled again for over a week, compiling the rt61 driver from source code, and was eventually able to get it working.  But I was never able to get the wireless to load on start-up with 7.04; I needed to manually load each time I booted-up.  Well then I loaded some updates, and wifi again stopped working.  I tried to go back to 6.10 and 6.06, with no success.

I have been with out wifi for over 2 weeks.  It is terribly frustrating.  It should not be this hard.  I think that until linux distributions can become more user friendly, windows will always be favored.

It is a shame...I was enjoying playing with command lines and experimenting with linux and Ubuntu.

I will check in here from time to time to see what is up, but I think it is windows for me.

---

### Post by kevinlyfellow on 2007-06-03
Just so you know, it wouldn't load up when you started the machine because it wasn't listed in /etc/modules (if you would issue the command modprobe rt61 then you would just put rt61 at the very bottom of the list).  You can keep it working by not updating your kernel or recompiling everytime you get a new kernel.  You can still get your wireless to work by booting the old kernel in grub.

Anyways, come back for Gutsy, your wireless _may_ work out of the box!

---

