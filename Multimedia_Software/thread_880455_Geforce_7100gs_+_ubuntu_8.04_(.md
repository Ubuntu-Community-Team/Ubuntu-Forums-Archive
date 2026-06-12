---
title: "Geforce 7100gs + ubuntu 8.04 :("
date: 2008-08-05
forum: Multimedia Software
---

### Post by SebastianEE612 on 2008-08-05
hello everyone, this is my first post here and the first thing i want to do is to apologize for my "english" :)

my problem started after i've upgraded my ubuntu from 7.04 to 8.04 - my graphic card refused to work. 
(Im working on AMD Athlon 2600XP+ (~2Ghz), 1gb DDR2 Dual Channel, Geforce 7100GS, Matrox ATA 160gb).
After upgrade i received message "ubuntu runs on low graphics mode" or sth similar. I thought it was drivers fault, so i changed my xorg.conf to settings which i had before and of course ive picked the "nvidia" driver instead of vesa or nv. But it did not change anything - still i was getting the same message. Then i've removed supported drivers (nvidia-glx-new) and changed my driver to "nv" - and everything worked fine, but as you know there is a huge difference between "nvidia" driver and "nv"... :/

On the polish ubuntu forum they told me that my card is not supported by the latest driver 169.12 (but why? i was using it when i had 7.04) and to take a look at this page [http://www.nvidia.pl/object/linux_supported_pl.html](http://www.nvidia.pl/object/linux_supported_pl.html) . They also told me to change my driver to 96.43 (nvidia-glx) so i did, but id did not work either (kernel errors, "cant find suitable driver for my kernel version" etc etc).
Then i tried to install kernel source (sudo apt-get install nvidia-glx nvidia-kernel-source) but i got this message:
> 
Configuring nvidia-kernel-source (1:96.43.05+2.6.24.500-500.23~envy) ...
Adding Module to DKMS build system
driver version= 96.43.05
Doing initial module build
Error! Your kernel source for kernel 2.6.22-14-generic cannot be found at
/lib/modules/2.6.22-14-generic/build or /lib/modules/2.6.22-14-generic/source.
Installing initial module
Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.22-14-generic (i686) first.
Done.


... So I tried drivers 173.08 but:
> 
The compiler used to compile the kernel (gcc 4.1) does not exactly match the
current compiler (gcc 4.2). The Linux 2.6 kernel module loader rejects kern
el modules built with a version of gcc that does not exactly match that of t
he compiler used to build the running kernel.
If you know what you are doing and want to ignore the gcc version check, sel
ect "No" to continue installation. Otherwise, select "Yes" to abort install
ation, set the CC environment variable to the name of the compiler used to c
ompile your kernel, and restart installation. Abort now?
(Answer: No)

later:
> 
ERROR: Unable to find the kernel source tree for the currently running kernel.
Please make sure you have installed the kernel source files for your
kernel and that they are properly configured; on Red Hat Linux systems,
for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
installed. If you know the correct kernel source files are installed,
you may specify the kernel source path with the '--kernel-source-path'
command line option.

At the end I tried using ENVY. It recognized my card as Geforce 7100GS, installation ended without errors but after restart everything went back to 800x600 with "nv" driver. 


Anyone? :( You are my last hope guys :) 
and one more time, sry for my english and all the grammar/spelling mistakes.

---

### Post by cdtech on 2008-08-05
Could I have a look at your "/etc/X11/xorg.conf" file....

Do you currently have the original setup?
```
nvidia-glx-new
nvidia-kernel-common
nvidia-new-kernel-source
nvidia-settings
```

Also, do you have the:
xserver-xorg-video-v4l

---

### Post by ne4ve on 2008-08-05
Just to give you some hope I've just got my 7100GS setup on 8.04 (Mythbuntu) x64. The drivers got into a pickle (probably my fault) and I then couldn't uninstall the nvidia-glx-new driver because it was looking for a 'lib32' folder which obviously didn't exist on my x64 install. Just created a folder called lib32 and was then able to remove and reinstall it.

In the end I removed all the drivers with something like:
```

apt-get --purge remove nvidia-glx-new nvidia-kernel-common nvidia-new-kernel-source nvidia-settings linux-restricted-modules-2.6.24-19-generic

```

then made sure I had a clean /etc/X11/xorg.conf file with :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then reinstalled them with
```
apt-get install nvidia-glx-new nvidia-kernel-common nvidia-new-kernel-source nvidia-settings linux-restricted-modules-2.6.24-19-generic
```

once I restarted I was then able to select System->Administration->Hardware Drivers and enable the nVidia driver. Another restart and I had sexy windows!

In my extremely limited Ubuntu knowledge I think it may be down to your kernel version. Notice the the restricted drivers are for 2.6.24-19. You may need to do something like

```

apt-get update
apt-get upgrade

```

to ensure you have the latest kernel. Once you've done this remove those drivers I mentioned previously and then reinstall them again. Check to see that the right versions get installed.

This is pretty fresh in my mind so if this doesn't work let me know and I'll try and help further. I'd like to check this myself just incase I ever need to refer back to it!

Good luck

---

### Post by SebastianEE612 on 2008-08-06
ok this is my xorg.conf after i did everything as ne4ve told me to and after i did "nvidia-xconfig":

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


I have noticed that in system->administration->drivers is nothing. it just says that my system doesn't need any of restricted drivers...

...restart...

...and again the same thing. "Ubuntu runs on low graphics mode". It seems it somehow refuses to work with nvidia drivers :(

Im going back to my old xorg.conf settings:
> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

help :)

---

### Post by ne4ve on 2008-08-06
After I did the 'apt-get --purge remove' and the xorg reconfigure my xorg.conf looks like this

```

...
Section "Device"
        Identifier      "Configured Video Device"
EndSection
...

```

if yours doesn't you could try:
```

sudo dpkg-reconfigure xserver-xorg

```
So same as before but without the -phigh option. This will present a text based interface where you have to select some basic stuff. Just accept the defaults (unless you fancy changing your locale settings. For example as I'm in the UK I had to enter 'en' then 'gb' for keyboard and variant.

Bear in mind that I'm all new to this but it's just what I got working. I've just noticed that on my laptop it removed the old restricted modules (2.6.24.16) as well as the new ones (2.6.24.19). 

Can you check what version of the kernel you are using (uname -a).

Also was the install successful? What version of the linux-restricted-modules was installed and what version of nvidia-glx-new was installed? (Should be indicated at the end of install)

After doing an uninstall make sure you do
```

apt-get-update
apt-get-upgrade

```
and you could also do
```

apt-get autoremove

```

Only after I'd enabled the restricted driver did the xorg.conf change to
```

...
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection
...

```

If it's not letting you select the nVidia restricted driver after all that then I'm a bit stumped. It's always let me do that. Except straight after the removal command (because you've just removed them all of course!).

---

### Post by SebastianEE612 on 2008-08-07
Weird :/ Now I am at work, so I will try your solution later, but it is amazing that everything worked fine in ver.7.04 or ver.6 and now something is wrong. I thought it was my fault because ive installed 8.04 beta and then ive upgraded it to 8.04 final version - but when I formatted my drives completely and I did fresh Ubuntu 8.04 install, I had again the same bug :/ 

As I said, I'll try your solution after work and I'll let you know what happened.

---

### Post by satbunny on 2008-08-07
I have almost the same problem.

If you look around here you'll see various people with similar issues.

The issue seems to me to be a kernel update and/or xserver update that just doesn't work with the current drivers. Running the old xserver configuration tools just seems to leave an almost empty and useless xorg.conf.

I am going to test rolling back to an older kernel and see if that works, be back in 30 minutes!

---

### Post by SebastianEE612 on 2008-08-07
more info, might be important:

> 
seba@sebalinux:/home$ uname -a
Linux sebalinux 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

seba@sebalinux:/home$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Coinfiguration Option: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
seba@sebalinux:/home$ 



and that is my attempt to install nvidia driver from nvidia.com site:
driver version -> 173.14.12

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Aug  7 15:56:58 2008
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

..the same with driver 96.xx and 169.xx :(

---------------------------------


... 5 min ago Ive used EnvyNG to install automatically drivers - and it worked with 173.xx o_O
Thanks guys anyway :)

---

### Post by ne4ve on 2008-08-07
Glad you got it working with Envy. I heard that people had lots of problems with Envy so I've not tried them. Guess they work for some!

---

