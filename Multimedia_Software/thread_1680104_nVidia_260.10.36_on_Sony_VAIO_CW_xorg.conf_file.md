---
title: "nVidia 260.10.36 on Sony VAIO CW xorg.conf file"
date: 2011-02-02
forum: Multimedia Software
---

### Post by burlak89 on 2011-02-02
I am running Ubuntu 10.10 on a 64-bit Sony VAIO CW with an nVidia 310M video card. I got to install the nVidia driver 260.19.36 (that should be in the title, not 260.10.36), but the xorg.conf file needs to be different. If I don't edit the file, X will fail to start and I won't get any video (just a command line). The xorg.conf file I found from that same tutorial doesn't do the job.

This is the tutorial I used: [http://ubuntuforums.org/archive/index.php/t-1481842.html](http://ubuntuforums.org/archive/index.php/t-1481842.html)

What can I replace the xorg.conf created by the driver originally with so that it works upon a restart of X?

EDIT: Here is the error I get when I run that startx with that version of xorg.conf:

"Error: API mismatch: the NVIDIA kernel module has version 260.19.06,
but this NVIDIA driver component has version 260.19.36. Please make
sure that the kernel module and all NVIDIA driver components
have the same version."

---

### Post by BicyclerBoy on 2011-02-02
With no consideration of the correctness of the commands w.r.t Sony laptop..
The xorg.conf in that link should have used DFP-0 & not DPF-0. Typo.

I think your video driver install is messed up hence the version mismatch.

If you installed by the nvidia script method (X server stopped) then:
The kernel module has to be compiled against the kernel headers package.
Install the kernel headers package that matches your kernel version first.
uname -r

This nvidia method is always broken by updates.. better to use a 3rd party ppa for pre-compiled binary that matches your kernel & is correctly package managed & installs in the desktop GUI.

So get the right kernel headers & try nvidia install script again & read the error messages.

---

