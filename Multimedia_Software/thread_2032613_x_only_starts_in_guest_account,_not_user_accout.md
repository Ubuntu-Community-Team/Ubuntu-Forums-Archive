---
title: "x only starts in guest account, not user accout"
date: 2012-07-24
forum: Multimedia Software
---

### Post by Subito Piano on 2012-07-24
Hi!  About 8 hours of frustration here...

      I recently installed lubuntu 12.04 to replace my Ubuntu Studio 10.04 system, keeping my home folder, which is on its own partition, sda3.  All went fine for several weeks, but somehow I got some extra "junk" I didn't need (failure to carefully monitor what I was doing), so I went to uninstall it.  In the process, I apparently eliminated some libs i should not have; but I had a remastersys backup of my system on hand.  Since I keep /home in a separate partition, I reinstalled root from my remastersys disk, using my same name and using sda3 as my home folder.   This is the usual way I reinstall and haven't had problems before.   Now I can get X only through the guest account.  When I attempt a graphical login to my user account, the following message briefly appears:
 ```
stopping system V runlevel compatibility
starting cups printing spooler/server
```Obviously, it's the first line that is the issue.  

[LIST]
[*] A reinstall using my original pristine lubuntu install disk (not my remastersys disk) made no difference
[*] I CAN log in to the shell
[*]apt-get install-update, fdisk, and similar commands have not change my situation
[*] I'm running 32-bit lubuntu 12.04 on a 64-bit Toshiba Satellite, AMD Turion dual-core
[*] I have an ATI Radeon graphics card
[/LIST]
      It seems to me there must be some sort of file equivalent to good old old xorg.conf in my home folder that isn't present in the guest account, but i can't find anything that looks like it.  I would think i need to find that configuration file and yank it out (er, rather, rename it temporarily and reboot).  I HOPE i don't have to jettison all my prefs....that took a lot of time.
 
      Of course, the important stuff is all my work; those files are safe and also backed up to another drive.
     
Hope someone can help -- and thanks!!

---

### Post by NikTh on 2012-07-24
Hi , 
if a file xorg.conf exists , then must be at /etc/X11/ path . So if you find it there, remove it.. 

You said that did fresh install , did you install AMD additional drivers , or you are with Open source radeon ? 

You can try to restart Display manager , from tty. (Console)
```
sudo service lightdm stop 
sudo service lightdm start
```

Additional info might needed . 
```
cat .xession-errors > xsession.txt 
cat /var/log/Xorg.0.log > Xorg.txt 
dmesg > dmesg.txt
lspci -nnk | grep -iA2 vga > lspci.txt
``` 

**Post these txt's here , inside [CODE] tags , by highlighting the text and click # symbol on top of message pane. **

Thanks

---

### Post by Subito Piano on 2012-07-24
Grrrr.....

stopping and restarting lightdm didn't help.  

