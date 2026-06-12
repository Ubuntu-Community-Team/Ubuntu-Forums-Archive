---
title: "Grip not ripping fast - Cant sort it out"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by drezha on 2006-11-22
HI all.

I'm trying to speed up Grip's ripping speed. It's currently taking about 1x speed.

I've read the help and it says to add the SCSI emulation to grub.conf or lilo.conf

And there in lies my problem. Neither are where they say they are. They should be in /etc/grub.conf and I should have the grub one there because I'm fairly certain I'm using Grub (as in IIRC it's Ubuntu's default and I've not changed it)

Is it supposed to be missing?:rolleyes:  Or is it somewhere else?

Any help would be nice, as I need to re rip all my CD's to ogg rather than Mp3](*,) 

Cheers

---

### Post by logos34 on 2006-11-22
I was wondering the same thing.  I too saw that in Grip help.  I made a mental note (since forgotten) to come back to it after I dealt with other configuration issues.  Sure would be nice speed things up a bit.  And I thought Exact Audio Copy in secure mode was slow!  

As you probably already know you can speed things up to around 11x speed by disablng paranoia -- its like burst mode in EAC and should be fine if the cds don't have scratches.  

I think the file in question here is /boot/grub/menu.lst  -- that's what comes up when you use GrubEd gui to edit boot options.  But I don't know for certain.  Anyone out there know?

---

### Post by drezha on 2006-11-22
Ah I didn't realise paranoia slowed it down. I'll try that.

Just seems odd I can rip 3 or 4 CD's in CDex on my Windows laptop in the time it takes to get one on Ubuntu.

Will try that and see what happens. Cheers

---

