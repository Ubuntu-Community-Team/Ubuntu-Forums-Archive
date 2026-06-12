---
title: "8-10 ATI Graphics Drivers Confusion"
date: 2008-12-03
forum: Multimedia Software
---

### Post by Sabar on 2008-12-03
The root of my Problem is I have a 32" HD Wide Screen T.V. That I can not seem to get to work with Ubuntu. 

I just recently installed 8-10 onto my computer. I am running a duel boot of 8-10 and Windows XP (Please don't hate me I don't use XP hardly at all.)

I have an ATI Radeon x550 Video Card installed (Three Year Old Computer) If I go to Applications > Accessories > ATI Catalyst Control Centre. It has listed under Driver version, 8.54.3  The other thing I noticed is, UNder display manager it has T.V. Listed how ever all these options are greyed out.

So I went looking under ATI's website, and When searching for drivers for Linux They listed Version 8.11 For what I think is my Card. Fear has capt me from trying to install it as of yet. and I don's really understand some of there directions. so I am looking here for advice can some one tell me if it is ok to install this? and do you think it will run a T.V.?

This is the minumim requirements


> Minimum System Requirements
       Before attempting to install the ATI Proprietary Linux driver, the following soft-
       ware must be installed:
       • POSIX Shared Memory (/dev/shm) support is required for 3D apps
       • glibc version 2.2 or 2.3
       • Linux kernel 2.6 or higher
       • XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 or 7.4
               Note: If a Linux 2.6.11 or newer kernel was built with CONFIG_AGP
               enabled, the kernel AGP frontend is required to load the fglrx kernel
               module. To identify whether your kernel was built with CONFIG_AGP
               enabled, look for CONFIG_AGP=y in the kernel config file, or if the
               'agpgart' module is loaded.



> System Recommendations
        For best performance and ease of use, ATI recommends the following:
        • Kernel module build environment
            • Kernel source code includes either the Kernel Source or Kernel Headers
                 packages
        • The RPM utility should be installed and configured correctly on your system,
            if you intend to install via RPM packages
                        ATI CatalystTM Linux Installer Note                           2
• The following packages must be installed in order for the CatalystTM Linux
  driver to install and work properly:
  • XFree86-Mesa-libGL
  • libstdc++
  • libgcc
  • XFree86-libs
  • fontconfig
  • freetype
  • zlib
  • gcc
       Note: In order to use the fglrx internal AGP support, you have to make
       sure that the kernel agpgart support is not active (i.e. it is not compiled
       into the kernel and the kernel modules are not loaded). If the fglrx kernel
       module detects that the kernel agpgart support is active, it will automati-
       cally use that even if its internal AGP support is requested in order to
       avoid conflicts that can cause problems under some circumstances.



I found all this information under there [[COLOR="RoyalBlue"]Installer Instructions[/COLOR]]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

Can anybody explain some of these things to me? and should I install this?

What is POSIX?

Thanks for any information you can give, Sorry its so long just wanted to make sure there was enough info
Sabar

---

### Post by CHaoSlayeR on 2008-12-04
Hi Sabar,

I for myself have had a very bad experience with the 8.11 driver on Hardy Heron (I didn't upgrade to Intrepid yet) but I can tell you I have seen a lot others that finally got things right with that driver.

If you want to install it please refer to this installation guide: [Ubuntu Intrepid Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide").

I hope that helps.

Greetz,

C]-[aoZ

---

