---
title: "ati to nvidia card...nvidia-glx install failure"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by burke2134 on 2006-07-24
Hope someone out there can lend be a big 'ol hand on this one...  I swapped out an ATI 9500 series video card for a new NVIDIA card.  Everytime I try to install the package 'nvidia-glx' from the repositories, I run up against this error:

p.s.  This is my first posting, so please let me know if more info is needed, I'm in the wrong forum, etc.  TIA. :)

-----------------------------------------------------------

hav-109-2:~> sudo apt-get install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4059kB of archives.
After unpacking 12.5MB of additional disk space will be used.
(Reading database ... 164656 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Paerez on 2006-07-24
try:
```
sudo aptitude remove xorg-driver-fglrx
sudo aptitude install nvidia-glx
```
that will remove the ATI stuff, then install nvidia. And you are in the right forum and you posted exactly what we need :D

---

### Post by burke2134 on 2006-07-24
Thanks for your help. :)  But I *knew* I was going to screw up something with my virgin post (DOH!)... I forgot to mention that I was running the ATI card using ATI's proprietary drivers using installation instructions I found here:

[http://ubuntuforums.org/showthread.php?t=204910&highlight=ati+proprietary](http://ubuntuforums.org/showthread.php?t=204910&highlight=ati+proprietary)

I didn't see anything in that thread that explicity explained how to uninstall the proprietary driver, but then again I *am* an idiot. :-p

Anyway, here's the result.  Any additonal tips greatly appreciated. :)

-----------------------------

hav-109-2:~> sudo aptitude remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


hav-109-2:~> sudo aptitude install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  nvidia-glx
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4059kB of archives. After unpacking 12.5MB will be used.
Writing extended state information... Done
(Reading database ... 164656 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
hav-109-2:~>

---

### Post by Paerez on 2006-07-24
try running this:
```
sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1
```
then installing nvidia-glx.

---

### Post by burke2134 on 2006-07-24
Wow.  Thanks again for your help.  Looked promising, but not quite smoking a cigar yet.... 

hav-109-2:~> sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1
Password:
Removing `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'

<<<< No errors reported >>>>

hav-109-2:~> sudo aptitude install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  nvidia-glx
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4059kB of archives. After unpacking 12.5MB will be used.
Writing extended state information... Done
(Reading database ... 164657 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb) ...
dpkg-divert: `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.8762+2.6.15.11-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by Paerez on 2006-07-24
now we have to do it again with the new path:
```
sudo dpkg-divert --rename --remove /usr/X11R6/lib/libGL.so.1
```

---

### Post by burke2134 on 2006-07-24
You're my new hero. :D  Looks good from here (I'm remote to that workstation at the moment).  Thank you SO much for your help. :D

---

### Post by Paerez on 2006-07-24
no prob. Thank my company for paying me for the time I spend on ubuntu forums because my jobs is boring :D

---

### Post by Kilz on 2007-07-25
Just a quick post to thank the orignal people in this post if they are still around. Good info never goes out of date. I replaced the radon express x200 graphics with a geforce 7100 gs today and this thread helped. :D

---

### Post by Victormd on 2008-03-28
Going to try this old thread to get some help...
I have an ATI X300 and just purchased a Nvidia 8800GT for the "swapin"... I still have a few days before the nvidia gets here but I want to be ready to swap without, hopefully, having to format and reinstall ubuntu. Here are my main questions:
1. Do I have to uninstall ATI + flglx software before making the switch?
2. If so, do I need to install any general video driver after the uninstall or is this automatic?
3. If not, than can I simply remove one card and put the and expect Ubuntu to detect the change and "suggest" the proper driver?
Not sure I made much sense but...
Thanks!

---

### Post by Knad on 2008-06-09
Hello,

I have the same error. I am getting:

adam@knad-server:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-kernel-source nvidia-settings
The following NEW packages will be installed
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7333kB of archives.
After this operation, 22.4MB of additional disk space will be used.
(Reading database ... 111586 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a96.43.05+2.6.24.13-19.42_amd64.deb) ...
dpkg-divert: Cannot divert directories

dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.13-19.42_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.13-19.42_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I had the errors previous and diverted them, now have this directory error....

Any ideas?
Thanks

---

### Post by raghothams on 2008-06-13
hello
I installed hardy recently. I use a Toshiba laptop which came with a nvidia graphics card- nvidia geforce go4. when i change my desktop apperance settings to NORMAL or FULL, the system installs a new version of _nvidia-glx_. but after installation ther is no display. again when  i reset it in recovery mode n restart, it gets back to old setttings. I cannot use those special effects at all. I very new to ubuntu pl pl help

---

