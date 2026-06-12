---
title: "Nvidia and the new kernel??? More problems???"
date: 2009-01-28
forum: Multimedia Software
---

### Post by ed-koala on 2009-01-28
Has anyone who had problems getting their Nvidia restricted drivers to work with 8.10 x64 done an upgrade to the new kernel??

I'd hate to go through hell again ... please please let me know if the update works smoothly this time.

---

### Post by xx.canes.rites on 2009-01-28
I've just updated about 10 minutes ago myself and my display is completely broken. It will not even detect my display device. I cannot play my games or anything right now. I'm not liking this update at all, maybe there is a way for me to revert to before the update.

---

### Post by cariboo on 2009-01-28
Which new kernel are you talking about? A little more info would help, if you don't know what kernel you are using in a Applications-->Accessories-->Terminal type:

```
uname -a
```

the result should look something like this:

```
 uname -a
Linux jack 2.6.28-5-generic #15-Ubuntu SMP Fri Jan 23 01:16:33 UTC 2009 x86_64 GNU/Linux
```

I'm currently running Juanty, so your kernel number may differ.

Jim

---

### Post by alexyz on 2009-01-28
The recent kernel update 2.6.27-11-generic also broke my nvidia driver.  card:  GeForce 6800 GS

NOTE:  I'm using the nvidia driver downloaded from nvidia and installed manually.  Not the one from the ubuntu repos (linux-restricted-modules).  I should be able to just rebuild the driver module against the new kernel but today that didn't work.  

First I tried to go back to the previous kernel but the driver was hosed there too.  After much hacking I got it working again (with the new kernel) but I'm not exactly sure what the problem was.

The latest nvidia driver did NOT work (with either kernel).  The earlier version I had installed - nvidia driver 180.06 - works for me.  With newer drivers compiz didn't work - not frozen but weird screen artifacts, completely unusable.

Sorry for the lack of detail but HTH somebody.

Also probably better to use the ubuntu repos now - I got it working with the manual install and didn't want to break anything. :| oh well...

edit:  FWIW I am now running from the repos (8.11) with no apparent problems.

---

### Post by ed-koala on 2009-01-28
Been looking at the answers, and the posts lately, and it seems this upgrade broke sound and ATI drivers more than nvidia (based on the number of posts seen)

I'll give it a rip soon, and pray if it dies, the old kernel will save me.  :)

---

