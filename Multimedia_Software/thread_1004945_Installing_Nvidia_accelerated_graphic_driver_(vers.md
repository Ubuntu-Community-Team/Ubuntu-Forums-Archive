---
title: "Installing Nvidia accelerated graphic driver (version 173)"
date: 2008-12-07
forum: Multimedia Software
---

### Post by Pablo W on 2008-12-07
Hi. I'm a newbie in Linux and illiterate in computers. I've just changed my old  graphic card for a DVI one. The hardware manager (sorry if this is not the right name in English) opened automatically as soon as I started the PC and it suggested me to install Nvidia accelerated graphic driver (version 173). After I accept, I get an error message which reads "SystemError: E:Unable to correct problems, you have held broken packages." and the screen looks funny, as if configured for a different screen.

Could anybody help?
Thanks!

Maybe the following details can help you know what I'm dealing with:

pablo@Tjena:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV34 [GeForce FX 5200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5

H/W path            Device      Class          Description
==========================================================
                                system         To Be Filled By O.E.M.
/0                              bus            A8V Deluxe
/0/0                            memory         64KiB BIOS
/0/4                            processor      AMD Athlon(tm) 64 Processor 3000+
/0/4/5                          memory         128KiB L1 cache
/0/4/6                          memory         512KiB L2 cache
/0/3c                           memory         1009MiB System Memory
/0/3c/0                         memory         256MiB DIMM DDR Synchronous 333 M
/0/3c/1                         memory         256MiB DIMM DDR Synchronous 333 M
/0/100                          bridge         K8T800Pro Host Bridge
/0/100/1                        bridge         VT8237 PCI bridge [K8T800/K8T890 
/0/100/1/0                      display        NV34 [GeForce FX 5200]
/0/100/7                        bus            VT6306 Fire II IEEE 1394 OHCI Lin
/0/100/8                        storage        PDC20378 (FastTrak 378/SATA 378)
/0/100/a            eth0        network        88E8001 Gigabit Ethernet Controll
/0/100/f            scsi3       storage        VIA VT6420 SATA RAID Controller
/0/100/f/0.0.0      /dev/sda    disk           82GB HDS722580VLSA80
/0/100/f/0.0.0/1    /dev/sda1   volume         73GiB EXT3 volume
/0/100/f/0.0.0/2    /dev/sda2   volume         2949MiB Extended partition
/0/100/f/0.0.0/2/5  /dev/sda5   volume         2949MiB Linux swap / Solaris part
/0/100/f.1          scsi5       storage        VT82C586A/B/VT82C686/A/B/VT823x/A
/0/100/f.1/0.0.0    /dev/cdrom  disk           DVD-RW  DVR-109
/0/100/10                       bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                     bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                     bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                     bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.4                     bus            USB 2.0
/0/100/11                       bridge         VT8237 ISA bridge [KT600/K8T800/K
/0/100/11.5                     multimedia     VT8233/A/8235/8237 AC97 Audio Con
/0/100/11.6                     communication  AC'97 Modem Controller
/0/101                          bridge         K8T800Pro Host Bridge
/0/102                          bridge         K8T800Pro Host Bridge
/0/103                          bridge         K8T800Pro Host Bridge
/0/104                          bridge         K8T800Pro Host Bridge
/0/105                          bridge         K8T800Pro Host Bridge
/0/106                          bridge         K8 [Athlon64/Opteron] HyperTransp
/0/107                          bridge         K8 [Athlon64/Opteron] Address Map
/0/108                          bridge         K8 [Athlon64/Opteron] DRAM Contro
/0/109                          bridge         K8 [Athlon64/Opteron] Miscellaneo
/0/1                scsi8       storage        
/0/1/0.0.0          /dev/sdb    disk           250GB 2500BEV External
/0/1/0.0.0/1        /dev/sdb1   volume         232GiB Windows FAT volume
/1                  pan0        network        Ethernet interface

---

### Post by DieB on 2008-12-07
please start synaptic for fixing broken packages (as the message mentions there are some).

---

### Post by Pablo W on 2008-12-08
> **DieB said:**
> please start synaptic for fixing broken packages (as the message mentions there are some).

Thanks DieB. I'm afraid that has not solved the problem. I went to Synaptic (edit, repair broken packages) and then went back to the hardware manager. I keep getting the same error message there (SystemError: E:Unable to correct problems, you have held broken packages.) Any other suggestion?

---

### Post by chongzi889 on 2008-12-08
Another type of bonnet construction in a **[gate valve](http://www.valvesupplier.net/index.htm)** is pressure seal bonnet. This construction is adopted for valves for high pressure service, typically in excess of 15 MPa (2250 psi). The unique feature about the pressure seal bonnet is that the body - bonnet joints seals improves as the internal pressure in the [gate valve]("http://www.valvesupplier.net/index.htm") increases, compared to other constructions where the increase in internal pressure tends to create leaks in the body-bonnet joint.

---

### Post by Pablo W on 2008-12-08
I wonder if this background info can help.

It seems I'm having problems with the updates manager. When I open it, all I see is two updates under Important Security updates. Those are:
linux-generic. Complete Generic Linux kernel and
linux-restricted-modules-generic. Restricted Linux modules for generic kernels

Both are greyish (I cannot tick them for updating)

At the same time, in Synaptic, I see I have a package called nvidia-glx-173 which supports my graphic card and is not installed. WHen I try to install it, I get an error message (nvidia-glx-173:
 depends: nvidia-173-kernel-source but will not be installed
 Recommends: nvidia-settings  but it is not installable) 

All in all, I still cannot install the driver for my NVIDIA graphic card and I'm completely lost.

Any expert there?

---

### Post by DieB on 2008-12-08
sure u fixed the broken packages?
are u using 8.10 or 8.04?

found [here]("http://ubuntuforums.org/showthread.php?t=766683") that:
> 
Note: You may have to perform "sudo apt-get update" twice after recovering from any of the errors below.

COMMON ERRORS

If you had errors while trying to do the above, one of these following commands may help. Did the terminal tell you to run "dpkg --configure -a"? All you have to do is add "sudo" to the front of that command, like so:

sudo dpkg --configure -a

or if it was the install -f command:

sudo apt-get install -f

Then make sure your system is up to date:

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

NON-EXISTANT PACKAGES

Do you keep getting messages that certain packages don't exist and can't be installed? First of all, make sure you have enabled the Medibuntu, Universe and Multiverse repositories. If you're certain that you have the necessary repositories enabled, then you may have a currupt apt list due to an interrupted "apt-get update", which would then make the package manager think certain packages don't exist on the server. Execute both of these commands in the terminal:

sudo rm /var/lib/apt/lists/partial/*

sudo apt-get update

NEWLINE ERROR/PACKAGE ERROR

An error which can prevent ANY system update/upgrade or package installation is the troublesome "final newline error", but there are also other errors and curruptions which can prevent upgrades and installations. If you notice the same package or application being mentioned when you're trying to upgrade or install something completely unrelated to it, take a note of which package the error is referring to, copy and paste the command below into the terminal, replace the "filename*" example with the name of the package that's giving you grief, then execute the edited command to remove the currupt file(s):

sudo rm /var/lib/dpkg/info/filename*

sudo apt-get update

This doesn't mean the package has been removed, just the pre/post-install scripts, md5sums, and file lists related to it. You should reinstall the package - even if you plan to remove it, as those deleted and currupted files related to it will be replaced with non-currupted ones.


hope this will help with broken packages

---

### Post by Pablo W on 2008-12-08
> **DieB said:**
> sure u fixed the broken packages?
are u using 8.10 or 8.04?

found [here]("http://ubuntuforums.org/showthread.php?t=766683") that:


hope this will help with broken packages

Thanks again, DieB.

No, I'm not sure I fixed the broken packages. I don't know how to make sure that has happened. When I try to do it (post #3) I get no confirmation as to the result. 

I'm running 8.1

As for the common errors you quoted, when I run sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade, the first one runs fine, but for the second and third one I get a message which reads as follows (sorry if any of the words is not correct in English):

The following packages have been kept:
  linux-generic linux-restricted-modules-generic
0 updated, 0 will be installed, 0 to be deleted y 2 not updated.

I guess the not updated ones are the ones mentioned in post #4 (linux-generic && linux-restricted-modules-generic).

Any further ideas?

---

### Post by element_G on 2008-12-08
The best, no hassle way to install NVIDIA's drivers is to do it yourself (without the hardware-manager)

get them from their site: [http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html) (32 bit) OR [http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html) (64 bit) 
you will most likely need the 32 bit

then follow the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia](http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia)

this method has not failed for me since ubuntu 7.04 

as far as worrying about those broken packages, the above link should take care of those.

---

### Post by Pablo W on 2008-12-08
> **element_G said:**
> The best, no hassle way to install NVIDIA's drivers is to do it yourself (without the hardware-manager)

get them from their site: [http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html) (32 bit) OR [http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html) (64 bit) 
you will most likely need the 32 bit

then follow the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia](http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia)

this method has not failed for me since ubuntu 7.04 

as far as worrying about those broken packages, the above link should take care of those.

Thanks element_G. I tried your suggestion and here is the result:
I downloaded the drivers from their site and started with the step by step instructions (I realised I have to replace the name of the driver with the one I have downloaded). When I reach step 4 in Terminal, I get the following (sorry if these are not the exact words in English):
The following packages will be DELETED:
  linux-generic linux-restricted-modules-2.6.27-7-generic
  linux-restricted-modules-common linux-restricted-modules-generic
  nvidia-173-modaliases nvidia-177-modaliases nvidia-71-modaliases
  nvidia-96-modaliases nvidia-common
0 updated, 0 will be installed, 9 yo be deleted y 0 not updated.
2814kB will be released after unpacking.
¿Do you want to continue [Y/n]? 

When I answer Y, I get an Aborted message.

This is getting really complicated :confused:

---

### Post by DieB on 2008-12-08
pls check out if there are any more broken apps. start synaptic look to the bottom left there should be a button named filters or close here u will then find a filter that shows only broken packages.

for repair [this]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages") might be helpfull.

pls tell what is the status now.

---

### Post by Pablo W on 2008-12-08
> **DieB said:**
> pls check out if there are any more broken apps. start synaptic look to the bottom left there should be a button named filters or close here u will then find a filter that shows only broken packages.

for repair [this]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages") might be helpfull.

pls tell what is the status now.

Thanks, DieB. I didn't know Synaptic has that feature. I applied the broken packages filter as you suggested. Synaptic sees no broken packages.

The status keeps the same: I cannot install the NVIDIA accelerated graphic driver. The hardware manager keeps telling me the following:"SystemError: E:Unable to correct problems, you have held broken packages."

---

### Post by DieB on 2008-12-08
tried that as mentioned a bit later in above link?

---

### Post by element_G on 2008-12-08
> **Pablo W said:**
> Thanks element_G. I tried your suggestion and here is the result:
I downloaded the drivers from their site and started with the step by step instructions (I realised I have to replace the name of the driver with the one I have downloaded). When I reach step 4 in Terminal, I get the following (sorry if these are not the exact words in English):
The following packages will be DELETED:
linux-generic linux-restricted-modules-2.6.27-7-generic
linux-restricted-modules-common linux-restricted-modules-generic
nvidia-173-modaliases nvidia-177-modaliases nvidia-71-modaliases
nvidia-96-modaliases nvidia-common
0 updated, 0 will be installed, 9 yo be deleted y 0 not updated.
2814kB will be released after unpacking.
¿Do you want to continue [Y/n]? 
 
When I answer Y, I get an Aborted message.
 
This is getting really complicated :confused:
 
you might try running
 
```
sudo apt-get remove -f nvidia* linux-restricted-modules*
```
 
the ' -f ' flag should force the removal of those packages. As far as fixing broken packages goes, I am not sure how to fix these (Synaptic has been good for me).

---

### Post by Pablo W on 2008-12-08
Thanks, DieB. I tried your suggestion, but unfortunately, Synaptic does not find any broken package. That is, if I open Synaptic and go to Edit > Fix Broken Packages from the menu, nothing happens. So I can't choose Apply Marked Changes from the Edit menu. That is exactly my problem. The hardware manager says I have broken packages (as a reason not to install the driver of my graphic card) and Synaptic does not find any such broken packages.

---

### Post by Pablo W on 2008-12-08
> **element_G said:**
> you might try running
 
```
sudo apt-get remove -f nvidia* linux-restricted-modules*
```
 
the ' -f ' flag should force the removal of those packages. As far as fixing broken packages goes, I am not sure how to fix these (Synaptic has been good for me).

Thanks element_G. I have applied your suggestion and 9 packages have been removed. What should I do next?

---

### Post by DieB on 2008-12-08
restart and then reload packet-information in synaptic - close it and try hardwareanddrivers again. it should therefor work than.

---

### Post by element_G on 2008-12-08
Instead of the  hardware-manager method, you could try the method I posted earlier ([http://ubuntuforums.org/showpost.php?p=6330659&postcount=7](http://ubuntuforums.org/showpost.php?p=6330659&postcount=7))
 
either method should work , I have never used the hardware-manager method

---

### Post by Pablo W on 2008-12-08
> **DieB said:**
> restart and then reload packet-information in synaptic - close it and try hardwareanddrivers again. it should therefor work than.

Thanks again DieB. I'm not sure if I understood your instructions this time. I have restarted and reloaded  package information in synaptic. I notice that I have a suggested package that was not there before. It is called nvidia-common. If I choose it to be installed I get an error message which, in English, would be something along these lines: "nvidia-common: The package nvidia-common does not have an available version, but it exists in the database. This usually means that the package was mentioned but was never uploaded, it has been declared obsolete or it is not available in the sources.list contents". So, I'm still stuck.

Did I do what you suggested? If not, could you please clarify? Thanks again.

---

### Post by DieB on 2008-12-08
this should fix: put in a terminal 

sudo rm /var/lib/apt/lists/partial/nvidia-*

sudo apt-get update

and then hardware&drivers

---

### Post by Pablo W on 2008-12-08
> **DieB said:**
> this should fix: put in a terminal 

sudo rm /var/lib/apt/lists/partial/nvidia-*

sudo apt-get update

and then hardware&drivers

Sorry, DieB. I know it is my fault, but I really do not understand what you mean. I'm a full newbie. I follow your first and second steps (sudo rm /var/lib/apt/lists/partial/nvidia-* and sudo apt-get update) without any problem. When it comes to the third ("and then hardware&drivers") I don't understand what should I suppose to do. I'm sorry; this is probably extremely easy for you, but I really don't get what you mean.

---

### Post by DieB on 2008-12-08
i'm sorry for writing not understandale, hm the last point should have ment: 
Now start your hardware and drivers application, it is in system-administration and let that one do the work again.

I'm sorry once again.

---

### Post by Pablo W on 2008-12-08
> **DieB said:**
> i'm sorry for writing not understandale, hm the last point should have ment: 
Now start your hardware and drivers application, it is in system-administration and let that one do the work again.

I'm sorry once again.

Oh, now I understand! No need to apologise, on the contrary.
It's funny what happens now. Instead of suggesting me to install the Nvidia accelerated graphic driver (version 173), the hardware manager is just blank now and in the title bar it reads something like "You do not have restricted drivers in your system":confused:

---

### Post by Pablo W on 2008-12-08
> **element_G said:**
> Instead of the  hardware-manager method, you could try the method I posted earlier ([http://ubuntuforums.org/showpost.php?p=6330659&postcount=7](http://ubuntuforums.org/showpost.php?p=6330659&postcount=7))
 
either method should work , I have never used the hardware-manager method

Thanks again, element_G. Since the hardware manager is giving me a headache (post# 21) I also took a full Ubuntu plunge and tried again your previous suggestions. The outcome now was that when I reach step 5 (sudo apt-get remove nvidia* linux-restricted-modules*
     sudo apt-get install linux-headers-$(uname -r) \
       build-essential pkg-config xorg-dev
     sudo sh ~/NVIDIA-Linux-x86-173.14.12-pkg1.run) I get an error message which read "the package built-essential cannot be found".

---

### Post by Pablo W on 2008-12-09
Hi again,
A brief update on the situation:

When I start the pc I briefly see a lines stating Nvidia GeForce FX 5200. The driver does not seem to be installed, though, since I'm having the following problems (none of them occurred before I change my old video card for this digital Nvidia):

i-I cannot set the screen resolution (should be 1680 x 1050 and the maximum I get in the drop down menu is 1024 x 768)
ii-I cannot turn desktop visual effects to normal or extra.


So, as far as I understand from what you kindly explained to me, I should:

A: either install the driver from the hardware manager or 
B: do it manually.

Option A cannot be followed, since when I go to the hardware manager there is a sign reading "you are not using restrictive drivers". That is, it does not even list the drivers as it did yesterday. 

Option B: Having dismissed option A, I tried to do it myself following the [step by step]("http://ubuntuforums.org/showthread.php?t=514161&highlight=install+nvidia") kindly provided in post # 7 by element_G. I reach step 4 (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.justin). When I try step 4, nothing happens. By the way, this step by step is quite complicated to me, since not only I'm a full newbie and illiterate in computers but also I don't know how to switch between the panel with the instructions described as step 2 and the panel where I should type the commands, so I end up restarting every time a new command must be written and typing it character by character maximising the chances that I do something wrong. Anyway, I got stuck at step 4 so I got nowhere this way so far.

Option B2: I have also tried to follow the instructions given in the Nvidia site. After download of the driver, when I type sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run, I get an error message reading "ERROR: You appear to be running an X server; please exit X before installing". So I get nowhere here either.

Anybody can help me please? :confused::confused:

It seems I'm having an awful start with Ubuntu. This is very frustrating :mad:

---

### Post by element_G on 2008-12-09
I will try to condense things from that tutorial in this post:

**1. **save this: [NVIDIA-Linux-x86-173.14.12.pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run") in your home directory (this is the installer script) just to be simple

**2. **now exit GNOME with Ctrl+Alt+F1. this will give you a console login, so login and then shut down GNOME with ```
sudo /etc/init.d/gdm stop
```**3. **Run the following commands seperately
```

sudo apt-get remove nvidia* linux-restricted-modules*
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install build-essential pkg-config xorg-dev
sudo sh ~/NVIDIA-Linux-x86-173.14.12-pkg1.run
```**4. **Say yes (or accept) to everything in the installer, after that, you should be OK.
Restart GNOME with ```
sudo /etc/init.d/gdm start
``` and you should see the NVIDIA logo flash on the screen. 

**5.** If you did then the driver is installed. You can now login to GNOME and if your screen resolution is messed up use the nvidia-settings program to fix it. You can do this by pressing Alt+F2 to get the run command window, then type ```
gksudo nvidia-settings
``` in the command box, hit enter and put in your password next.

If things are not working at step 4. I can give you some more hints to finish the instructions from the tutorial thread.

---

### Post by Pablo W on 2008-12-10
Thanks, element_G for a very helpful post.

I have followed your step-by-step. When in step 3 I run "sudo apt-get install build-essential pkg-config xorg-dev" I get a message reading "package xorg-dev could not be found". 

Any clue as to what to do now?

---

### Post by element_G on 2008-12-10
skip the xorg-dev package, I'm not entirely sure it's needed.(instead run ' sudo apt-get install build-essential pkg-config ')

---

### Post by Pablo W on 2008-12-10
Thanks, element_G. I followed your instructions step-by-step from the beginning, running "sudo apt-get install build-essential pkg-config" instead of "sudo apt-get install build-essential pkg-config xorg-dev"

The result is:

I get the Licence Agreement; after accepting it I get a message reading "No precompiled kernel interface was found to match your kernel. Would you like the installer to attempt to download a kernel interface for your kernel?"

I answered Yes, and after a while I get another message reading "No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel" An then "ERROR: Unable to build the NVIDIA kernel module. Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details"

Do you know what all this is about? :confused:

---

### Post by element_G on 2008-12-10
That's strange. This is what the packages build-essential and pkg-config are needed for, and since you have them installed, it should be able to build your kernel module. 

could you post the output of 
```
cat /var/log/nvidia-installer.log
```

---

### Post by Pablo W on 2008-12-10
Sure. Here it comes (please tell me if the Spanish sentences cause you trouble; and thanks!)

pablo@Tjena:~$ cat /var/log/nvidia-installer.log
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Dec 10 21:04:58 2008
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
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-7-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-7-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-7-generi
   c/build SYSOUT=/lib/modules/2.6.27-7-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=
   /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz8722/NVIDIA-Linux-x86-173.14.1
   2-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -i
   nclude include/linux/autocon
   f.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-
   strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -
   msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -ma
   rch=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchro
   nous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/
   mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibl
   ing-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz8
   722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"173.14.12\" -UDEBUG -U_DEBUG -DNDEBUG -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MOD
   NAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pk
   g1/usr/src/nv/.tmp_nv.o /tmp/selfgz8
   722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm/bitops.h: En la función ‘set_bit’:
   include/asm/bitops.h:60: aviso: se usó un puntero de tipo ‘void *’ en l
   a aritmética
   include/asm/bitops.h: En la función ‘clear_bit’:
   include/asm/bitops.h:97: aviso: se usó un puntero de tipo ‘void *’ en l
   a aritmética
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: En la función ‘prefetch_range’:
   include/linux/prefetch.h:57: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: En la función ‘object_is_on_stack’:
   include/linux/sched.h:1969: aviso: se usó un puntero de tipo ‘void *’ e
   n la aritmética
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: En la función ‘sg_virt’:
   include/linux/scatterlist.h:199: aviso: se usó un puntero de tipo ‘void *
   ’ en la aritmética
   En el archivo incluído de /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/u
   sr/src/nv/nv.c:14:
   /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:107:27
   : error: asm/semaphore.h: No existe el fichero ó directorio
   In file included from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv-linux.h:109,
                    from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: En la función ‘zero_user_segments’:
   include/linux/highmem.h:134: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:134: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:134: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:134: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:137: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:137: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:137: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   include/linux/highmem.h:137: aviso: se usó un puntero de tipo ‘void *’ 
   en la aritmética
   In file included from /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h: En la
   función ‘nv_execute_on_all_cpus’:
   /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:674: e
   rror: demasiados argumentos para la función ‘on_each_cpu’
   /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c: En la funci
   ón ‘nv_kern_cpu_callback’:
   /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1299: error:
   demasiados argumentos para la función ‘smp_call_function’
   /tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1306: error:
   demasiados argumentos para la función ‘smp_call_function’
   make[3]: *** [/tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz8722/NVIDIA-Linux-x86-173.14.12-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by element_G on 2008-12-10
I know this is a redundant question, but you have installed your linux headers, right?
[FONT=monospace]
sudo apt-get install linux-headers-$(uname -r)
[/FONT]
This is the only thing I can gather from that log file, it is missing some header files; this is starting to go over my head :mad:

---

### Post by Pablo W on 2008-12-10
element_G: Please do not hesitate to pose redundant questions, because since I'm a newbie I might be making a basic mistake without realising it.

Yes, I did  run "sudo apt-get install linux-headers-$(uname -r)" and the outcome of that would be in English something like:

Reading packages list... Done
Creating tree       
Reading status information... Done
linux-headers-2.6.27-7-generic is already in its most recent version.
The following packages have been installed automatically and are no longer necessary.
  binutils-static
Use «apt-get autoremove» to delete them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Does this help in any way?

---

### Post by element_G on 2008-12-10
can you post the output of ```
uname -a
```

---

### Post by Pablo W on 2008-12-10
Here it is:

pablo@Tjena:~$ uname -a
Linux Tjena 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

---

### Post by element_G on 2008-12-10
I am not sure what the problem is at this point, to me it seems your PC should be able to manually build the nvidia driver. At this point I don't know how to continue doing this, but as we have not installed any drivers I think it is safe to try a third way: envy-ng

envy-ng is a program that is similar to jockey (the auto hardware-manager that you first used). It can properly detect your video card and get the appropriate drivers. I don't know what the difference is between the two, just that it is another way and worth a shot.

so, install envy with ```
sudo apt-get install envyng-gtk
``` after that it should be available from the GNOME menu or run sudo envyng-gtk

more info on envy-ng: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Pablo W on 2008-12-10
Thanks, element_G.

When I run "sudo apt-get install envyng-gtk"

I get the following message:

"Some packages could not be installed. This could mean that you asked for an impossible status or, if you are using the unstable version, that some required packages have not been created or have been moved out from Incoming. Since you have only asked for a single operation, it is highly likely that the package is just not installable. You should submit an error report against that package. The following information may help solve the issue:
The following packages have unsolved dependencies:
  envyng-gtk: depends: envyng-core (>= 2.0.1) but will not be installed
E: Packages broken"

And that's the end of the error message I get. Maybe the focus should go back to post #4? I'm just guessing...:confused:

Any suggestion?

EDIT 11-DEC: I've checked again in Synaptic and it keeps telling me that I have no broken packages. Now I remember that it's been a long time since I got the orange "download" arrow in the top right corner of my desktop; that's why I wonder if the problem for not being able to install the driver might be in the download/handling of packages :confused:

---

### Post by Pablo W on 2008-12-13
Since no other suggestions were made, I've no other choice but to reinstall Ubuntu 8.1 :mad:

I'll search in the forums about how you do that, and report here the outcome.

---

### Post by Pablo W on 2008-12-13
Update:

I have reinstalled Ubuntu 8.1 and got a message from the hardware manager which guided me through the installation of the driver. The driver is now installed :p

Now, I have an issue with the card settings. The screen resolution has been automatically set to 1600x1200. The monitor manual suggests a resolution of 1680 x 1050, but that is not among the options given.

So I have followed element_G's suggestion (post 24) and run

gksudo nvidia-settings

There, in the X server display configuration left menu, under Display, I cannot change the resolution either, since it is set in auto and every time I change the values in the resolution text box, it just ignores my values and sticks to 1600 x 1200.

Any idea as to how to set the resolution manually? Thanks!

---

### Post by element_G on 2008-12-14
Glad you've got it working:KS

After you set your resolution from the drop-down box you need to press the ' Save to X Configuration File ' button. You can also switch the resolution right away by pressing Apply.

---

### Post by Pablo W on 2008-12-14
Thanks, element_G
I'm afraid I cannot apply your suggestion. I don't have 1680x1050 as an option in the drop-down box.

I have noticed, though, that  if I click on "advanced" I get an additional box called Panning, where I can manually write 1680x1050, but when I apply it, the screen does not look right.

I have also noticed that in the"DFP-0" left menu, it displays the right name for my monitor (Viewsonic VA2026 W), but the native resolution and the "best fit" resolution are wrong (1600x1200 instead of 1680x1050) and I don't find the way to change it here either :confused:

Any suggestion?

Thanks in advance.

---

### Post by element_G on 2008-12-15
You will have to manually edit your xorg.conf
gksudo gedit /etc/X11/xorg.conf

[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)

> At some point, it will be as easy as adding one of these resolutions as a possible Mode in the Section "Screen" as such:
  Section "Screen"
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"
DefaultDepth 24
SubSection "Display"
    Viewport  0 0
    Depth     24
    [COLOR=Red]Modes     "1680x1050"[/COLOR]
EndSubSection
EndSection


---

### Post by Pablo W on 2008-12-15
Thanks, element_G

I guess I'm doing something  wrong. I have followed your instructions: I opened a Terminal and typed 

gksudo gedit /etc/X11/xorg.conf

I have changed and saved that file so that now looks as follows:

```
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA2026w"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1680x1050 @1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

...but nothing changed! If I type nvidia-settings, I still see the old values (even after restarting). I have tried it a couple of times after posting here. Nvidia settings still says that the native resolution and the "best fit" resolution are 1600x1200 instead of 1680x1050.

If I go to the resolution screen tool, it keeps the list of resolutions as it was, that is, without the possibility to choose 1680x1050.

Any idea about how to solve it?

---

### Post by element_G on 2008-12-17
under meta modes, remove ' nvidia-auto-select +0+0; ' that way the only option available for your screen should be 1680x1050

---

### Post by Pablo W on 2008-12-18
Thanks, element_G

I'm afraid it didn't work. After reinstalling Ubuntu (already for the 2nd time), when I try to modify the file from the nvidia-settings application I get this error message now:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

If I open the files navigator and go to /etc/X11 and open the xorg.conf file, I see this:

```
# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

whereas if I open the same file from the nvidia X server settings I see this:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA2026w"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```
This happens even though I have tried many times and replaced the 1600x1024 with 1680x1050.

Any ideas as to how can I change the resolution and make it work properly?

Thanks in advance.

---

### Post by element_G on 2008-12-21
backup xorg
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 

rewrite it with your new config
gksudo gedit /etc/X11/xorg.conf

delete everything and then paste the following as your xorg.conf
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA2026w"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Pablo W on 2008-12-21
Thanks, element_G. I have applied your instructions to the letter. Nevertheless, I think I'm still not getting it. After restarting, my xorg.conf looks now:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA2026w"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
# Removed Option "metamodes" "1680x1050 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Pablo W on 2008-12-21
Update:
I have noticed that the xorg.conf I copied in the previous post is the xorg.conf available through button "Save to X configuration file" into System > Administration > NVIDIA x server settings. I see a different version of xorg.conf, though, if I type  gksudo gedit /etc/X11/xorg.conf

In this second case, what I get is:
```
Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA2026w"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Nevertheless, 1680x1050 is still not applied. Any idea of what is going on? :confused:
Thanks in advance.

---

### Post by element_G on 2008-12-22
unfortunately, no. Your xorg is set so that it should only have the option of 1680x1050.

I'm not sure where to go from here but try running  ' xvidtune ' in  a terminal. Then click the 'Show' button in the window that pops up. This should print something in the terminal; this is the modeline that xvidtune deems best for the monitor. Can you post this output?

---

### Post by Pablo W on 2008-12-22
Here it is:

pablo@hem:~$ xvidtune
Vendor: Unknown, Model: ViewSonic VA2026w
Num hsync: 1, Num vsync: 1
hsync range 0:  30.00 -  82.00
vsync range 0:  50.00 -  75.00
"1600x1024"   103.12   1600 1600 1656 1664   1024 1024 1029 1030 +hsync +vsync


By the way, I am also checking this long ongoing [thread]("http://ubuntuforums.org/showthread.php?t=993668") in search for useful information.

---

