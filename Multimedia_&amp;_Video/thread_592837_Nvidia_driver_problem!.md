---
title: "Nvidia driver problem!"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by bordomat on 2007-10-26
Hi everyone,

I'm pretty new in all this, thou I have to say I learned some basics just in last two weeks since I installed Ubuntu 7.10. and tried to get my Nvidia driver to work. The problem I have is that when ever I enable nvidia driver, eather in xserver or restricted drivers manager, after reboot I get the black screen. When that appears, hard disk lights go off and keyboard stops working. The only thing that works is when I mark nv and not nvidia in xserver. But that does not allow me to use any fancy 3D stuff. I used Restricted drivers manager, Sypatic pagage manager and on the last try Envy, to install the driver. Any idea what' going one? Please be specific on what to do, I just started with linux.

I use:

Ubuntu 7.10 (gutsy)
Kernel Linux 2.6.22-14-generic
Gnome 2.20.0

Processor: AMD Athlon(tm) 64 Processor 300+
Nvidia Ge Force 6600GT

---

### Post by maculata on 2007-10-26
I'm having the same problem/issue. 

Ubuntu 7.10 (gutsy)
Kernel Linux 2.6.22-14-generic
Gnome 2.20.0

Processor: AMD Athlon(tm) 64 Processor 300+
Nvidia Ge Force 7600GT
__________________

---

### Post by PmDematagoda on 2007-10-26
Try this:-

1) Download the latest Nvidia driver for Linux.

2) Install the driver according to the instructions given on the Nvidia web site. You will also have to stop the X-server when installing the driver, a good way would be to install the driver in Recovery Mode.

3) After installation, configure the x-server using:-
```

sudo dpkg-reconfigure xserver-xorg
```

And then see if that solved your problem.

---

### Post by bordomat on 2007-10-27
I instailed the driver using the driver from Nvidia website. But now dont know how to start Nvidia xserver. When I go to Nvidia settings it says: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by PmDematagoda on 2007-10-27
Did you do:-

```
dpkg-reconfigure xserver-xorg
```

Select the driver as Nvidia. The other values can be default.

---

### Post by bordomat on 2007-10-28
I've been there, done that!!

---

### Post by mlalkaka on 2007-10-28
I am having the same problem with the nvidia driver; everything works fine with the nv driver, though. Has anyone been able to fix this? It worked fine in Ubuntu 7.04 (Feisty Fawn) for me.

Video Card: nVIDIA GeForce FX 5200
Processor: Intel Pentium 4 1.60 GHz
Distribution: Ubuntu 7.10 (Gutsy Gibbon)

By the way, when the black screen appears, you can press Ctrl+Alt+F1 to go to a console. That still works.

---

