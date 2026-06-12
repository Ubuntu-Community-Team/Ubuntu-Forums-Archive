---
title: "NVIDIA Legacy driver headache"
date: 2010-12-06
forum: Multimedia Software
---

### Post by gabetehcabbage on 2010-12-06
Hi there, Ive only been using ubuntu about 2 years so I'm not the most clued up user. My girlfriends laptop melted so I've dug out her old pc, wiped it clean and put a fresh ubuntu 10.10 32 bit install on it.

I'm now trying to configure the old AGP NVIDIA GeForce2 GTS/Pro its got in it because without it video playback is horrible. I downloaded the legacy driver 7184 ([http://www.nvidia.com/object/linux_display_ia32_1.0-7184.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7184.html)) as it seemed to be the most upto date legacy driver for her card.
I shut down xserver with "sudo /etc/init.d/gdm stop", pressed Ctrl+Alt+F1 and ran the driver with sudo sh NVIDIA-Linux-x86-1.0-7184-pkg1.run.

It returned an error saying 
"No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download the kernel interface for your kernel from the NVIDIA ftp site (ftp://download.nvidia.com)?"
When I select yes it says 
"No matching precompiled kernel interface was found on the NVIDIA ftp site; this means the installer will need to compile a kernel interface for your kernel."
When I press OK it says 
"Unable to determine the version of the kernel sources located in '/lib/modules/2.6.35-23-generic/build'. Please make sure you have installed the kernel source files for your kernel and that they are properly configured. If you know the correct kernel files are installed, you may specify the kernel source path with '--kernel-source-path' command line option."

I've hunted round forums for the last couple of days but nothing I've fund so far has helped at all. I'm stumped and I barely understand half of whats been said. Help would be appreciated, the computer needs to last at least another 6 months until we can afford to replace the laptop.
Thanks in advance.

---

