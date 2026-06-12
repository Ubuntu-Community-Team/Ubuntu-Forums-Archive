---
title: "v4l-dvb compile error (implicit declaration of function 'skip_spaces')"
date: 2010-08-26
forum: Multimedia Software
---

### Post by LloydM999 on 2010-08-26
I am running Lucid Lynx. I downloaded the [latest v4l-dvb package]("http://linuxtv.org/hg/v4l-dvb/rev/a4c762698bcb"), generated the .config file, and changed the FiredTV support to "n." However I'm still getting an error with the initial "make":

[FONT=Courier New][SIZE=1]v4l-dvb/v4l/ir-sysfs.c:137: error: implicit declaration of function 'skip_spaces'[/SIZE][/FONT]

The line is [FONT=Courier New]tmp = skip_spaces(data)[/FONT], it looks like there's no .h declaration or .c definition of that method in the v4l directory.

How do I fix it, I didn't see any solutions for this on the web. Or does it even matter, I went ahead with "make install" and it installed the firmware without any errors.

 -Thanks, LloydM999

---

### Post by Chunk of Earth on 2010-08-29
Lloyd,

Copy and paste [this patch file from Mauro]("http://permalink.gmane.org/gmane.linux.drivers.video-input-infrastructure/21772") into a text file and save it in the v4l-dvb/linux directory of your repository.  (the file name is your choice)

cd into the linux directory and run the following command
```
patch -p1 -i *patchfile-name*
```(replace *patchfile-name* with the name you gave the patch file)

You should then be able to compile and install as normal.

---

### Post by LloydM999 on 2010-08-31
CoE -

That patch didn't work for me. All 5 "hunks" succeeded, but "make" gave me errors in "firedtv-1394.c".


 -LloydM999

---

### Post by Chunk of Earth on 2010-08-31
See? I told you it would compile normally. You've now encountered a different and well-known problem. One to which the solution may be found in your original post.

---

### Post by LloydM999 on 2010-09-01
OK, I didn't know I had to change .config again (to not compile fired-tv) after the patch. After the change, both make and make install didn't give any errors. 

mythtv-setup detected the DVB stick, but the Terrestrial channel scan didn't find any channels. I guess that's a different problem though...

---

