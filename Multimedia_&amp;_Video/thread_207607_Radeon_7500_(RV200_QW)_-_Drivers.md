---
title: "Radeon 7500 (RV200 QW) - Drivers ?"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by narandill on 2006-07-02
Hi, i'm trying for few days to turn on Direct Rendering on my ATI video card, with no success... 

Anyone have done this ? Or how to increse fps i glxgears ?
I have Radeon 7500 (RV200 QW)
Cel 900
256 ram
kernel 2.6.15-25-386

glxgears:
> 530 frames in 5.6 seconds = 95.041 FPS
397 frames in 5.9 seconds = 66.885 FPS
530 frames in 5.7 seconds = 92.665 FPS
530 frames in 5.0 seconds = 105.268 FPS
663 frames in 5.9 seconds = 112.868 FPS
662 frames in 6.0 seconds = 110.189 FPS 

glxinfo:
> mieszko@mieszko:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No 

xorg.conf:
> Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon 7500 (RV200 QW)"
    Driver        "radeon"
    BusID        "PCI:1:0:0"
EndSection 

As yu can see - i have compiled last CVS radeon drivers, but when adding module to the kernel i have error like this:

> WARNING: Error inserting drm (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting radeon (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by gborzi on 2006-07-02
Hello Narandill, I have the same video card on my laptop (Compaq evo n610c) and it works without problems using the prepackaged radeon driver.
In order to have dri you must enable it in the Module section of xorg.conf, i.e.
> Section "Module"
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
and also you need to install the libgl1-mesa-dri package. My Device section looks like this
> Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mo
bility 9000]"
        Driver  "radeon"
        BusID           "PCI:1:0:0"
        VideoRam        32768
        Option  "Accel"
        Option  "AGPMode"       "4"
        Option  "AGPSize"       "64"
        Option  "BufferSize"    "2"
        Option  "ColorTiling"   "yes"
        Option  "DisplayPriority"       "BIOS"
        Option  "DynamicClocks" "yes"
        Option  "EnableDepthMoves"      "yes"
        Option  "EnablePageFlip"        "yes"
        Option  "RenderAccel"   "yes"
        Option  "RingSize"      "8"
#       Option  "VBERestore"    "true"
EndSection
I took these settings from this thread [http://ubuntuforums.org/showthread.php?t=122094](http://ubuntuforums.org/showthread.php?t=122094) . As for glxgears fps, they are not really relevant, increasing them does not translates in an increased fps for your 3D games.

---

### Post by narandill on 2006-07-02
I arleady have Load "dri" on modules in xorg.conf and libgl1-mesa-dri package...

and:
> glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


I know that the  fglrx drivers don't work with my ati 7500, thats correct?
When i changed the Driver to "fglrx" in xorg.conf - the X crashes at start....

But why "radeon" drivers (CVS) dont work ? maybe this is the answer?
(when compiling CVS radeon drivers, adding module to kernel):

> WARNING: Error inserting drm (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting radeon (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by gborzi on 2006-07-02
I can confirm that fglrx don't work with ATI Radeon 7500. I have not tried it, but I have read that doesn't work so many times. BTW, the default radeon driver works fine for me. Have you tried to uninstall the CVS modules ? Perhaps you can achieve the same effect (of uninstalling) by reinstalling the kernel, i.e.
> sudo apt-get install --reinstall linux-image-2.6.15-25-386
To be sure that the module is loaded do
> sudo modprobe radeon
this should also load the drm module.

---

### Post by narandill on 2006-07-02
After reinstall of kernel....

> mieszko@mieszko:~$ sudo modprobe radeon
Password:
WARNING: Error inserting drm (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/drm.ko): Cannot allocate memory
FATAL: Error inserting radeon (/lib/modules/2.6.15-25-686/kernel/drivers/char/drm/radeon.ko): Unknown symbol in module, or unknown parameter (see dmesg)


> mieszko@mieszko:~$ dmesg
[17179863.940000] radeon: Unknown symbol drm_open
[17179863.940000] radeon: Unknown symbol drm_fasync
[17179863.940000] radeon: Unknown symbol drm_poll
[17179863.940000] radeon: Unknown symbol drm_get_resource_len
[17179863.940000] radeon: Unknown symbol drm_core_get_reg_ofs
[17179863.940000] radeon: Unknown symbol drm_irq_uninstall
[17179863.944000] radeon: Unknown symbol drm_ioctl
[17179863.944000] radeon: Unknown symbol drm_exit
[17179863.944000] radeon: Unknown symbol drm_debug
[17179863.944000] radeon: Unknown symbol drm_core_get_map_ofs
[17179863.944000] radeon: Unknown symbol drm_init
[17179863.948000] radeon: Unknown symbol drm_addmap
[17179863.948000] radeon: Unknown symbol drm_get_resource_start
[17179863.948000] radeon: Unknown symbol drm_vbl_send_signals
[17179863.948000] radeon: Unknown symbol drm_ati_pcigart_init
[17179863.948000] radeon: Unknown symbol drm_mmap
[17179863.948000] radeon: Unknown symbol drm_order
[17179863.948000] radeon: Unknown symbol drm_ati_pcigart_cleanup
[17179863.948000] radeon: Unknown symbol drm_core_reclaim_buffers
[17179863.952000] radeon: Unknown symbol drm_release


any ideas?? :/

---

### Post by gborzi on 2006-07-02
In my previous post i mentioned the linux-image-2.6.15-25-**386** kernel, I should have mentioned the linux-image-2.6.15-25-**686** kernel. Which one you reinstalled ? In case you have installed the 386 kernel, reboot with this kernel and check if dri works.

---

### Post by narandill on 2006-07-02
My last post is on 686, and on 386 :

> 
root@mieszko:~# sudo modprobe radeon
root@mieszko:~#


This is correct?

But in glxinfo still is rendering: NO :/

---

### Post by gborzi on 2006-07-02
It seems the reinstallation didn't get rid of the modules you recompiled from CVS. For now, lets continue with the 386 kernel. Which is the output of > lsmod|grep radeon
It should display something like this
> radeon                119872  1
drm                    78484  2 radeon.
My xorg.conf is attached to this post, please try it.

---

### Post by narandill on 2006-07-02
> mieszko@mieszko:~$ lsmod|grep radeon
radeon                116000  1
drm                    73236  2 radeon


I have also reconfigured xorg, and used yours xorg.conf, but still i dont have direct rendering... :/ pice of crap, what to do ....

but fps in glxgears are 2x now :P - 140 fps ;] lol

---

### Post by gborzi on 2006-07-02
It's really strange. Can you post or upload your /var/log/Xorg.0.log file ? In case you can't post or upload it, check the lines starting with "(EE)" and "(WW)".

---

### Post by narandill on 2006-07-02
Here, thanks for help :)

---

### Post by gborzi on 2006-07-02
There are 2 error lines in your Xorg.0.log, namely 
> (EE) Unable to find a valid framebuffer device
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
        (you may have to look at the server log to see warnings)
which is quite strange because by default the framebuffer device is off. Try to force it off by adding the following option to the Section "Device"
> Option "UseFBDev" "no"
after restarting X check if there are still the two error lines.
BTW, now I'm going to sleep, it's late here. But tomorrow I'll be able to help.

---

### Post by narandill on 2006-07-02
Ok, after rebooting X - that error (2  lines) dont exist now.
Direct Rendering - No, so bye and lets get do it tomorrow :)

---

### Post by gborzi on 2006-07-03
Today I have re-checked your Xorg.0.log file, comparing it with my Xorg.0.log. I noticed that X detects your card to be different from mine, but all lines referring to dri seems OK. Sorry, but I haven't any other idea on how to solve your problem.

---

### Post by narandill on 2006-07-03
Hmm thats impressive - i have installed X 6.9 CVS, and Xs has crashed at starting of system... so i have removed xserver-xorg and installed it from repo, and Direct Rendering works !!! Strange.... - on ati driver ;) but im happy

---

### Post by theonlyandy on 2007-03-19
Ahoi.

It seems I got the same problem.

My card is
VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

and Direct Rendering: No.

Unfortunately I can't tell how you solved the problem, because in the end it suddenly works.
I would be very happy getting some help =)

In my xorg.log stands:
```
(WW) RADEON(0): Direct rendering disabled

```

Greetings,
 Andy

---

