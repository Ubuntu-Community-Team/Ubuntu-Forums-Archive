---
title: "ubuntu 12.02 Fatal server error: no screens found (EE)"
date: 2014-02-12
forum: Multimedia Software
---

### Post by frank_de_kievit on 2014-02-12
Hi,

I recently ran the update manager and updated my stuff.
unfortunatelly i also upgraded the nvidia driver - which causes my system not to recognise my screens anymore.
if i startup ubuntu now i get only the command line.

i tried repairing xserver-xorg and reinstalling x.org.

at some point i had it working again on 1 monitor (im using 2) but after rebooting it didnt anymore :(

I dont know how to fix this and really need help.


I have a log file of x.org but i cannot post it here since i cant access it at the moment (posting this from the win7 installed as dual boot on the same system)


P.s. I tried several suggestions found on the forum but nothing works so far...
(tried: sudo dpkg-reconfogure xserver-xorg
sudo service gdm start (doesnt recognise service)

tried sudo unity but it gives a warning that no displays are found.


P.p.s. title needs to be 12.04 not 12.02 :x

---

### Post by frank_de_kievit on 2014-02-12
I managed to upload the Xorg.0.log file using dropbox:

> 
[     3.094] 
X.Org X Server 1.12.3
Release Date: 2012-07-09
[     3.094] X Protocol Version 11, Revision 0
[     3.094] Build Operating System: Linux 2.6.24-29-xen x86_64 Ubuntu
[     3.094] Current Operating System: Linux fronk-K55VD 3.8.0-35-generic #52~precise1-Ubuntu SMP Thu Jan 30 17:24:40 UTC 2014 x86_64
[     3.094] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-35-generic root=UUID=440cae76-d7a4-4c2b-88b9-00d7794d7df0 ro quiet splash
[     3.094] Build Date: 09 July 2012  05:20:18PM
[     3.094] xorg-server 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     3.094] Current version of pixman: 0.30.2
[     3.094]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     3.094] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.094] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 12 12:42:34 2014
[     3.097] (==) Using config file: "/etc/X11/xorg.conf"
[     3.097] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.097] (==) ServerLayout "layout"
[     3.097] (**) |-->Screen "nvidia" (0)
[     3.097] (**) |   |-->Monitor "<default monitor>"
[     3.098] (**) |   |-->Device "nvidia"
[     3.098] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[     3.098] (**) |-->Inactive Device "intel"
[     3.098] (==) Automatically adding devices
[     3.098] (==) Automatically enabling devices
[     3.098] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.098]     Entry deleted from font path.
[     3.098] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.098]     Entry deleted from font path.
[     3.098] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.098]     Entry deleted from font path.
[     3.098] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.098]     Entry deleted from font path.
[     3.098] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.098]     Entry deleted from font path.
[     3.098] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     3.098]     Entry deleted from font path.
[     3.098] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     3.098] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.098] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.098] (II) Loader magic: 0x7f289d9d8b00
[     3.098] (II) Module ABI versions:
[     3.098]     X.Org ANSI C Emulation: 0.4
[     3.098]     X.Org Video Driver: 12.0
[     3.098]     X.Org XInput driver : 16.0
[     3.098]     X.Org Server Extension : 6.0
[     3.099] (--) PCI:*(0:0:2:0) 8086:0166:1043:1457 rev 9, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[     3.099] (--) PCI: (0:1:0:0) 10de:1058:1043:1457 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/134217728, 0xe8000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     3.099] (II) Open ACPI successful (/var/run/acpid.socket)
[     3.099] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     3.099] (II) "extmod" will be loaded by default.
[     3.099] (II) "dbe" will be loaded by default.
[     3.099] (II) "glx" will be loaded by default.
[     3.099] (II) "record" will be loaded by default.
[     3.099] (II) "dri" will be loaded by default.
[     3.099] (II) "dri2" will be loaded by default.
[     3.099] (II) LoadModule: "extmod"
[     3.100] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     3.101] (II) Module extmod: vendor="X.Org Foundation"
[     3.101]     compiled for 1.12.3, module version = 1.0.0
[     3.101]     Module class: X.Org Server Extension
[     3.101]     ABI class: X.Org Server Extension, version 6.0
[     3.101] (II) Loading extension MIT-SCREEN-SAVER
[     3.101] (II) Loading extension XFree86-VidModeExtension
[     3.101] (II) Loading extension XFree86-DGA
[     3.101] (II) Loading extension DPMS
[     3.101] (II) Loading extension XVideo
[     3.101] (II) Loading extension XVideo-MotionCompensation
[     3.101] (II) Loading extension X-Resource
[     3.101] (II) LoadModule: "dbe"
[     3.101] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     3.101] (II) Module dbe: vendor="X.Org Foundation"
[     3.101]     compiled for 1.12.3, module version = 1.0.0
[     3.101]     Module class: X.Org Server Extension
[     3.101]     ABI class: X.Org Server Extension, version 6.0
[     3.101] (II) Loading extension DOUBLE-BUFFER
[     3.101] (II) LoadModule: "glx"
[     3.101] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.103] (II) Module glx: vendor="X.Org Foundation"
[     3.104]     compiled for 1.12.3, module version = 1.0.0
[     3.104]     ABI class: X.Org Server Extension, version 6.0
[     3.104] (==) AIGLX enabled
[     3.104] (II) Loading extension GLX
[     3.104] (II) LoadModule: "record"
[     3.104] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     3.105] (II) Module record: vendor="X.Org Foundation"
[     3.105]     compiled for 1.12.3, module version = 1.13.0
[     3.105]     Module class: X.Org Server Extension
[     3.105]     ABI class: X.Org Server Extension, version 6.0
[     3.105] (II) Loading extension RECORD
[     3.105] (II) LoadModule: "dri"
[     3.105] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     3.105] (II) Module dri: vendor="X.Org Foundation"
[     3.105]     compiled for 1.12.3, module version = 1.0.0
[     3.105]     ABI class: X.Org Server Extension, version 6.0
[     3.105] (II) Loading extension XFree86-DRI
[     3.105] (II) LoadModule: "dri2"
[     3.105] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     3.106] (II) Module dri2: vendor="X.Org Foundation"
[     3.106]     compiled for 1.12.3, module version = 1.2.0
[     3.106]     ABI class: X.Org Server Extension, version 6.0
[     3.106] (II) Loading extension DRI2
[     3.106] (II) LoadModule: "nvidia"
[     3.106] (WW) Warning, couldn't open module nvidia
[     3.106] (II) UnloadModule: "nvidia"
[     3.106] (II) Unloading nvidia
[     3.106] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     3.106] (II) LoadModule: "modesetting"
[     3.106] (WW) Warning, couldn't open module modesetting
[     3.106] (II) UnloadModule: "modesetting"
[     3.106] (II) Unloading modesetting
[     3.106] (EE) Failed to load module "modesetting" (module does not exist, 0)
[     3.106] (==) Matched intel as autoconfigured driver 0
[     3.106] (==) Matched vesa as autoconfigured driver 1
[     3.106] (==) Matched fbdev as autoconfigured driver 2
[     3.106] (==) Assigned the driver to the xf86ConfigLayout
[     3.106] (II) LoadModule: "intel"
[     3.106] (WW) Warning, couldn't open module intel
[     3.106] (II) UnloadModule: "intel"
[     3.106] (II) Unloading intel
[     3.106] (EE) Failed to load module "intel" (module does not exist, 0)
[     3.106] (II) LoadModule: "vesa"
[     3.107] (WW) Warning, couldn't open module vesa
[     3.107] (II) UnloadModule: "vesa"
[     3.107] (II) Unloading vesa
[     3.107] (EE) Failed to load module "vesa" (module does not exist, 0)
[     3.107] (II) LoadModule: "fbdev"
[     3.107] (WW) Warning, couldn't open module fbdev
[     3.107] (II) UnloadModule: "fbdev"
[     3.107] (II) Unloading fbdev
[     3.107] (EE) Failed to load module "fbdev" (module does not exist, 0)
[     3.107] (II) LoadModule: "modesetting"
[     3.107] (WW) Warning, couldn't open module modesetting
[     3.107] (II) UnloadModule: "modesetting"
[     3.107] (II) Unloading modesetting
[     3.107] (EE) Failed to load module "modesetting" (module does not exist, 0)
[     3.107] (EE) No drivers available.
[     3.107] 
Fatal server error:
[     3.107] no screens found
[     3.107] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[     3.107] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     3.107] 


