---
title: "Help with enabling 3d on dell latitude cpx"
date: 2006-03-14
forum: Multimedia &amp; Video
---

### Post by carny on 2006-03-14
Gday, I recently installed Ubuntu 5.10 and its bloody awesome so far, however it does not seem to recognize my graphics card as being capable of 3d acceleration (dri). I have googled and researched and found out how to enable it.. however when i am trying to install the driver, it comes up with the following error message: 

/home/carny/Desktop/mach64-20060311-linux.i386/drm/linux-core/Makefile:289: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/carny/Desktop/mach64-20060311-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'

Also in my xorg.conf file.. it says that it loads dri and all the opengl crap.. but it just does not work. I think the ati driver that i am trying to install is already installed but just not configured properly and i have no clue of howto get it working.. here is are some extracts from my xorg.conf file:

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility P/M (AGP)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "DRI"
        Mode    0666
EndSection

So i dont know what is wrong and i would appreciate greatly any advice on how i can go about getting dri working and opengl working. Do i need to recompile my kernel?? reconfigure my xorg.conf file?? Here is my system config if its any help:
Dell latitude cpx:
p3500
8mb ati mobility m1 (uses mach64 chipset.. is definetly 3d capable)
6gb hdd
ubuntu 5.10

Thankyou,
carny

---

### Post by grumpymole on 2006-04-06
carny,

I have the same laptop and have got it working.

1. Download the latest common* and mach64* files from [http://dri.freedesktop.org/snapshots](http://dri.freedesktop.org/snapshots).
2. Make sure that you have installed build-essential.
3. Make sure that you have the appropriate kernel headers installed. ```
sudo apt-get install linux-headers-`uname -r`
```
4. unpack common* and mach64*.
5. Change to common* directory and ```
sudo ./install.sh
```  I just selected enter for everything.
6. Change to mach64* directory and repeat the command in (5).  this takes longer because of the compilation stage.
7. if all ends well, then ctrl-alt-backspace to restart X.
8. check that it is working by

    a.  ```
glxinfo | grep direct
``` and you should see something like 'direct rendering: yes'.  If it refers to 'Indirect rendering' then it is not accelerated.

    b.  ```
glxgears -printfps
``` should show smooth gears spinning and prints out your frames per second rate.  Apparently not a scientific measure though.

Hope this helps.

Regards

Warren

---

### Post by ajack on 2006-04-11
I have downloaded that latest snapshots from dri.freedesktop.org (snapshot 0403) of the mach64 sources and successfully compiled and installed it.  However, I seem to experience a lot of flickering and tearing to the 3d accellerator.  Any solution for this?

I am at 1024x768 at 63hz running dapper testing build.

Appreciate any help to this annoying problem.

](*,)

---

