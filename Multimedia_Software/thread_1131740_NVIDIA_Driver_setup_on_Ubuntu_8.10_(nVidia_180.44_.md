---
title: "NVIDIA Driver setup on Ubuntu 8.10 (nVidia 180.44 run vs synaptic)"
date: 2009-04-21
forum: Multimedia Software
---

### Post by muscule_boy on 2009-04-21
**NVIDIA DRIVER setup for a GeForce 6800GS video card**

I had many problems trying to get my GeForce 6800GS video card drivers installed and xorg.conf file configured correctly.... so decided to post some hints and tricks I used to get things working.

1.  I had problems using the ubuntu respository to install the version 180.11 so suggest that the following packages be removed if you want to install the [www.nvidia.com](www.nvidia.com) NVIDIA-Linux-x86-180.44-pkg1.run file (or the latest version from nvidia. The problems I had may be because I installed the nvidia site run file first and then tried to convert to using the ubuntu repository).

HERE IS WHAT YOU DON'T NEED SO REMOVE THEM:

  apt-get remove "nvidia-glx-*"
  apt-get remove "nvidia-settings"
  apt-get remove "nvidia-xconfig"
  apt-get remove "nvidia-*-kernel-source"
  apt-get remove "nvidia-kernel-common"

HERE IS WHAT YOU DO NEED:

  apt-get install "nvidia-common"
  apt-get install "nvidia-180-modaliases"
  apt-get install "nvidia-71-modaliases"
  apt-get install "nvidia-173-modaliases"
  apt-get install "nvidia-177-modaliases"
  apt-get install "nvidia-96-modaliases"
  apt-get install "xserver-xorg-video-nv"
AND PERHAPS YOU ALSO NEED:
  apt-get install "jockey-common"
  apt-get install "jockey-gtk"
  apt-get install "smartdimmer"

As for the xorg.conf file.. you don't need much because everything is handled for you.  The NVIDIA run installer actually will update and modify your existing xorg.conf file to work correctly.


Here is mine:

== xorg.conf ==
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "HWP"
    ModelName      "HP P1110"
    DisplaySize     400    300
    HorizSync       29.0 - 121.0
    VertRefresh     50.0 - 180.0
    Option         "DPMS"
    Option         "MinClock" "10.0"
    Option         "MaxClock" "300.0" # < 300 MHz
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "nVidia Corporation [NVIDIA]"
    BoardName      "G73 [GeForce 7600 GS] (rev a2)"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
    EndSubSection
EndSection
====

NOW THE IMPORTANT PART.. WHAT YOU NEED TO SUCCESSFULLY RUN THE NVIDIA run:

You must have the following installed, check with synaptic package mgr:
   
    Software Element         Min Requirement          Check With...
    ---------------------    ---------------------    ---------------------
    Linux kernel             2.4.7                    `cat /proc/version`
    XFree86/X.Org            4.0.1/6.7                `XFree86
                                                      -version/Xorg
                                                      -version`
    Kernel modutils          2.1.121                  `insmod --version`


If you need to build the NVIDIA kernel module (Need for Ubuntu 8.10):

    Software Element         Min Requirement          Check With...
    ---------------------    ---------------------    ---------------------
    binutils                 2.9.5                    `size --version`
    GNU make                 3.77                     `make --version`
    gcc                      2.91.66                  `gcc --version`
    glibc                    2.0                      `ls /lib/libc.so.*` > 6


NOW GO TO "www.nvidia.com" and get the Linux driver for your box:

I got the file:
  NVIDIA-Linux-x86-180.44-pkg1.run 

Now I ran this file by starting up my Ubuntu in single user mode without the X server running.  I think it was level 1 (level 3 is not needed and level 5 is using X).  I am not sure how Ubuntu keeps track of the levels but things worked for me (you may need to know Ctrl-Alt-F1 to show your display when in single user mode).

Now you must login as root or use "sudo -i" first (or add sudo infront of the following command):

  sh NVIDIA-Linux-x86-180.44-pkg1.run

Make sure that you build the NVIDIA kernel module if asked.  I could not download a version since my Internet connection is not active and I always feel that building it with your kernel is the best anywayz.

Now reboot.  If you do not get the NVIDIA logo screen before you get into Ubuntu then things probably did not work.  I had to hit enter to see the failure message indicating that X server could not be started.

If it did not work the first time.. your NVIDIA kernel module was probably not built correctly...  reboot to single user mode and reinstall.  I had to reinstall a second time for things to work for me because I had to uninstall the conflicting synaptic package manager nvidia packages as explained above.

So I hope this helps someone.. this may not work for everyone but I think the important thing is that this explains what packages don't work with the NVIDIA installer.

Good luck.  If you have other suggestions or solutions you found for your special case.. please add them to this thread so they can help others... thanks.
:popcorn:

---

