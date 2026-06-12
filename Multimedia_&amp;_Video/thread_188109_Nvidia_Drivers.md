---
title: "Nvidia Drivers"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by mdh on 2006-06-03
Hi Ubuntu users,

The nvidia driver installation is a source of misery for a lot of people. The howtos in this forums greatly help starters to install and troubleshoot problems with nvidia installations. Thanks to all the people who wrote these howtos.

I have some questions on what each packages in the nvidia install process do. I have read that 'nvidia-glx' package installs the GL and GLU libraries, but what purpose does the 'nvidia-kernel-module' and 'nvidia-settings' serve ?

Is there a difference between *apt-get nvidia-glx nvidia-kernel-module nvidia-settings* and *downloading and installing the nvidia driver from the nvidia website ([www.nvidia.com/object/unix.html)](www.nvidia.com/object/unix.html))*.  Whenever I do the latter, I see the script building a kernel module and then installing the libs in /usr/lib directory. Looks like these two steps are equivalent, if so, what are the advantages of one over other.

Sometimes after running the nvidia installer script (downloaded from nvidia website), X fails to start giving an error message that says something like version mismatch between the kernel module and the X module. After doing a apt-get remove nvidia-glx and running then installer script again causes to start normally. 

What am I missing here ??. Any thoughts and help will be greatly appreciated.

---

