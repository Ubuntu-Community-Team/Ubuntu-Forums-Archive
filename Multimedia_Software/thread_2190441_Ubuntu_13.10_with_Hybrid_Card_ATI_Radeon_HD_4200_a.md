---
title: "Ubuntu 13.10 with Hybrid Card ATI Radeon HD 4200 and RADEON HD 6370M/7370M"
date: 2013-11-27
forum: Multimedia Software
---

### Post by michelmarechal on 2013-11-27
Hello, everyone!

I'm having some issues to install the correrct drivers to my hybrid card system on Ubuntu 13.10. Actually, these cards never worked fine on any version of Ubuntu.

But, I'm excited about the new Ubuntu sopport for those kind of driver and I want to know: can I install them correctly?

I've already tried some solutions, but with no success:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
And install proprietary driver from repositorys.

I also know that the HD 4200 is no longer supportet by AMD, but 6370 is. And, if it's impossible to install them correctly, is at least possible to chosse wich card i want to use with the OpenSource driver?

Thanks and really sorry about my poor english!

sudo lspci -nnk | grep -A5 VGA
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:1445]
    Kernel driver in use: radeon
01:05.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series] [1002:970f]
    Subsystem: Hewlett-Packard Company Device [103c:1445]
    Kernel driver in use: snd_hda_intel
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] [1002:68e4]
    Subsystem: Hewlett-Packard Company Radeon HD 6370M [103c:1445]
    Kernel driver in use: radeon
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: wl

---

### Post by Bashing-om on 2013-11-28
michelmarechal; Hi ! Welcome to the forum .

Sorry I have no direct help I can offer. Indirectly, a lot has been done in version 13.10 to support graphics:
see these and see if they offer any relevancy :
[https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)
[http://test.ubuntu-discourse.org/t/hybrid-graphics-with-amd-and-nvidia-in-ubuntu-13-10-and-12-04-3/1144](http://test.ubuntu-discourse.org/t/hybrid-graphics-with-amd-and-nvidia-in-ubuntu-13-10-and-12-04-3/1144)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

[INDENT][INDENT]good info is where you find it
[/INDENT][/INDENT]

---

### Post by michelmarechal on 2013-12-01
Thanks for the help, but I've already tried all these methods, with absolutely no success.

---

### Post by Bashing-om on 2013-12-01
michelmarechal; Hey !

The solution I see most recommended is the BumbleBee project:
example:
[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)

For BumbleBee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

Not much,
[INDENT][INDENT]hope it still helps
[/INDENT][/INDENT]

---

### Post by michelmarechal on 2013-12-01
Ok, but isn't BumbleBee for Nvidia drivers? I'm using two AMD video cards...

Thx!

---

### Post by QIII on 2013-12-01
Yes.  Bumblebee is for Nvidia.

You don't actually have a hybrid, which is Intel with either AMD or Nvidia.

What you have is dual graphics.  The problem is that if you want to use a proprietary driver, you won't be able to in 13.10 because uses a version of X Server that the driver for the HD 4200 will not work with.  AMD dropped support for their cards prior to HD 5000 quite a while ago.

You may get suggestions for ways to hack that, but I highly recommend against those methods because they downgrade X, use the legacy driver and add patches to the kernel.  Effectively, they break your installation.

Ubuntu now includes good support for the hybrids -- that is Intel/AMD hybrids.  I don't think that extends to dual AMD/AMD systems where one of the GPUs is not supported by AMD/ATI.

---

### Post by Atominus on 2013-12-13
Hello, I batteled with the same problem for a week and a half.
My boot parameter looks like this:

   GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi="**
GRUB_CMDLINE_LINUX=""



If you have dual boot, you can edit the parameters above.
Choose "advanced options for ubuntu" at startup.
Press "e" on the topmost line.
Edit boot options on following line: 
[B]"quiet splash nomodeset acpi_osi="
[/B]Press ctrl+x
Then you should be able to sign in.


If you don´t have dual boot, then press sift repeateldy during boot.Choose "advanced options for ubuntu" at startup.
Press "e" on the topmost line.
Edit boot options on following line: [B]
**"quiet splash nomodeset acpi_osi="**[/B]
Press ctrl+x
Then you should be able to sign in.
IF you succeed to sign in, you must edit grub.conf
Open terminal.
code
sudo gedit etc/default/grub
(enter password)

edit line where is quiet splash to following[B]
**[B][B]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi="**
[/B][/B][/B]save and exit

add **ppa:xorg-edgers/ppa**           to your system's Software Sources
sudo apt-get update && sudo apt-get upgrade

you should be able to use ubuntu, but you are not able to use fglrx (ati driver)

This helped:
 [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by michelmarechal on 2013-12-17
Hey, I'm back again for one last try...

I was thinking on my problem and i realized, the biggest issue is the lack of support for the Radeon 4000 series, but no for de Radeon HD 6370, am I right?

So, it is possible to make Ubuntu ignore completely the Radeon 4200 and work only with the dedicated GPU? This way I would be able to install the driver properly and run Ubuntu 13.10 with no problem. At least I hope so...

Is there some light for me?

Thanks!

---

### Post by michelmarechal on 2014-01-08
[COLOR=#000000]Hey, I'm back again for one last try...[/COLOR]

[COLOR=#000000]I was thinking on my problem and i realized, the biggest issue is the lack of support for the [/COLOR][COLOR=#417394]Radeon[/COLOR][COLOR=#000000] 4000 series, but no for de [/COLOR][COLOR=#417394]Radeon[/COLOR][COLOR=#000000] HD [/COLOR][COLOR=#417394]6370[/COLOR][COLOR=#000000], am I right?[/COLOR]

[COLOR=#000000]So, it is possible to make Ubuntu ignore completely the [/COLOR][COLOR=#417394]Radeon[/COLOR][COLOR=#000000] 4200 and work only with the dedicated GPU? This way I would be able to install the driver properly and run Ubuntu 13.10 with no problem. At least I hope so...[/COLOR]

[COLOR=#000000]Is there some light for me?[/COLOR]

---

### Post by agripinoduarte on 2014-03-20
I think HD 4200 has supported drivers, acording to this: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Have you tried to use vgaswitcheroo to switch between primary and discrete cards?

I have a HP laptop with the same dual boot gpu and same issue with proprietary drivers in Linux Mint 16 64bit kernel 3.13. The open source driver is ok, but it has a low fps when I play Team Fortress 2, unlike Windows and I really want to play this game on linux. My last try was installing fglrx + fglrx-pxexpress (which writes the correct xorg.conf config for the dual gpu set). But for some reason the driver crashes, the X doesn't starts. Also, I tried this [http://ubuntuforums.org/showthread.php?t=1906654&p=11600468#post11600468](http://ubuntuforums.org/showthread.php?t=1906654&p=11600468#post11600468) but it only switches between mesa and fglrx. I think the 

If I find a practical solution I wlll post it here or in my github page

---

