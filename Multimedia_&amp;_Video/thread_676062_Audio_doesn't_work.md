---
title: "Audio doesn't work"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by baztard on 2008-01-23
Hi, i've just putted kubuntu 7.10 into my HP Pavilion DV2000 laptop with conexant audio system and there is no sound. Is there any chance I could get drivers or make it work somehow?

Many thanks,
Justin

---

### Post by balaknair on 2008-01-23
You can try this thread
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

Or you can upgrade the driver from the Ubuntu repositories with the following steps
>Enable Gutsy backports repositories in software sources (System menu> Administration> Software sources--> Updates> Enable the Backports option)

>Open a terminal(Applications menu> Accessories> Terminal) and paste the following command to install the packages
*sudo apt-get install linux-backports-modules-generic*
[Note: if you're running a kernel version other than generic, change the line accordingly; to know what kernel version you have, type in a terminal *uname -r* ]

After installing reboot the system.

---

### Post by kmfdmk on 2008-01-26
I'm having the same problem on my DV2000.  My sound originally didn't work, then it did, and now it doesn't again.  Using XMMS...

Currently working on doing the second option with the Update Backports.

---

