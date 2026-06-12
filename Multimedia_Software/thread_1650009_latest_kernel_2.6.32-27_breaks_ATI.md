---
title: "latest kernel 2.6.32-27 breaks ATI"
date: 2010-12-20
forum: Multimedia Software
---

### Post by markthekdeguy on 2010-12-20
Kubuntu 10.04 LTS
Propriety ATI 'driver' installed via Jockey-KDE
was on kernel 2.6.32-27
then took a kernel update to
2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux
and lost all 2D and 3D acceleration. again.

anyone know why / how / when this breakage will stop plz ?

Mark

---

### Post by PhantmKllr on 2010-12-21
Get the fully supported drivers from the AMD website. [http://www.amd.com/]("http://www.amd.com/")

---

### Post by markthekdeguy on 2010-12-21
these still break X ...

---

### Post by PhantmKllr on 2010-12-21
There is a update to the kernel. Update the kernel, and try the ATI drivers again.

---

### Post by markthekdeguy on 2010-12-22
it still breaks X :(

any attempt to get good 2d / 3d acceleration using FGLRX fails.
the propriety ATI web driver errors out :

Architecture: i686 (32-bit)
X Server: X.Org 7.5
DKMS part of installation failed. 

so does jockey with similar complaints about FGLRX:
so ran ATI uninstall. errored again:


Error! There are no instances of module: fglrx
8.801 located in the DKMS tree.
Errors during DKMS module removal

(all headers were correct and installed)

so i went back to 2.6.32.26 after ten minutes of pain.
i knew this would happen again. i have a second HD with a clean
fresh install on. same errors.

so i wont bother, it seems there is a subtle difference
between minor these minor revs of the kernel, enough to kill X.
had to remove the .27 kernel et al, set xorg to VESA (to get X up) then run jockey, install FGLRX. working.

---

### Post by PhantmKllr on 2010-12-22
I know that there were some issues with 10.04 and ATI graphics cards (I have ATI Radeon Xpress 1150). These issues were solved in 10.10.

---

### Post by morick on 2010-12-22
I've just discovered the exact same problem Mark faced recently. I ran update manager and installed the new kernel (linux-image-2.6.32-27-generic) and it is now screwing up fglrx. I've been trying to remove the kernel via Synaptic and also by running apt-get remove --purge linux-image-2.6.32-27-generic but I get the following error:


Removing linux-image-2.6.32-27-generic ...
Examining /etc/kernel/prerm.d.
Failed to process /etc/kernel/prerm.d at /var/lib/dpkg/info/linux-image-2.6.32-27-generic.prerm line 268.
dpkg: error processing linux-image-2.6.32-27-generic (--purge):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32-27-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


How the hell do I get rid of this kernel so I can use my graphics card again!?

Patrick
Ubuntu 10.04 - AMD

---

### Post by markthekdeguy on 2010-12-22
> **PhantmKllr said:**
> I know that there were some issues with 10.04 and ATI graphics cards (I have ATI Radeon Xpress 1150). These issues were solved in 10.10.

using Ubuntu 10.10 or Kubuntu 10.10, same machine,
similar problems, because i tried them  :(
Also Nvidia caused similar problems, different machine.

linux Mint derived from *buntu 10.04 also failed.

not the end of the world though, i have 2d / 3d accel and its ok.
i only wish to use LTS on these 2 main machines.

Thanx anyway PhantmKllr .. Happy Holidays :)

---

### Post by markthekdeguy on 2010-12-22
Hi Patrick, as long as you have your previous kernel installed, 
i would just uninstall the naughty one :)

i guess you have Synaptic package manager installed ?
here's what i did, 

i booted up, logged in and using the unwanted kernel, i opened a terminal,
typed  uname -a  to see which kernel i was to dispose of, in my case it said:

Linux orac 2.6.32-27-generic. blah blah blah

- the previous kernel that worked with FGLRX was 2.6.32-26, and
i wanted to go back. so i searched for 2.6.32-27 in Synaptic, 
and removed it all. )  DKMS lets the kernel device drivers __ be automatically
rebuilt when a new kernel is installed and so it runs after removing the newer
(but not-wanted) kernel. good.

reboot, using 2.6.32-26, u will prob log in to your desktop ok,
(x died for me, so i edited /etc/X11/xorg.conf to replace    vesa
in place of  glx and fglrx)

sudo nano /etx/X11/xorg.conf

Load    "glx"
Driver   "fglrx"

but you may not need to if X starts ..
rebooted, x came up, ran jockey, jockey installed ATI
rebooted again, and got on with making my curry :)
good luck !

---

### Post by morick on 2010-12-24
I finally uninstalled the buggy kernel. I ended up booting into 2.6.32-27, uninstalling the bad kernel, and reinstalling fglrx. Thanks Mark! 


Cheers,
- Patrick

---

### Post by Chocrates on 2010-12-24
i purged fglrx and reinstalled mesa.  Definitely not ideal but the lappy works again.  Ill see if i can get a previous kernal or reinstall ati to get it to work

---

### Post by markthekdeguy on 2010-12-24
cool :) nice work Patrick !
Happy Christmas !

---

