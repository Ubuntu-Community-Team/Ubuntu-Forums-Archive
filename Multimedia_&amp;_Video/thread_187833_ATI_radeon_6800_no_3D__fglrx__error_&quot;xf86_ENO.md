---
title: "ATI radeon 6800 no 3D : fglrx : error &quot;xf86_ENOMEM&quot;"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by tichadok on 2006-06-03
I have an ATI radeon 9800 pro and no 3D acceleration with fglrx 8.25.18 [May 18 2006] I need it to work with openGL networking mapping softwares:

**fglrxinfo**
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

**My xorg.conf :**
[PHP]
Section "Device"
        Identifier      "radeon 9800 pro"
        Driver          "fglrx"
        #Option         "KernelModuleParm" "agplock=0"
        Option          "UseFastTLS" "2"
        Option          "UseInternalAGPGART" "no"
        BusID           "PCI:1:0:0"
        #VideoRam       128000
EndSection[/PHP]

This is a common error I have, in the Xorg log:
**(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"**

Here are some details to help me:

The fglrx module is loaded :

**$ lsmod | grep agp**
```

fglrx                 388908  0
agpgart                34888  2 fglrx,sis_agp
```

**dmesg | grep agp**
```
[4294686.027000] Linux agpgart interface v0.101 (c) Dave Jones
[4294686.080000] agpgart: Detected SiS 760 chipset
[4294686.081000] agpgart: AGP aperture is 4M @ 0xe0000000
```
[B]

dmesg | grep fglrx[/B]
```
[4294688.996000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294688.998000] [fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
[4294688.998000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294702.260000] [fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
[4294702.260000] [fglrx:firegl_unlock] *ERROR* Process 4651 using kernel context 0
```

**lspci | grep Radeon**
```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
```

**lspci | grep bridge**
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```


[SIZE="4"]**I tried this solutions without success :**[/SIZE]](*,) 

Question 4.3: When I try to start X, it fails with a message saying it was 'unable to acquire AGP, error "xf86_ENOMEM"'
This error is generally more difficult to diagnose and fix than the "xf86_ENODEV" error. Some things to try:

    * If you are using the kernel AGP support (ie "UseInternalAGPGART" is set to "no"), ensure that you have the necessary modules (agpgart + chipset-specific module) loaded BEFORE loading the fglrx module. For example, if you have a VIA motherboard, load the "agpgart" and "via-agp" modules, then load the fglrx module (on 2.4 kernels, you only have to load the "agpgart" module). If you had an nForce board, you would load "agpgart" and "nvidia-agp", followed by fglrx, and so on for the other chipset types.
    * Increase your AGP aperture size in the BIOS (particularly for nForce2 boards)
    * If you have an nForce2 board, try disabling the "AGP 8x Support" option in the BIOS.
    * Check that you haven't set "UseInternalAGPGART" to "yes" and have your kernel AGP settings compiled in (this won't work)
    * Set "UseFastTLS" to "2" in your XF86Config/xorg.conf file.
    * Try adding the line
      Option "KernelModuleParm" "agplock=0"
      to your xorg.conf file (in the same place as the other ATI-specific options).
    * Check the output of the "dmesg" command for errors.
    * Check that your kernel configuration is correct.
    * Try a newer kernel version.

---------------------------------------------------
---------------------------------------------------

You need some support for your AGP chipset. You have two choices: the ATI driver's built-in AGP support or the kernel agpgart driver. It's difficult to say in advance which one is better or will work at all, because it depends on the exact driver and kernel versions you're using, but the kernel driver should be your preferred choice if it works for you. To use the kernel driver, add the following line to the "Device" section of your X server config file:

Option "UseInternalAGPGART" "no"

The X server configuration is discussed in more detail below, but the AGP configuration is important so I'm mentioning this detail early because I'd like to make sure that it sticks in your memory somewhere.

The error unable to acquire AGP, error "xf86_ENOMEM" in your X server log usually means that you are using the built-in AGP support with an unsupported chipset. Set "UseInternalAGPGART" to "no" and load the kernel driver (see below for details) which will hopefully support your AGP chipset.
If you want to use the ATI driver's built-in AGP support instead, set "UseInternalAGPGART" to "yes" (it's the default setting, so you can just omit it) and make sure that the kernel driver is not compiled into your kernel: either compile it as a module or disable it entirely. Beware that discover (and possibly other hardware detection tools) might try to load the kernel driver automatically during startup. If that happens to you, you can tweak discover's configuration or you can simply move the agpgart.* files away from /lib/modules.

If neither one supports your chipset, try using the kernel driver with the agp_try_unsupported=1 option on the kernel command line or as a parameter when you load the module.

Note that in the 2.6 kernel the AGP chipset drivers are separate from the agpgart driver itself, so if you build them as modules you will need to load the agpgart module and a chipset module such as via-agp, nvidia-agp, etc.

**[SIZE="4"]Help me please, help me I don't want to use windows again !![/SIZE]**:mad:

---

