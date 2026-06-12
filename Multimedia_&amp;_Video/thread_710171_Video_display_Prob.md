---
title: "Video display Prob"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by nnjond on 2008-02-28
Video Prob

Hi,

The only Video app I have working is M player (I just get a display of red dots in the others), but it will not fullscrn; Just a small display! Does anyone know what's wrong?

Thanks.

---

### Post by deepclutch on 2008-02-28
^that means ur XVideo(xv) is not working!did u know what is ur graphics card etc?
may be u can open a terminal and post the output of command "lspci" without quotes.

also,try opening gmplayer's settings and select video driver as "xv"  and audio driver as "esd".
U can check whether ur graphics card is working via command :
```
glxinfo |grep direct
```
^in a terminal ;)

---

### Post by nnjond on 2008-02-29
Thanks for your help,

does this data give you any better idea about my prob?

-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
nnjond@nnjond-desktop:~$ 
nnjond@nnjond-desktop:~$ glxinfo |grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
nnjond@nnjond-desktop:~$  LIBGL_DEBUG=verbose)
bash: syntax error near unexpected token `)'
nnjond@nnjond-desktop:~$ OpenGL renderer string: Mesa GLX Indirect
bash: OpenGL: command not found
nnjond@nnjond-desktop:~$

---

### Post by deepclutch on 2008-03-01
^ur Direct rendering is not enabled.the X is using "vesa" driver hence sluggish performance.

U have to edit ur /etc/X11/xorg.conf and in section "device" choose "sis" as the driver.
u can do the above by opening a terminal and :
```
 sudo dpkg-reconfigure xserver-xorg
 
```
make sure xserver-xorg-video-sis is installed.

In a "windowish" language- ur linux "video driver" is not installed.for that u have to choose above method mentioned.

---