when i entered
```
cat .xession-errors > xsession.txt 
```  i received in reply
```
"no such file or directory."
```When i entered ```
cat /var/log/Xorg.0.log > Xorg.txt
```i was informed there was no space left on device!!!  (not true, there's still 5GB on /home and 2GB on root).

So i stopped there.... **[EDIT: see next post]**

Perhaps i should rename some openbox or LXDE folders, reboot, and see if the offending file is in one of them?  Seems to me the problem can't be my installed drivers or anything in the root folder (i.e., "/") because i CAN log in as guest and get a screen.  It must be in my home prefs....

---

### Post by Subito Piano on 2012-07-24
OK -- i used Puppy to access my root folder and get some of the requested files to post here: 

this is /var/log/Xorg.0.log:
```
 [    17.402] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    17.402] X Protocol Version 11, Revision 0
[    17.402] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    17.402] Current Operating System: Linux dad 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686
[    17.402] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=ee2d57f6-c009-4e34-9c91-5181d7a9bcf6 ro quiet splash vt.handoff=7
[    17.402] Build Date: 04 April 2012  11:58:38PM
[    17.402] xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
[    17.402] Current version of pixman: 0.24.4
[    17.402]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    17.402] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.402] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 24 13:25:49 2012
[    17.402] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.403] (==) No Layout section.  Using the first Screen section.
[    17.403] (==) No screen section available. Using defaults.
[    17.403] (**) |-->Screen "Default Screen Section" (0)
[    17.403] (**) |   |-->Monitor "<default monitor>"
[    17.403] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    17.403] (==) Automatically adding devices
[    17.403] (==) Automatically enabling devices
[    17.403] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.403]     Entry deleted from font path.
[    17.403] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.403]     Entry deleted from font path.
[    17.403] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.403]     Entry deleted from font path.
[    17.403] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    17.403]     Entry deleted from font path.
[    17.403] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.403]     Entry deleted from font path.
[    17.403] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.403]     Entry deleted from font path.
[    17.403] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    17.403]     Entry deleted from font path.
[    17.403] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    17.403] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.403] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.403] (II) Loader magic: 0x70a5a0
[    17.403] (II) Module ABI versions:
[    17.403]     X.Org ANSI C Emulation: 0.4
[    17.403]     X.Org Video Driver: 11.0
[    17.403]     X.Org XInput driver : 16.0
[    17.403]     X.Org Server Extension : 6.0
[    17.405] (--) PCI:*(0:1:5:0) 1002:791f:1179:ff00 rev 0, Mem @ 0xf0000000/134217728, 0xf8100000/65536, 0xf8000000/1048576, I/O @ 0x00009000/256
[    17.405] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    17.405] (II) LoadModule: "extmod"
[    17.405] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.405] (II) Module extmod: vendor="X.Org Foundation"
[    17.405]     compiled for 1.11.3, module version = 1.0.0
[    17.405]     Module class: X.Org Server Extension
[    17.405]     ABI class: X.Org Server Extension, version 6.0
[    17.405] (II) Loading extension MIT-SCREEN-SAVER
[    17.405] (II) Loading extension XFree86-VidModeExtension
[    17.405] (II) Loading extension XFree86-DGA
[    17.405] (II) Loading extension DPMS
[    17.405] (II) Loading extension XVideo
[    17.405] (II) Loading extension XVideo-MotionCompensation
[    17.405] (II) Loading extension X-Resource
[    17.405] (II) LoadModule: "dbe"
[    17.406] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.406] (II) Module dbe: vendor="X.Org Foundation"
[    17.406]     compiled for 1.11.3, module version = 1.0.0
[    17.406]     Module class: X.Org Server Extension
[    17.406]     ABI class: X.Org Server Extension, version 6.0
[    17.406] (II) Loading extension DOUBLE-BUFFER
[    17.406] (II) LoadModule: "glx"
[    17.406] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.406] (II) Module glx: vendor="X.Org Foundation"
[    17.406]     compiled for 1.11.3, module version = 1.0.0
[    17.406]     ABI class: X.Org Server Extension, version 6.0
[    17.406] (==) AIGLX enabled
[    17.406] (II) Loading extension GLX
[    17.406] (II) LoadModule: "record"
[    17.406] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.407] (II) Module record: vendor="X.Org Foundation"
[    17.407]     compiled for 1.11.3, module version = 1.13.0
[    17.407]     Module class: X.Org Server Extension
[    17.407]     ABI class: X.Org Server Extension, version 6.0
[    17.407] (II) Loading extension RECORD
[    17.407] (II) LoadModule: "dri"
[    17.407] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.407] (II) Module dri: vendor="X.Org Foundation"
[    17.407]     compiled for 1.11.3, module version = 1.0.0
[    17.407]     ABI class: X.Org Server Extension, version 6.0
[    17.407] (II) Loading extension XFree86-DRI
[    17.407] (II) LoadModule: "dri2"
[    17.407] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.407] (II) Module dri2: vendor="X.Org Foundation"
[    17.407]     compiled for 1.11.3, module version = 1.2.0
[    17.407]     ABI class: X.Org Server Extension, version 6.0
[    17.407] (II) Loading extension DRI2
[    17.407] (==) Matched fglrx as autoconfigured driver 0
[    17.407] (==) Matched ati as autoconfigured driver 1
[    17.407] (==) Matched vesa as autoconfigured driver 2
[    17.407] (==) Matched fbdev as autoconfigured driver 3
[    17.408] (==) Assigned the driver to the xf86ConfigLayout
[    17.408] (II) LoadModule: "fglrx"
[    17.408] (WW) Warning, couldn't open module fglrx
[    17.408] (II) UnloadModule: "fglrx"
[    17.408] (II) Unloading fglrx
[    17.408] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.408] (II) LoadModule: "ati"
[    17.409] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.409] (II) Module ati: vendor="X.Org Foundation"
[    17.409]     compiled for 1.11.3, module version = 6.14.99
[    17.409]     Module class: X.Org Video Driver
[    17.409]     ABI class: X.Org Video Driver, version 11.0
[    17.409] (II) LoadModule: "radeon"
[    17.409] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.409] (II) Module radeon: vendor="X.Org Foundation"
[    17.409]     compiled for 1.11.3, module version = 6.14.99
[    17.409]     Module class: X.Org Video Driver
[    17.409]     ABI class: X.Org Video Driver, version 11.0
[    17.409] (II) LoadModule: "vesa"
[    17.410] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.410] (II) Module vesa: vendor="X.Org Foundation"
[    17.410]     compiled for 1.11.3, module version = 2.3.0
[    17.410]     Module class: X.Org Video Driver
[    17.410]     ABI class: X.Org Video Driver, version 11.0
[    17.410] (II) LoadModule: "fbdev"
[    17.410] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.410] (II) Module fbdev: vendor="X.Org Foundation"
[    17.410]     compiled for 1.11.3, module version = 0.4.2
[    17.410]     ABI class: X.Org Video Driver, version 11.0
[    17.410] (==) Matched fglrx as autoconfigured driver 0
[    17.410] (==) Matched ati as autoconfigured driver 1
[    17.410] (==) Matched vesa as autoconfigured driver 2
[    17.410] (==) Matched fbdev as autoconfigured driver 3
[    17.410] (==) Assigned the driver to the xf86ConfigLayout
[    17.410] (II) LoadModule: "fglrx"
[    17.411] (WW) Warning, couldn't open module fglrx
[    17.411] (II) UnloadModule: "fglrx"
[    17.411] (II) Unloading fglrx
[    17.411] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.411] (II) LoadModule: "ati"
[    17.411] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    17.411] (II) Module ati: vendor="X.Org Foundation"
[    17.411]     compiled for 1.11.3, module version = 6.14.99
[    17.411]     Module class: X.Org Video Driver
[    17.411]     ABI class: X.Org Video Driver, version 11.0
[    17.412] (II) LoadModule: "vesa"
[    17.412] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.412] (II) Module vesa: vendor="X.Org Foundation"
[    17.412]     compiled for 1.11.3, module version = 2.3.0
[    17.412]     Module class: X.Org Video Driver
[    17.412]     ABI class: X.Org Video Driver, version 11.0
[    17.412] (II) UnloadModule: "vesa"
[    17.412] (II) Unloading vesa
[    17.412] (II) Failed to load module "vesa" (already loaded, 0)
[    17.412] (II) LoadModule: "fbdev"
[    17.412] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.412] (II) Module fbdev: vendor="X.Org Foundation"
[    17.412]     compiled for 1.11.3, module version = 0.4.2
[    17.412]     ABI class: X.Org Video Driver, version 11.0
[    17.412] (II) UnloadModule: "fbdev"
[    17.412] (II) Unloading fbdev
[    17.412] (II) Failed to load module "fbdev" (already loaded, 0)
[    17.412] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    17.418] (II) VESA: driver for VESA chipsets: vesa
[    17.418] (II) FBDEV: driver for framebuffer: fbdev
[    17.418] (++) using VT number 7

[    17.418] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.418] (II) [KMS] Kernel modesetting enabled.
[    17.418] (WW) Falling back to old probe method for vesa
[    17.418] (WW) Falling back to old probe method for fbdev
[    17.418] (II) Loading sub module "fbdevhw"
[    17.418] (II) LoadModule: "fbdevhw"
[    17.418] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.418] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.418]     compiled for 1.11.3, module version = 0.0.2
[    17.418]     ABI class: X.Org Video Driver, version 11.0
[    17.419] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    17.419] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    17.419] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    17.419] (==) RADEON(0): Default visual is TrueColor
[    17.419] (==) RADEON(0): RGB weight 888
[    17.419] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    17.419] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[    17.419] (II) RADEON(0): PCI card detected
[    17.419] drmOpenDevice: node name is /dev/dri/card0
[    17.419] drmOpenDevice: open result is 8, (OK)
[    17.419] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    17.419] drmOpenDevice: node name is /dev/dri/card0
[    17.419] drmOpenDevice: open result is 8, (OK)
[    17.419] drmOpenByBusid: drmOpenMinor returns 8
[    17.419] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    17.419] (II) Loading sub module "exa"
[    17.419] (II) LoadModule: "exa"
[    17.419] (II) Loading /usr/lib/xorg/modules/libexa.so
[    17.419] (II) Module exa: vendor="X.Org Foundation"
[    17.419]     compiled for 1.11.3, module version = 2.5.0
[    17.419]     ABI class: X.Org Video Driver, version 11.0
[    17.419] (II) RADEON(0): KMS Color Tiling: enabled
[    17.419] (II) RADEON(0): KMS Pageflipping: enabled
[    17.419] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    17.596] (II) RADEON(0): Output VGA-0 has no monitor section
[    17.596] (II) RADEON(0): Output LVDS has no monitor section
[    17.772] (II) RADEON(0): Output S-video has no monitor section
[    17.948] (II) RADEON(0): EDID for output VGA-0
[    17.948] (II) RADEON(0): EDID for output LVDS
[    17.948] (II) RADEON(0): Manufacturer: LPL  Model: dc00  Serial#: 0
[    17.948] (II) RADEON(0): Year: 2006  Week: 0
[    17.948] (II) RADEON(0): EDID Version: 1.3
[    17.948] (II) RADEON(0): Digital Display Input
[    17.948] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    17.948] (II) RADEON(0): Gamma: 2.20
[    17.948] (II) RADEON(0): No DPMS capabilities specified
[    17.948] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.948] (II) RADEON(0): First detailed timing is preferred mode
[    17.948] (II) RADEON(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
[    17.948] (II) RADEON(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
[    17.948] (II) RADEON(0): Manufacturer's mask: 0
[    17.948] (II) RADEON(0): Supported detailed timing:
[    17.948] (II) RADEON(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
[    17.948] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    17.948] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    17.948] (II) RADEON(0):  LGPhilipsLCD
[    17.948] (II) RADEON(0):  LP154WX4-TLD2
[    17.948] (II) RADEON(0): EDID (in hex):
[    17.948] (II) RADEON(0):     00ffffffffffff00320c00dc00000000
[    17.948] (II) RADEON(0):     00100103802115780ab3409959538d27
[    17.948] (II) RADEON(0):     25505400000001010101010101010101
[    17.948] (II) RADEON(0):     010101010101bc1b00a0502017303020
[    17.948] (II) RADEON(0):     36004bcf100000190000000000000000
[    17.948] (II) RADEON(0):     00000000000000000000000000fe004c
[    17.948] (II) RADEON(0):     475068696c6970734c43440a000000fe
[    17.948] (II) RADEON(0):     004c503135345758342d544c44320043
[    17.948] (II) RADEON(0): Printing probed modes for output LVDS
[    17.948] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[    17.948] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    17.948] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.948] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    17.948] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    17.948] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    17.948] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    17.948] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    18.124] (II) RADEON(0): EDID for output S-video
[    18.124] (II) RADEON(0): Output VGA-0 disconnected
[    18.124] (II) RADEON(0): Output LVDS connected
[    18.124] (II) RADEON(0): Output S-video disconnected
[    18.124] (II) RADEON(0): Using exact sizes for initial modes
[    18.124] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    18.124] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.124] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7bd8000
[    18.124] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    18.124] (==) RADEON(0): DPI set to (96, 96)
[    18.124] (II) Loading sub module "fb"
[    18.124] (II) LoadModule: "fb"
[    18.124] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.124] (II) Module fb: vendor="X.Org Foundation"
[    18.124]     compiled for 1.11.3, module version = 1.0.0
[    18.124]     ABI class: X.Org ANSI C Emulation, version 0.4
[    18.124] (II) Loading sub module "ramdac"
[    18.124] (II) LoadModule: "ramdac"
[    18.124] (II) Module "ramdac" already built-in
[    18.124] (II) UnloadModule: "vesa"
[    18.124] (II) Unloading vesa
[    18.124] (II) UnloadModule: "fbdev"
[    18.124] (II) Unloading fbdev
[    18.124] (II) UnloadModule: "fbdevhw"
[    18.124] (II) Unloading fbdevhw
[    18.124] (--) Depth 24 pixmap format is 32 bpp
[    18.125] (II) RADEON(0): [DRI2] Setup complete
[    18.125] (II) RADEON(0): [DRI2]   DRI driver: r300
[    18.125] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    18.125] (II) RADEON(0): Front buffer size: 4000K
[    18.125] (II) RADEON(0): VRAM usage limit set to 110534K
[    18.125] (==) RADEON(0): Backing store disabled
[    18.125] (II) RADEON(0): Direct rendering enabled
[    18.125] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    18.125] (II) RADEON(0): Setting EXA maxPitchBytes
[    18.125] (II) EXA(0): Driver allocated offscreen pixmaps
[    18.125] (II) EXA(0): Driver registered support for the following operations:
[    18.125] (II)         Solid
[    18.125] (II)         Copy
[    18.125] (II)         Composite (RENDER acceleration)
[    18.125] (II)         UploadToScreen
[    18.125] (II)         DownloadFromScreen
[    18.125] (II) RADEON(0): Acceleration enabled
[    18.125] (==) RADEON(0): DPMS enabled
[    18.125] (==) RADEON(0): Silken mouse enabled
[    18.125] (II) RADEON(0): Set up textured video
[    18.125] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    18.125] (II) RADEON(0): [XvMC] Extension initialized.
[    18.125] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.126] (--) RandR disabled
[    18.126] (II) Initializing built-in extension Generic Event Extension
[    18.126] (II) Initializing built-in extension SHAPE
[    18.126] (II) Initializing built-in extension MIT-SHM
[    18.126] (II) Initializing built-in extension XInputExtension
[    18.126] (II) Initializing built-in extension XTEST
[    18.126] (II) Initializing built-in extension BIG-REQUESTS
[    18.126] (II) Initializing built-in extension SYNC
[    18.126] (II) Initializing built-in extension XKEYBOARD
[    18.126] (II) Initializing built-in extension XC-MISC
[    18.126] (II) Initializing built-in extension SECURITY
[    18.126] (II) Initializing built-in extension XINERAMA
[    18.126] (II) Initializing built-in extension XFIXES
[    18.126] (II) Initializing built-in extension RENDER
[    18.126] (II) Initializing built-in extension RANDR
[    18.126] (II) Initializing built-in extension COMPOSITE
[    18.126] (II) Initializing built-in extension DAMAGE
[    18.152] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.152] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.152] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.152] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.153] (II) AIGLX: Loaded and initialized r300
[    18.153] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.154] (II) RADEON(0): Setting screen physical size to 338 x 211
[    18.166] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.171] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.171] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.171] (II) LoadModule: "evdev"
[    18.171] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.171] (II) Module evdev: vendor="X.Org Foundation"
[    18.171]     compiled for 1.11.3, module version = 2.7.0
[    18.171]     Module class: X.Org XInput Driver
[    18.171]     ABI class: X.Org XInput driver, version 16.0
[    18.172] (II) Using input driver 'evdev' for 'Power Button'
[    18.172] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.172] (**) Power Button: always reports core events
[    18.172] (**) evdev: Power Button: Device: "/dev/input/event2"
[    18.172] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.172] (--) evdev: Power Button: Found keys
[    18.172] (II) evdev: Power Button: Configuring as keyboard
[    18.172] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    18.172] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.172] (**) Option "xkb_rules" "evdev"
[    18.172] (**) Option "xkb_model" "pc105"
[    18.172] (**) Option "xkb_layout" "us"
[    18.173] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    18.173] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.173] (II) Using input driver 'evdev' for 'Video Bus'
[    18.173] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.173] (**) Video Bus: always reports core events
[    18.173] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    18.173] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.173] (--) evdev: Video Bus: Found keys
[    18.173] (II) evdev: Video Bus: Configuring as keyboard
[    18.173] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25/LNXVIDEO:01/input/input5/event5"
[    18.173] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    18.173] (**) Option "xkb_rules" "evdev"
[    18.173] (**) Option "xkb_model" "pc105"
[    18.173] (**) Option "xkb_layout" "us"
[    18.174] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.174] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.174] (II) Using input driver 'evdev' for 'Power Button'
[    18.174] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.174] (**) Power Button: always reports core events
[    18.174] (**) evdev: Power Button: Device: "/dev/input/event1"
[    18.174] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.174] (--) evdev: Power Button: Found keys
[    18.174] (II) evdev: Power Button: Configuring as keyboard
[    18.174] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    18.174] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    18.174] (**) Option "xkb_rules" "evdev"
[    18.174] (**) Option "xkb_model" "pc105"
[    18.174] (**) Option "xkb_layout" "us"
[    18.175] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    18.175] (II) No input driver specified, ignoring this device.
[    18.175] (II) This device may have been added with another device file.
[    18.175] (II) config/udev: Adding input device 2.4G Wireless Mouse (/dev/input/event4)
[    18.175] (**) 2.4G Wireless Mouse: Applying InputClass "evdev pointer catchall"
[    18.175] (II) Using input driver 'evdev' for '2.4G Wireless Mouse'
[    18.175] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.175] (**) 2.4G Wireless Mouse: always reports core events
[    18.175] (**) evdev: 2.4G Wireless Mouse: Device: "/dev/input/event4"
[    18.176] (--) evdev: 2.4G Wireless Mouse: Vendor 0x4f3 Product 0x2f4
[    18.176] (--) evdev: 2.4G Wireless Mouse: Found 9 mouse buttons
[    18.176] (--) evdev: 2.4G Wireless Mouse: Found scroll wheel(s)
[    18.176] (--) evdev: 2.4G Wireless Mouse: Found relative axes
[    18.176] (--) evdev: 2.4G Wireless Mouse: Found x and y relative axes
[    18.176] (II) evdev: 2.4G Wireless Mouse: Configuring as mouse
[    18.176] (II) evdev: 2.4G Wireless Mouse: Adding scrollwheel support
[    18.176] (**) evdev: 2.4G Wireless Mouse: YAxisMapping: buttons 4 and 5
[    18.176] (**) evdev: 2.4G Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.176] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input4/event4"
[    18.176] (II) XINPUT: Adding extended input device "2.4G Wireless Mouse" (type: MOUSE, id 9)
[    18.176] (II) evdev: 2.4G Wireless Mouse: initialized for relative axes.
[    18.176] (**) 2.4G Wireless Mouse: (accel) keeping acceleration scheme 1
[    18.176] (**) 2.4G Wireless Mouse: (accel) acceleration profile 0
[    18.176] (**) 2.4G Wireless Mouse: (accel) acceleration factor: 2.000
[    18.176] (**) 2.4G Wireless Mouse: (accel) acceleration threshold: 4
[    18.176] (II) config/udev: Adding input device 2.4G Wireless Mouse (/dev/input/mouse0)
[    18.176] (II) No input driver specified, ignoring this device.
[    18.176] (II) This device may have been added with another device file.
[    18.177] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event7)
[    18.177] (II) No input driver specified, ignoring this device.
[    18.177] (II) This device may have been added with another device file.
[    18.177] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event8)
[    18.177] (II) No input driver specified, ignoring this device.
[    18.177] (II) This device may have been added with another device file.
[    18.178] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    18.178] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.178] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.178] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.178] (**) AT Translated Set 2 keyboard: always reports core events
[    18.178] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    18.178] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.178] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.178] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.178] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    18.178] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    18.178] (**) Option "xkb_rules" "evdev"
[    18.178] (**) Option "xkb_model" "pc105"
[    18.178] (**) Option "xkb_layout" "us"
[    18.181] (II) config/udev: Adding input device Toshiba input device (/dev/input/event6)
[    18.181] (**) Toshiba input device: Applying InputClass "evdev keyboard catchall"
[    18.181] (II) Using input driver 'evdev' for 'Toshiba input device'
[    18.181] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.181] (**) Toshiba input device: always reports core events
[    18.181] (**) evdev: Toshiba input device: Device: "/dev/input/event6"
[    18.181] (--) evdev: Toshiba input device: Vendor 0 Product 0
[    18.181] (--) evdev: Toshiba input device: Found keys
[    18.181] (II) evdev: Toshiba input device: Configuring as keyboard
[    18.181] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    18.181] (II) XINPUT: Adding extended input device "Toshiba input device" (type: KEYBOARD, id 11)
[    18.181] (**) Option "xkb_rules" "evdev"
[    18.181] (**) Option "xkb_model" "pc105"
[    18.181] (**) Option "xkb_layout" "us"
[    21.620] (II) AIGLX: Suspending AIGLX clients for VT switch
[   188.848] (II) evdev: Toshiba input device: Close
[   188.849] (II) UnloadModule: "evdev"
[   188.849] (II) Unloading evdev
[   188.849] (II) evdev: AT Translated Set 2 keyboard: Close
[   188.849] (II) UnloadModule: "evdev"
[   188.849] (II) Unloading evdev
[   188.849] (II) evdev: 2.4G Wireless Mouse: Close
[   188.849] (II) UnloadModule: "evdev"
[   188.849] (II) Unloading evdev
[   188.849] (II) evdev: Power Button: Close
[   188.849] (II) UnloadModule: "evdev"
[   188.849] (II) Unloading evdev
[   188.849] (II) evdev: Video Bus: Close
[   188.849] (II) UnloadModule: "evdev"
[   188.849] (II) Unloading evdev
[   188.849] (II) evdev: Power Button: Close
[   188.849] (II) UnloadModule: "evdev"
[   188.849] (II) Unloading evdev
[   188.850]  ddxSigGiveUp: Closing log
[   188.850] Server terminated successfully (0). Closing log file.
```here is dmesg

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077e70000 (usable)
[    0.000000]  BIOS-e820: 0000000077e70000 - 0000000077e83000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077e83000 - 0000000077e85000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077e85000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: TOSHIBA Satellite A215/IALAA, BIOS V1.90 02/25/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x77e70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f7300] f7300
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36504000 - 3727a000
[    0.000000] ACPI: RSDP 000f7260 00024 (v02 TOSCPL)
[    0.000000] ACPI: XSDT 77e7aa18 00064 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 77e828f7 000F4 (v03 TOSCPL Herring  06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 77e7aa7c 07E7B (v01 TOSCPL    SB600 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 77e84fc0 00040
[    0.000000] ACPI: TCPA 77e82a5f 00032 (v02 TOSCPL          06040000 PTEC 00000000)
[    0.000000] ACPI: SLIC 77e82a91 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
[    0.000000] ACPI: SSDT 77e82c07 00206 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 77e82e0d 00054 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 77e82e61 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: HPET 77e82e9d 00038 (v01 PTLTD  HPETTBL  06040000  LTP 00000001)
[    0.000000] ACPI: ASF! 77e82ed5 0012B (v32    DMA AMDTBL   06040000 PTL  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1030MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00077e70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00077e70
[    0.000000] On node 0 totalpages: 491005
[    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map f5604200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2061 pages used for memmap
[    0.000000]   HighMem zone: 261733 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s31616 r0 d21632 u2097152
[    0.000000] pcpu-alloc: s31616 r0 d21632 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 487168
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=ee2d57f6-c009-4e34-9c91-5181d7a9bcf6 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7857664 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00077e70)
[    0.000000] Memory: 1916216k/1964480k available (5627k kernel code, 47804k reserved, 2764k data, 712k init, 1055176k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
[    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4408000 soft=f440a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.932 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.86 BogoMIPS (lpj=7979728)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004043] Security Framework initialized
[    0.004067] AppArmor: AppArmor initialized
[    0.004070] Yama: becoming mindful.
[    0.004144] Mount-cache hash table entries: 512
[    0.004314] Initializing cgroup subsys cpuacct
[    0.004322] Initializing cgroup subsys memory
[    0.004333] Initializing cgroup subsys devices
[    0.004336] Initializing cgroup subsys freezer
[    0.004340] Initializing cgroup subsys blkio
[    0.004350] Initializing cgroup subsys perf_event
[    0.004377] CPU: Physical Processor ID: 0
[    0.004380] CPU: Processor Core ID: 0
[    0.004385] mce: CPU supports 5 MCE banks
[    0.004396] using AMD E400 aware idle routine
[    0.008266] ACPI: Core revision 20110623
[    0.008271] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.008403] ACPI: Forced DSDT copy: length 0x07E7B copied locally, original unmapped
[    0.016014] ftrace: allocating 25954 entries in 51 pages
[    0.020084] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.020474] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.024001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.024001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.024001] ..... (found apic 0 pin 0) ...
[    0.065278] ....... works.
[    0.065280] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-60 stepping 02
[    0.068003] Performance Events: AMD PMU driver.
[    0.068003] ... version:                0
[    0.068003] ... bit width:              48
[    0.068003] ... generic registers:      4
[    0.068003] ... value mask:             0000ffffffffffff
[    0.068003] ... max period:             00007fffffffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             000000000000000f
[    0.068003] NMI watchdog enabled, takes one hw-pmu counter.
[    0.068003] CPU 1 irqstacks, hard=f44d2000 soft=f44d4000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 99000
[    0.008000] Initializing CPU#1
[    0.152124] NMI watchdog enabled, takes one hw-pmu counter.
[    0.152151] System has AMD C1E enabled
[    0.152155] Brought up 2 CPUs
[    0.152158] Total of 2 processors activated (7979.85 BogoMIPS).
[    0.152151] Switch to broadcast mode on CPU1
[    0.152727] Switch to broadcast mode on CPU0
[    0.152727] devtmpfs: initialized
[    0.152727] EVM: security.selinux
[    0.152727] EVM: security.SMACK64
[    0.152727] EVM: security.capability
[    0.152727] PM: Registering ACPI NVS region at 77e83000 (8192 bytes)
[    0.153320] print_constraints: dummy: 
[    0.153358] RTC time: 17:25:32, date: 07/24/12
[    0.153405] NET: Registered protocol family 16
[    0.153440] Trying to unpack rootfs image as initramfs...
[    0.153573] EISA bus registered
[    0.153578] node 0 link 0: io port [1000, fffff]
[    0.153582] TOM: 0000000080000000 aka 2048M
[    0.153585] node 0 link 0: mmio [f8100000, ffffffff]
[    0.153589] node 0 link 0: mmio [f8000000, f80fffff]
[    0.153593] node 0 link 0: mmio [f8000000, f7ffffff]
[    0.153596] node 0 link 0: mmio [f0000000, f7ffffff]
[    0.153599] node 0 link 0: mmio [a0000, bffff]
[    0.153602] node 0 link 0: mmio [f0000000, efffffff]
[    0.153605] node 0 link 0: mmio [e0000000, efffffff]
[    0.153609] node 0 link 0: mmio [80000000, dfffffff]
[    0.153612] bus: [00, ff] on node 0 link 0
[    0.153615] bus: 00 index 0 [io  0x0000-0xffff]
[    0.153618] bus: 00 index 1 [mem 0x80000000-0xffffffff]
[    0.153621] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.153656] ACPI: bus type pci registered
[    0.153730] PCI: MMCONFIG for domain 0000 [bus 00-1a] at [mem 0xe0000000-0xe1afffff] (base 0xe0000000)
[    0.153734] PCI: MMCONFIG at [mem 0xe0000000-0xe1afffff] reserved in E820
[    0.153737] PCI: Using MMCONFIG for extended config space
[    0.153739] PCI: Using configuration type 1 for base access
[    0.168075] bio: create slab <bio-0> at 0
[    0.168189] ACPI: Added _OSI(Module Device)
[    0.168191] ACPI: Added _OSI(Processor Device)
[    0.168194] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.168196] ACPI: Added _OSI(Processor Aggregator Device)
[    0.169552] ACPI: EC: Look up EC in DSDT
[    0.170283] ACPI Error: No handler for Region [ERAM] (f4421f90) [EmbeddedControl] (20110623/evregion-373)
[    0.170290] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20110623/exfldio-292)
[    0.170296] ACPI Error: Method parse/execution failed [\_SB_.HTEV] (Node f4420e10), AE_NOT_EXIST (20110623/psparse-536)
[    0.170306] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_._REG] (Node f4429d08), AE_NOT_EXIST (20110623/psparse-536)
[    0.170306] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.180056] ACPI: Interpreter enabled
[    0.180062] ACPI: (supports S0 S3 S4 S5)
[    0.180081] ACPI: Using IOAPIC for interrupt routing
[    0.180766] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.272404] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.272811] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.272979] ACPI: No dock devices found.
[    0.272981] HEST: Table not found.
[    0.272985] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.273836] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.275476] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.275480] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d1fff]
[    0.275483] pci_root PNP0A08:00: host bridge window [mem 0x000d2000-0x000d3fff]
[    0.275487] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d5fff]
[    0.275490] pci_root PNP0A08:00: host bridge window [mem 0x000d6000-0x000d7fff]
[    0.275493] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000d9fff]
[    0.275496] pci_root PNP0A08:00: host bridge window [mem 0x000da000-0x000dbfff]
[    0.275500] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000ddfff]
[    0.275503] pci_root PNP0A08:00: host bridge window [mem 0x000de000-0x000dffff]
[    0.275507] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff]
[    0.275510] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
[    0.275514] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.275517] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.275533] pci 0000:00:00.0: [1002:7910] type 0 class 0x000600
[    0.275565] pci 0000:00:01.0: [1002:7912] type 1 class 0x000604
[    0.275612] pci 0000:00:05.0: [1002:7915] type 1 class 0x000604
[    0.275650] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.275654] pci 0000:00:05.0: PME# disabled
[    0.275670] pci 0000:00:06.0: [1002:7916] type 1 class 0x000604
[    0.275706] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.275710] pci 0000:00:06.0: PME# disabled
[    0.275726] pci 0000:00:07.0: [1002:7917] type 1 class 0x000604
[    0.275763] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.275766] pci 0000:00:07.0: PME# disabled
[    0.275803] pci 0000:00:12.0: [1002:4380] type 0 class 0x000101
[    0.275823] pci 0000:00:12.0: reg 10: [io  0x8440-0x8447]
[    0.275835] pci 0000:00:12.0: reg 14: [io  0x8434-0x8437]
[    0.275847] pci 0000:00:12.0: reg 18: [io  0x8438-0x843f]
[    0.275859] pci 0000:00:12.0: reg 1c: [io  0x8430-0x8433]
[    0.275870] pci 0000:00:12.0: reg 20: [io  0x8400-0x840f]
[    0.275882] pci 0000:00:12.0: reg 24: [mem 0xf8709000-0xf87093ff]
[    0.275906] pci 0000:00:12.0: set SATA to AHCI mode
[    0.275950] pci 0000:00:13.0: [1002:4387] type 0 class 0x000c03
[    0.275966] pci 0000:00:13.0: reg 10: [mem 0xf8704000-0xf8704fff]
[    0.276053] pci 0000:00:13.1: [1002:4388] type 0 class 0x000c03
[    0.276070] pci 0000:00:13.1: reg 10: [mem 0xf8705000-0xf8705fff]
[    0.276146] pci 0000:00:13.2: [1002:4389] type 0 class 0x000c03
[    0.276162] pci 0000:00:13.2: reg 10: [mem 0xf8706000-0xf8706fff]
[    0.276238] pci 0000:00:13.3: [1002:438a] type 0 class 0x000c03
[    0.276254] pci 0000:00:13.3: reg 10: [mem 0xf8707000-0xf8707fff]
[    0.276329] pci 0000:00:13.4: [1002:438b] type 0 class 0x000c03
[    0.276346] pci 0000:00:13.4: reg 10: [mem 0xf8708000-0xf8708fff]
[    0.276428] pci 0000:00:13.5: [1002:4386] type 0 class 0x000c03
[    0.276450] pci 0000:00:13.5: reg 10: [mem 0xf8709400-0xf87094ff]
[    0.276546] pci 0000:00:13.5: supports D1 D2
[    0.276548] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.276554] pci 0000:00:13.5: PME# disabled
[    0.276579] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.276605] pci 0000:00:14.0: reg 10: [io  0x8410-0x841f]
[    0.276701] pci 0000:00:14.1: [1002:438c] type 0 class 0x000101
[    0.276717] pci 0000:00:14.1: reg 10: [io  0x01f0-0x01f7]
[    0.276728] pci 0000:00:14.1: reg 14: [io  0x03f4-0x03f7]
[    0.276740] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.276752] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.276763] pci 0000:00:14.1: reg 20: [io  0x8420-0x842f]
[    0.276811] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.276836] pci 0000:00:14.2: reg 10: [mem 0xf8700000-0xf8703fff 64bit]
[    0.276913] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.276918] pci 0000:00:14.2: PME# disabled
[    0.276934] pci 0000:00:14.3: [1002:438d] type 0 class 0x000601
[    0.277020] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.277075] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.277100] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.277118] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.277140] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.277192] pci 0000:01:05.0: [1002:791f] type 0 class 0x000300
[    0.277203] pci 0000:01:05.0: reg 10: [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.277212] pci 0000:01:05.0: reg 18: [mem 0xf8100000-0xf810ffff 64bit]
[    0.277218] pci 0000:01:05.0: reg 20: [io  0x9000-0x90ff]
[    0.277224] pci 0000:01:05.0: reg 24: [mem 0xf8000000-0xf80fffff]
[    0.277243] pci 0000:01:05.0: supports D1 D2
[    0.277260] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.277265] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.277269] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xf81fffff]
[    0.277274] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.277300] pci 0000:00:05.0: PCI bridge to [bus 08-0d]
[    0.277352] pci 0000:0e:00.0: [10ec:8136] type 0 class 0x000200
[    0.277369] pci 0000:0e:00.0: reg 10: [io  0xa000-0xa0ff]
[    0.277395] pci 0000:0e:00.0: reg 18: [mem 0xf8300000-0xf8300fff 64bit]
[    0.277427] pci 0000:0e:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.277493] pci 0000:0e:00.0: supports D1 D2
[    0.277496] pci 0000:0e:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.277501] pci 0000:0e:00.0: PME# disabled
[    0.277522] pci 0000:0e:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.277532] pci 0000:00:06.0: PCI bridge to [bus 0e-0e]
[    0.277537] pci 0000:00:06.0:   bridge window [io  0xa000-0xafff]
[    0.277541] pci 0000:00:06.0:   bridge window [mem 0xf8300000-0xf83fffff]
[    0.277585] pci 0000:14:00.0: [168c:001c] type 0 class 0x000200
[    0.277605] pci 0000:14:00.0: reg 10: [mem 0xf8200000-0xf820ffff 64bit]
[    0.277714] pci 0000:14:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.277723] pci 0000:00:07.0: PCI bridge to [bus 14-14]
[    0.277728] pci 0000:00:07.0:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.277770] pci 0000:1a:04.0: [104c:8039] type 2 class 0x000607
[    0.277795] pci 0000:1a:04.0: reg 10: [mem 0xf8404000-0xf8404fff]
[    0.277837] pci 0000:1a:04.0: supports D1 D2
[    0.277840] pci 0000:1a:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.277846] pci 0000:1a:04.0: PME# disabled
[    0.277871] pci 0000:1a:04.1: [104c:803a] type 0 class 0x000c00
[    0.277897] pci 0000:1a:04.1: reg 10: [mem 0xf8406000-0xf84067ff]
[    0.277912] pci 0000:1a:04.1: reg 14: [mem 0xf8400000-0xf8403fff]
[    0.278013] pci 0000:1a:04.1: supports D1 D2
[    0.278016] pci 0000:1a:04.1: PME# supported from D0 D1 D2 D3hot
[    0.278022] pci 0000:1a:04.1: PME# disabled
[    0.278047] pci 0000:1a:04.2: [104c:803b] type 0 class 0x000180
[    0.278071] pci 0000:1a:04.2: reg 10: [mem 0xf8405000-0xf8405fff]
[    0.278180] pci 0000:1a:04.2: supports D1 D2
[    0.278183] pci 0000:1a:04.2: PME# supported from D0 D1 D2 D3hot
[    0.278188] pci 0000:1a:04.2: PME# disabled
[    0.278213] pci 0000:1a:04.3: [104c:803c] type 0 class 0x000805
[    0.278237] pci 0000:1a:04.3: reg 10: [mem 0xf8406800-0xf84068ff]
[    0.278345] pci 0000:1a:04.3: supports D1 D2
[    0.278347] pci 0000:1a:04.3: PME# supported from D0 D1 D2 D3hot
[    0.278353] pci 0000:1a:04.3: PME# disabled
[    0.278415] pci 0000:00:14.4: PCI bridge to [bus 1a-1b] (subtractive decode)
[    0.278423] pci 0000:00:14.4:   bridge window [mem 0xf8400000-0xf84fffff]
[    0.278430] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.278433] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d1fff] (subtractive decode)
[    0.278437] pci 0000:00:14.4:   bridge window [mem 0x000d2000-0x000d3fff] (subtractive decode)
[    0.278440] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d5fff] (subtractive decode)
[    0.278444] pci 0000:00:14.4:   bridge window [mem 0x000d6000-0x000d7fff] (subtractive decode)
[    0.278447] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000d9fff] (subtractive decode)
[    0.278451] pci 0000:00:14.4:   bridge window [mem 0x000da000-0x000dbfff] (subtractive decode)
[    0.278455] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000ddfff] (subtractive decode)
[    0.278458] pci 0000:00:14.4:   bridge window [mem 0x000de000-0x000dffff] (subtractive decode)
[    0.278462] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xdfffffff] (subtractive decode)
[    0.278465] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.278469] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.278473] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.278528] pci_bus 0000:1b: [bus 1b-1e] partially hidden behind transparent bridge 0000:1a [bus 1a-1b]
[    0.278546] pci_bus 0000:00: on NUMA node 0
[    0.278550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.278641] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.278687] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.278728] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.278771] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BB5_._PRT]
[    0.278847] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.278901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.278950]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.278975]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.284643] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.284695] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.284742] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.284795] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.284842] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.284892] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.284939] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.284985] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.285125] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.285132] vgaarb: loaded
[    0.285133] vgaarb: bridge control possible 0000:01:05.0
[    0.285301] i2c-core: driver [aat2870] using legacy suspend method
[    0.285303] i2c-core: driver [aat2870] using legacy resume method
[    0.285405] SCSI subsystem initialized
[    0.288017] libata version 3.00 loaded.
[    0.288017] usbcore: registered new interface driver usbfs
[    0.288017] usbcore: registered new interface driver hub
[    0.288017] usbcore: registered new device driver usb
[    0.288017] PCI: Using ACPI for IRQ routing
[    0.288017] PCI: pci_cache_line_size set to 64 bytes
[    0.288017] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.288017] reserve RAM buffer: 0000000077e70000 - 0000000077ffffff 
[    0.288017] NetLabel: Initializing
[    0.288017] NetLabel:  domain hash size = 128
[    0.288017] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.288017] NetLabel:  unlabeled traffic allowed by default
[    0.288017] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.288017] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.288077] Switching to clocksource hpet
[    0.301081] AppArmor: AppArmor Filesystem Enabled
[    0.301118] pnp: PnP ACPI init
[    0.301140] ACPI: bus type pnp registered
[    0.302068] pnp 00:00: [bus 00-ff]
[    0.302072] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.302075] pnp 00:00: [mem 0x000c0000-0x000c1fff window]
[    0.302078] pnp 00:00: [mem 0x000c2000-0x000c3fff window]
[    0.302082] pnp 00:00: [mem 0x000c4000-0x000c5fff window]
[    0.302085] pnp 00:00: [mem 0x000c6000-0x000c7fff window]
[    0.302088] pnp 00:00: [mem 0x000c8000-0x000c9fff window]
[    0.302091] pnp 00:00: [mem 0x000ca000-0x000cbfff window]
[    0.302094] pnp 00:00: [mem 0x000cc000-0x000cdfff window]
[    0.302097] pnp 00:00: [mem 0x000ce000-0x000cffff window]
[    0.302100] pnp 00:00: [mem 0x000d0000-0x000d1fff window]
[    0.302103] pnp 00:00: [mem 0x000d2000-0x000d3fff window]
[    0.302106] pnp 00:00: [mem 0x000d4000-0x000d5fff window]
[    0.302109] pnp 00:00: [mem 0x000d6000-0x000d7fff window]
[    0.302112] pnp 00:00: [mem 0x000d8000-0x000d9fff window]
[    0.302115] pnp 00:00: [mem 0x000da000-0x000dbfff window]
[    0.302118] pnp 00:00: [mem 0x000dc000-0x000ddfff window]
[    0.302121] pnp 00:00: [mem 0x000de000-0x000dffff window]
[    0.302124] pnp 00:00: [mem 0x000e0000-0x000e1fff window]
[    0.302127] pnp 00:00: [mem 0x000e2000-0x000e3fff window]
[    0.302131] pnp 00:00: [mem 0x000e4000-0x000e5fff window]
[    0.302134] pnp 00:00: [mem 0x000e6000-0x000e7fff window]
[    0.302137] pnp 00:00: [mem 0x000e8000-0x000e9fff window]
[    0.302140] pnp 00:00: [mem 0x000ea000-0x000ebfff window]
[    0.302143] pnp 00:00: [mem 0x000ec000-0x000edfff window]
[    0.302148] pnp 00:00: [mem 0x000ee000-0x000effff window]
[    0.302152] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.302155] pnp 00:00: [mem 0xf0000000-0xffffffff window]
[    0.302158] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.302161] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.302164] pnp 00:00: [io  0x0d00-0xffff window]
[    0.302242] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.302295] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.302298] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.302371] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.302375] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.302379] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.302752] pnp 00:02: [io  0x0000-0x001f]
[    0.302755] pnp 00:02: [io  0x0080-0x008f]
[    0.302758] pnp 00:02: [io  0x00c0-0x00df]
[    0.302761] pnp 00:02: [dma 4]
[    0.302803] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.302813] pnp 00:03: [io  0x00f0-0x00fe]
[    0.302829] pnp 00:03: [irq 13]
[    0.302872] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.302884] pnp 00:04: [io  0x0070-0x0071]
[    0.302893] pnp 00:04: [irq 8]
[    0.302934] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.302944] pnp 00:05: [io  0x0061]
[    0.302984] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.302995] pnp 00:06: [io  0x0060]
[    0.302998] pnp 00:06: [io  0x0064]
[    0.303006] pnp 00:06: [irq 1]
[    0.303050] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.303066] pnp 00:07: [irq 12]
[    0.303110] pnp 00:07: Plug and Play ACPI device, IDs SYN0705 SYN0700 SYN0002 PNP0f13 (active)
[    0.303127] pnp 00:08: [io  0x0022-0x0023]
[    0.303130] pnp 00:08: [io  0x002e-0x002f]
[    0.303133] pnp 00:08: [io  0x0072-0x0073]
[    0.303135] pnp 00:08: [io  0x1080]
[    0.303138] pnp 00:08: [io  0x00b0-0x00b1]
[    0.303140] pnp 00:08: [io  0x0092]
[    0.303143] pnp 00:08: [io  0x0220-0x022f]
[    0.303145] pnp 00:08: [io  0x040b]
[    0.303148] pnp 00:08: [io  0x04d0-0x04d1]
[    0.303150] pnp 00:08: [io  0x04d6]
[    0.303153] pnp 00:08: [io  0x0530-0x0537]
[    0.303156] pnp 00:08: [io  0x0c00-0x0c01]
[    0.303158] pnp 00:08: [io  0x0c14]
[    0.303161] pnp 00:08: [io  0x0c50-0x0c52]
[    0.303163] pnp 00:08: [io  0x0c6c]
[    0.303166] pnp 00:08: [io  0x0c6f]
[    0.303168] pnp 00:08: [io  0x0cd0-0x0cd1]
[    0.303171] pnp 00:08: [io  0x0cd2-0x0cd3]
[    0.303174] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.303176] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.303179] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.303182] pnp 00:08: [io  0x8000-0x805f]
[    0.303185] pnp 00:08: [io  0x8100-0x81ff window]
[    0.303188] pnp 00:08: [io  0x8200-0x82ff window]
[    0.303190] pnp 00:08: [io  0x0f40-0x0f47]
[    0.303193] pnp 00:08: [io  0x087f]
[    0.303195] pnp 00:08: [io  0xfd60-0xfddf]
[    0.303292] system 00:08: [io  0x1080] has been reserved
[    0.303296] system 00:08: [io  0x0220-0x022f] has been reserved
[    0.303300] system 00:08: [io  0x040b] has been reserved
[    0.303303] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.303306] system 00:08: [io  0x04d6] has been reserved
[    0.303310] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.303313] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.303316] system 00:08: [io  0x0c14] has been reserved
[    0.303320] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.303323] system 00:08: [io  0x0c6c] has been reserved
[    0.303326] system 00:08: [io  0x0c6f] has been reserved
[    0.303330] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.303333] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.303337] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.303340] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.303344] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.303347] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.303351] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.303354] system 00:08: [io  0x8200-0x82ff window] has been reserved
[    0.303358] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.303361] system 00:08: [io  0x087f] has been reserved
[    0.303365] system 00:08: [io  0xfd60-0xfddf] has been reserved
[    0.303368] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.303415] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.303418] pnp 00:09: [mem 0xfff00000-0xffffffff]
[    0.303421] pnp 00:09: [mem 0x00000000-0xffffffff disabled]
[    0.303492] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.303496] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
[    0.303500] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.303599] pnp 00:0a: [mem 0xfed00000-0xfed003ff]
[    0.303644] pnp 00:0a: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.324085] pnp: PnP ACPI: found 11 devices
[    0.324087] ACPI: ACPI bus type pnp unregistered
[    0.324090] PnPBIOS: Disabled by ACPI PNP
[    0.360986] PCI: max bus depth: 2 pci_try_num: 3
[    0.361026] pci 0000:00:06.0: BAR 15: assigned [mem 0x80000000-0x800fffff pref]
[    0.361032] pci 0000:00:14.4: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.361038] pci 0000:00:14.4: BAR 13: assigned [io  0x2000-0x2fff]
[    0.361043] pci 0000:00:05.0: BAR 14: assigned [mem 0x80100000-0x802fffff]
[    0.361048] pci 0000:00:05.0: BAR 15: assigned [mem 0x80300000-0x804fffff 64bit pref]
[    0.361053] pci 0000:00:05.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.361057] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.361061] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.361065] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xf81fffff]
[    0.361069] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.361074] pci 0000:00:05.0: PCI bridge to [bus 08-0d]
[    0.361077] pci 0000:00:05.0:   bridge window [io  0x3000-0x3fff]
[    0.361081] pci 0000:00:05.0:   bridge window [mem 0x80100000-0x802fffff]
[    0.361085] pci 0000:00:05.0:   bridge window [mem 0x80300000-0x804fffff 64bit pref]
[    0.361091] pci 0000:0e:00.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.361094] pci 0000:00:06.0: PCI bridge to [bus 0e-0e]
[    0.361097] pci 0000:00:06.0:   bridge window [io  0xa000-0xafff]
[    0.361101] pci 0000:00:06.0:   bridge window [mem 0xf8300000-0xf83fffff]
[    0.361105] pci 0000:00:06.0:   bridge window [mem 0x80000000-0x800fffff pref]
[    0.361110] pci 0000:00:07.0: PCI bridge to [bus 14-14]
[    0.361114] pci 0000:00:07.0:   bridge window [mem 0xf8200000-0xf82fffff]
[    0.361123] pci 0000:1a:04.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.361127] pci 0000:1a:04.0: BAR 15: assigned [mem 0x84000000-0x87ffffff pref]
[    0.361130] pci 0000:1a:04.0: BAR 14: assigned [io  0x2000-0x20ff]
[    0.361134] pci 0000:1a:04.0: BAR 13: assigned [io  0x2400-0x24ff]
[    0.361137] pci 0000:1a:04.0: CardBus bridge to [bus 1b-1e]
[    0.361140] pci 0000:1a:04.0:   bridge window [io  0x2400-0x24ff]
[    0.361149] pci 0000:1a:04.0:   bridge window [io  0x2000-0x20ff]
[    0.361156] pci 0000:1a:04.0:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.361162] pci 0000:1a:04.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.361169] pci 0000:00:14.4: PCI bridge to [bus 1a-1b]
[    0.361173] pci 0000:00:14.4:   bridge window [io  0x2000-0x2fff]
[    0.361179] pci 0000:00:14.4:   bridge window [mem 0xf8400000-0xf84fffff]
[    0.361185] pci 0000:00:14.4:   bridge window [mem 0x84000000-0x87ffffff pref]
[    0.361200] pci 0000:00:05.0: enabling device (0000 -> 0003)
[    0.361205] pci 0000:00:05.0: setting latency timer to 64
[    0.361210] pci 0000:00:06.0: setting latency timer to 64
[    0.361216] pci 0000:00:07.0: setting latency timer to 64
[    0.361239] pci 0000:1a:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.361247] pci_bus 0000:00: resource 4 [mem 0x000a0000-0x000bffff]
[    0.361250] pci_bus 0000:00: resource 5 [mem 0x000d0000-0x000d1fff]
[    0.361253] pci_bus 0000:00: resource 6 [mem 0x000d2000-0x000d3fff]
[    0.361256] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d5fff]
[    0.361260] pci_bus 0000:00: resource 8 [mem 0x000d6000-0x000d7fff]
[    0.361263] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000d9fff]
[    0.361266] pci_bus 0000:00: resource 10 [mem 0x000da000-0x000dbfff]
[    0.361269] pci_bus 0000:00: resource 11 [mem 0x000dc000-0x000ddfff]
[    0.361272] pci_bus 0000:00: resource 12 [mem 0x000de000-0x000dffff]
[    0.361275] pci_bus 0000:00: resource 13 [mem 0x80000000-0xdfffffff]
[    0.361278] pci_bus 0000:00: resource 14 [mem 0xf0000000-0xffffffff]
[    0.361282] pci_bus 0000:00: resource 15 [io  0x0000-0x0cf7]
[    0.361285] pci_bus 0000:00: resource 16 [io  0x0d00-0xffff]
[    0.361288] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.361291] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xf81fffff]
[    0.361294] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
[    0.361298] pci_bus 0000:08: resource 0 [io  0x3000-0x3fff]
[    0.361301] pci_bus 0000:08: resource 1 [mem 0x80100000-0x802fffff]
[    0.361304] pci_bus 0000:08: resource 2 [mem 0x80300000-0x804fffff 64bit pref]
[    0.361308] pci_bus 0000:0e: resource 0 [io  0xa000-0xafff]
[    0.361311] pci_bus 0000:0e: resource 1 [mem 0xf8300000-0xf83fffff]
[    0.361314] pci_bus 0000:0e: resource 2 [mem 0x80000000-0x800fffff pref]
[    0.361317] pci_bus 0000:14: resource 1 [mem 0xf8200000-0xf82fffff]
[    0.361321] pci_bus 0000:1a: resource 0 [io  0x2000-0x2fff]
[    0.361324] pci_bus 0000:1a: resource 1 [mem 0xf8400000-0xf84fffff]
[    0.361327] pci_bus 0000:1a: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.361330] pci_bus 0000:1a: resource 4 [mem 0x000a0000-0x000bffff]
[    0.361333] pci_bus 0000:1a: resource 5 [mem 0x000d0000-0x000d1fff]
[    0.361336] pci_bus 0000:1a: resource 6 [mem 0x000d2000-0x000d3fff]
[    0.361340] pci_bus 0000:1a: resource 7 [mem 0x000d4000-0x000d5fff]
[    0.361343] pci_bus 0000:1a: resource 8 [mem 0x000d6000-0x000d7fff]
[    0.361346] pci_bus 0000:1a: resource 9 [mem 0x000d8000-0x000d9fff]
[    0.361349] pci_bus 0000:1a: resource 10 [mem 0x000da000-0x000dbfff]
[    0.361352] pci_bus 0000:1a: resource 11 [mem 0x000dc000-0x000ddfff]
[    0.361355] pci_bus 0000:1a: resource 12 [mem 0x000de000-0x000dffff]
[    0.361358] pci_bus 0000:1a: resource 13 [mem 0x80000000-0xdfffffff]
[    0.361362] pci_bus 0000:1a: resource 14 [mem 0xf0000000-0xffffffff]
[    0.361365] pci_bus 0000:1a: resource 15 [io  0x0000-0x0cf7]
[    0.361368] pci_bus 0000:1a: resource 16 [io  0x0d00-0xffff]
[    0.361371] pci_bus 0000:1b: resource 0 [io  0x2400-0x24ff]
[    0.361374] pci_bus 0000:1b: resource 1 [io  0x2000-0x20ff]
[    0.361377] pci_bus 0000:1b: resource 2 [mem 0x84000000-0x87ffffff pref]
[    0.361380] pci_bus 0000:1b: resource 3 [mem 0x88000000-0x8bffffff]
[    0.361427] NET: Registered protocol family 2
[    0.361498] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.361797] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.362455] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.362781] TCP: Hash tables configured (established 131072 bind 65536)
[    0.362784] TCP reno registered
[    0.362788] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.362798] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.362901] NET: Registered protocol family 1
[    0.362950] pci 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.362980] pci 0000:00:13.0: PCI INT A disabled
[    0.362993] pci 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.363009] pci 0000:00:13.1: PCI INT B disabled
[    0.363021] pci 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.363037] pci 0000:00:13.2: PCI INT C disabled
[    0.363045] pci 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.363060] pci 0000:00:13.3: PCI INT B disabled
[    0.363069] pci 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.363085] pci 0000:00:13.4: PCI INT C disabled
[    0.363098] pci 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.363115] pci 0000:00:13.5: PCI INT D disabled
[    0.363141] pci 0000:01:05.0: Boot video device
[    0.363163] PCI: CLS 32 bytes, default 64
[    0.363655] audit: initializing netlink socket (disabled)
[    0.363666] type=2000 audit(1343150731.356:1): initialized
[    0.394519] highmem bounce pool size: 64 pages
[    0.394526] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.407823] VFS: Disk quotas dquot_6.5.2
[    0.407908] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.408636] fuse init (API version 7.17)
[    0.408749] msgmni has been set to 1681
[    0.409130] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.409165] io scheduler noop registered
[    0.409168] io scheduler deadline registered
[    0.409176] io scheduler cfq registered (default)
[    0.409350] pcieport 0000:00:05.0: setting latency timer to 64
[    0.409383] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    0.409469] pcieport 0000:00:06.0: setting latency timer to 64
[    0.409493] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    0.409556] pcieport 0000:00:07.0: setting latency timer to 64
[    0.409580] pcieport 0000:00:07.0: irq 42 for MSI/MSI-X
[    0.409676] pcieport 0000:00:05.0: Signaling PME through PCIe PME interrupt
[    0.409681] pcie_pme 0000:00:05.0:pcie01: service driver pcie_pme loaded
[    0.409696] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
[    0.409699] pci 0000:0e:00.0: Signaling PME through PCIe PME interrupt
[    0.409703] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
[    0.409721] pcieport 0000:00:07.0: Signaling PME through PCIe PME interrupt
[    0.409724] pci 0000:14:00.0: Signaling PME through PCIe PME interrupt
[    0.409728] pcie_pme 0000:00:07.0:pcie01: service driver pcie_pme loaded
[    0.409752] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.409800] pciehp 0000:00:05.0:pcie04: HPC vendor_id 1002 device_id 7915 ss_vid 1179 ss_did ff00
[    0.409822] pciehp 0000:00:05.0:pcie04: service driver pciehp loaded
[    0.409833] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.412075] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.415885] ACPI: AC Adapter [ACAD] (on-line)
[    0.415959] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.415988] ACPI: Lid Switch [LID]
[    0.416060] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.416065] ACPI: Power Button [PWRB]
[    0.416129] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.416133] ACPI: Power Button [PWRF]
[    0.416217] ACPI: processor limited to max C-state 1
[    0.440259] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.440270] ACPI: Battery Slot [BAT1] (battery present)
[    0.440301] ERST: Table is not found!
[    0.440303] GHES: HEST is not enabled!
[    0.440400] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.440608] isapnp: Scanning for PnP cards...
[    0.537967] Freeing initrd memory: 13784k freed
[    0.569497] ACPI: Battery Slot [BAT1] (battery present)
[    0.797234] isapnp: No Plug & Play device found
[    0.852554] Linux agpgart interface v0.103
[    0.855085] brd: module loaded
[    0.856275] loop: module loaded
[    0.856424] ahci 0000:00:12.0: version 3.0
[    0.856452] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.856479] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    0.856583] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    0.856588] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.857653] scsi0 : ahci
[    0.857829] scsi1 : ahci
[    0.857967] scsi2 : ahci
[    0.858093] scsi3 : ahci
[    0.858259] ata1: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709100 irq 22
[    0.858264] ata2: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709180 irq 22
[    0.858269] ata3: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709200 irq 22
[    0.858273] ata4: SATA max UDMA/133 abar m1024@0xf8709000 port 0xf8709280 irq 22
[    0.858479] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.858520] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.859031] Fixed MDIO Bus: probed
[    0.859060] tun: Universal TUN/TAP device driver, 1.6
[    0.859062] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.859157] PPP generic driver version 2.4.2
[    0.859325] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.859342] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.859362] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.859427] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.859458] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.859475] ehci_hcd 0000:00:13.5: debug port 1
[    0.859501] ehci_hcd 0000:00:13.5: irq 19, io mem 0xf8709400
[    0.868031] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.868236] hub 1-0:1.0: USB hub found
[    0.868242] hub 1-0:1.0: 10 ports detected
[    0.868365] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.868383] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.868396] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.868465] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.868492] ohci_hcd 0000:00:13.0: irq 16, io mem 0xf8704000
[    0.924213] hub 2-0:1.0: USB hub found
[    0.924224] hub 2-0:1.0: 2 ports detected
[    0.924302] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.924314] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.924385] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.924411] ohci_hcd 0000:00:13.1: irq 17, io mem 0xf8705000
[    0.980209] hub 3-0:1.0: USB hub found
[    0.980220] hub 3-0:1.0: 2 ports detected
[    0.980299] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.980312] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.980376] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.980405] ohci_hcd 0000:00:13.2: irq 18, io mem 0xf8706000
[    1.036225] hub 4-0:1.0: USB hub found
[    1.036236] hub 4-0:1.0: 2 ports detected
[    1.036321] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.036334] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    1.036397] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    1.036415] ohci_hcd 0000:00:13.3: irq 17, io mem 0xf8707000
[    1.092222] hub 5-0:1.0: USB hub found
[    1.092233] hub 5-0:1.0: 2 ports detected
[    1.092311] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.092323] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    1.092390] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    1.092408] ohci_hcd 0000:00:13.4: irq 18, io mem 0xf8708000
[    1.148210] hub 6-0:1.0: USB hub found
[    1.148221] hub 6-0:1.0: 2 ports detected
[    1.148302] uhci_hcd: USB Universal Host Controller Interface driver
[    1.148395] usbcore: registered new interface driver libusual
[    1.148452] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.174457] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.174464] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.174658] mousedev: PS/2 mouse device common for all mice
[    1.175632] rtc_cmos 00:04: RTC can wake from S4
[    1.175768] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.175798] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.175891] device-mapper: uevent: version 1.0.3
[    1.175999] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.176055] EISA: Probing bus 0 at eisa.0
[    1.176058] EISA: Cannot allocate resource for mainboard
[    1.176061] Cannot allocate resource for EISA slot 1
[    1.176064] Cannot allocate resource for EISA slot 2
[    1.176067] Cannot allocate resource for EISA slot 3
[    1.176073] ata4: SATA link down (SStatus 0 SControl 300)
[    1.176078] Cannot allocate resource for EISA slot 4
[    1.176081] Cannot allocate resource for EISA slot 5
[    1.176084] Cannot allocate resource for EISA slot 6
[    1.176087] Cannot allocate resource for EISA slot 7
[    1.176096] Cannot allocate resource for EISA slot 8
[    1.176099] EISA: Detected 0 cards.
[    1.176111] cpufreq-nforce2: No nForce2 chipset.
[    1.176114] ata2: SATA link down (SStatus 0 SControl 300)
[    1.176119] cpuidle: using governor ladder
[    1.176121] cpuidle: using governor menu
[    1.176124] EFI Variables Facility v0.08 2004-May-17
[    1.176151] ata3: SATA link down (SStatus 0 SControl 300)
[    1.176430] TCP cubic registered
[    1.176590] NET: Registered protocol family 10
[    1.177239] NET: Registered protocol family 17
[    1.177258] Registering the dns_resolver key type
[    1.177297] Using IPI No-Shortcut mode
[    1.177456] PM: Hibernation image not present or could not be loaded.
[    1.177469] registered taskstats version 1
[    1.182644] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.190911]   Magic number: 4:986:441
[    1.191022] rtc_cmos 00:04: setting system clock to 2012-07-24 17:25:33 UTC (1343150733)
[    1.191032] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 (2 cpu cores) (version 2.20.00)
[    1.191077] powernow-k8: fid 0xc (2000 MHz), vid 0x11
[    1.191079] powernow-k8: fid 0xa (1800 MHz), vid 0x12
[    1.191081] powernow-k8: fid 0x8 (1600 MHz), vid 0x13
[    1.191084] powernow-k8: fid 0x0 (800 MHz), vid 0x1e
[    1.191168] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.191172] EDD information not available.
[    1.196683] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.316134] Initializing USB Mass Storage driver...
[    1.316309] scsi4 : usb-storage 1-1:1.0
[    1.316399] usbcore: registered new interface driver usb-storage
[    1.316401] USB Mass Storage support registered.
[    1.352042] ata1: softreset failed (device not ready)
[    1.352046] ata1: applying PMP SRST workaround and retrying
[    1.524047] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.525172] ata1.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC33P, max UDMA/133
[    1.525176] ata1.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.525180] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.526482] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.526486] ata1.00: configured for UDMA/133
[    1.526690] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BBCO PQ: 0 ANSI: 5
[    1.526854] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.526894] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.526912] sd 0:0:0:0: [sda] Write Protect is off
[    1.526916] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.526940] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.632036] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    1.855015]  sda: sda1 sda2 sda3 sda4
[    1.855621] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.855638] Freeing unused kernel memory: 712k freed
[    1.856143] Write protecting the kernel text: 5628k
[    1.856195] Write protecting the kernel read-only data: 2324k
[    1.878063] udevd[99]: starting version 175
[    1.985132] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.985157] r8169 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.985187] r8169 0000:0e:00.0: setting latency timer to 64
[    1.985255] r8169 0000:0e:00.0: irq 43 for MSI/MSI-X
[    1.987867] r8169 0000:0e:00.0: eth0: RTL8101e at 0xf8032000, 00:1e:ec:05:64:90, XID 94200000 IRQ 43
[    1.995898] scsi5 : pata_atiixp
[    1.997844] input: 2.4G Wireless Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input4
[    1.998102] generic-usb 0003:04F3:02F4.0001: input,hiddev0,hidraw0: USB HID v1.11 Mouse [2.4G Wireless Mouse] on usb-0000:00:13.1-1/input0
[    1.998130] usbcore: registered new interface driver usbhid
[    1.998132] usbhid: USB HID core driver
[    2.001329] scsi6 : pata_atiixp
[    2.001898] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    2.001902] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    2.019102] sdhci: Secure Digital Host Controller Interface driver
[    2.019106] sdhci: Copyright(c) Pierre Ossman
[    2.180520] ata5.00: ATAPI: TSSTcorp CDDVDW TS-L632H, TO01, max UDMA/33
[    2.212547] ata5.00: configured for UDMA/33
[    2.217198] scsi 5:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  TO01 PQ: 0 ANSI: 5
[    2.225326] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.225330] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.225510] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    2.225679] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    2.226327] sdhci-pci 0000:1a:04.3: SDHCI controller found [104c:803c] (rev 0)
[    2.226350] sdhci-pci 0000:1a:04.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.226395] mmc0: no vmmc regulator found
[    2.226445] Registered led device: mmc0::
[    2.227536] mmc0: SDHCI controller on PCI [0000:1a:04.3] using DMA
[    2.228645] firewire_ohci 0000:1a:04.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.284122] firewire_ohci: Added fw-ohci device 0000:1a:04.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.317004] scsi 4:0:0:0: Direct-Access     Lexar    JD FireFly       1100 PQ: 0 ANSI: 0 CCS
[    2.317939] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.318493] sd 4:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[    2.319109] sd 4:0:0:0: [sdb] Write Protect is off
[    2.319114] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    2.319751] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.319756] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.322611] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.322615] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.323291]  sdb: sdb1
[    2.325603] sd 4:0:0:0: [sdb] No Caching mode page present
[    2.325606] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    2.325610] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    2.346295] EXT3-fs (sda1): recovery required on readonly filesystem
[    2.346300] EXT3-fs (sda1): write access will be enabled during recovery
[    2.506376] kjournald starting.  Commit interval 5 seconds
[    2.506422] EXT3-fs (sda1): recovery complete
[    2.507447] EXT3-fs (sda1): mounted filesystem with ordered data mode
[    2.784160] firewire_core: created device fw0: GUID 00023f82c0404a19, S400
[   10.461641] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.491340] udevd[327]: starting version 175
[   10.528105] lp: driver loaded but no devices found
[   10.591532] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   10.637154] acpi device:27: registered as cooling_device2
[   10.637643] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25/LNXVIDEO:01/input/input5
[   10.640078] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   10.658479] Adding 2048280k swap on /dev/sda2.  Priority:-1 extents:1 across:2048280k 
[   10.682927] wmi: Mapper loaded
[   10.687674] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[   10.687795] input: Toshiba input device as /devices/virtual/input/input6
[   10.688861] cfg80211: Calling CRDA to update world regulatory domain
[   10.688974] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.704914] Registered led device: toshiba::illumination
[   10.720237] ath5k 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.720250] ath5k 0000:14:00.0: setting latency timer to 64
[   10.720301] ath5k 0000:14:00.0: registered as 'phy0'
[   10.830024] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.832605] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   10.833154] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   10.833296] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   10.845754] EXT3-fs (sda1): using internal journal
[   10.871664] [drm] Initialized drm 1.1.0 20060810
[   10.909594] yenta_cardbus 0000:1a:04.0: CardBus bridge found [1179:ff00]
[   10.909619] yenta_cardbus 0000:1a:04.0: Enabling burst memory read transactions
[   10.909625] yenta_cardbus 0000:1a:04.0: Using CSCINT to route CSC interrupts to PCI
[   10.909629] yenta_cardbus 0000:1a:04.0: Routing CardBus interrupts to PCI
[   10.909636] yenta_cardbus 0000:1a:04.0: TI: mfunc 0x10a01b22, devctl 0x64
[   10.975406] [drm] radeon defaulting to kernel modesetting.
[   10.975410] [drm] radeon kernel modesetting enabled.
[   10.975503] radeon 0000:01:05.0: power state changed by ACPI to D0
[   10.975508] radeon 0000:01:05.0: power state changed by ACPI to D0
[   10.975517] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   10.978320] [drm] initializing kernel modesetting (RS690 0x1002:0x791F 0x1179:0xFF00).
[   10.978351] [drm] register mmio base: 0xF8100000
[   10.978353] [drm] register mmio size: 65536
[   10.978499] ATOM BIOS: ATI
[   10.978529] radeon 0000:01:05.0: VRAM: 128M 0x0000000078000000 - 0x000000007FFFFFFF (128M used)
[   10.978533] radeon 0000:01:05.0: GTT: 512M 0x0000000080000000 - 0x000000009FFFFFFF
[   10.978556] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.978558] [drm] Driver supports precise vblank timestamp query.
[   10.978571] [drm] radeon: irq initialized.
[   11.175803] [drm] Detected VRAM RAM=128M, BAR=128M
[   11.175807] [drm] RAM width 128bits DDR
[   11.216276] [TTM] Zone  kernel: Available graphics memory: 437768 kiB.
[   11.216279] [TTM] Zone highmem: Available graphics memory: 965356 kiB.
[   11.216281] [TTM] Initializing pool allocator.
[   11.216311] [drm] radeon: 128M of VRAM memory ready
[   11.216314] [drm] radeon: 512M of GTT memory ready.
[   11.216341] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   11.231739] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   11.241565] [drm] PCIE GART of 512M enabled (table at 0x0000000031B80000).
[   11.243275] radeon 0000:01:05.0: WB enabled
[   11.243417] [drm] Loading RS690/RS740 Microcode
[   11.250238] ath: EEPROM regdomain: 0x65
[   11.250243] ath: EEPROM indicates we should expect a direct regpair map
[   11.250248] ath: Country alpha2 being used: 00
[   11.250250] ath: Regpair used: 0x65
[   11.255070] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   11.255077] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255080] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   11.255084] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255086] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   11.255090] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255093] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   11.255096] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255099] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   11.255102] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255105] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   11.255109] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255111] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   11.255115] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255118] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   11.255121] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255124] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   11.255127] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255130] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   11.255134] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255136] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   11.255140] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255143] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   11.255146] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255149] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   11.255152] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   11.255155] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   11.266672] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   11.295888] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   11.297010] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   11.318833] type=1400 audit(1343150743.621:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=533 comm="apparmor_parser"
[   11.319362] type=1400 audit(1343150743.621:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=533 comm="apparmor_parser"
[   11.319664] type=1400 audit(1343150743.621:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=533 comm="apparmor_parser"
[   11.321114] yenta_cardbus 0000:1a:04.0: ISA IRQ mask 0x0cf8, PCI irq 20
[   11.321121] yenta_cardbus 0000:1a:04.0: Socket status: 30000006
[   11.321125] pci_bus 0000:1a: Raising subordinate bus# of parent bus (#1a) from #1b to #1e
[   11.323719] type=1400 audit(1343150743.625:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=590 comm="apparmor_parser"
[   11.327923] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[   11.327929] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff 0x2400-0x24ff
[   11.333756] type=1400 audit(1343150743.637:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=593 comm="apparmor_parser"
[   11.337198] type=1400 audit(1343150743.641:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=593 comm="apparmor_parser"
[   11.338833] type=1400 audit(1343150743.641:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=593 comm="apparmor_parser"
[   11.343688] type=1400 audit(1343150743.645:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=596 comm="apparmor_parser"
[   11.344842] 
[   11.344848] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge window: [mem 0xf8400000-0xf84fffff]
[   11.344853] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf8400000-0xf84fffff: excluding 0xf8400000-0xf840ffff
[   11.344871] yenta_cardbus 0000:1a:04.0: pcmcia: parent PCI bridge window: [mem 0x84000000-0x87ffffff pref]
[   11.344875] pcmcia_socket pcmcia_socket0: cs: memory probe 0x84000000-0x87ffffff: excluding 0x84000000-0x87ffffff
[   11.355060] tifm_7xx1 0000:1a:04.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   11.420324] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.491773] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   11.491890] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   11.499042] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   11.499049] cfg80211: World regulatory domain updated:
[   11.499051] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.499055] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.499059] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.499062] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.499065] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.499068] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.503980] [drm] radeon: ring at 0x0000000080001000
[   11.504146] [drm] ring test succeeded in 0 usecs
[   11.504355] [drm] radeon: ib pool ready.
[   11.504431] [drm] ib test succeeded in 0 usecs
[   11.504756] [drm] Radeon Display Connectors
[   11.504759] [drm] Connector 0:
[   11.504761] [drm]   VGA
[   11.504764] [drm]   DDC: 0x7e50 0x7e40 0x7e54 0x7e44 0x7e58 0x7e48 0x7e5c 0x7e4c
[   11.504766] [drm]   Encoders:
[   11.504768] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   11.504770] [drm] Connector 1:
[   11.504772] [drm]   LVDS
[   11.504775] [drm]   DDC: 0x7e40 0x7e50 0x7e44 0x7e54 0x7e48 0x7e58 0x7e4c 0x7e5c
[   11.504777] [drm]   Encoders:
[   11.504779] [drm]     LCD1: INTERNAL_LVTM1
[   11.504781] [drm] Connector 2:
[   11.504782] [drm]   S-video
[   11.504784] [drm]   Encoders:
[   11.504786] [drm]     TV1: INTERNAL_KLDSCP_DAC1
[   11.718880] kjournald starting.  Commit interval 5 seconds
[   11.719257] EXT3-fs (sda3): using internal journal
[   11.719262] EXT3-fs (sda3): mounted filesystem with ordered data mode
[   11.895970] init: failsafe main process (707) killed by TERM signal
[   11.981049] ppdev: user-space parallel port driver
[   11.991696] type=1400 audit(1343150744.293:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=773 comm="apparmor_parser"
[   11.997757] type=1400 audit(1343150744.301:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=774 comm="apparmor_parser"
[   12.028427] Bluetooth: Core ver 2.16
[   12.028483] NET: Registered protocol family 31
[   12.028488] Bluetooth: HCI device and connection manager initialized
[   12.028495] Bluetooth: HCI socket layer initialized
[   12.028500] Bluetooth: L2CAP socket layer initialized
[   12.028511] Bluetooth: SCO socket layer initialized
[   12.050861] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.050865] Bluetooth: BNEP filters: protocol multicast
[   12.056210] Bluetooth: RFCOMM TTY layer initialized
[   12.056218] Bluetooth: RFCOMM socket layer initialized
[   12.056220] Bluetooth: RFCOMM ver 1.11
[   12.157251] [drm] fb mappable at 0xF0040000
[   12.157255] [drm] vram apper at 0xF0000000
[   12.157257] [drm] size 4096000
[   12.157259] [drm] fb depth is 24
[   12.157261] [drm]    pitch is 5120
[   12.157502] fbcon: radeondrmfb (fb0) is primary device
[   12.158616] Console: switching to colour frame buffer device 160x50
[   12.158658] fb0: radeondrmfb frame buffer device
[   12.158661] drm: registered panic notifier
[   12.158671] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   12.262877] r8169 0000:0e:00.0: eth0: link down
[   12.262891] r8169 0000:0e:00.0: eth0: link down
[   12.263174] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.263688] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.356555] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.357011] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```when i tried 
```
lspci -nnk | grep -iA2 vga > lspci.txt
```i received a message something like there was no file or directory named vga.  --  ???

Also, I noticed that when booting puppy, it says many deleted inodes are referenced in sda3.

---

### Post by NikTh on 2012-07-25
> **Subito Piano said:**
> when i tried 
```
lspci -nnk | grep -iA2 vga > lspci.txt
```i received a  message something like there was no file or directory named vga.  --   ???

Hi , 
its ok , this command shows the vga card and what driver is in use , but i can see that you have AMD and you enabled fglrx ? (additional driver). 

I cannot see something strange in dmesg that will prevent you from login screen . As you said you can login with guest account , but you cannot login with your account. 

On the other hand i see some errors and warnings in Xorg.0.log file 


> **Subito Piano said:**
> 

```