---

### Post by agross2 on 2014-02-12
I have the same problem: I'm running 12.04 on an Asus laptop.  I ran updates, and the next time I logged on, the screen went blank at the login screen.

If I plug in an second monitor, it detects that, but it doesn't recognize the laptop monitor.

Some similar cases I've found:

**xorg catches segmentation fault** - [http://ubuntuforums.org/showthread.php?t=2200018&highlight=screen+detected](http://ubuntuforums.org/showthread.php?t=2200018&highlight=screen+detected)
I didn't understand a lot of this, and so far its unresolved

**No screens found error** - [http://ubuntuforums.org/showthread.php?t=2205096&highlight=xorg](http://ubuntuforums.org/showthread.php?t=2205096&highlight=xorg)
Also unresolved

**Does not detect laptop display** - [http://ubuntuforums.org/showthread.php?t=850326](http://ubuntuforums.org/showthread.php?t=850326)
Someone suggests moving the file /etc/X11/xorg.conf so that settings reset.  I'm trying this now and will update momentarily.

---

### Post by agross2 on 2014-02-12
Didn't work.  

New plans:
1) compare settings between my computer and my brother's computer.  Both are running 12.04 on Asus laptops with the same graphics cards.
2) Replace the driver?

---

### Post by agross2 on 2014-02-12
Removing the xorg.conf file had no effect.  Replacing it with xorg.conf.failsafe had an effect, but not the one I wanted.

I replaced xorg.conf with xorg.conf.failsafe.  My original problem is that the graphics display on an external monitor, but the laptop screen is dead.  When I replaced xorg.conf and booted up, the laptop screen and the external screen entered a tty1 shell environment.  The downside is that it didn't load the GUI at all, but the upside is, it outputted to the laptop screen.  

I'm going to resume trying to replace the driver.

---

### Post by frank_de_kievit on 2014-02-12
Ok, a bit of an overkill, but i managed to get into command line using ctrl+alt+f4.
on the command line i typed "sudo apt-get purge nvidia-*"

this removes all nvidia drivers from the system.

it works, im back in ubuntu!

---

### Post by agross2 on 2014-02-12
Removing the xorg.conf file had no effect.  Replacing it with xorg.conf.failsafe had an effect, but not the one I wanted.

I replaced xorg.conf with xorg.conf.failsafe.  My original problem is that the graphics display on an external monitor, but the laptop screen is dead.  When I replaced xorg.conf and booted up, the laptop screen and the external screen entered a tty1 shell environment.  The downside is that it didn't load the GUI at all, but the upside is, it outputted to the laptop screen.  

I'm going to resume trying to replace the driver.

---

### Post by angenio2 on 2014-08-14
This works for me. Thanks.

---

### Post by angenio2 on 2014-08-14
> **frank_de_kievit said:**
> Ok, a bit of an overkill, but i managed to get into command line using ctrl+alt+f4.
on the command line i typed "sudo apt-get purge nvidia-*"

this removes all nvidia drivers from the system.

it works, im back in ubuntu!

sudo apt-get purge nvidia-* works for me. Thank you.

---

