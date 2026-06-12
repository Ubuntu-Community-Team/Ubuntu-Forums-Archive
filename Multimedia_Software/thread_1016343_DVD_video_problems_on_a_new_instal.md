---
title: "DVD video problems on a new instal"
date: 2008-12-19
forum: Multimedia Software
---

### Post by evilempire on 2008-12-19
My employer just hooked me up with a old IBM Thinkpad T42, which I promptly formated with Ubuntu 8.10 32 bit. I've set up Ubuntu systems before, but I've never had the DVD drive completely refuse to play movies. I've added the medibuntu repository, installed libdvdcss2, and all the "restricted codecs", but I can't get any commercial dvds to play. I can play movies i've previously ripped to mp4 or divx just fine.

 I know the dvd drive itself is good - I can boot to a Vista DVD and I even tried swapping it out for a second just to verify. 

I tried removing libdvdcss2 and reinstalling an older version - no luck. I tried upgrading that older version using the automatic update feature - still no luck. I've installed VLC - it also won't play the dvds. 


Totem will simply hang when I try to open the dvd - it spins it up and then goes gray and has to be force quit. VLC will flicker for a second and resize the window - but then do nothing. 

My test DVDs are recognised and show up with their proper titles on the desktop..... And the system otherwise works fine. 

I even tried reformatting and reinstalling (the ubuntu load was only 24 hours old so no great time lost)


Any one got any ideas of what to try next?

---

### Post by ironslave on 2008-12-19
Have you tried re-installing your DVDrom Drivers?

I would try an external dvd drive for testing if possible.

also try running the liveCD and installing the required files to see if it works.

If it does I would then Re-install ubuntu in live CD mode (without rebooting) which in turn should give you a working DVD drive as it will copy the loaded live CD in it's current config onto the drive.

oh BTW you lucky you! could you possibly pass one of those along to me? Ive always wanted a T42. :) way better then my T20 I used to have although I loved that thing.

Thinkpads.com has an excellent forum for anyone who owns thinkpads you could also try there. It's a great community.

---

### Post by mc4man on 2008-12-19
i would first ck .and see if a region has been set on the drive. While it's not always needed for commercial disks, laptop drives tend to be more restrictive.

Otherwise try switching audio, video outputs, though considering you can play dvd video now doesn't seem hopeful.

If nothing works I'd try 8.04.


To check the region install regionset and with a disk in the drive run regionset in a terminal. If it's set it'll say so around line 4.



Edit: while it's probably no help it never hurts to delete the .dvdcss folder in your home folder in case you got bad keys. (hidden folder

---

### Post by evilempire on 2008-12-20
mc4man - that was exactly it - it was the region code. I would never have checked that - I had just assumed that because it was a 3 year old laptop that the region had been set long ago...


Thank you mc4man and ironslave!

---

### Post by ironslave on 2008-12-21
wow i totally forgot about the region code thing... looks like you found a bug AND you got your problem solved :) 

Welcome to Ubuntu BTW!

---