[    17.408] (II) LoadModule: "fglrx"
[    17.408] (WW) Warning, couldn't open module fglrx
[    17.408] (II) UnloadModule: "fglrx"
[    17.408] (II) Unloading fglrx
[    17.408] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    17.418] (WW) Falling back to old probe method for vesa
[    17.418] (WW) Falling back to old probe method for fbdev
[    17.418] (II) Loading sub module "fbdevhw"
[    17.418] (II) LoadModule: "fbdevhw"
[    17.418] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so

```If you have fglrx enabled then it can be a mistake with driver . Maybe if purged, corrected the problem ?
If you don't have fglrx driver (and you have open source , radeon) then you can ignore above messages.




> **Subito Piano said:**
> Also, I noticed that when booting puppy, it says many deleted inodes are referenced in sda3.

This is a clue too , but you said you can login successfully with quest account , so i focused to your preferences. 

You know , an option might be to create a new user , and give him administrative privileges  . Then move all your files from old user to new.. and if all work correct , you can delete old (corrupt) user. 

Thanks

---

### Post by Subito Piano on 2012-07-25
Ah - you are in Greece, which explains the time lag between our responses.

You've been most helpful...alas, it's not going to work, as there are multitudinous problems.  Creating a new account did not work, as i could still only log in as a guest.  After reading some posts about lightdm failing, I did "sudo apt-get install gdm" and chose gdm for my default display manager and FINALLY saw my desktop, but too many other things have gone crazy -- no menu, PrintScreen crashing, etc.  So i must have REALLY done some damage!

At this point i will double-check that i have my /home files backed up, then wipe the entire HD, reinstall the OS from my remastersys disk, then copy the files from my backup HD to the newly-created home folder.  I'll have to watch out for anything I replace (i.e., configuration files).   I am hoping that creating a new /home folder and copying files into it will solve the problem that I couldn't solve by trying to retain my original home folder.  If that fails i might rename my configuration files -- or maybe go crazy myself and install BSD!!!  :P  

Fortunately, for now Puppy is working great from the USB stick and i can access all my files, e-mail, etc.  I've often thought of switching entirely to Puppy but the ease of configuring Ubuntu-based distros has been much in their favor -- I really don't have time for much hacking anymore.  I put off switching to Lubuntu 12.04 from Ubuntu Studio 10.04 until summer vacation so i would have extra time for the task and for reconfiguring everything I need/want, but between switching earlier this summer and trying to fix this mistake, it's really taking way too much of my time...  :(  

I'll post again once it's up and running -- or whenever I get SOMETHING going!!!

---

### Post by Subito Piano on 2012-07-26
Done.... :shock:

Maybe 32 hours total....too little sleep, too much important stuff ignored, and sick with a cold!!  :-({|= 

Long story short, i reformatted both the root and home partitions and reinstalled (again) from my remstastersys disk.  Reinstalling my old files didn't work (the menu was missing) -- so I took a tip from you, created a new user and moved all from the old user to the new one EXCEPT some hidden configuration files (.conf, .gconf, etc.) It WORKED -- but looked wrong, so i carefully added *_most_* of the rest of the hidden files.  Then of course, i need to give this new username root privileges, then i had to change ownership of most/all my files from root to the new name...which means if down the road i have to reinstall again (like hardware failure?) -- i;ll have to remember to return ownership to root...yada, yada... ](*,)  

Wow.  It's 98% done.  Lesson learned - go SLOWLY, do one or two changes at a time if you aren't sure what you are doing, take notes....(and *_always_* backup, of course).  

Thanks for you help!

---

