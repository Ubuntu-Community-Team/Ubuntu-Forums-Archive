---
title: "Installing an older nVidia driver issue"
date: 2012-07-01
forum: Mythbuntu
---

### Post by mapota on 2012-07-01
I was having issues with MythTV and video Blanking for short periods.
 
Jean-Yves Avenard suggested reverting back to a 270.* nVidia driver and I am have trouble getting them to install.
 
I have tried following a few suggestions I found via google but having no joy.
 
Firstly I am running Mythbuntu 12.04 LTS. Current Kernel is 3.2.0-26-Generic
 
When at a tty session with X stopped via sudo service lightdm stop.
 
I then run 
 
sudo sh ./NVIDIA-Linux-x86_64-270.41.19.run
 
I get an error to do with kernel sources I believe so tried the following
 
sudo sh ./NVIDIA-Linux-x86_64-270.41.19.run --kernel-source-path=/usr/src/linux-headers-3.2.0-26-Generic/
 
But still getting the same error. The following is the detail from the nvidia-installer.log
 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Jul 1 09:36:45 2012
installer version: 270.41.19
 
PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
 
option status:
license pre-accepted : false
update : false
force update : false
expert : false
uninstall : false
driver info : false
precompiled interfaces : true
no ncurses color : false
query latest version : false
no questions : false
silent : false
no recursion : false
no backup : false
kernel module only : false
sanity : false
add this kernel : false
no runlevel check : false
no network : false
no ABI note : false
no RPMs : false
no kernel module : false
force SELinux : default
no X server check : false
no cc version check : false
run distro scripts : true
no nouveau check : false
run nvidia-xconfig : false
sigwinch work around : true
force tls : (not specified)
force compat32 tls : (not specified)
X install prefix : (not specified)
X library install path : (not specified)
X module install path : (not specified)
OpenGL install prefix : (not specified)
OpenGL install libdir : (not specified)
compat32 install chroot : (not specified)
compat32 install prefix : (not specified)
compat32 install libdir : (not specified)
utility install prefix : (not specified)
utility install libdir : (not specified)
installer prefix : (not specified)
doc install prefix : (not specified)
kernel name : (not specified)
kernel include path : (not specified)
kernel source path :
/usr/src/linux-headers-3.2.0-26-generic/
kernel output path : (not specified)
kernel install path : (not specified)
precompiled kernel interfaces path : (not specified)
precompiled kernel interfaces url : (not specified)
proc mount point : /proc
ui : (not specified)
tmpdir : /tmp
ftp mirror : [[COLOR=#22229c]ftp://download.nvidia.com[/COLOR]]("ftp://download.nvidia.com/")
RPM file list : (not specified)
selinux chcon type : (not specified)
 
Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 270.41.19.
-> Running distribution scripts
executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed! Continue installation 
anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-3.2.0-26-generic/' as
specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-3.2.0-26-generic/'
-> Kernel output path: '/usr/src/linux-headers-3.2.0-26-generic/'
ERROR: If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.
 
If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.
 
Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find suggestions
on fixing installation problems in the README available on the Linux
driver download page at [[COLOR=#22229c]www.nvidia.com[/COLOR]]("http://www.nvidia.com/").
 
 
My view on this is that it is telling me I do not have the kernel headers installed, but when I try 
 
**sudo apt-get install linux-headers-$(uname -r)**
 
 
 I get
 
[COLOR=#1f497d][FONT=Calibri]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]Building dependency tree [/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]Reading state information... Done[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]linux-headers-3.2.0-26-generic is already the newest version.[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]The following packages were automatically installed and are no longer required:[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]libreoffice-help-en-gb thunderbird-locale-en-gb thunderbird-locale-en-us[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]mythes-en-au mythes-en-us hyphen-en-us firefox-locale-en[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]libreoffice-l10n-en-gb thunderbird-locale-en openoffice.org-hyphenation[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]libreoffice-l10n-en-za[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]Use 'apt-get autoremove' to remove them.[/FONT][/COLOR]
[COLOR=#1f497d][FONT=Calibri]0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.[/FONT][/COLOR]
 
I can only assume it means I have the headers!!
 
Thanks for any help you can give
 
Andrew

---

### Post by diskmaster23 on 2012-12-23
Did you ever get this resolved? I am having the same problem.

---

### Post by mapota on 2012-12-24
Sorry no, I never really got to the bottom of this issue, it just went away. So can only assume an update to either ubuntu or mythtv solved my issues.

---

### Post by nickrout on 2012-12-24
Why use the nvidia download? Ubuntu package the nvidia drivers.

---

### Post by diskmaster23 on 2012-12-24
> **nickrout said:**
> Why use the nvidia download? Ubuntu package the nvidia drivers.

Because I want to use 290.10 driver version. I, like others, have been having issues with the display freezing and xorg freezing. 

See [here]("http://ubuntuforums.org/showthread.php?t=2097056") for my post on my issue. I give a good synopsis of the problem and possible solutions tried. I am trying to put 290.10 driver on and seeing if that solves the problem. 

So....could you provide me deb version of 290.10 and earlier drivers that will allow me to compile the nvidia module in a 2.6+ kernel version, that would be great.

---

### Post by nickrout on 2012-12-24
So you are presently on 304.51 and want to go to 290.xx? Trouble is 290 doesn't seem to have been packaged at all for ubuntu. [http://packages.ubuntu.com/search?keywords=nvidia-current&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=nvidia-current&searchon=names&suite=all&section=all)

---

### Post by diskmaster23 on 2012-12-24
> **nickrout said:**
> So you are presently on 304.51 and want to go to 290.xx? Trouble is 290 doesn't seem to have been packaged at all for ubuntu. [http://packages.ubuntu.com/search?keywords=nvidia-current&searchon=namesrsrs](http://packages.ubuntu.com/search?keywords=nvidia-current&searchon=namesrsrs) &suite=all&section=all.

What about this? [https://launchpad.net/ubuntu/precise/i386/nvidia-current/290.10-0ubuntu1](https://launchpad.net/ubuntu/precise/i386/nvidia-current/290.10-0ubuntu1)

But, the problem is what exactly the original Submitter submitted, how do you compile the module into a newer kernel. Either the nvidia bin file or the deb file compiles. It just errors out.

---

### Post by nickrout on 2012-12-24
> **diskmaster23 said:**
> What about this? [https://launchpad.net/ubuntu/precise/i386/nvidia-current/290.10-0ubuntu1](https://launchpad.net/ubuntu/precise/i386/nvidia-current/290.10-0ubuntu1)

But, the problem is what exactly the original Submitter submitted, how do you compile the module into a newer kernel. Either the nvidia bin file or the deb file compiles. It just errors out.that is for precise but in your other thread you said you were on quantal. also are you on 32 or 64 bit? that is a 32 bit package.

---

### Post by diskmaster23 on 2012-12-24
i386

It shouldn't matter what version of Ubuntu it was made for. As long as the dependencies are satisfied (right?) then it should not be a problem. Folks take yum packages and alien them to Debian packages all the time. But as the Submitter mentioned, it doesn't compile the module and it errors out.

The issue here is how to fix the module compile issue. I've tried the [solution here]("http://forums.opensuse.org/english/get-technical-help-here/tumbleweed/473658-kernel-3-3-nvidia-driver-fix-2.html#post2450534") or versions of this solution, but it still isn't working.

I am hoping someone more knowledgeable than me can point me and the Submitter in the right direction.

---

### Post by nickrout on 2012-12-24
how about you post the output of your install command?

---

### Post by diskmaster23 on 2012-12-26
I decided to fall back to the 173 driver series. Installing that didn't have any issues.

---

