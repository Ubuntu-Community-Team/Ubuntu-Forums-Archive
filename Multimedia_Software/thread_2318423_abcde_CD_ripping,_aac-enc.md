---
title: "abcde CD ripping, aac-enc"
date: 2016-03-26
forum: Multimedia Software
---

### Post by arlenn2 on 2016-03-26
I am trying to rip some CDs using abcde.  It works well with FLAC and MP3 but I am having trouble getting the AAC encoding to work correctly.  It appears that Ubuntu is calling the FDKAAC that abcde is expecting, aac-enc; and abcde is passing it some arguments it isn't liking.  

" fdkaac: invalid option -- '-' "

I didn't know if it was tripping up on simply the name of the  executable, I tried symbolically linking the names, if that would help.   It didn't

Does anybody know of a work-around for this?  The Nero encoder appears to be one option, but is reportedly inferior to the FDK.


Thanks in advance.

---

### Post by mc4man on 2016-03-26
Have never tried using aac-enc, maybe it'll work if that's what you specified on the FDKAAC= line in abcde.conf. If so you'd need to use options that aac-enc supports on the FDKAACENCOPTS= line which are likely very limited.
(above assumes your using the latest abcde,

Probably better to use the fdkaac binary instead, you can build your own or if using 14.04.x or 16.04 then available here, inc. newer abcde for 14.04 & newer fdk-aac libs - 
[https://launchpad.net/~mc3man/+archive/ubuntu/fdkaac-encoder](https://launchpad.net/~mc3man/+archive/ubuntu/fdkaac-encoder)

reference mat. for use.
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

---

### Post by arlenn2 on 2016-03-26
Wasn't aware of the PPA... Thanks that is helpful.

The arguments are actually very similar. As abcde is a big Bash script... with a enough looking, it is probably patchable; I think I can see where its tripping up.

but I'll give the PPA a whirl.

---

### Post by andrew.46 on 2016-03-26
Good time to find a bug if this is the case as version 2.7.2 is coming out in a few days. And I see from Xenial Xerus that a decent version of abcde = 2.7.1 will be in place as well as fdkaac. Good times ahead for abcde :)

---

### Post by arlenn2 on 2016-03-28
The FDKAAC front is MUCH more complete than the AAC-ENC.  The Xenial PPA binaries worked just fine with Wiley.

Thanks for the help.

---

### Post by andrew.46 on 2016-03-28
Mind you best quality aac sound will still come with qaac and *--tvbr 100* in the settings: abcde 2.7.1 can do this...

---

