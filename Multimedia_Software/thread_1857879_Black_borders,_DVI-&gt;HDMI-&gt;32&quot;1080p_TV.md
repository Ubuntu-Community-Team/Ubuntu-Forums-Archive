---
title: "Black borders, DVI-&gt;HDMI-&gt;32&quot;1080p TV"
date: 2011-10-11
forum: Multimedia Software
---

### Post by sandle on 2011-10-11
Hello!
I recently felt like installing Ubuntu instead of Windows 7 and I did, but I realised pretty fast that it wasnt a good idea.

Setup:
AMD HD 6600
DVI to HDMI cable (if i use DVI->VGA kable it works just fine, prolly cause of overscan/subpixelrendering)
32" 1080p capable TV (yes im sure its 1080p and not 1080i)

Problems:

[LIST]
[*]I get black borders around the screen (if i fiddle around with overscan settings in amdcccle i only get it on the top and on the bottom of the screen, same with both 1080i and 720p)
[*]Text is blurry (can barely read this while im writing)
[*]Cannot set 1080p at all, while i do this in amdcccle nothing happends
[*]Lag while moving windows, could be because of unity (turning unity off removes the lag)
[/LIST]
As i said, any 1080p resolutions/hertz doesnt work at all. If i choose it ant press apply/ok nothing happens, only a yes/no answer box if i want to keep the settings but nothing else happens, not even a screen flicker.

1080p doesnt work at all, 1080i and 720p works but gives me black borders and is very blurry.

I do not feel like buying a new VGA kabel or buying an Nvidia card just to get this OS working properly, there has to be a way to fix this.

Could be worth to mention that it has worked before with a previous version of ubuntu (think it was 10 something).

Using the drivers from "additional drivers" applikation but i have tried installing the latest drivers from amd.com but with the same results.

Using the "monitor" applikation in ubuntu doesnt even give me the option to change the Hz to 50 or 60 which I am totally sure my TV is capable of, since it has worked before both on Ubuntu, Arch and Windows 7.

Any idea on what to do/try?

---

### Post by Grenage on 2011-10-11
I presume that the EDID data is not getting through due to the converter, but the bottom line is that it's not getting through; no EDID data, and the OS doesn't know what the screen can handle.

You can go two ways for fixing the resolution - xrandr or xorg.conf.  xrandr is a more on-the-fly/dynamic option, and is more commonly recommended by folk.  xorg.conf is basically a config file where you enter your parameters of choice, and that's how I prefer to do things.  There is a chance that the scan issues will be resolved by the correct resolution, but we can deal with that later if it does not help.  Now, guides:

xrandr: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

