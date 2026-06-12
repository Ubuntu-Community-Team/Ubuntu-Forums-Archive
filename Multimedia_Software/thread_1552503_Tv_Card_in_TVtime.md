---
title: "Tv Card in TVtime"
date: 2010-08-13
forum: Multimedia Software
---

### Post by tommah04 on 2010-08-13
hello awesome people of ubuntu forums,

I got my hands on a pretty cheap TV card AverMedia m791, also known as 23888, so I'm just trying to get it to work.
I've read TVtime is a good, simple application to just watch live tv.  whenever I open TVtime the window pops up but immediately closes.  I went into the terminal and this is the error...

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/tom/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/tom/.tvtime/tvtime.xml: Permission denied.
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    Your capture card driver: pac207 [CIF Single Chip     /usb-0000:00:02.0-2/132864]
    does not support full size studio-quality images required by tvtime.
    This is true for many low-quality webcams.  Please select a
    different video device for tvtime to use with the command line
    option --device.

I/O error : Permission denied
I/O error : Permission denied
Segmentation fault

when adding "sudo" it solves the "Permission denied" but there's something else wrong that's well over my head. Any help would be awesome, its not a huge problem because I dual boot win7 and I got it to work in there, I just find it a pain to switch back and forth just for TV.

Ubuntu 10.04
amd64
TVtime
AverMedia m791   23888
ATI Radeon HD 4600


thanks in advance!

---

### Post by tommah04 on 2010-08-17
bump

---

### Post by jobix on 2010-08-18
> **tommah04 said:**
> 

when adding "sudo" it solves the "Permission denied" but there's something else wrong that's well over my head. 



What are the error messages when you use sudo? What is this "something else wrong" that you refer to? More specific information can help others to diagnose the issue.

---

