---
title: "NVIDIA: Failed to load GLX, API mismatch error"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by cro on 2007-05-25
After a recent round of updates, Ubuntu decided to be narky and fail to load GDM. After staring at the logs for ages, and finding basically no reference to anything, I started investigating.

The base error was this:
```
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9755, but this X module has the version 1.0-9631.  Please make sure that the kernel module and all NVIDIA driver components have the same version.
```
Reading this it seemed to indicate that I needed to have version 1.0-9631 of the Nvidia drivers installed. These are also known as 'nvidia-glx'

However, no matter how many times I removed and reinstalled version 9631 of the drivers, xorg kept complaining about the version mismatch.

The eventual fix was to:
1: remove nvidia-glx
2: install nvidia-glx-new

The error message seems to explicitly say that I have version 9755 of the nvidia drivers installed, which is what was confusing (as I didn't). Rather, it's telling me is that I need to *install* 9755.

This is not the same error as reported on bugtracker, even though the error message is the same.

---

### Post by Ek0nomik on 2007-05-30
Thanks for posting your findings.  This might help someone else in another thread.  ;)

---

### Post by rumli on 2007-06-06
> The error message seems to explicitly say that I have version 9755 of the nvidia drivers installed, which is what was confusing (as I didn't). Rather, it's telling me is that I need to *install* 9755.

This error message confused me as well.  Mine said that the nVidia kernel module has version 1.0-7184 and the X module had version 1.0-9631.  As you point out, the solution is to install nvidia-glx-legacy (1.0-7184), nvidia-glx (1.0-9631), or nvidia-glx-new (1.0-9755) so as to match the version of nVidia kernel module in the error message.

---

### Post by onno on 2007-06-14
I had the same problem: an api mismatch because the nvidia kernel module was version 1.0-7184 and the X module version was  1.0-9631.

Installing nvidia-glx-new did the trick for my system. It's probably worth mentioning here, though, that if you've experimented heavily with all the nvidia related packages or even a self compiled nvidia driver, you should remove these first (see [http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/]("http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/"), step 3)

When I had finished installing Ubuntu Feisty, I had my Iiyama A702HT VisionMaster Pro 410 monitor working on my NVIDIA GeForce 6800 video card, but not until I booted into Ubuntu using the recovery mode (using Grub). Apparently, the recovery mode had some generic xorg.conf configuration (maybe vesa? -- can't reconstruct that, messed up things afterwards), because it all worked fine -- albeit in a low resolution and video refresh rate.

So, while in recovery mode, I installed the nvidia "restricted driver" (System > Administration > Restricted Drivers Manager). This worked fine, especially after I configured Xorg to use all the available screen resolutions. You do this through /etc/X11/xorg.conf, where you introduce new "modelines" (see [http://www.bohne-lang.de/spec/linux/modeline/]("http://www.bohne-lang.de/spec/linux/modeline/") ). This is also explained in detail here: [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973").

Then I foolishly decided I wanted to get more performance out of my video card by compiling Nvidia's own drivers. This is explained here: [http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/]("http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/"). After I first uninstalled some crucial packages, I ended up with an xorg.conf file which was totally ruined.

I first had to uninstall the nvidia driver, using:

sudo sh NVIDIA-Linux-x86-1.0-*-pkg1.run --uninstall

And then I had to install nvidia-glx-new.

Anyway, four hours later I now finally understand how xorg.conf works -- at least from the perspective of an end user.

Onno

---

By the way: use ```
sudo nvidia-settings
``` to start a nice nvidia configuration utility.

And one other thing: If you want to use your own "modelines", you have to add ```
Option "UseEdidFreqs" "no"
``` to the "monitor" section of the xorg.conf file, otherwise all your modelines will be ignored.

One final note: to calculate the appropriate modeline, you can also use the command line utility gtf. This worked best for me. Here's an example:

```

onno@onno-desktop:~$ gtf 1152 864 120

  # 1152x864 @ 120.00 Hz (GTF) hsync: 111.12 kHz; pclk: 176.01 MHz
  Modeline "1152x864_120.00"  176.01  1152 1240 1368 1584  864 865 868 926  -HSync +Vsync

```

---

### Post by fanatick on 2008-01-04
ok I installed the driver NVIDIA-Linux-x86-169.07-pkg1.run for my Nvidia 8800gts and reboot

 it restarts and goes to a black screen that says "Starting K Display manager: Kdm" and some other "starting" lines ending with" [OK]"


so I looked around on forum and found I could type "cat /var/log/nvidia-installer.log" to check out the installation went

 And showed everything installed completely and correctly. 

I read other people problems about kubuntu not starting up after installing drivers and I learned that I can do startx to get to the desktop when i typed it,

it says "ERROR: API musmatch: This NVIDIA driver compnent have version 169.07, but the NVIDIA kernel module's version does not match. Please make sure that the kernel module and all NVIDIA driver components have the same version"

can someone please help me I have Idea what to do I keep running into problem after problem but I dont want to give up cause I like the benefits linux bring. I'm new to this so can someone tell me step-by-step what I need to do  and write out the code.

---

### Post by fanatick on 2008-01-04
can anyone help me with my post above?

---

