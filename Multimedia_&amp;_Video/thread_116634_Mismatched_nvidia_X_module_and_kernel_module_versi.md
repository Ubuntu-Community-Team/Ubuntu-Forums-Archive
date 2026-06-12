---
title: "Mismatched nvidia X module and kernel module versions!!!"
date: 2006-01-13
forum: Multimedia &amp; Video
---

### Post by mmcmonster on 2006-01-13
I installed the version 7667 linux drivers as mentioned in method 1 [here](http://ubuntuforums.org/showthread.php?t=75074).  I later (the next day) followed the instructions in method 2 to upgrade to the latest driver version (8178).  Everything seemed fine, and the nvidia control panel said that I had version 8178.

I turned the computer off last night.  When I rebooted this am, X was not able to start up.  It said that the kernel module version did not match the X module version.

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux delta 2.6.12-10-k7 #1 Thu Dec 22 12:32:10 UTC 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-k7 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 12:32:10 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 13 06:27:11 2006
(==) Using config file: "/etc/X11/xorg.conf"
Error: API mismatch: the NVIDIA kernel module is version 1.0.7667, but
this X module is version 1.0.8178. Please be sure that your kernel
module and all NVIDIA driver files have the same driver version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Please, any help would be appreciated!

---

### Post by mmcmonster on 2006-01-13
To answer my own question (yet again!), I had to remove linux-restricted-modules.

I've really got jump the gun when asking questions sometimes. :-)

At least I'm learning about the ins and outs of the system. :-)

---

### Post by whoscheesemine on 2008-03-07
Were you ever able to play any 3d games though? I'm having a very similar issue, but it seems that the only way I'll be able to play 3d games is if I have the restricted driver, which for some weird reason will not work for me. Here's a link to my thread:

[http://ubuntuforums.org/showthread.php?t=717271](http://ubuntuforums.org/showthread.php?t=717271)

---

