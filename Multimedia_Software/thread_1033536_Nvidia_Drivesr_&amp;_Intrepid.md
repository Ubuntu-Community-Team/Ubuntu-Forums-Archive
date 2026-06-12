---
title: "Nvidia Drivesr &amp; Intrepid"
date: 2009-01-07
forum: Multimedia Software
---

### Post by ricardo_78 on 2009-01-07
Having a few problems with Intrepid and Nvidia Drivers...

Trying to install the 177 via Hardware Drivers did not work even though i can see three drivers are available.

Looked at Nvidia site guidelines downloaded package stopped GDM as it suggested and tryto install from command line 

Deleted various bits of Nvidia-glx packages and Disabled Modules in linux-restricted-modules-common 

sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

Install fails and output from nvidia install log file...

```


.......
Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 177.82.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.


```

This appears more tricky than it should be :D

---

### Post by memories on 2009-01-07
Basically, to install the drivers, you need to have the sourcecode for the kernel you're currently using. You might just need the linux-headers or you can have a symlink /usr/src/linux point to your linux kernel source (which would be somewhere in /usr/src/). 

Try **apt-cache search linux-headers** and install the ones for your kernel. Also install **linux-source**

To see what kernel you're running do **uname -a**. 

Make sure gdm/Xorg are OFF when you're installing the drivers (sudo killall gdm)

---

### Post by gasto on 2009-01-07
I had the kernel compiled correctly. Too bad everything seemed fine... until I booted to my session. Argh black screen.

---

### Post by ed-koala on 2009-01-08
I could really use a "how-to" on this issue ... If I were to turn off gdm, install Nvidia drivers per Nvidia's instructions, and I end up booting to a command line ... How do I un-do things so I can boot up and not have to reinstall 8.10 from scratch?  (I've had this problem more than once trying to get the driver working)

Also ... should I use the latest 177 series or use the new 180 series drivers??  Dual 9800 GTX+ video cards, sli setup

---

### Post by lamikins on 2009-01-08
Ed-Koala - boot into CLI, sudo aptitude remove all your nvidia packages.  Trying to load xserver (just ctrl alt backspace) should prompt you with a GUI "low graphics mode" notice.  Reject this mode and choose to troubleshoot the problem or to restore some config files (i forget the exact wording - there are three options).  Choose to restore xorg.config to default, reboot X.  If this doesn't work, try the same thing with the backup xorg.conf option (if you have made one).  Of course, if you have made a backup xorg.conf you can manually copy xorg.conf.backup (or whatever it is called) back into .conf from CLI without booting X.  Err...  and *then* boot X.

---

### Post by lamikins on 2009-01-08
Oh...  err...  just occurred to me - that whole rant only applies if you run Xubuntu.  Though I'm sure there are closely equivalent KDE and gnome means by which to achieve the same thing.

*cough* sorry for my egregious presumption.

---

### Post by ricardo_78 on 2009-01-08
Memories: Thanks - Finally got rounnd to it and having downloaded the linux-headers I got it to work with 177 Drivers....

---

### Post by lamikins on 2009-01-08
ricardo!  could you possibly expand on Memory's directions?  I'm not sure exactly how to implement his advice.

---

### Post by lamikins on 2009-01-15
memories - i'm most likely in precisely the same situation as ricardo_78. I tried to create a symlink as per your suggestion:

/usr/src/linux$ ln -s /usr/src/linux-headers-2.6.27-9 my_sym_link

but the nvidia installer still cannot find the required headers (and fails to build them successfully when prompted).  Perhaps i should've labelled the symlink differently?  Still unable to get nvidia running, and my irritation is turning to desperation.  Any help would be awesome.

---

