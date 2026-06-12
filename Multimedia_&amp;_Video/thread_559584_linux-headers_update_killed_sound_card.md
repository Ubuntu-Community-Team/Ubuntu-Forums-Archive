---
title: "linux-headers update killed sound card"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by blakecraw on 2007-09-25
So, I just updated to linux-headers-2.6.20-16-generic version 2.6.20-16.32, and after rebooting it can't find my sound card. It says I either do not have the correct version of gstreamer, or I don't have a configured sound card. I couldn't find the older version of linux-headers.

Help?

Blake

---

### Post by enneth on 2007-09-25
I have the exact same problem. This is the second time an update f***s up my sound. The first time this happened I found an excellent thread on how to fix this -- just can't seem to find it now.

I am also very interested in getting a solution for this sad problem.
[B]
EDIT:[/B] I got everything working again. Just download the alsa-packages from [http://alsa-project.org/main/index.php/Download](http://alsa-project.org/main/index.php/Download) and install it manually. My sound works again.

---

### Post by blakecraw on 2007-09-25
> **enneth said:**
> I got everything working again. Just download the alsa-packages from [http://alsa-project.org/main/index.php/Download](http://alsa-project.org/main/index.php/Download) and install it manually. My sound works again.

Thanks. However, I like to have all my stuff installed via apt if I can, so I'm gonna hold off on that until it's absolutely necessary.

---

### Post by soltanis on 2007-09-25
Installing drivers manually works....

Trying to compile the apt-get alsa-source stuff doesn't seem to fix the problem, my compiler just errors out and stops.

I don't know why, but I can't get my sound keys to work still, but at least my sound works again.

---

### Post by clmcdanne on 2007-09-25
same here:  reloaded alsa-drivers 1.0.14 per link for Toshiba sound fix! located on forums on a Toshiba Satellite A135-S2276 and sounds works again!  then saw theres a new version of the drivers already (1.0.15)...uugghh! trying to ditch MS Windows on new laptop (and eventually entire home network) but Ubuntu update" blow outs" making it really difficult.  just looking for some consistency first.  :)

---

### Post by blakecraw on 2007-09-26
Well, I gave in and installed via that link, and it all works again. Thanks a lot.

Blake

---

### Post by El~Zilcho on 2007-09-27
Hi, the update gave me the same problem so I'm hoping the same solution will work, I followed the link above and unpacked the stable driver release but when I tried to configure it I got this:

desktop:~/My_programs/alsa-driver-1.0.14$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler               cannot create executables
See `config.log' for more details.

Is that the file I need? Any idea what I'm doing wrong to it? Thank you.

---

### Post by El~Zilcho on 2007-09-30
Hi, can someone help me a little with this? I still have no sound. When I try and configure the alsa package I get this:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

At the top of the config.log is this:

gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2334: $? = 0
configure:2341: gcc -V >&5
gcc: '-V' option must have argument
configure:2344: $? = 1
configure:2367: checking for C compiler default output file name
configure:2394: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2397: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2436: error: C compiler cannot create executables
See `config.log' for more details.

Any help would be really quite welcome.

---