xorg.conf: [http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html) (fair warning, it's my guide)

If you have any problems, post back with where you are stuck, and we'll help you out.

---

### Post by sandle on 2011-10-11
Thanks for the fast reply, I tried with xrandr but i cannot add "--newmode" read somewhere that some graphics card isnt capable with xrandr and im guessing thats the case.

Input:
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

Output:
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  27
  Current serial number in output stream:  27

Checking into the xorg.conf solution instead and ill get back with results.


*Update* added the modeline to xorg.conf, rebooting

---

### Post by Grenage on 2011-10-11
Ok dokes; if it doesn't work as expected, feel free to post your config here (in code tags).

---

### Post by sandle on 2011-10-11
Well i rebooted and first i only got my background with my mouse, then i made a sudo servide gdm restart and it seemed to be working. My firefox hanged and didnt want to work. And the resolution was still at 30 hertz interlaced.

changed the "    Option        "TargetRefresh" "30"" to 60 just for fun and after a restart of gdm i only got a black screen with my mouse. Restarting gdm now doesnt work, still only mouse with black screen (if i move my mouse i can se there is still black strips on my screen).

Removed the modeline and set refresh to 30 again and rebooted (restart gdm didnt work) and now im back to where i left.

This is my xorg.conf right now:

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "30"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

This is what im trying with:
```

Section "Monitor"
    Identifier   "0-DFP2"
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    HorizSync 67.16
    VertRefresh 173.00
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection
```

---

### Post by sandle on 2011-10-11
Rebooted with previous stated xorg.conf.

Now i only get a black screen, cant even press ctrl alt f1 to get a terminal, so i cant even change back to my old xorg.conf.

Feels like i have to reinstall my machine or something.

(writing this on my ipad)

If i press the pwr button to shutdwon i see the ubuntu sålash screen but thats the only thing i can see, trying atm to connect an ordinary crappy lcd screen to se if i can at least see something so i can restore xconf



Successfully changed my xorg.conf to the old one by connecting an old LCD panel display.

Now i have my TV "working" again but what did i do wrong with the xorg.conf?

---

### Post by sandle on 2011-10-11
Also tried these solutions for trying to fix the insane lag when moving windows:
[http://www.youtube.com/watch?v=mK9x8QNGFXo](http://www.youtube.com/watch?v=mK9x8QNGFXo)
Related thread:
[http://ubuntuforums.org/showthread.php?t=1721551](http://ubuntuforums.org/showthread.php?t=1721551)

And it did not work, lags just as much.

I also get a black screen whenever i restart my computer, everytime i restart i have to go into ctrl alt f1 and write sudo gdm restart and it works.

It's amazing how many problems I just got by switching OS.


[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/764330](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/764330)

---

### Post by Grenage on 2011-10-11
Hi again!  If you've got a liveCD available, you can at least use that to boot from and delete/change your local xorg.conf.  Let's keep this basic and have a simple config; rename your old one (or delete it), and use this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "unknownv"
	ModelName "unknownm"
	HorizSync 25 - 65
	VertRefresh 50 - 75
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "fglrx"
	VendorName "ati"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1920x1080"
	EndSubSection
EndSection
```

This is assuming that you have an ntsc TV (using 60Mhz), and not a pal TV (50Mhz).  I'm not even sure if there is a difference in modern TV screens.

---

### Post by sandle on 2011-10-11
Just tried that, made my computer show me an eternal splash screen and no more, reverted to the old one and it booted right up.

I actually have no idea if my TV is NTSC or PAL, I bought it in Sweden though so i guess its PAL.

Going to try ""1920x1080_50.00"  141.50  1920 2032 2232 2544  1080 1083 1088 1114 -hsync +vsync" then i guess.

Its still the same, stuck at splash screen saying Xubuntu in an enternity (waited approx 8min, when i switch back to the old xorg.conf it shows for 0.5 secs and then it starts). Just installed Xubuntu-desktop cause of ubuntu unity making moving windows a living hell.

---

### Post by sandle on 2011-10-11
Also tried to disable xrandr like in:
[http://ubuntuforums.org/showthread.php?t=1204055](http://ubuntuforums.org/showthread.php?t=1204055)

But with the same result, right now im running 1080i 30hz with overscale so i dont have the black borders but my it makes it go outside the screen so I cant see the edges now but at least i dont have any black striped.

Getting pretty tired of booting livecd all the time the xorg.conf fail.

Also interlaced sucks d:

---

### Post by Grenage on 2011-10-12
Hi again,

Have you tried removing the fglrx (proprietary) driver, and using the open driver instead?  First have a look here for removing the driver:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Then replace "fglrx" with "radeon" in xorg.conf.  I'm fairly sure it's "radeon" and not "ati" - it's been a while since I've used an ati card!

---

### Post by sandle on 2011-10-15
Not sure if I want to do that since those drivers are deprecated and does not support 3d-acceleration to the amount that anything can be playable. Also setting font hinting to full made the text readable inside gdm, but not while in other applications (chromium for example).

I'm also trying to update to pre-release ATI proprietary driver through jockey but i get this:

```
2011-10-15 15:22:54,394 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0>
2011-10-15 15:22:55,643 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-10-15 15:22:55,857 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-15 15:22:55,857 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-15 15:22:55,880 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-15 15:22:55,901 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-15 15:22:56,004 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-15 15:22:56,004 DEBUG: Firmware for DVB cards not available
2011-10-15 15:22:56,004 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-15 15:22:56,007 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-15 15:22:56,023 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-15 15:22:56,023 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-15 15:22:56,023 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-15 15:22:56,028 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-15 15:22:56,028 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-15 15:22:56,028 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-15 15:22:56,028 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-15 15:22:56,046 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-15 15:22:56,086 DEBUG: Software modem not available
2011-10-15 15:22:56,086 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-15 15:22:56,130 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-15 15:22:56,136 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-15 15:22:56,136 DEBUG: nvidia.available: falling back to default
2011-10-15 15:22:56,204 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 15:22:56,207 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-15 15:22:56,213 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-15 15:22:56,213 DEBUG: nvidia.available: falling back to default
2011-10-15 15:22:56,246 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 15:22:56,249 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-15 15:22:56,255 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-15 15:22:56,255 DEBUG: nvidia.available: falling back to default
2011-10-15 15:22:56,287 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 15:22:56,288 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-15 15:22:56,292 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-15 15:22:56,297 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-15 15:22:56,298 DEBUG: nvidia.available: falling back to default
2011-10-15 15:22:56,330 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 15:22:56,334 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-15 15:22:56,339 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-15 15:22:56,340 DEBUG: nvidia.available: falling back to default
2011-10-15 15:22:56,372 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 15:22:56,375 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-15 15:22:56,381 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-15 15:22:56,381 DEBUG: nvidia.available: falling back to default
2011-10-15 15:22:56,413 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 15:22:56,414 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-15 15:22:56,419 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-15 15:22:56,424 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-15 15:22:56,425 DEBUG: fglrx.available: falling back to default
2011-10-15 15:22:56,457 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 15:22:56,467 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-15 15:22:56,467 DEBUG: fglrx.available: falling back to default
2011-10-15 15:22:56,500 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-15 15:22:56,501 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-15 15:22:56,505 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-15 15:22:56,505 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-15 15:22:56,521 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-15 15:22:56,522 DEBUG: all custom handlers loaded
2011-10-15 15:22:56,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 15:22:56,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'input:b0003v1532p000Ce0100-e0,1,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,lsfw')
2011-10-15 15:22:56,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:22:56,586 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:56,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-15 15:22:56,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 15:22:56,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001462sd00007673bc07sc80i00')
2011-10-15 15:22:56,763 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-15 15:22:56,763 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:56,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 15:22:56,764 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 15:22:56,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 15:22:56,776 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:22:56,776 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:56,776 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 15:22:56,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 15:22:56,777 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-15 15:22:56,777 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:56,777 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-15 15:22:56,777 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:56,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'platform:parport_pc')
2011-10-15 15:22:56,777 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2011-10-15 15:22:56,777 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2011-10-15 15:22:56,777 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:56,778 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00000100sv00001462sd00007681bc06sc00i00')
2011-10-15 15:22:56,779 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00001033d00000194sv00001462sd00007673bc0Csc03i30')
2011-10-15 15:22:56,779 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-15 15:22:56,780 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:56,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-15 15:22:56,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 15:22:56,780 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00001002d00006758sv00001458sd00002205bc03sc00i00')
2011-10-15 15:22:56,963 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-10-15 15:22:56,964 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:56,964 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2011-10-15 15:22:56,987 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:56,987 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:22:56,964 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 15:22:57,058 DEBUG: fglrx.available: falling back to default
2011-10-15 15:22:57,098 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,099 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:22:57,073 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 15:22:57,165 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-10-15 15:22:57,185 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,185 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:22:57,165 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 15:22:57,189 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-15 15:22:57,195 DEBUG: fglrx.available: falling back to default
2011-10-15 15:22:57,237 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,237 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:22:57,212 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 15:22:57,238 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-10-15 15:22:57,263 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,263 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:22:57,238 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 15:22:57,339 DEBUG: fglrx.available: falling back to default
2011-10-15 15:22:57,383 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,383 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:22:57,356 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 15:22:57,449 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00001B21d00001080sv00001462sd00007673bc06sc04i00')
2011-10-15 15:22:57,450 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2011-10-15 15:22:57,450 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 15:22:57,450 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001462sd00007673bc0Csc05i00')
2011-10-15 15:22:57,452 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-15 15:22:57,452 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,452 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'usb:v1532p000Cd2100dc00dsc00dp00ic03isc00ip02')
2011-10-15 15:22:57,453 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-15 15:22:57,453 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,453 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'usb:v045Ep074Bd0260dc00dsc00dp00ic03isc00ip00')
2011-10-15 15:22:57,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-15 15:22:57,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'input:b0003v045Ep074Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-10-15 15:22:57,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:22:57,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,492 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 15:22:57,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-10-15 15:22:57,497 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-15 15:22:57,497 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,497 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'input:b0003v1532p000Ce0100-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2011-10-15 15:22:57,497 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:22:57,497 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 15:22:57,498 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00001C00sv00001462sd00007673bc01sc01i8a')
2011-10-15 15:22:57,499 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 15:22:57,499 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:22:57,500 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,500 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.9:bd03/02/2011:svnMSI:pnMS-7673:pvr1.0:rvnMSI:rnP67A-C43(MS-7673):rvr1.0:cvnMSI:ct3:cvr1.0:')
2011-10-15 15:22:57,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 15:22:57,508 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00001C08sv00001462sd00007673bc01sc01i85')
2011-10-15 15:22:57,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007673bc02sc00i00')
2011-10-15 15:22:57,515 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-15 15:22:57,515 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,515 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'usb:v045Ep074Bd0260dc00dsc00dp00ic03isc01ip01')
2011-10-15 15:22:57,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-15 15:22:57,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-15 15:22:57,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-15 15:22:57,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-15 15:22:57,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001462sd00007673bc04sc03i00')
2011-10-15 15:22:57,518 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 15:22:57,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,518 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 15:22:57,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'input:b0003v045Ep074Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-15 15:22:57,518 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:22:57,518 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001462sd00007673bc0Csc03i20')
2011-10-15 15:22:57,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 15:22:57,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'usb:v1532p000Cd2100dc00dsc00dp00ic03isc01ip01')
2011-10-15 15:22:57,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-15 15:22:57,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,521 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-15 15:22:57,521 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,521 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00001002d0000AA90sv00001458sd0000AA90bc04sc03i00')
2011-10-15 15:22:57,523 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 15:22:57,523 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-15 15:22:57,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-15 15:22:57,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 15:22:57,524 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001462sd00007673bc06sc04i01')
2011-10-15 15:22:57,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00001C46sv00001462sd00007673bc06sc01i00')
2011-10-15 15:22:57,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-15 15:22:57,527 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,527 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 15:22:57,527 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-15 15:22:57,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-15 15:22:57,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-15 15:22:57,528 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:22:57,528 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:22:57,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001462sd00007673bc0Csc03i20')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xf017a0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'input:b0003v1532p000Ce0100-e0,1,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,lsfw')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001462sd00007673bc07sc80i00')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'platform:parport_pc')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00000100sv00001462sd00007681bc06sc00i00')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00001033d00000194sv00001462sd00007673bc0Csc03i30')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00001002d00006758sv00001458sd00002205bc03sc00i00')
2011-10-15 15:22:57,530 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00001B21d00001080sv00001462sd00007673bc06sc04i00')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001462sd00007673bc0Csc05i00')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'usb:v1532p000Cd2100dc00dsc00dp00ic03isc00ip02')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'usb:v045Ep074Bd0260dc00dsc00dp00ic03isc00ip00')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'input:b0003v045Ep074Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'input:b0003v1532p000Ce0100-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00001C00sv00001462sd00007673bc01sc01i8a')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.9:bd03/02/2011:svnMSI:pnMS-7673:pvr1.0:rvnMSI:rnP67A-C43(MS-7673):rvr1.0:cvnMSI:ct3:cvr1.0:')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00001C08sv00001462sd00007673bc01sc01i85')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007673bc02sc00i00')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'usb:v045Ep074Bd0260dc00dsc00dp00ic03isc01ip01')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001462sd00007673bc04sc03i00')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'input:b0003v045Ep074Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001462sd00007673bc0Csc03i20')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'usb:v1532p000Cd2100dc00dsc00dp00ic03isc01ip01')
2011-10-15 15:22:57,531 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00001002d0000AA90sv00001458sd0000AA90bc04sc03i00')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001462sd00007673bc06sc04i01')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00001C46sv00001462sd00007673bc06sc01i00')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001462sd00007673bc0Csc03i20')
2011-10-15 15:22:57,532 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1110440> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 15:22:57,583 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,583 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:22:57,642 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,642 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:22:57,826 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,826 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:22:57,884 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,884 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:22:57,926 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:22:57,926 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:23:00,121 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:23:00,121 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:23:00,816 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:23:00,816 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:23:02,483 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:23:02,483 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:23:05,649 DEBUG: Installing package: fglrx-updates
2011-10-15 15:23:05,972 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-10-15 15:23:05,989 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-10-15 15:23:06,070 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-10-15 15:23:06,092 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.000000
2011-10-15 15:23:06,142 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.002674
2011-10-15 15:23:06,643 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.227761
2011-10-15 15:23:07,143 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.563661
2011-10-15 15:23:07,644 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 0.858005
2011-10-15 15:23:08,145 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.155813
2011-10-15 15:23:08,646 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.450158
2011-10-15 15:23:09,147 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 1.744503
2011-10-15 15:23:09,648 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.038848
2011-10-15 15:23:10,149 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.336656
2011-10-15 15:23:10,649 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.627538
2011-10-15 15:23:11,150 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 2.925346
2011-10-15 15:23:11,651 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.219691
2011-10-15 15:23:12,152 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.514036
2011-10-15 15:23:12,653 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 3.808381
2011-10-15 15:23:13,154 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.102726
2011-10-15 15:23:13,655 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.397071
2011-10-15 15:23:14,156 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.694879
2011-10-15 15:23:14,656 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 4.982298
2011-10-15 15:23:15,157 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.276643
2011-10-15 15:23:15,658 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.570988
2011-10-15 15:23:16,159 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 5.854944
2011-10-15 15:23:16,660 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.156215
2011-10-15 15:23:17,161 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.450560
2011-10-15 15:23:17,662 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 6.748367
2011-10-15 15:23:18,163 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.042712
2011-10-15 15:23:18,663 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.337057
2011-10-15 15:23:19,164 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.634865
2011-10-15 15:23:19,665 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 7.929210
2011-10-15 15:23:20,166 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.223555
2011-10-15 15:23:20,667 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.517900
2011-10-15 15:23:21,168 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 8.815708
2011-10-15 15:23:21,669 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.110053
2011-10-15 15:23:22,170 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.404398
2011-10-15 15:23:22,671 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.698743
2011-10-15 15:23:23,172 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 9.996551
2011-10-15 15:23:23,673 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.290895
2011-10-15 15:23:24,174 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.585240
2011-10-15 15:23:24,675 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 10.841494
2011-10-15 15:23:25,176 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.173930
2011-10-15 15:23:25,676 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.468275
2011-10-15 15:23:26,177 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 11.766083
2011-10-15 15:23:26,678 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.060428
2011-10-15 15:23:27,178 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.354773
2011-10-15 15:23:27,679 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.652581
2011-10-15 15:23:28,180 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 12.946926
2011-10-15 15:23:28,681 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.241271
2011-10-15 15:23:29,182 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.535616
2011-10-15 15:23:29,683 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 13.829961
2011-10-15 15:23:30,184 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.120843
2011-10-15 15:23:30,685 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.411725
2011-10-15 15:23:31,186 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 14.706070
2011-10-15 15:23:31,687 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.000415
2011-10-15 15:23:32,187 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.294760
2011-10-15 15:23:32,688 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.582179
2011-10-15 15:23:33,189 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 15.879987
2011-10-15 15:23:33,690 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.174332
2011-10-15 15:23:34,191 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.472139
2011-10-15 15:23:34,692 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 16.704153
2011-10-15 15:23:35,192 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.060829
2011-10-15 15:23:35,693 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.358637
2011-10-15 15:23:36,194 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.652982
2011-10-15 15:23:36,695 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 17.947327
2011-10-15 15:23:37,196 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.245135
2011-10-15 15:23:37,697 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.539480
2011-10-15 15:23:38,198 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 18.833825
2011-10-15 15:23:38,699 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.131633
2011-10-15 15:23:39,200 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.425978
2011-10-15 15:23:39,700 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 19.720323
2011-10-15 15:23:40,201 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.014668
2011-10-15 15:23:40,702 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.295161
2011-10-15 15:23:41,203 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.606820
2011-10-15 15:23:41,704 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 20.897702
2011-10-15 15:23:42,204 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.195510
2011-10-15 15:23:42,705 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.489855
2011-10-15 15:23:43,206 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 21.721868
2011-10-15 15:23:43,707 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.082008
2011-10-15 15:23:44,208 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.376353
2011-10-15 15:23:44,708 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.670698
2011-10-15 15:23:45,209 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 22.968506
2011-10-15 15:23:45,710 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.262851
2011-10-15 15:23:46,211 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.557196
2011-10-15 15:23:46,712 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 23.855003
2011-10-15 15:23:47,213 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.149348
2011-10-15 15:23:47,714 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.443693
2011-10-15 15:23:48,214 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 24.738038
2011-10-15 15:23:48,715 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.035846
2011-10-15 15:23:49,216 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.330191
2011-10-15 15:23:49,717 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.624536
2011-10-15 15:23:50,218 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 25.922344
2011-10-15 15:23:50,719 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.216689
2011-10-15 15:23:51,220 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.511034
2011-10-15 15:23:51,720 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 26.805379
2011-10-15 15:23:52,221 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.103187
2011-10-15 15:23:52,722 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.397531
2011-10-15 15:23:53,223 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.691876
2011-10-15 15:23:53,724 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 27.958518
2011-10-15 15:23:54,225 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.280566
2011-10-15 15:23:54,726 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.578374
2011-10-15 15:23:55,226 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 28.872719
2011-10-15 15:23:55,727 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.167064
2011-10-15 15:23:56,228 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.464872
2011-10-15 15:23:56,729 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 29.759217
2011-10-15 15:23:57,230 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.053562
2011-10-15 15:23:57,731 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.351370
2011-10-15 15:23:58,232 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.645715
2011-10-15 15:23:58,732 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 30.940060
2011-10-15 15:23:59,233 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.234404
2011-10-15 15:23:59,734 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.528749
2011-10-15 15:24:00,235 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 31.823094
2011-10-15 15:24:00,736 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.117439
2011-10-15 15:24:01,236 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.408321
2011-10-15 15:24:01,737 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.699203
2011-10-15 15:24:02,238 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 32.958920
2011-10-15 15:24:02,739 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.291356
2011-10-15 15:24:03,240 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.585701
2011-10-15 15:24:03,741 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 33.880046
2011-10-15 15:24:04,242 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.177854
2011-10-15 15:24:04,742 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.472199
2011-10-15 15:24:05,243 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 34.766544
2011-10-15 15:24:05,744 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.064352
2011-10-15 15:24:06,245 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.358697
2011-10-15 15:24:06,746 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.653042
2011-10-15 15:24:07,247 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 35.950849
2011-10-15 15:24:07,748 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.245194
2011-10-15 15:24:08,248 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.539539
2011-10-15 15:24:08,749 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 36.833884
2011-10-15 15:24:09,250 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.128229
2011-10-15 15:24:09,751 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.422574
2011-10-15 15:24:10,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 37.716919
2011-10-15 15:24:10,752 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.014727
2011-10-15 15:24:11,253 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.309072
2011-10-15 15:24:11,754 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.603417
2011-10-15 15:24:12,255 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 38.897762
2011-10-15 15:24:12,756 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.192107
2011-10-15 15:24:13,256 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.486452
2011-10-15 15:24:13,757 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 39.780797
2011-10-15 15:24:14,258 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.078605
2011-10-15 15:24:14,759 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.300229
2011-10-15 15:24:15,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.649980
2011-10-15 15:24:15,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 40.965102
2011-10-15 15:24:16,261 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.259447
2011-10-15 15:24:16,762 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.550329
2011-10-15 15:24:17,263 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 41.848137
2011-10-15 15:24:17,764 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.145945
2011-10-15 15:24:18,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.440290
2011-10-15 15:24:18,765 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 42.734635
2011-10-15 15:24:19,266 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.032443
2011-10-15 15:24:19,767 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.326788
2011-10-15 15:24:20,268 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.621133
2011-10-15 15:24:20,769 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 43.918940
2011-10-15 15:24:21,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.213285
2011-10-15 15:24:21,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.507630
2011-10-15 15:24:22,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 44.805438
2011-10-15 15:24:22,772 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.099783
2011-10-15 15:24:23,273 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.394128
2011-10-15 15:24:23,774 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.685010
2011-10-15 15:24:24,275 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 45.979355
2011-10-15 15:24:24,776 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.277163
2011-10-15 15:24:25,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.571508
2011-10-15 15:24:25,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 46.865853
2011-10-15 15:24:26,279 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.160198
2011-10-15 15:24:26,779 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.458006
2011-10-15 15:24:27,280 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 47.752351
2011-10-15 15:24:27,781 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.043233
2011-10-15 15:24:28,282 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.341040
2011-10-15 15:24:28,783 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.631923
2011-10-15 15:24:29,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 48.926267
2011-10-15 15:24:29,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.217150
2011-10-15 15:24:30,286 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.511495
2011-10-15 15:24:30,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 49.802377
2011-10-15 15:24:31,287 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.096722
2011-10-15 15:24:31,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.387604
2011-10-15 15:24:32,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.681949
2011-10-15 15:24:32,790 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 50.979756
2011-10-15 15:24:33,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.236010
2011-10-15 15:24:33,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.564983
2011-10-15 15:24:34,293 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 51.862791
2011-10-15 15:24:34,794 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.157136
2011-10-15 15:24:35,295 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.451481
2011-10-15 15:24:35,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 52.742363
2011-10-15 15:24:36,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.040171
2011-10-15 15:24:36,797 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.334516
2011-10-15 15:24:37,298 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.628861
2011-10-15 15:24:37,799 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 53.926669
2011-10-15 15:24:38,300 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.221014
2011-10-15 15:24:38,801 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.515359
2011-10-15 15:24:39,301 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 54.809704
2011-10-15 15:24:39,802 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.107511
2011-10-15 15:24:40,303 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.401856
2011-10-15 15:24:40,804 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.696201
2011-10-15 15:24:41,305 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 55.994009
2011-10-15 15:24:41,806 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.229485
2011-10-15 15:24:42,307 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.582699
2011-10-15 15:24:42,808 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 56.880507
2011-10-15 15:24:43,308 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.174852
2011-10-15 15:24:43,809 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.469197
2011-10-15 15:24:44,310 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 57.760079
2011-10-15 15:24:44,811 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.057887
2011-10-15 15:24:45,312 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.352232
2011-10-15 15:24:45,813 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.646577
2011-10-15 15:24:46,314 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 58.940922
2011-10-15 15:24:46,814 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.238729
2011-10-15 15:24:47,315 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.533074
2011-10-15 15:24:47,816 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 59.827419
2011-10-15 15:24:48,317 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.121764
2011-10-15 15:24:48,818 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.416109
2011-10-15 15:24:49,319 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 60.713917
2011-10-15 15:24:49,820 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.008262
2011-10-15 15:24:50,321 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.240275
2011-10-15 15:24:50,822 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.600415
2011-10-15 15:24:51,323 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 61.891297
2011-10-15 15:24:51,823 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.168327
2011-10-15 15:24:52,324 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.483450
2011-10-15 15:24:52,825 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 62.777795
2011-10-15 15:24:53,326 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.075602
2011-10-15 15:24:53,826 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.369947
2011-10-15 15:24:54,327 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.664292
2011-10-15 15:24:54,828 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 63.962100
2011-10-15 15:24:55,329 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.256445
2011-10-15 15:24:55,830 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.550790
2011-10-15 15:24:56,331 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 64.845135
2011-10-15 15:24:56,832 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.142943
2011-10-15 15:24:57,333 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.437288
2011-10-15 15:24:57,834 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 65.731633
2011-10-15 15:24:58,334 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.029441
2011-10-15 15:24:58,835 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.320323
2011-10-15 15:24:59,336 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.618131
2011-10-15 15:24:59,837 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 66.909013
2011-10-15 15:25:00,338 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.203358
2011-10-15 15:25:00,838 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.490777
2011-10-15 15:25:01,339 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 67.719327
2011-10-15 15:25:01,840 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.051764
2011-10-15 15:25:02,341 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.346109
2011-10-15 15:25:02,841 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.640453
2011-10-15 15:25:03,342 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 68.934798
2011-10-15 15:25:03,843 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.229143
2011-10-15 15:25:04,344 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.523488
2011-10-15 15:25:04,844 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 69.821296
2011-10-15 15:25:05,345 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.115641
2011-10-15 15:25:05,846 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.409986
2011-10-15 15:25:06,346 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 70.704331
2011-10-15 15:25:06,847 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.002139
2011-10-15 15:25:07,348 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.293021
2011-10-15 15:25:07,849 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.587366
2011-10-15 15:25:08,350 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 71.885174
2011-10-15 15:25:08,851 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.179519
2011-10-15 15:25:09,352 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.473864
2011-10-15 15:25:09,853 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 72.737043
2011-10-15 15:25:10,353 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.062554
2011-10-15 15:25:10,854 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.356898
2011-10-15 15:25:11,355 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.654706
2011-10-15 15:25:11,856 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 73.904034
2011-10-15 15:25:12,357 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.236470
2011-10-15 15:25:12,858 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.530815
2011-10-15 15:25:13,359 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 74.828623
2011-10-15 15:25:13,859 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.122968
2011-10-15 15:25:14,360 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.420776
2011-10-15 15:25:14,861 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 75.715121
2011-10-15 15:25:15,362 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.009466
2011-10-15 15:25:15,863 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.303811
2011-10-15 15:25:16,364 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.594693
2011-10-15 15:25:16,864 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 76.889038
2011-10-15 15:25:17,365 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.183383
2011-10-15 15:25:17,866 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.481191
2011-10-15 15:25:18,367 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 77.775536
2011-10-15 15:25:18,868 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.069881
2011-10-15 15:25:19,369 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.364226
2011-10-15 15:25:19,870 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.658570
2011-10-15 15:25:20,371 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 78.897509
2011-10-15 15:25:20,872 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.250723
2011-10-15 15:25:21,372 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.548531
2011-10-15 15:25:21,873 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 79.842876
2011-10-15 15:25:22,374 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.137221
2011-10-15 15:25:22,875 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.435029
2011-10-15 15:25:23,376 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 80.729374
2011-10-15 15:25:23,876 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.027182
2011-10-15 15:25:24,377 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.321527
2011-10-15 15:25:24,878 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.615872
2011-10-15 15:25:25,379 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 81.913679
2011-10-15 15:25:25,880 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.208024
2011-10-15 15:25:26,381 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.478129
2011-10-15 15:25:26,882 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 82.800177
2011-10-15 15:25:27,382 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.094522
2011-10-15 15:25:27,883 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.392330
2011-10-15 15:25:28,384 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.676286
2011-10-15 15:25:28,885 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 83.977557
2011-10-15 15:25:29,386 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.275365
2011-10-15 15:25:29,887 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.566247
2011-10-15 15:25:30,388 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 84.864055
2011-10-15 15:25:30,889 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.151474
2011-10-15 15:25:31,390 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.445819
2011-10-15 15:25:31,891 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 85.712461
2011-10-15 15:25:32,392 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.034509
2011-10-15 15:25:32,892 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.328854
2011-10-15 15:25:33,252 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.543469
2011-10-15 15:25:33,257 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.546238
2011-10-15 15:25:33,758 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 86.840583
2011-10-15 15:25:34,259 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.134928
2011-10-15 15:25:34,760 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.429273
2011-10-15 15:25:35,260 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 87.723618
2011-10-15 15:25:35,761 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.017963
2011-10-15 15:25:36,262 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.315771
2011-10-15 15:25:36,763 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.603190
2011-10-15 15:25:37,264 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 88.897535
2011-10-15 15:25:37,769 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.195343
2011-10-15 15:25:38,270 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.455059
2011-10-15 15:25:38,771 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 89.784032
2011-10-15 15:25:39,272 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.078377
2011-10-15 15:25:39,773 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.372722
2011-10-15 15:25:40,274 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.670530
2011-10-15 15:25:40,775 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 90.961412
2011-10-15 15:25:41,276 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.255757
2011-10-15 15:25:41,777 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.553565
2011-10-15 15:25:42,277 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 91.847910
2011-10-15 15:25:42,778 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.138792
2011-10-15 15:25:43,279 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.433137
2011-10-15 15:25:43,780 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 92.727482
2011-10-15 15:25:44,281 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.021827
2011-10-15 15:25:44,782 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.316172
2011-10-15 15:25:45,283 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.610517
2011-10-15 15:25:45,784 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 93.904862
2011-10-15 15:25:46,284 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.199207
2011-10-15 15:25:46,785 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.462386
2011-10-15 15:25:47,286 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 94.791359
2011-10-15 15:25:47,787 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.085704
2011-10-15 15:25:48,288 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.380049
2011-10-15 15:25:48,788 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.677857
2011-10-15 15:25:49,289 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 95.972202
2011-10-15 15:25:49,790 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.266547
2011-10-15 15:25:50,291 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.560892
2011-10-15 15:25:50,792 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 96.855237
2011-10-15 15:25:51,292 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.149582
2011-10-15 15:25:51,793 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.443927
2011-10-15 15:25:52,294 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 97.738272
2011-10-15 15:25:52,795 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.032617
2011-10-15 15:25:53,296 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.326962
2011-10-15 15:25:53,796 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.621307
2011-10-15 15:25:54,297 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 98.919115
2011-10-15 15:25:54,798 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.196145
2011-10-15 15:25:55,299 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.452398
2011-10-15 15:25:55,800 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 99.798687
2011-10-15 15:25:56,135 DEBUG: download progress <Package: name:'fglrx-updates' architecture='amd64' id:16491L> 100.000000
2011-10-15 15:25:56,302 DEBUG: install progress dpkg-exec 0.000000
2011-10-15 15:25:56,542 DEBUG: install progress fglrx-amdcccle 0.000000
2011-10-15 15:25:56,615 DEBUG: install progress fglrx-amdcccle 6.250000
2011-10-15 15:25:56,615 DEBUG: install progress fglrx-amdcccle 12.500000
2011-10-15 15:25:56,801 DEBUG: install progress fglrx-amdcccle 18.750000
2011-10-15 15:25:57,242 DEBUG: install progress fglrx 18.750000
2011-10-15 15:25:57,343 DEBUG: install progress fglrx 25.000000
2011-10-15 15:26:26,424 DEBUG: install progress fglrx 31.250000
2011-10-15 15:26:27,392 DEBUG: install progress fglrx 37.500000
2011-10-15 15:26:27,535 DEBUG: install progress bamfdaemon 37.500000
2011-10-15 15:26:27,703 DEBUG: install progress gnome-menus 37.500000
2011-10-15 15:26:27,855 DEBUG: install progress libc-bin 37.500000
2011-10-15 15:26:28,091 DEBUG: install progress ureadahead 37.500000
2011-10-15 15:26:28,259 DEBUG: install progress initramfs-tools 37.500000
2011-10-15 15:26:37,166 DEBUG: install progress dpkg-exec 37.500000
2011-10-15 15:26:37,732 DEBUG: install progress fglrx-updates 37.500000
2011-10-15 15:26:37,832 DEBUG: install progress fglrx-updates 43.750000
2011-10-15 15:26:39,937 DEBUG: install progress fglrx-updates 50.000000
2011-10-15 15:26:40,029 DEBUG: install progress fglrx-updates 56.250000
2011-10-15 15:26:40,252 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2011-10-15 15:26:40,352 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2011-10-15 15:26:40,796 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2011-10-15 15:26:40,886 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2011-10-15 15:26:40,997 DEBUG: install progress ureadahead 75.000000
2011-10-15 15:26:41,370 DEBUG: install progress dpkg-exec 75.000000
2011-10-15 15:26:41,406 DEBUG: install progress fglrx-updates 75.000000
2011-10-15 15:26:41,903 DEBUG: install progress fglrx-updates 81.250000
2011-10-15 15:26:59,835 DEBUG: install progress fglrx-updates 87.500000
2011-10-15 15:27:00,465 DEBUG: install progress bamfdaemon 87.500000
2011-10-15 15:27:00,675 DEBUG: install progress gnome-menus 87.500000
2011-10-15 15:27:00,976 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2011-10-15 15:27:01,069 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2011-10-15 15:27:01,186 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-10-15 15:27:01,295 DEBUG: install progress initramfs-tools 100.000000
2011-10-15 15:27:08,053 DEBUG: install progress libc-bin 100.000000
2011-10-15 15:27:09,657 DEBUG: (Reading database ... 186242 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Selecting previously deselected package fglrx-updates.
(Reading database ... 185998 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.881-0ubuntu6_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.881-0ubuntu6_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.881-0ubuntu6) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.881 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.881-0ubuntu6) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-10-15 15:27:09,832 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-15 15:27:09,903 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-15 15:27:10,009 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:27:10,009 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:27:10,026 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:27:10,026 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:31:11,971 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:31:11,971 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:31:11,987 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:31:11,987 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:31:12,033 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:31:12,033 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:31:12,179 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:31:12,179 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:31:12,195 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:31:12,195 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:31:12,227 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:31:12,227 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:31:12,242 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:31:12,242 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:31:12,270 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:31:12,270 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:32:35,593 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:35,593 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:35,620 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:35,621 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:38,181 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-15 15:32:38,256 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-15 15:32:38,343 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:38,343 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:38,371 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:38,371 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:41,682 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:41,683 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:41,710 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:41,710 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:41,756 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:41,757 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:32:41,929 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:41,930 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:41,957 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:41,957 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:42,017 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:42,017 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:42,044 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:42,045 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:42,089 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:42,090 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:32:44,319 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:44,319 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:32:45,439 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:45,440 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:45,467 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:45,467 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:32:46,153 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:46,153 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:32:47,792 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:32:47,792 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:32:48,067 DEBUG: Installing package: fglrx
2011-10-15 15:32:48,567 DEBUG: install progress dpkg-exec 0.000000
2011-10-15 15:32:48,807 DEBUG: install progress fglrx-amdcccle-updates 0.000000
2011-10-15 15:32:48,897 DEBUG: install progress fglrx-amdcccle-updates 6.250000
2011-10-15 15:32:48,897 DEBUG: install progress fglrx-amdcccle-updates 12.500000
2011-10-15 15:32:49,033 DEBUG: install progress fglrx-amdcccle-updates 18.750000
2011-10-15 15:32:49,508 DEBUG: install progress fglrx-updates 18.750000
2011-10-15 15:32:49,609 DEBUG: install progress fglrx-updates 25.000000
2011-10-15 15:32:53,492 DEBUG: install progress fglrx-updates 31.250000
2011-10-15 15:32:53,984 DEBUG: install progress fglrx-updates 37.500000
2011-10-15 15:32:54,110 DEBUG: install progress bamfdaemon 37.500000
2011-10-15 15:32:54,237 DEBUG: install progress gnome-menus 37.500000
2011-10-15 15:32:54,354 DEBUG: install progress libc-bin 37.500000
2011-10-15 15:32:54,540 DEBUG: install progress ureadahead 37.500000
2011-10-15 15:32:54,659 DEBUG: install progress initramfs-tools 37.500000
2011-10-15 15:33:02,065 DEBUG: install progress dpkg-exec 37.500000
2011-10-15 15:33:02,575 DEBUG: install progress fglrx 37.500000
2011-10-15 15:33:02,676 DEBUG: install progress fglrx 43.750000
2011-10-15 15:33:05,245 DEBUG: install progress fglrx 50.000000
2011-10-15 15:33:05,304 DEBUG: install progress fglrx 56.250000
2011-10-15 15:33:05,494 DEBUG: install progress fglrx-amdcccle 56.250000
2011-10-15 15:33:05,595 DEBUG: install progress fglrx-amdcccle 62.500000
2011-10-15 15:33:06,005 DEBUG: install progress fglrx-amdcccle 68.750000
2011-10-15 15:33:06,061 DEBUG: install progress fglrx-amdcccle 75.000000
2011-10-15 15:33:06,207 DEBUG: install progress ureadahead 75.000000
2011-10-15 15:33:06,537 DEBUG: install progress dpkg-exec 75.000000
2011-10-15 15:33:06,572 DEBUG: install progress fglrx 75.000000
2011-10-15 15:33:06,918 DEBUG: install progress fglrx 81.250000
2011-10-15 15:33:20,122 DEBUG: install progress fglrx 87.500000
2011-10-15 15:33:20,610 DEBUG: install progress bamfdaemon 87.500000
2011-10-15 15:33:20,794 DEBUG: install progress gnome-menus 87.500000
2011-10-15 15:33:20,997 DEBUG: install progress fglrx-amdcccle 87.500000
2011-10-15 15:33:21,081 DEBUG: install progress fglrx-amdcccle 93.750000
2011-10-15 15:33:21,206 DEBUG: install progress fglrx-amdcccle 100.000000
2011-10-15 15:33:21,291 DEBUG: install progress initramfs-tools 100.000000
2011-10-15 15:33:28,239 DEBUG: install progress libc-bin 100.000000
2011-10-15 15:33:29,843 DEBUG: (Reading database ... 181601 files and directories currently installed.)
Removing fglrx-amdcccle-updates ...
Removing fglrx-updates ...
Removing all DKMS Modules
Done.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Selecting previously deselected package fglrx.
(Reading database ... 181357 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.881-0ubuntu4) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.881 DKMS files...
Building only for 3.0.0-12-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-10-15 15:33:29,975 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:00.0
2011-10-15 15:33:43,984 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:43,985 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:33:44,072 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,072 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:33:44,197 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,197 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:33:44,221 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,221 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:33:44,278 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,278 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:33:44,357 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,357 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:33:44,483 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,483 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:33:44,574 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,574 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:33:44,705 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,705 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:33:44,734 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,735 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:33:44,781 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,781 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:33:44,871 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:44,871 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:33:47,834 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:47,834 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:33:47,864 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:33:47,864 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:33:49,070 DEBUG: Shutting down
2011-10-15 15:42:57,961 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0>
2011-10-15 15:42:59,547 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic/modules.alias
2011-10-15 15:42:59,663 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-15 15:42:59,677 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-15 15:42:59,708 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-15 15:42:59,733 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-15 15:42:59,820 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-15 15:42:59,820 DEBUG: Firmware for DVB cards not available
2011-10-15 15:42:59,821 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-15 15:42:59,850 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-15 15:42:59,866 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-15 15:42:59,866 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-15 15:42:59,866 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-15 15:42:59,871 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-15 15:42:59,871 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-15 15:42:59,871 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-15 15:42:59,871 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-15 15:42:59,890 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-15 15:42:59,909 DEBUG: Software modem not available
2011-10-15 15:42:59,909 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-15 15:42:59,943 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-15 15:42:59,947 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-15 15:42:59,947 DEBUG: nvidia.available: falling back to default
2011-10-15 15:43:00,015 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 15:43:00,018 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-15 15:43:00,024 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-15 15:43:00,024 DEBUG: nvidia.available: falling back to default
2011-10-15 15:43:00,056 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 15:43:00,059 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-15 15:43:00,065 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-15 15:43:00,065 DEBUG: nvidia.available: falling back to default
2011-10-15 15:43:00,097 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 15:43:00,097 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-15 15:43:00,101 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-15 15:43:00,107 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-15 15:43:00,107 DEBUG: nvidia.available: falling back to default
2011-10-15 15:43:00,139 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 15:43:00,143 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-15 15:43:00,148 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-15 15:43:00,148 DEBUG: nvidia.available: falling back to default
2011-10-15 15:43:00,181 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-15 15:43:00,184 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-15 15:43:00,190 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-15 15:43:00,190 DEBUG: nvidia.available: falling back to default
2011-10-15 15:43:00,222 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 15:43:00,223 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-15 15:43:00,228 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-15 15:43:00,234 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-15 15:43:00,234 DEBUG: fglrx.available: falling back to default
2011-10-15 15:43:00,266 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-15 15:43:00,276 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-15 15:43:00,276 DEBUG: fglrx.available: falling back to default
2011-10-15 15:43:00,308 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-15 15:43:00,309 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-15 15:43:00,312 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-15 15:43:00,313 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-15 15:43:00,335 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-15 15:43:00,335 DEBUG: all custom handlers loaded
2011-10-15 15:43:00,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 15:43:00,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'input:b0003v1532p000Ce0100-e0,1,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,lsfw')
2011-10-15 15:43:00,341 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:43:00,400 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:00,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-15 15:43:00,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 15:43:00,400 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001462sd00007673bc07sc80i00')
2011-10-15 15:43:00,574 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mei'}
2011-10-15 15:43:00,574 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mei', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:00,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 15:43:00,574 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 15:43:00,586 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 15:43:00,586 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:43:00,587 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:00,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 15:43:00,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 15:43:00,587 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-15 15:43:00,587 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:00,587 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-15 15:43:00,587 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:00,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'platform:parport_pc')
2011-10-15 15:43:00,587 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2011-10-15 15:43:00,587 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi'}
2011-10-15 15:43:00,588 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mxm_wmi', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:00,588 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00000100sv00001462sd00007681bc06sc00i00')
2011-10-15 15:43:00,589 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00001033d00000194sv00001462sd00007673bc0Csc03i30')
2011-10-15 15:43:00,589 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd'}
2011-10-15 15:43:00,590 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'xhci_hcd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:00,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-15 15:43:00,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 15:43:00,590 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00001002d00006758sv00001458sd00002205bc03sc00i00')
2011-10-15 15:43:00,771 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'radeon'}
2011-10-15 15:43:00,771 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'radeon', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:00,771 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx'}
2011-10-15 15:43:01,400 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:01,400 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:43:00,771 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 15:43:01,471 DEBUG: fglrx.available: falling back to default
2011-10-15 15:43:01,511 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:01,511 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:43:01,486 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 15:43:01,575 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx_updates', 'package': 'fglrx-updates'}
2011-10-15 15:43:01,593 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:01,594 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:43:01,575 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 15:43:01,597 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-15 15:43:01,602 DEBUG: fglrx.available: falling back to default
2011-10-15 15:43:01,643 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:01,644 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:43:01,619 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-15 15:43:01,644 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'fglrx', 'package': 'fglrx'}
2011-10-15 15:43:01,669 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:01,669 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:43:01,644 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 15:43:01,737 DEBUG: fglrx.available: falling back to default
2011-10-15 15:43:01,779 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:01,779 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:43:01,753 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-15 15:43:01,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00001B21d00001080sv00001462sd00007673bc06sc04i00')
2011-10-15 15:43:01,841 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'shpchp'}
2011-10-15 15:43:01,841 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'shpchp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 15:43:01,841 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001462sd00007673bc0Csc05i00')
2011-10-15 15:43:01,845 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-15 15:43:01,845 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,845 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'usb:v1532p000Cd2100dc00dsc00dp00ic03isc00ip02')
2011-10-15 15:43:01,846 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-15 15:43:01,846 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,846 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'usb:v045Ep074Bd0260dc00dsc00dp00ic03isc00ip00')
2011-10-15 15:43:01,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-15 15:43:01,884 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,884 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'input:b0003v045Ep074Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-10-15 15:43:01,884 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:43:01,884 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,885 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-15 15:43:01,885 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,885 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-10-15 15:43:01,889 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-15 15:43:01,890 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'input:b0003v1532p000Ce0100-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2011-10-15 15:43:01,890 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:43:01,890 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 15:43:01,890 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00001C00sv00001462sd00007673bc01sc01i8a')
2011-10-15 15:43:01,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 15:43:01,892 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:43:01,892 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,892 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.9:bd03/02/2011:svnMSI:pnMS-7673:pvr1.0:rvnMSI:rnP67A-C43(MS-7673):rvr1.0:cvnMSI:ct3:cvr1.0:')
2011-10-15 15:43:01,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 15:43:01,900 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00001C08sv00001462sd00007673bc01sc01i85')
2011-10-15 15:43:01,902 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007673bc02sc00i00')
2011-10-15 15:43:01,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-15 15:43:01,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'usb:v045Ep074Bd0260dc00dsc00dp00ic03isc01ip01')
2011-10-15 15:43:01,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-15 15:43:01,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,907 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-15 15:43:01,907 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,907 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-15 15:43:01,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-15 15:43:01,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001462sd00007673bc04sc03i00')
2011-10-15 15:43:01,910 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 15:43:01,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,910 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 15:43:01,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'input:b0003v045Ep074Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-15 15:43:01,910 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:43:01,910 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,910 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001462sd00007673bc0Csc03i20')
2011-10-15 15:43:01,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 15:43:01,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'usb:v1532p000Cd2100dc00dsc00dp00ic03isc01ip01')
2011-10-15 15:43:01,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-15 15:43:01,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,912 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2011-10-15 15:43:01,912 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,912 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00001002d0000AA90sv00001458sd0000AA90bc04sc03i00')
2011-10-15 15:43:01,914 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-15 15:43:01,914 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-15 15:43:01,914 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-15 15:43:01,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 15:43:01,915 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001462sd00007673bc06sc04i01')
2011-10-15 15:43:01,917 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00001C46sv00001462sd00007673bc06sc01i00')
2011-10-15 15:43:01,918 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-15 15:43:01,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 15:43:01,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2011-10-15 15:43:01,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2011-10-15 15:43:01,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-15 15:43:01,919 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-15 15:43:01,919 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-15 15:43:01,919 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001462sd00007673bc0Csc03i20')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x2ab67a0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'input:b0003v1532p000Ce0100-e0,1,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,lsfw')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:INT3F0D:PNP0C02:')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00001C3Asv00001462sd00007673bc07sc80i00')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'platform:pcspkr')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'platform:parport_pc')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'wmi:F6CB5C3C-9CAE-4EBD-B577-931EA32A2CC0')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00000100sv00001462sd00007681bc06sc00i00')
2011-10-15 15:43:01,921 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00001033d00000194sv00001462sd00007673bc0Csc03i30')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00001002d00006758sv00001458sd00002205bc03sc00i00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00001B21d00001080sv00001462sd00007673bc06sc04i00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00001C22sv00001462sd00007673bc0Csc05i00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'usb:v1532p000Cd2100dc00dsc00dp00ic03isc00ip02')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'usb:v045Ep074Bd0260dc00dsc00dp00ic03isc00ip00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'input:b0003v045Ep074Be0111-e0,1,2,3,4,k71,72,73,74,77,80,82,83,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B5,B6,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F1,100,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r6,a20,m4,lsfw')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'input:b0003v1532p000Ce0100-e0,1,2,4,k110,111,112,113,114,115,116,117,r0,1,8,am4,lsfw')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00001C00sv00001462sd00007673bc01sc01i8a')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrV1.9:bd03/02/2011:svnMSI:pnMS-7673:pvr1.0:rvnMSI:rnP67A-C43(MS-7673):rvr1.0:cvnMSI:ct3:cvr1.0:')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00001C08sv00001462sd00007673bc01sc01i85')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001462sd00007673bc02sc00i00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'usb:v045Ep074Bd0260dc00dsc00dp00ic03isc01ip01')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp01ic09isc00ip00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00001C20sv00001462sd00007673bc04sc03i00')
2011-10-15 15:43:01,922 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'input:b0003v045Ep074Be0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00001C2Dsv00001462sd00007673bc0Csc03i20')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'usb:v1532p000Cd2100dc00dsc00dp00ic03isc01ip01')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00001002d0000AA90sv00001458sd0000AA90bc04sc03i00')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'usb:v1D6Bp0003d0300dc09dsc00dp03ic09isc00ip00')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001462sd00007673bc06sc04i01')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00001C46sv00001462sd00007673bc06sc01i00')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw8,')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'pci:v00008086d00001C26sv00001462sd00007673bc0Csc03i20')
2011-10-15 15:43:01,923 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2cc5440> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-15 15:43:01,985 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:01,985 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:43:02,073 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:02,073 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:43:02,253 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:02,253 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:43:02,311 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:02,311 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:43:02,352 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:02,352 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:43:04,754 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:43:04,754 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:43:07,769 DEBUG: Installing package: fglrx-updates
2011-10-15 15:43:08,280 DEBUG: install progress dpkg-exec 0.000000
2011-10-15 15:43:08,535 DEBUG: install progress fglrx-amdcccle 0.000000
2011-10-15 15:43:08,620 DEBUG: install progress fglrx-amdcccle 6.250000
2011-10-15 15:43:08,620 DEBUG: install progress fglrx-amdcccle 12.500000
2011-10-15 15:43:08,807 DEBUG: install progress fglrx-amdcccle 18.750000
2011-10-15 15:43:09,271 DEBUG: install progress fglrx 18.750000
2011-10-15 15:43:09,372 DEBUG: install progress fglrx 25.000000
2011-10-15 15:43:22,595 DEBUG: install progress fglrx 31.250000
2011-10-15 15:43:23,297 DEBUG: install progress fglrx 37.500000
2011-10-15 15:43:23,475 DEBUG: install progress bamfdaemon 37.500000
2011-10-15 15:43:23,651 DEBUG: install progress gnome-menus 37.500000
2011-10-15 15:43:23,819 DEBUG: install progress libc-bin 37.500000
2011-10-15 15:43:24,263 DEBUG: install progress ureadahead 37.500000
2011-10-15 15:43:24,448 DEBUG: install progress initramfs-tools 37.500000
2011-10-15 15:43:33,180 DEBUG: install progress dpkg-exec 37.500000
2011-10-15 15:43:33,785 DEBUG: install progress fglrx-updates 37.500000
2011-10-15 15:43:33,886 DEBUG: install progress fglrx-updates 43.750000
2011-10-15 15:43:37,302 DEBUG: install progress fglrx-updates 50.000000
2011-10-15 15:43:37,387 DEBUG: install progress fglrx-updates 56.250000
2011-10-15 15:43:37,599 DEBUG: install progress fglrx-amdcccle-updates 56.250000
2011-10-15 15:43:37,699 DEBUG: install progress fglrx-amdcccle-updates 62.500000
2011-10-15 15:43:38,262 DEBUG: install progress fglrx-amdcccle-updates 68.750000
2011-10-15 15:43:38,376 DEBUG: install progress fglrx-amdcccle-updates 75.000000
2011-10-15 15:43:38,471 DEBUG: install progress ureadahead 75.000000
2011-10-15 15:43:38,837 DEBUG: install progress dpkg-exec 75.000000
2011-10-15 15:43:38,873 DEBUG: install progress fglrx-updates 75.000000
2011-10-15 15:43:39,285 DEBUG: install progress fglrx-updates 81.250000
2011-10-15 15:43:56,002 DEBUG: install progress fglrx-updates 87.500000
2011-10-15 15:43:56,522 DEBUG: install progress bamfdaemon 87.500000
2011-10-15 15:43:56,699 DEBUG: install progress gnome-menus 87.500000
2011-10-15 15:43:56,935 DEBUG: install progress fglrx-amdcccle-updates 87.500000
2011-10-15 15:43:57,027 DEBUG: install progress fglrx-amdcccle-updates 93.750000
2011-10-15 15:43:57,127 DEBUG: install progress fglrx-amdcccle-updates 100.000000
2011-10-15 15:43:57,220 DEBUG: install progress initramfs-tools 100.000000
2011-10-15 15:44:04,739 DEBUG: install progress libc-bin 100.000000
2011-10-15 15:44:06,443 DEBUG: (Reading database ... 182059 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Selecting previously deselected package fglrx-updates.
(Reading database ... 181815 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a8.881-0ubuntu6_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a8.881-0ubuntu6_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-updates (2:8.881-0ubuntu6) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-8.881 DKMS files...
Building only for 3.0.0-12-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle-updates (2:8.881-0ubuntu6) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2011-10-15 15:44:06,683 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-15 15:44:06,753 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
2011-10-15 15:44:06,855 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:06,856 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:44:06,883 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:06,883 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:44:09,216 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:09,216 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:44:09,231 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:09,232 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:44:09,256 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:09,256 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:44:09,401 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:09,401 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:44:09,417 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:09,417 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:44:09,449 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:09,449 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:44:09,465 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:09,465 DEBUG: fglrx_updates is not the alternative in use
2011-10-15 15:44:09,488 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:09,489 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:44:13,535 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-15 15:44:13,535 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-15 15:44:15,467 DEBUG: Shutting down

```

---

