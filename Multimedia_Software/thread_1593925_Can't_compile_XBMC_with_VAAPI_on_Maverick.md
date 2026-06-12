---
title: "Can't compile XBMC with VAAPI on Maverick"
date: 2010-10-11
forum: Multimedia Software
---

### Post by sizeak on 2010-10-11
Hello,

I've been trying to compile XBMC on Maverick with VAAPI support enabled (--enable-vaapi) however during the configure step I get the error that libva-glx is missing. (More specifically that -lva-glx failed). I have installed libva-x11-1, libva-dev, libva1 and xvba-video. I'm using the proprietary ATI drivers (Catalyst) and the actual card is a HD4350 if it helps.

I can't for the life of me find any information of where to get libva-glx  and it's doing my head in. Can anyone help?

Sizeak

---

### Post by Yellow Pasque on 2010-10-11
You'll need to install libva(-dev) from here: [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)

---

### Post by sizeak on 2010-10-12
Well I can't remove libva1 for some reason. I type apt-get remove libva1 and it says that some random package s to be removed and another installed. Then it does it and is finished, however neither package was libva1 and it doesn't get removed :S

---

### Post by svenni on 2010-10-12
> **sizeak said:**
> Well I can't remove libva1 for some reason. I type apt-get remove libva1 and it says that some random package s to be removed and another installed. Then it does it and is finished, however neither package was libva1 and it doesn't get removed :S

Could you post the output from the console here? Maybe there are some errors indicating why it is not removed. You could also try apt-get purge, in case that would make any difference (although I don't think it would).

---

### Post by sizeak on 2010-10-12
Ok well it seems to have fixed itself :confused: Sometimes Linux makes me rage. Thank you anyways

---

### Post by Hirs on 2010-10-12
Did you do something special? I am having this problem right now :(

---

### Post by Hirs on 2010-10-12
I finally downloaded the packages and did:

sudo dpkg -i --force-overwrite libva1-dbg_0.31.1-1+sds4_amd64.deb libva-dev_0.31.1-1+sds4_amd64.deb libva1_0.31.1-1+sds4_amd64.deb

Now it's compiling, lets see if it works...

---

### Post by Hirs on 2010-10-12
Well, xbmc crash:

Running DIL (3.6.0) Version
DtsDeviceOpen: Opening HW in mode 0
DtsDeviceOpen: Create File Failed
libva: libva version 0.31.1-sds1
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/i965_drv_video.so
xbmc.bin: intel_driver.c:59: intel_driver_init: Assertion `dri_state' failed.
Aborted (core dumped)
Crash report available at /home/carlos/xbmc_crashlog-20101012_154547.log

---

### Post by sizeak on 2010-10-12
Not really to be honest. Once I finally got libva1, libva and libva-dev removed with apt (I accidently installed them from the repos) I just downloaded the libva1 package from the site linked in the second post and then built the libva package on the same site. 

So the correct package fro your arch from here: [http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/](http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/)

then grab the most up to date archieve from here: [http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/)

and build it (short instructions on the bottom of the same page). 

Next I had to install autopoint from the repositorys and the I just built xbmc from the svn repo following these instructions: [http://wiki.xbmc.org/index.php?title=HOW-TO_compile_XBMC_for_Linux_from_source_code](http://wiki.xbmc.org/index.php?title=HOW-TO_compile_XBMC_for_Linux_from_source_code)

Hope it helps,
Sizeak

---

### Post by Georche on 2010-10-30
Thanks everyone here for the help!

For anyone stumbling across the same problems, this is what I did:
-Removed packages LIBVA1, LIBVA-dev using package manager.
-Installed LIBVA-1 package from package folder in link in second post.
-compiled as described above (had to fix some dependencies).
-Installed LIBVA-DEV and LIBVA-DBG from the site packages folder of the site above.

I might have done some things twice, or in the wrong order, but at least XBMC is now building :).

---

### Post by Hirs on 2010-11-05
> **Georche said:**
> 
I might have done some things twice, or in the wrong order, but at least XBMC is now building :).

Is xbmc using hw acceleration for you? I could compile but not use it :(

---

### Post by ddewaele on 2010-11-08
> **Hirs said:**
> Is xbmc using hw acceleration for you? I could compile but not use it :(

Here's a post showing how to get GPU acceleration up & running with ubuntu & XBMC using Intel HD graphics (Core i3)

[http://doityourselfhtpc.wordpress.com/2010/09/09/intel-core-i3-h264-gpu-acceleration-using-ubuntu-and-xbmc/](http://doityourselfhtpc.wordpress.com/2010/09/09/intel-core-i3-h264-gpu-acceleration-using-ubuntu-and-xbmc/)

---

