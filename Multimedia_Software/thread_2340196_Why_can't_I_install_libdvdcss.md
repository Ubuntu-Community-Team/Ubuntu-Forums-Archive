---
title: "Why can't I install libdvdcss?"
date: 2016-10-16
forum: Multimedia Software
---

### Post by caraj on 2016-10-16
I went to this page [http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu](http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu) for instructions. 

Clicking the install link just gets me > Package 'libdvdcss2' is virtual. [FONT=courier new]Typing sudo apt-get install libdvdcss [/FONT]just gets me ```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

I'm using the above methods instead of the software center because it just says No Application Data Found when I open it.

**Update:**

I experimentally typed [FONT=courier new]sudo apt-get install libdvdcss2 [/FONT]instead, and it looked like i was making progress until I got the message > [FONT=courier new]This package automates the process of launching downloads of the source   &#9474; 
 &#9474; files for libdvdcss2 from videolan.org, compiling them, and installing    &#9474; 
 &#9474; the binary packages (libdvdcss2 libdvdcss-dev).                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Please run "sudo dpkg-reconfigure libdvd-pkg" to launch this process for  &#9474; 
 &#9474; the first time.  [/FONT]
But that didn't work, and now I'm getting the message > [FONT=courier new]libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reconfigure libdvd-pkg".
libdvd-pkg: Building and installation of package(s) [libdvdcss2 libdvdcss-dev] postponed till after next APT operation.
Processing triggers for libc-bin (2.23-0ubuntu3) ...
W: Operation was interrupted before it could finish[/FONT]

[B]
Update:[/B]

I did [FONT=courier new]sudo dpkg-reconfigure libdvd-pkg[/FONT] wrong. When I typed it again, it worked. DVDs now play.
[FONT=courier new]
[/FONT]

---

### Post by jeremy31 on 2016-10-16
Did you have Software Center open when you tried the terminal command?  Close it if it was open and try the terminal command again

---

### Post by deadflowr on 2016-10-16
What version of Ubuntu?
in 16.04 the package is
libdvd-pkg, so
```
sudo apt install libdvd-pkg
```
it is in multiverse, so make sure it is enabled, fwiw.

---

### Post by ajgreeny on 2016-10-16
Yes, I think those instructions you linked are now out of date.

You need to follow the simplified info for **Ubuntu 15.10 and newer** at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs), assuming you are on 16.04.

If on 14.04 you will need to follow the info in the section **Ubuntu 12.04 up to 15.04 (i386, amd64)**.

---

