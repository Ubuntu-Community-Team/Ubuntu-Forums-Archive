---
title: "Connecting to Android 2.2 wifi hotspot makes 11.04 to crash."
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by BrigTSD on 2011-04-29
I often connects my laptop (Asus EEE) to my HTC desire hd with the wifi hotspot. But this doesn't work since yesterday when I upgraded to 11.04. When I connect the laptop to the phone the screen on the laptop goes black with a lot of scrolling text then it freezes.

This worked out of the box without any problems with 10.10. Is there anyone else who experience the same problem with 11.04?

---

### Post by _gaffer on 2011-05-03
Yep, I'm getting the exact same problem.

Everything worked fine, then after dist upgrade any attempt by the netbook to connect to the HTC Desire's wifi hotspot results in a kernel panic.

If there's anyone here better acquainted with the voodoo of wifi connectivity, I'm happy to help with any info that might be helpful since the main point of both the netbook and mobile data plan I have is using them together.

---

### Post by richwillal on 2011-05-18
On Kubuntu 11.04 it's not crashing, but it continually tries to connect to my wifi hotspot on an Droid 2 Global.  The same connection works on 10.04 and from Windows with no issues.

---

### Post by linux_one on 2011-05-19
the problem is with the kernel in 11.04, seems to include all newer asus eeepc's and is solved in latest kernel.
 to solve that you can download the latest kernel and install it very easily;
 go to 
http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/
and download the files; 

linux-headers-2.6.39-999_2.6.39-999.201105191210_all.deb
linux-headers-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb
linux-image-2.6.39-999-generic_2.6.39-999.201105191210_i386.deb

(or different versions depending on time) then install them in exactly same order by the command;

sudo dpkg -i filename

one after the other, then restart the netbook. it worked perfectly for me.

---

