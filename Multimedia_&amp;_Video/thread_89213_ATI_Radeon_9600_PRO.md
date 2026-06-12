---
title: "ATI Radeon 9600 PRO"
date: 2005-11-12
forum: Multimedia &amp; Video
---

### Post by matthinckley on 2005-11-12
Hello everyone, I am totally new to ubuntu, just came from FC4, anyways.. I really like this distro but I'm having some issues with my video card.

After following the howto for the ATI drivers my GL drivers are correct but I still have really slow 3D performance.. specifically the screensavers (that's all I've tested so far).  anyways I did some searching around and ran  **dmesg | grep fglrx** and it gave me this :

```
[4294705.271000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294705.273000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294705.273000] [fglrx] module loaded - fglrx 8.19.10 [Nov  9 2005] on minor 0
[4294705.307000] [fglrx] ACPI power management is initialized.
[4294705.900000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294705.900000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294705.900000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294705.900000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[4294705.901000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294705.990000] [fglrx] free  AGP = 121909248
[4294705.990000] [fglrx] max   AGP = 121909248
[4294705.990000] [fglrx] free  LFB = 108974080
[4294705.990000] [fglrx] max   LFB = 108974080
[4294705.990000] [fglrx] free  Inv = 0
[4294705.990000] [fglrx] max   Inv = 0
[4294705.990000] [fglrx] total Inv = 0
[4294705.990000] [fglrx] total TIM = 0
[4294705.990000] [fglrx] total FB  = 0
[4294705.990000] [fglrx] total AGP = 32768
[4294771.374000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294771.374000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294771.374000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[4294771.375000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294771.463000] [fglrx] free  AGP = 121909248
[4294771.463000] [fglrx] max   AGP = 121909248
[4294771.463000] [fglrx] free  LFB = 108974080
[4294771.463000] [fglrx] max   LFB = 108974080
[4294771.463000] [fglrx] free  Inv = 0
[4294771.463000] [fglrx] max   Inv = 0
[4294771.463000] [fglrx] total Inv = 0
[4294771.463000] [fglrx] total TIM = 0
[4294771.463000] [fglrx] total FB  = 0
[4294771.463000] [fglrx] total AGP = 32768

```

So I am wondering if I need to disable the kernel AGP support? and if so how do I do this?  or maybe I am just totally on the wrong track here.. 

Anyways thank you for any help you can give me.. I've been skimming these forums for about 2 days now and have learned a lot.

Thanks again.

Matt

---

### Post by mlomker on 2005-11-12
You can't disable the internal gart without building a custom kernel (not sure that'd solve your issue anyway).  Look through the /var/log/Xorg.0.log file for errors.  Does **fglrxinfo** and **glxgears -printfps** look correct?

Are you running 32 or 64-bit?  I couldn't get the latest driver to work on 64-bit.

---

### Post by matthinckley on 2005-11-12
here are the warnings I get in the Xorg.0.log file

```
(WW) The core pointer device wasn't specified explicitly in the layout.
        Using the first mouse device.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)

```

fglrxinfo:

```
matt@hinckley:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5461 (X4.3.0-8.19.10)

```


glxgears -printfps:

```
matt@hinckley:~$ glxgears -printfps
14897 frames in 5.0 seconds = 2979.298 FPS
15065 frames in 5.0 seconds = 3012.863 FPS
10463 frames in 5.0 seconds = 2092.489 FPS
15087 frames in 5.0 seconds = 3017.355 FPS
14970 frames in 5.0 seconds = 2993.950 FPS
17245 frames in 5.0 seconds = 3448.940 FPS
14951 frames in 5.0 seconds = 2990.175 FPS
13886 frames in 5.0 seconds = 2777.044 FPS
15019 frames in 5.0 seconds = 3003.671 FPS
matt@hinckley:~$

```

^^^
that is if I leave the window that pops up alone.. it's really small and I run 1600x1200 resolution

here is what it looks like if I maximize the glxgears window:

```
matt@hinckley:~$ glxgears -printfps
5277 frames in 5.0 seconds = 1054.402 FPS
807 frames in 5.0 seconds = 161.299 FPS
807 frames in 5.0 seconds = 161.362 FPS
807 frames in 5.0 seconds = 161.313 FPS
807 frames in 5.0 seconds = 161.363 FPS
806 frames in 5.0 seconds = 161.160 FPS
647 frames in 5.0 seconds = 129.375 FPS
434 frames in 5.0 seconds = 86.781 FPS
451 frames in 5.0 seconds = 90.006 FPS
450 frames in 5.0 seconds = 89.990 FPS
426 frames in 5.0 seconds = 85.106 FPS
matt@hinckley:~$

```

Also I have noticed it seems to only be the XAnalogTV screensaver that is having problems.  I thought they all were but i guess i didn't check any of the others after I put the ATI drivers on.  So I don't know what the deal is.. I had the same screensaver on FC4 and it worked perfectly.

Anyways, are any of these warnings things i need to be worried about?

Thanks

Matt

---

### Post by mlomker on 2005-11-12
I have the same errors, so that all looks normal to me.  Could be a bug in the screensaver.

---

### Post by garciadc on 2005-11-12
I have ATI9600SE and it's the same here as well, but I am having problems with more than just XanalogTV screen saver--I really haven't troubleshooted yet.   But I seem to have more of the screen savers give me a blank screen or a psycedelic guatemalan quilt on my amd64 laptop which has Via Unichrome Pro IGP.  I tried to change to via driver from vesa, but I think there are compatilbilty issues cause screen went blank instead of login.

---

### Post by matthinckley on 2005-11-12
wierd.. oh well i guess i'll just live without XanalogTV.. I really like that one though, especially with it grabbing my family pictures..

Is there any way to re-install that particular screen saver?

---

### Post by LuxoDave on 2005-11-13
I have a ATI 9600 AIW Pro. If is to glrxgears, here is what I get:

> david@Herrman:~$ glxgears -printfps
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1716 frames in 5.4 seconds = 319.673 FPS
1820 frames in 5.1 seconds = 355.409 FPS
1960 frames in 5.4 seconds = 365.867 FPS
1820 frames in 5.2 seconds = 350.610 FPS
3500 frames in 5.1 seconds = 689.746 FPS
4480 frames in 5.1 seconds = 880.168 FPS
4480 frames in 5.1 seconds = 878.881 FPS


What is XFree86-DRI?

---

### Post by kori.mendocino on 2005-11-25
you CAN disable the internal agp gart with the following line in your Section "Device":
	Option "UseInternalAGPGART" 	"no"

and my glxgears' fps is between 3000 and 4000. yes, i am using a radeon 9600

---

### Post by mlomker on 2005-11-25
[QUOTE=kori.mendocino]you CAN disable the internal agp gart with the following line in your Section "Device":
	Option "UseInternalAGPGART" 	"no"
[/QUOTE]

No, you can't...without building a custom kernel.  If you look at **dmesg | grep fglrx** after boot it'll tell you that it is using the internal part regardless of that setting.

---

### Post by mirak63 on 2006-05-03
I confirm that I finally made them work on 9600 pro by building my own kernel without radeon support.

---

