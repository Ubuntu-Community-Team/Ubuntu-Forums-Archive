---
title: "Installing Nvidia driver on bleeding edge 2.6.25-rc* kernels"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by gaspard.leon on 2008-04-05
for those nvidia users trying to use a 2.6.25-rc* kernel, and having trouble building the Nvidia kernel module:

Patches to use nvidia drivers with 2.6.25-rc* kernels: **[http://www.nvnews.net/vbulletin/showthread.php?t=110088](http://www.nvnews.net/vbulletin/showthread.php?t=110088)**
(I found it in this discussion on page 6: [http://www.nvnews.net/vbulletin/showthread.php?t=107144](http://www.nvnews.net/vbulletin/showthread.php?t=107144))

**there are patches for 71, 96, 169 series drivers there, and they work.**

[COLOR="Red"]I'm currently using gutsy with the 2.6.25-rc8 kernel w/ the 169.12 driver and it works!![/COLOR]

Steps I used to upgrade (this is my Ubuntu 7.10, I don't know if feisty or hardy would work):
(replace [COLOR="Navy"]NVIDIA-Linux-x86-169.12-pkg1.run[/COLOR] names in navy text with your filenames)


[LIST=1]
[*]build a 2.6.25-rc* kernel (I used [KernelCheck]("http://kcheck.sourceforge.net/"), and spent 2 hours customizing the config...)
[*]download nvidia driver from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) , and patch from link above
[*]patch the driver using instructions from link above (run this in a terminal: [FONT="monospace"][COLOR="DarkSlateGray"]sudo sh [COLOR="Navy"]NVIDIA-Linux-x86-169.12-pkg1.run[/COLOR] --apply-patch ./[COLOR="Navy"]NVIDIA_kernel-169.12-2286310.diff.txt[/COLOR][/COLOR][/FONT]) this step will spit out a new [COLOR="Navy"]NVIDIA-Linux-x86-169.12-pkg1-custom.run[/COLOR] file
[*]reboot into your new kernel (cross your fingers the config was right), failsafe X will probably come up.. use vesa driver for now
[*]jump into tty1 (ctrl-alt-F1)
[*]kill gdm and X: [FONT="monospace"][COLOR="DarkSlateGray"]sudo /etc/init.d/gdm stop[/COLOR][/FONT]
[*]run driver install: [FONT="monospace"][COLOR="DarkSlateGray"]sudo sh [COLOR="Navy"]NVIDIA-Linux-x86-169.12-pkg1-custom.run[/COLOR][/COLOR][/FONT]
[*]????
[*]PROFIT!!
[/LIST]

BTW: here is the Kernel thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by gaspard.leon on 2008-04-21
just installed nvidia (patched) on a 2.6.25 release kernel I compiled w/ KernelCheck... it works!!
:popcorn:

---

### Post by master_kernel on 2008-04-27
I think I'll use this method for nVidia driver integration for KernelCheck.

Thanks,
master_kernel

---

