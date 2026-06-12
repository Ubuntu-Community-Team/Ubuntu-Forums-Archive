---
title: "Belkin wireless adaptor"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by gdn1947 on 2009-03-29
Ubuntu 8.10 standalone installation on IBM R40e laptop. Still trying to get my Belkin USB wireless adaptor working!

These are the initial instructions

Installation instructions for the Legacy rt73 module
[[http://rt2x00.serialmonkey.com]](http://rt2x00.serialmonkey.com])


==================
Build Instructions
==================

    1. Unpack the driver sources and go to the Module directory:
          $ tar -xvzf rt73-cvs-daily.tar.gz
          $ cd ./rt73-cvs-YYYYMMDDHH/Module

    2. Compile the driver sources:
          $ make

    3. Install the driver (as root):
          # make install

and this the Terminal response

george@george-laptop:~$ tar -xvzf rt73-cvs-daily.tar.gz
tar: rt73-cvs-daily.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Ive obviously done something wrong or missed a step etc so any help would be appreciated

Thanks

---

### Post by chili555 on 2009-03-29
It probably means you are not in the directory where the .tar.gz was downloaded. Firefox by default, downloads to Desktop. Your command prompt:> george@george-laptop:[COLOR="Red"]~[/COLOR]$tells us you are in '/home/george.' You probably want to be in '/home/george/Desktop.'

Do you see the downloaded file on your desktop? If so, open your terminal and do:```
cd Desktop
```Now proceed with your commands.

---

### Post by sgosnell on 2009-03-29
Or you can open the file manager, find the archive, right-click on it, and select Open with Archive Manager.  When that opens, select the directory where you want to put it, probably george, and click on Extract.  Then open a terminal and start from 

cd ./rt73-cvs-YYYYMMDDHH/Module

where I assume YYYYMMDDHH would be changed to numbers representing the date and time of the build.  Entering cd rt73 and then pressing Tab should get you into the correct directory.

---

