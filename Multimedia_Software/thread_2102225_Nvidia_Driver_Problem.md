---
title: "Nvidia Driver Problem"
date: 2013-01-06
forum: Multimedia Software
---

### Post by David Vincent-Jones on 2013-01-06
Xubuntu 12.10 ... Lenovo W530 1920 x 1080 display
Installed the latest NVIDIA-Linux-x86_64-304.37 on order to utilize my vga port. Nvidia X-Servings gui appears to be running correctly.

I am getting 'twinkling' pixels (in both black and white) in random sections (attached png) of the top left area of my screen .. AND .. large areas of my screen, again at the top, keep going black and need refreshing by moving a program to replace the color.

The computer is being dual booted and if I run the Windows 7 system there is no sign of similar problems so I am assuming that this is not a screen failure problem.

The following information may be of help:

david@david-W530:~$ uname -ar
Linux david-W530 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
david@david-W530:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [Quadro K1000M] [10de:0ffc] (rev a1)
	Subsystem: Lenovo Device [17aa:21f6]
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nouveau, nvidiafb
david@david-W530:~$ sudo apt-cache policy nvidia-current
[sudo] password for david: 
nvidia-current:
  Installed: (none)
  Candidate: 304.51.really.304.43-0ubuntu1
  Version table:
     304.51.really.304.43-0ubuntu1 0
        500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
david@david-W530:~$ cat /sys/module/nvidia/version
304.37
david@david-W530:~$ /usr/lib/nux/unity_support_test -p
bash: /usr/lib/nux/unity_support_test: No such file or directory
david@david-W530:~$ nvidia-settings --vv

nvidia-settings:  version 304.37 
(buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Wed Aug  8 21:03:08 PDT
2012
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.
  For more detail, please see the nvidia-settings(1) man page.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.

david@david-W530:~$ 

Thank you;

David

---