### Post by mlalkaka on 2007-10-28
I thought it might be useful to provide some more information. 
If I run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```, then restart my computer, X starts up perfectly and uses the nv driver. Now if all I do is modify the file /etc/X11/xorg.conf so that the line
```
Driver    "nv"
``` reads ```
Driver    "nvidia"
```
then X fails like I described in my last post. 

Also after switching to a terminal by pressing Ctrl+Alt+F1, if I check what processes are running, I can see that Xorg and gdm, among other graphical programs are running as root, which I think is supposed to be the failsafe X server. However, I cannot see the graphical interfaces of these programs, if I press any of Ctrl+Alt+F{1-12}.

The packages "nvidia-glx" (version 1.0.9639) and "nvidia-kernel-common" (version 20051028+1ubuntu7) are installed.

---

### Post by bordomat on 2007-10-28
More information:

I go to dpkg-reconfigure xserver-xorg and change "nv" to "nvidia". Afterwords it says: "file back up in etc/x11/xorg.conf.20071028090600. But if I go back to reconfigure xserver-xorg, "nv" is still there. I reboot and get the message: "Your screen and graphics card could not be detected correctly...." Then I suppose to set up the resolution etc.. For my card it shows Nvidia Geforce 6800 (generic). I have GeForce 6600gt Nvidia card. When I log on to ubuntu I have low graphics and resolution option only 600x800. If I try to go to Nvidia settings it still says: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
[B]
But I no longer have black screen at the beginning!!![/B]

Please be specific, I'm new in Linux!

Thank you...

---

### Post by mlalkaka on 2007-10-28
Ok I found some more information that should be useful. There are 3 versions of the nvidia driver on Ubuntu. Each version is in a different package:
[LIST]
[*]nvidia-glx-legacy contains version 1.0.7185
[*]nvidia-glx contains version 1.0.9639
[*]nvidia-glx-new contains version 100.14.19[/LIST]Each version supports a different set of nVIDIA graphics cards. Go to [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html) to determine which version supports your graphics card. If you don't know what graphics card you have, go to System > Preferences > Hardware Information, or run the command lspci on the command line.

I have an nVIDIA GeForce FX 5200, which needs nvidia-glx-new, but I had nvidia-glx installed. I'm going to try installing nvidia-glx-new and see whether that gets me any further.

---

### Post by mlalkaka on 2007-10-28
[SIZE=3][B]It worked!
[/B][SIZE=2]So here's the process from start to finish:
[/SIZE][/SIZE][LIST=1]
[*]```
sudo dpkg-reconfigure -phigh xserver-xorg
```
[*]Restart the computer. This will load the nv driver, and should at least get you further than the black screen.
[*]Log in to your desktop and run Synaptic Package Manager from System > Administration > Synaptic Package Manager.
[*]Search for the package "nvidia-glx-new". If you have a legacy card, search for "nvidia-glx-legacy" or "nvidia-glx". (See [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html) to determine which version is needed for your graphics card.) Install the package, and close Synaptic.
[*]Run the Restricted Drivers Manager by going to System > Administration > Restricted Drivers Manager. Enable the checkbox beside "NVIDIA accelerated graphics driver...". Then close Restricted Drivers Manager.
[*]Restart the computer. The nvidia driver should be used now instead of the nv driver. To check, run the command "glxgears". If you see three gears spinning, then graphics acceleration is working.[/LIST]I'm not sure whether steps 3 and 4 above are necessary; I think the Restricted Drivers Manager would perform those steps for you. I'm just reporting what worked for me.

Did this work for anyone else?

---

### Post by bordomat on 2007-10-28
None of that works for me. 

I formated and reinstalled Ubuntu 7.10. Installed nvidia driver version 100.14.19 (**Have nvidia GeForce 6600GT video card**) from official website. Went to safe mode and reconfigure  xserver; change "nv" to "nvidia" and it still wont log on. Unless I reconfigure xserver back to "nv" and log on under low resolution 800x600.

**Is there a way to look at the xserver specifics and find the problem?**

If I do "sudo nano /etc/x11/xorg.conf" I get an empty screen. Don't know what to do from then one.

---

### Post by mlalkaka on 2007-10-28
>  If I do "sudo nano /etc/x11/xorg.conf" I get an empty screen. Don't know what to do from then one.
That's weird. xorg.conf should definitely not be empty. Have you tried the steps I had posted earlier? I think the Restricted Drivers Manager may make certain modifications to the xorg.conf file that dpkg-reconfigure does not. So it may be worth trying. Also, I did not use the drivers from the nVIDIA website. I used the drivers from the Ubuntu main software repository.

---

### Post by Kool_Kat on 2007-10-28
Hi

I am having the same problem, in that Nvidia drivers are not working on 7.10 - and strangely I also have a 6600GT - coincidence?

I have tried everything that has been described and much more - and I am still stuck. See my post at the end of this thread here: [http://ubuntuforums.org/showthread.php?t=497284&highlight=easy](http://ubuntuforums.org/showthread.php?t=497284&highlight=easy)

Have you looked to see what errors are being generated by the xserver?
i.e. try - cat /etc/X11/Xorg.0.log

---

### Post by bordomat on 2007-10-28
I've tried your steps before. I've installed nvidia driver many times and used 3-4 diferent methods. Yours was one of them. I don't think the problem is in the driver or installation. I think the problem is in my settings. This is why I formated my partition and reinstalled ubuntu. Then on the fresh  sistem I installed nvidia driver. The only thing that it asked me for is "libc heather files". I got the package and the nvidia driver installation went through. Right after that I've tried "/etc/x11/xorg.conf enable and got nothing but an empty screen. No text, if there is to be one. After reboot got the black screen. Then had to change in xserver "nvidia" back to "nv" to be able to log on under low resolution. 

 "/etc/X11/Xorg.0.log" gives me the following screen:

---

### Post by Kool_Kat on 2007-10-28
But have you looked to see what errors have been produced in /var/log/Xorg.0.log or /var/log/kdm.log or gdm.log? - that might provide some clues.

I have noticed that there are quite a lot of people having problems on the forum with Gutsy and Nvidia - so we are not alone. But there does not seem to be a common answer to those that have managed to solve their problems, and there are quite a few like us who are still stranded without a solution.

---

### Post by bordomat on 2007-10-28
Agree...There is lots of posts about this issue.And I envy people that solved it. i just wanna get over it and move forward to explore the world of ubuntu. Im rookie as far Linux goes, so I'm sure there will be more mountains to climb.

This is why I appreciate any anwser and desire to help!

---

### Post by Kool_Kat on 2007-10-28
Hi - apologies - I slipped up with my last but one message. I should have referred you to /var/log/Xorg.0.log (case is important)....and not /etc/X11/... (that is where xorg.conf lives - sorry for the mixup).

Also suggest using cat and not nano - as nano will open an empty file if one does not exist...so clouding any problems related to non-existence....see my last post.

---

### Post by SoAnIs on 2007-10-28
Same goes for the Xorg.conf thing:
/etc/x11/xorg.conf
/etc/X11/xorg.conf
Those two are different! The X in X11 MUST be capital.

---

### Post by bordomat on 2007-10-28
My /etc/X11/xorg.conf file:
 [HTML]xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "si"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV43 [GeForce 6600 GT]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6600 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection[/HTML]

---

### Post by bordomat on 2007-10-28
And a /var/log/Xorg.0.log file:

[HTML]/var/log/kdm.log
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux matej-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Build Date: 29 September 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 29 01:28:13 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV43 [GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cd8a0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cd8a0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1458,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1458,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1458,5004 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,00ea card 1458,a002 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1458,b002 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f1 card 107d,2011 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 14f1,8800 card 1462,8606 rev 05 class 04,00,00 hdr 80
(II) PCI: 02:07:1: chip 14f1,8801 card 1462,8606 rev 05 class 04,80,00 hdr 80
(II) PCI: 02:08:0: chip 1102,0002 card 1102,8065 rev 0a class 04,01,00 hdr 80
(II) PCI: 02:08:1: chip 1102,7002 card 1102,0020 rev 0a class 09,80,00 hdr 80
(II) PCI: 02:09:0: chip 1033,00f2 card 1033,00ce rev 01 class 0c,00,10 hdr 00
(II) PCI: 02:0a:0: chip 1186,1300 card 1186,1303 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 11ab,4320 card 1458,e000 rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xf2000000 - 0xf4ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000a000 - 0x0000a0ff (0x100) IX[B]
        [1] -1  0       0x0000a400 - 0x0000a4ff (0x100) IX[B]
        [2] -1  0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [3] -1  0       0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xf5000000 - 0xf8ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0x50000000 - 0x500fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] rev 162, Mem @ 0xf2000000/24, 0xe0000000/28, 0xf3000000/24
(--) PCI: (2:7:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xf5000000/24
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x100000000) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf1ffffff to 0xefffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xf8000000 - 0xf8003fff (0x4000) MX[B]
        [1] -1  0       0xf8005000 - 0xf80050ff (0x100) MX[B]
        [2] -1  0       0xf8004000 - 0xf8004fff (0x1000) MX[B]
        [3] -1  0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [4] -1  0       0xf9001000 - 0xf9001fff (0x1000) MX[B]
        [5] -1  0       0xf9005000 - 0xf90050ff (0x100) MX[B]
        [6] -1  0       0xf9004000 - 0xf9004fff (0x1000) MX[B]
        [7] -1  0       0xf9003000 - 0xf9003fff (0x1000) MX[B]
        [8] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [9] -1  0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [10] -1 0       0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [12] -1 0       0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
        [13] -1 0       0x0000ac00 - 0x0000acff (0x100) IX[B]
        [14] -1 0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [15] -1 0       0x0000a400 - 0x0000a407 (0x8) IX[B]
        [16] -1 0       0x0000a000 - 0x0000a01f (0x20) IX[B]
        [17] -1 0       0x0000e000 - 0x0000e07f (0x80) IX[B]
        [18] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [19] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [20] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [21] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [22] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [23] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [24] -1 0       0x0000c000 - 0x0000c07f (0x80) IX[B]
        [25] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
        [26] -1 0       0x00002000 - 0x0000203f (0x40) IX[B]
        [27] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [28] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xf8000000 - 0xf8003fff (0x4000) MX[B]
        [1] -1  0       0xf8005000 - 0xf80050ff (0x100) MX[B]
        [2] -1  0       0xf8004000 - 0xf8004fff (0x1000) MX[B]
        [3] -1  0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [4] -1  0       0xf9001000 - 0xf9001fff (0x1000) MX[B]
        [5] -1  0       0xf9005000 - 0xf90050ff (0x100) MX[B]
        [6] -1  0       0xf9004000 - 0xf9004fff (0x1000) MX[B]
        [7] -1  0       0xf9003000 - 0xf9003fff (0x1000) MX[B]
        [8] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [9] -1  0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [10] -1 0       0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [12] -1 0       0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
        [13] -1 0       0x0000ac00 - 0x0000acff (0x100) IX[B]
        [14] -1 0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [15] -1 0       0x0000a400 - 0x0000a407 (0x8) IX[B]
        [16] -1 0       0x0000a000 - 0x0000a01f (0x20) IX[B]
        [17] -1 0       0x0000e000 - 0x0000e07f (0x80) IX[B]
        [18] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [19] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [20] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [21] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [22] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [23] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [24] -1 0       0x0000c000 - 0x0000c07f (0x80) IX[B]
        [25] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
        [26] -1 0       0x00002000 - 0x0000203f (0x40) IX[B]
        [27] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [28] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf8000000 - 0xf8003fff (0x4000) MX[B]
        [5] -1  0       0xf8005000 - 0xf80050ff (0x100) MX[B]
        [6] -1  0       0xf8004000 - 0xf8004fff (0x1000) MX[B]
        [7] -1  0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [8] -1  0       0xf9001000 - 0xf9001fff (0x1000) MX[B]
        [9] -1  0       0xf9005000 - 0xf90050ff (0x100) MX[B]
        [10] -1 0       0xf9004000 - 0xf9004fff (0x1000) MX[B]
        [11] -1 0       0xf9003000 - 0xf9003fff (0x1000) MX[B]
        [12] -1 0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [13] -1 0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [14] -1 0       0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
        [15] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [16] -1 0       0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
        [17] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [18] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [19] -1 0       0x0000ac00 - 0x0000acff (0x100) IX[B]
        [20] -1 0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [21] -1 0       0x0000a400 - 0x0000a407 (0x8) IX[B]
        [22] -1 0       0x0000a000 - 0x0000a01f (0x20) IX[B]
        [23] -1 0       0x0000e000 - 0x0000e07f (0x80) IX[B]
        [24] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [25] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [26] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [27] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [28] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [29] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [30] -1 0       0x0000c000 - 0x0000c07f (0x80) IX[B]
        [31] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
        [32] -1 0       0x00002000 - 0x0000203f (0x40) IX[B]
        [33] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [34] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux matej-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
Build Date: 29 September 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 29 01:28:13 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV43 [GeForce 6600 GT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cd8a0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1458,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1458,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1458,5004 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,00ea card 1458,a002 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1458,b002 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,00f1 card 107d,2011 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 14f1,8800 card 1462,8606 rev 05 class 04,00,00 hdr 80
(II) PCI: 02:07:1: chip 14f1,8801 card 1462,8606 rev 05 class 04,80,00 hdr 80
(II) PCI: 02:08:0: chip 1102,0002 card 1102,8065 rev 0a class 04,01,00 hdr 80
(II) PCI: 02:08:1: chip 1102,7002 card 1102,0020 rev 0a class 09,80,00 hdr 80
(II) PCI: 02:09:0: chip 1033,00f2 card 1033,00ce rev 01 class 0c,00,10 hdr 00
(II) PCI: 02:0a:0: chip 1186,1300 card 1186,1303 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 11ab,4320 card 1458,e000 rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:51:24 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.3.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 2.1.5
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
       ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
        Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
        Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
        GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
        GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
        Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
        GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
        GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
        GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
        GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
        GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
        GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
        Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
        GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
        GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
        GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
        Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
        GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
        Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
        GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
        GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
        GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
        GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
        GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
        GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
        Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
        GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
        GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
        GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
        GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
        GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
        Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
        GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
        GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
        GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
        GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
        Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
        GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
        GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
        GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
        Quadro FX 540, GeForce 6200, GeForce 6500,
        GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
        Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
        GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
        GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
        GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
        Quadro FX 540, GeForce 6200, GeForce 6500,
        GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
        GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
        GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
        GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
        GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
        GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
        GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
        GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
        GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
        GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
        GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
        GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
        Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
        GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
        GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
        Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
        Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
        GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
        GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
        GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT, GeForce 8700M GT,
        Quadro FX 370, Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M,
        Quadro FX 570, Quadro FX 1700, GeForce 8500 GT, GeForce 8400 GS,
        GeForce 8300 GS, GeForce 8600M GS, GeForce 8400M GT,
        GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
        Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce 6600 GT found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf8000000 - 0xf8003fff (0x4000) MX[B]
        [5] -1  0       0xf8005000 - 0xf80050ff (0x100) MX[B]
        [6] -1  0       0xf8004000 - 0xf8004fff (0x1000) MX[B]
        [7] -1  0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [8] -1  0       0xf9001000 - 0xf9001fff (0x1000) MX[B]
        [9] -1  0       0xf9005000 - 0xf90050ff (0x100) MX[B]
        [10] -1 0       0xf9004000 - 0xf9004fff (0x1000) MX[B]
        [11] -1 0       0xf9003000 - 0xf9003fff (0x1000) MX[B]
        [12] -1 0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [13] -1 0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [14] -1 0       0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
        [15] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [16] -1 0       0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
        [17] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [18] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [19] -1 0       0x0000ac00 - 0x0000acff (0x100) IX[B]
        [20] -1 0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [21] -1 0       0x0000a400 - 0x0000a407 (0x8) IX[B]
        [22] -1 0       0x0000a000 - 0x0000a01f (0x20) IX[B]
        [23] -1 0       0x0000e000 - 0x0000e07f (0x80) IX[B]
        [24] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [25] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [26] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [27] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [28] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [29] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [30] -1 0       0x0000c000 - 0x0000c07f (0x80) IX[B]
        [31] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
        [32] -1 0       0x00002000 - 0x0000203f (0x40) IX[B]
        [33] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [34] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf8000000 - 0xf8003fff (0x4000) MX[B]
        [5] -1  0       0xf8005000 - 0xf80050ff (0x100) MX[B]
        [6] -1  0       0xf8004000 - 0xf8004fff (0x1000) MX[B]
        [7] -1  0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [8] -1  0       0xf9001000 - 0xf9001fff (0x1000) MX[B]
        [9] -1  0       0xf9005000 - 0xf90050ff (0x100) MX[B]
        [10] -1 0       0xf9004000 - 0xf9004fff (0x1000) MX[B]
        [11] -1 0       0xf9003000 - 0xf9003fff (0x1000) MX[B]
        [12] -1 0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [13] -1 0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [14] -1 0       0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
        [15] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [16] -1 0       0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
        [17] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [18] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [19] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x0000ac00 - 0x0000acff (0x100) IX[B]
        [23] -1 0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [24] -1 0       0x0000a400 - 0x0000a407 (0x8) IX[B]
        [25] -1 0       0x0000a000 - 0x0000a01f (0x20) IX[B]
        [26] -1 0       0x0000e000 - 0x0000e07f (0x80) IX[B]
        [27] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [28] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [29] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [30] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [31] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [32] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [33] -1 0       0x0000c000 - 0x0000c07f (0x80) IX[B]
        [34] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
        [35] -1 0       0x00002000 - 0x0000203f (0x40) IX[B]
        [36] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [37] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [38] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [39] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(WW) NV(0): Bad V_BIOS checksum
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6600 GT"
(II) NV(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE0000000
(--) NV(0): MMIO registers at 0xF2000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: SAM  Model: 1b6  Serial#: 1447309625
(II) NV(0): Year: 2005  Week: 51
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) NV(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) NV(0): Monitor name: SyncMaster
(II) NV(0): Serial No: HVFYC03770
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff004c2db60139314456
(II) NV(0):     330f010380261e782aee95a3544c9926
(II) NV(0):     0f5054bfef8081808140714f01010101
(II) NV(0):     010101010101302a009851002a403070
(II) NV(0):     1300782d1100001e000000fd00384c1e
(II) NV(0):     510e000a202020202020000000fc0053
(II) NV(0):     796e634d61737465720a2020000000ff
(II) NV(0):     00485646594330333737300a2020001f
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 1024
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) NV(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) NV(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) NV(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) NV(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) NV(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) NV(0): Panel is TMDS
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) NV(0): Estimated virtual size for aspect ratio 1.2667 is 1280x1024
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using driver mode "1280x1024" (hsync out of range)
(--) NV(0): Virtual size is 1280x1024 (pitch 1280)
(**) NV(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0): *Driver mode "1280x1024": 109.0 MHz, 63.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(**) NV(0): *Driver mode "1280x1024": 90.8 MHz, 63.0 kHz, 59.8 Hz
(II) NV(0): Modeline "1280x1024"   90.75  1280 1328 1360 1440  1024 1027 1034 1054 +hsync -vsync
(**) NV(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0): *Driver mode "1280x960": 101.2 MHz, 59.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(**) NV(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) NV(0): *Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) NV(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) NV(0): *Driver mode "1152x864": 104.0 MHz, 67.7 kHz, 74.8 Hz
(II) NV(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) NV(0): *Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) NV(0): *Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) NV(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0): Display dimensions: (380, 300) mm
(**) NV(0): DPI set to (85, 86)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xf3000000 - 0xf3ffffff (0x1000000) MX[B]
        [1] 0   0       0xe0000000 - 0xefffffff (0x10000000) MX[B]
        [2] 0   0       0xf2000000 - 0xf2ffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xf8000000 - 0xf8003fff (0x4000) MX[B]
        [8] -1  0       0xf8005000 - 0xf80050ff (0x100) MX[B]
        [9] -1  0       0xf8004000 - 0xf8004fff (0x1000) MX[B]
        [10] -1 0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [11] -1 0       0xf9001000 - 0xf9001fff (0x1000) MX[B]
        [12] -1 0       0xf9005000 - 0xf90050ff (0x100) MX[B]
        [13] -1 0       0xf9004000 - 0xf9004fff (0x1000) MX[B]
        [14] -1 0       0xf9003000 - 0xf9003fff (0x1000) MX[B]
        [15] -1 0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [16] -1 0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [17] -1 0       0xf3000000 - 0xf3ffffff (0x1000000) MX[B](B)
        [18] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [19] -1 0       0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
        [20] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [21] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [22] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [23] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [24] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [25] -1 0       0x0000ac00 - 0x0000acff (0x100) IX[B]
        [26] -1 0       0x0000a800 - 0x0000a8ff (0x100) IX[B]
        [27] -1 0       0x0000a400 - 0x0000a407 (0x8) IX[B]
        [28] -1 0       0x0000a000 - 0x0000a01f (0x20) IX[B]
        [29] -1 0       0x0000e000 - 0x0000e07f (0x80) IX[B]
        [30] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [31] -1 0       0x00000b70 - 0x00000b73 (0x4) IX[B]
        [32] -1 0       0x00000970 - 0x00000977 (0x8) IX[B]
        [33] -1 0       0x00000bf0 - 0x00000bf3 (0x4) IX[B]
        [34] -1 0       0x000009f0 - 0x000009f7 (0x8) IX[B]
        [35] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [36] -1 0       0x0000c000 - 0x0000c07f (0x80) IX[B]
        [37] -1 0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
        [38] -1 0       0x00002000 - 0x0000203f (0x40) IX[B]
        [39] -1 0       0x00001c00 - 0x00001c3f (0x40) IX[B]
        [40] -1 0       0x0000e400 - 0x0000e41f (0x20) IX[B]
        [41] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [42] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xe0000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Scanline Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "si"
(**) Generic Keyboard: XkbLayout: "si"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9[/HTML]

---

### Post by gp95ac on 2007-10-28
I was having no end of trouble with mt older nvidia card (combined with a widescreen monitor)
Obviously do this
 
sudo dpkg-reconfigure xserver-xorg

and pay attention to the questions, i made several small slips, so i had to run it multiple times.

Also see system->admin->screens and graphics, there are some settings in there you may need to correct

As inspiration, the relevant section of my xorg, running 1440x900, compiz, avant

Section "Device"
	Identifier	"nVidia Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 940T/940B/940Fn(Analog)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV15 [GeForce2 GTS/Pro]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1440x900@75"	"1440x900@60"	"1280x800@60"	"1600x1024@60"	"1280x768@75"	"1680x1050@60"	"1280x800@75"	"1920x1200@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

---

### Post by Kool_Kat on 2007-10-29
bordomat

you have posted the wrong log file i.e. from the time you were using the Driver="nv" option - not the one from when you set Driver="nvidia" - so we cannot see what the errors are - for there are none (apart from not being able to use glx of course).

---

### Post by gganitis on 2007-10-29
Hello everybody! I have the same problems too!

Using nv driver, I can have the resolution I want, but I can't enable visual effects.
Using the nvidia driver by the restricted manager, when I am booting I receive a failure message and the low resolution menu to chose my monitor and my driver, but I still see my desktop on 800X600!

I have tried everything you have written in this threat but, nothing happened!

---

### Post by Phrellex on 2007-10-30
I am having alot of problems with nvidia drivers on my geforce 6200. Firstly it detects as 6800 (generic) in Screens and Graphics. I can use restricted drivers, which run fine with the game Urban Terror, but any games that I use in wine are poor quality and run laggy. My graphics card did run fine in Fiesty, until I thought upgrading could be a good idea. After the upgrade I was faced with a black screen and numerous error messages, saying about too much work. Login did work and so did command prompt after it shutdown the non functioning xserver. 

Running the command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

does get the computer running, but as previously stated here, the graphics set themselves to allow resolutions, but to allow OpenGL effects on desktop, you must enable the restricted driver, while there Envy drivers installed.

I have tried alot of attempts at fixing it and nothing has proven much sucess.

---

### Post by ndefron on 2007-10-31
to: ggantis

you have exactly the same problem as me - have you found a way to enable the effects yet?


i've got: amd64,  nvidia 8600 gt

kind regards
ndefron

---

### Post by Eddie Wilson on 2007-10-31
To start off with my graphics was working great. Then one day without notice I got a black screen. when I did get booted up I was stuck on 800x600 and could not change it. Also none of my 3d app. would work. What I did to fix the problem was going to Synaptic, and I pick the Nvidia new driver. I then installed and at the same time it uninstalled the old Nvidia driver. After that I went to restricted drivers and enabled the nvidia driver. After reboot all my problems were solved. Anyway thats what I did to fix my graphic problems. 
Eddie

---

### Post by emperon on 2007-10-31
I had the same problem too. I used Envy and it fixed the issue.

---

### Post by gganitis on 2007-11-01
Ndefron I haven't solved my problem! I tried and the way installing nvidia driver, as the official site of the nvidia says. I read and tried some advice of the 
[http://www.nvnews.net/vbulletin/showthread.php?t=101008](http://www.nvnews.net/vbulletin/showthread.php?t=101008)
but nothing still happened.
I run again the x server, made many backups of the xorg.conf, but it didn't work.


Does anyone know what has to do with the envy? Is that important? May it solve our problem?
What has to do the driver and the visual effects with glx and the XGL?
   [http://ubuntuforums.org/showthread.php?t=580082&highlight=xgl+server+gutsy](http://ubuntuforums.org/showthread.php?t=580082&highlight=xgl+server+gutsy)
   [http://www.nvnews.net/vbulletin/showthread.php?t=101008](http://www.nvnews.net/vbulletin/showthread.php?t=101008)

---

### Post by gganitis on 2007-11-01
I am going to install envy as emperon suggests...

---

### Post by ndefron on 2007-11-01
ok. i'm fixed!

this is what i did:

disabled the restricted driver, 'nvidia accelerated graphics driver' in restricted drivers manager. 

removed the nvidia drivers that i had installed via synaptic. 

rebooted into low graphics mode, then ran envy.

(envy automatically downloaded and rebuilt the nvidia drivers for me.)

re-enabled the accelerated graphics driver.. 

rebooted, and all was super slick again:)

---

### Post by gganitis on 2007-11-02
I had a really long adventure, but I made the driver work.

Mainly I did it using the envy, but there happened and it couldn't finish the installation. It was because it didn't find the sources to download the right driver. So I went manually, by the site of the nvidia, I put the file in the directory envy said, and it worked. After that an other error occurred and it was telling me that I am connected in a PROXY, although I wasn't. 

Now... the driver works fine but the visual effects work on "Normal".

And we start from the beginning, because when I go to enable the "Extra" visual effects I receive a message to "Install the Nvidia driver"!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Any help please???

---

### Post by gganitis on 2007-11-02
OK it worked!!!

I just said enable the driver and after the restart, it was ok in extra effects. Before, it wasn't ok probably because the driver of the nvidia wasn't right and it couldn't find the right one on its own.

(Be careful when you install the driver with the envy. if it doesn't find the file you need, you can find it on your own and copy it on the directory it says you)

Thanks for the advice.
Good luck!

---

### Post by oedha on 2007-11-02
What card did you have....?
I had NVIDIA 7000m and i've been work on it for a month
i knew the type from windows installation and the manual book
now i can make it work.
this what i did

1. go to application - add/remove
2. type in nvidia ( look at all available software, reload if necessary )
3. i choose NVIDIA binary x.org ( 'new' driver )
4. go to terminal
5. sudo /etc/X11/xorg.conf
6. i changed the resolution from "800x600" to "1280x800" manually
7. save and reboot
8. now my geforce 7000m works

OedhA

---

### Post by ddavod on 2007-11-04
please geforce 7600 gt driver for ubuntu 7.10

---

### Post by ndefron on 2007-11-04
ddavod

i'm no expert, however i recommend you download and run envy:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

kind regards
ndefron

---

### Post by gganitis on 2007-11-05
I suggest you too download the envy
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb)

By the window manager, simply as in windows you would do, run this file and everything is goint to be alright!

_Be carefull and watch the messages you receive_ while envy installs the right card. For example in my case, it didn't find the file of the driver which was needed and I went to 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
I downloaded it manually and I copied to the directory envy said. (It was writing that it didn't find the file, try again, or download and copy the file to the *blablabla* directory.

I am a new user too, I hope so I help you

---

### Post by artilheiro20 on 2007-11-05
hello everyone..
i have a Nvidia Geforce4 mx440, and i want to install linux ubuntu 7.10 with that nice effects.. :lolflag:

i'm a "new guy" in the linux area, can you pleaaase tell me how to install the driver and how to put this working please...


thanks :)

---

### Post by gganitis on 2007-11-05
I guess you have installed the Ubuntu 7.04 Feisty...??? You want to upgrade?

---

### Post by TurnedintoaNewt on 2007-11-05
I was having the same issue with the blank screen after enabling the proprietary nvidia driver.  I am using a dell inspiron 8200 with the geforce 440 go card.

i looked on the nvidia linux support forum and an answer to this same question was to add the following to the display driver section in xorg.conf

Option    "UseDisplayDevice" "DFP"


I did that and it worked, don't know what it does, but it worked...

now if i can get it to actually set the resolution i want...then it would be perfect

---

### Post by FooAtari on 2007-11-06
I have a 7300GT and a 19" wide screen monitor. Also having black screen problems.

Some good suggestions here that might help.

Have a couple of questions though.

Does using Synaptic, Envy, the Nvidia driver site or the Proprietary driver menu all install the most recent drivers?

And Im interested to know what Option "UseDisplayDevice" "DFP" does?

---

### Post by oedha on 2007-11-08
Based on my experience, i can't solve my problem with envy
i solved it manually

For GeForce440....i think you should download NVIDIA binary X.Org 'legacy' driver from Applications - Add/Remove
then go to restricted.....enable it
restart
change the resolution
( before change the resolution, maybe you can check whether your driver has been installed or not from System - Administration - Screen & Graphic - Graphic Card tab, if you see nvidia there......you can change the res )

~O~

---

### Post by speedqueen on 2007-11-25
I'm having this same issue.  One thing that occurred to me is that it might be a hardware issue.  Older NVIDIA cards may be in their own slot rather than a PCI.  I'm going to update my bios and change the location of my video card.  Sorry if this is vague.  I'll post specifics if it works.

I'm running GeForce4 Ti 4400 with legacy drivers and Linux reverts to Generic settings (Vesa @ 640x480) upon reboot.

---

### Post by kolibri on 2007-12-18
Same problem here.

I upgraded to Gutsy, and now it won't use the NVIDIA driver.  I have one monitor working on low resolution, i need to get the other monitor up and going.

I downloaded and installed the latest NVIDIA driver.

 'sudo nvidia-settings'
 gets me to a NVIDIA X Server Settings dialog, and the error message:
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

'nvidia-xconfig' does not change anything- I still get this error.

this is what xorg.conf has:
-----------
Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7300 GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
--------------

If I go to the restricted drivers manager is says that the NVIDIA driver is enabled but not in use. 

How do I get the NVIDIA driver to actually be used?

---

### Post by kkolev on 2007-12-19
Hi guys,
I am not sure if this have been written somewhere but here what I have done to make my GF 7600 (8xAGP) work:

I installed the latest nvidia driver.
I found that the module l2c_core is loaded.
I put it in the /etc/modprobe/blacklist so it don't get loaded.
I edited the xorg.conf file and enabled the nvidia driver.
Finally I restarted the Gutsy.

Hope this works for you guys that have a NVidia AGP card which is recognized as a PCIe card.

---

