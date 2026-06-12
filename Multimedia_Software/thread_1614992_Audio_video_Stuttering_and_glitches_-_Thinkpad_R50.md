---
title: "Audio video Stuttering and glitches - Thinkpad R50e"
date: 2010-11-06
forum: Multimedia Software
---

### Post by Closrapexa on 2010-11-06
I'm still having  a problem with this. I don't know what information I should provide,  but I installed 10.10 a few days ago on my Thinkpad r50e, and there  seems to be a lag in the mouse movement, and a severe stutter in video.  When I play only music, it's a little better, but still very noticeable.

I thought gstreamer-properties would help, and I switched from pulse to  alsa, played with the video options, and I also tried the tsched=0  option, but to no avail. The video stutters in Youtube and other video  sites as well as VLC.

The output of lspci in terms of graphics is 

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

I don't know if I have given enough information, but I would be glad of  any help, especially since I had to skip a version, and used 9.10 until  now, since I had the dreaded Black Screen of Death problem with 10.4,  and could not fix it, as all the solutions I found online didn't help.

When I try to play a song on VLC through the terminal, I get an error every time the sound "jumps".

VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x978dd6c] dummy interface: using the dummy interface module...
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
[0x9796644] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0x9796644] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 344 ms)

I suspect it could be a graphics problem, as when i try to enable  desktop effects, I get an error message, saying they can't be enabled

---

### Post by lidex on 2010-11-06
Did you upgrade directly from 9.10 to 10.10?
What do you get for this:
```
sudo lshw -C multimedia
uname -a
```

---

### Post by Closrapexa on 2010-11-07
No, I did a clean install, and I had to erase ui from the syslinux.cfg file to get it to boot. When I enter the commands, I get 

sudo lshw -C multimedia
*-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0
       resources: irq:11 ioport:1c00(size=256) ioport:18c0(size=64) memory:d0100c00-d0100dff memory:d0100800-d01008ff

and

uname -a
Linux mozes 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

---

### Post by Closrapexa on 2010-11-07
It actually feels like a kind of "slide." Whenever the sound and video glitch, the system freezes momentarily

---

### Post by lidex on 2010-11-07
Sorry I should have asked for this:
```
sudo lshw -C display
```
Something else that may provide a clue is compiz-check - the link is in my sig. Also post this output please:
```
cat /var/log/Xorg.0.log
```

---

### Post by Closrapexa on 2010-11-07
I must say I don't understand any of this, I really appreciate your taking the time :)

Anyway, 

sudo lshw -C display

  *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:e0000000-e7ffffff memory:d0000000-d007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:d0080000-d00fffff

cat /var/log/Xorg.0.log

959.399] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   959.550] (II) Power Button: Device reopened after 1 attempts.
[   959.550] (II) Video Bus: Device reopened after 1 attempts.
[   959.550] (II) Sleep Button: Device reopened after 1 attempts.
[   959.550] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[   959.550] (II) TPPS/2 IBM TrackPoint: Device reopened after 1 attempts.
[   959.550] (II) ThinkPad Extra Buttons: Device reopened after 1 attempts.

Also, I tried clicking the compiz check link in your signature, I got an 
Invalid Request provider

---

### Post by lidex on 2010-11-07
> **Closrapexa said:**
> I must say I don't understand any of this, I really appreciate your taking the time :)

Anyway, 

sudo lshw -C display

  *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:11 memory:e0000000-e7ffffff memory:d0000000-d007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:d0080000-d00fffff

cat /var/log/Xorg.0.log

959.399] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   959.550] (II) Power Button: Device reopened after 1 attempts.
[   959.550] (II) Video Bus: Device reopened after 1 attempts.
[   959.550] (II) Sleep Button: Device reopened after 1 attempts.
[   959.550] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[   959.550] (II) TPPS/2 IBM TrackPoint: Device reopened after 1 attempts.
[   959.550] (II) ThinkPad Extra Buttons: Device reopened after 1 attempts.

Also, I tried clicking the compiz check link in your signature, I got an 
Invalid Request provider

That link works for me:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Your Xorg.0.log data is incomplete. Open your terminal and got to the 'edit > profiles' menu. Select the profile you're using - probably 'default'. Click the 'edit' button and then select the 'scrolling' tab. Under 'Scrollback' tick to enable 'unlimited'. Now close that out and reboot. Next run this command again:
```
cat /var/log/Xorg.0.log
```
Make sure to copy and paste the entire output into your next post using the code tags. (# in the toolbar)

---

### Post by ChrisHartley on 2010-11-07
Hello,

Sorry to jump in to your thread but I have the same system (R50e) and am having the same audio/video stuttering problem with 10.10. 

The output of 'sudo lshw -C display' is the same for me but my /var/log/Xorg.0.log is 16M - there are two hundred thousand repeated lines like this:
[  6170.667] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument

$ ./compiz-check
Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) n

--
So why is Xorg using vesa? It looks like there are significant bugs in the Intel drivers so they disabled them by default in 10.10: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

I tried switching to glasen's Intel drivers as detailed here: [http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver-on-ubuntu-10-10-maverick-meerkat/4659#4659](http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver-on-ubuntu-10-10-maverick-meerkat/4659#4659) 
but that resulted in an unusable system (no mouse pointer, screen updates slowly in blocks, etc). I removed /etc/X11/xorg.conf and I'm now back with vesa. My mouse pointer works again but audio and video still stutter. I'll keep watching this thread in the hope that there is a solution.

---

### Post by ChrisHartley on 2010-11-07
Ok, I googled around a bit and found that Glasen also has a fix for the missing mouse pointer. I followed the steps here: [http://www.glasen-hardt.de/?p=959](http://www.glasen-hardt.de/?p=959) (installed Glasen's 855gm-fix ppa) and then re-followed the steps here: [http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver-on-ubuntu-10-10-maverick-meerkat/4659#4659](http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver-on-ubuntu-10-10-maverick-meerkat/4659#4659) (installed Glasen's intel driver) and edited my /etc/X11/xorg.conf to use the new Intel driver:
--
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
--

When I re-started the mouse pointer was visible and I could log in but whenever I moused over an icon on my desktop the icon was replaced with a square from the purple login screen background and the pointer disappeared. I was eventually able to blindly click around and get VLC started - low and behold I now have stutter free audio and video. By the time VLC was running the strange purple boxes and other display problems had gone away and now everything appears normal.  

When I run compiz-check it told me to install mesa-utils. After I installed mesa-utils I get this:
--
$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

--
Woo hoo? So it works now but my understanding is that there are still stability problems with the Intel driver, even the Glasen version. I'll run it for a few days and see if it crashes.

---

### Post by Closrapexa on 2010-11-07
Sorry about the omission, here is the complete xorg

```

mozes@mozes:~$ cat /var/log/Xorg.0.log
[    45.045] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    45.045] X Protocol Version 11, Revision 0
[    45.045] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    45.046] Current Operating System: Linux mozes 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    45.046] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=deaeccd5-9890-4d2f-9df0-6a7db0281ca3 ro quiet splash
[    45.046] Build Date: 16 September 2010  05:39:22PM
[    45.046] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    45.046] Current version of pixman: 0.18.4
[    45.046]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    45.046] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.046] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  8 06:29:11 2010
[    45.152] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.152] (==) No Layout section.  Using the first Screen section.
[    45.152] (==) No screen section available. Using defaults.
[    45.152] (**) |-->Screen "Default Screen Section" (0)
[    45.152] (**) |   |-->Monitor "<default monitor>"
[    45.153] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    45.153] (==) Automatically adding devices
[    45.153] (==) Automatically enabling devices
[    45.153] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.153]     Entry deleted from font path.
[    45.153] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    45.153] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.153] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.153] (II) Loader magic: 0x81f8e00
[    45.153] (II) Module ABI versions:
[    45.153]     X.Org ANSI C Emulation: 0.4
[    45.153]     X.Org Video Driver: 8.0
[    45.153]     X.Org XInput driver : 11.0
[    45.153]     X.Org Server Extension : 4.0
[    45.154] (--) PCI:*(0:0:2:0) 8086:3582:1014:0562 rev 2, Mem @ 0xe0000000/134217728, 0xd0000000/524288, I/O @ 0x00001800/8
[    45.154] (--) PCI: (0:0:2:1) 8086:3582:1014:0562 rev 2, Mem @ 0xe8000000/134217728, 0xd0080000/524288
[    45.154] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    45.154] (II) LoadModule: "extmod"
[    45.308] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    45.308] (II) Module extmod: vendor="X.Org Foundation"
[    45.308]     compiled for 1.9.0, module version = 1.0.0
[    45.308]     Module class: X.Org Server Extension
[    45.308]     ABI class: X.Org Server Extension, version 4.0
[    45.308] (II) Loading extension MIT-SCREEN-SAVER
[    45.308] (II) Loading extension XFree86-VidModeExtension
[    45.308] (II) Loading extension XFree86-DGA
[    45.308] (II) Loading extension DPMS
[    45.308] (II) Loading extension XVideo
[    45.308] (II) Loading extension XVideo-MotionCompensation
[    45.308] (II) Loading extension X-Resource
[    45.308] (II) LoadModule: "dbe"
[    45.309] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    45.309] (II) Module dbe: vendor="X.Org Foundation"
[    45.309]     compiled for 1.9.0, module version = 1.0.0
[    45.309]     Module class: X.Org Server Extension
[    45.309]     ABI class: X.Org Server Extension, version 4.0
[    45.309] (II) Loading extension DOUBLE-BUFFER
[    45.309] (II) LoadModule: "glx"
[    45.309] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    45.309] (II) Module glx: vendor="X.Org Foundation"
[    45.309]     compiled for 1.9.0, module version = 1.0.0
[    45.309]     ABI class: X.Org Server Extension, version 4.0
[    45.310] (==) AIGLX enabled
[    45.310] (II) Loading extension GLX
[    45.310] (II) LoadModule: "record"
[    45.310] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    45.310] (II) Module record: vendor="X.Org Foundation"
[    45.310]     compiled for 1.9.0, module version = 1.13.0
[    45.310]     Module class: X.Org Server Extension
[    45.310]     ABI class: X.Org Server Extension, version 4.0
[    45.310] (II) Loading extension RECORD
[    45.310] (II) LoadModule: "dri"
[    45.311] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    45.311] (II) Module dri: vendor="X.Org Foundation"
[    45.311]     compiled for 1.9.0, module version = 1.0.0
[    45.311]     ABI class: X.Org Server Extension, version 4.0
[    45.311] (II) Loading extension XFree86-DRI
[    45.311] (II) LoadModule: "dri2"
[    45.311] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    45.311] (II) Module dri2: vendor="X.Org Foundation"
[    45.311]     compiled for 1.9.0, module version = 1.2.0
[    45.311]     ABI class: X.Org Server Extension, version 4.0
[    45.311] (II) Loading extension DRI2
[    45.311] (==) Matched vesa as autoconfigured driver 0
[    45.311] (==) Matched fbdev as autoconfigured driver 1
[    45.311] (==) Assigned the driver to the xf86ConfigLayout
[    45.312] (II) LoadModule: "vesa"
[    45.549] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    45.549] (II) Module vesa: vendor="X.Org Foundation"
[    45.549]     compiled for 1.8.99.905, module version = 2.3.0
[    45.549]     Module class: X.Org Video Driver
[    45.549]     ABI class: X.Org Video Driver, version 8.0
[    45.549] (II) LoadModule: "fbdev"
[    45.550] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    45.550] (II) Module fbdev: vendor="X.Org Foundation"
[    45.550]     compiled for 1.8.99.905, module version = 0.4.2
[    45.550]     ABI class: X.Org Video Driver, version 8.0
[    45.550] (II) VESA: driver for VESA chipsets: vesa
[    45.550] (II) FBDEV: driver for framebuffer: fbdev
[    45.550] (++) using VT number 7

[    45.590] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    45.590] (WW) Falling back to old probe method for vesa
[    45.590] (II) Loading sub module "fbdevhw"
[    45.590] (II) LoadModule: "fbdevhw"
[    45.591] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    45.591] (II) Module fbdevhw: vendor="X.Org Foundation"
[    45.591]     compiled for 1.9.0, module version = 0.0.2
[    45.591]     ABI class: X.Org Video Driver, version 8.0
[    45.591] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    45.591] (II) FBDEV(0): using default device
[    45.591] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    45.591] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    45.591] (==) FBDEV(0): RGB weight 888
[    45.591] (==) FBDEV(0): Default visual is TrueColor
[    45.591] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    45.591] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    45.591] (II) FBDEV(0): checking modes against framebuffer device...
[    45.591] (II) FBDEV(0): checking modes against monitor...
[    45.591] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    45.591] (**) FBDEV(0):  Built-in mode "current"
[    45.591] (==) FBDEV(0): DPI set to (96, 96)
[    45.591] (II) Loading sub module "fb"
[    45.591] (II) LoadModule: "fb"
[    45.591] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.591] (II) Module fb: vendor="X.Org Foundation"
[    45.591]     compiled for 1.9.0, module version = 1.0.0
[    45.591]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.705] (**) FBDEV(0): using shadow framebuffer
[    45.705] (II) Loading sub module "shadow"
[    45.706] (II) LoadModule: "shadow"
[    45.706] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    45.706] (II) Module shadow: vendor="X.Org Foundation"
[    45.706]     compiled for 1.9.0, module version = 1.1.0
[    45.706]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.706] (==) Depth 24 pixmap format is 32 bpp
[    53.092] (==) FBDEV(0): Backing store disabled
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (==) FBDEV(0): DPMS enabled
[    53.103] (==) RandR enabled
[    53.103] (II) Initializing built-in extension Generic Event Extension
[    53.103] (II) Initializing built-in extension SHAPE
[    53.103] (II) Initializing built-in extension MIT-SHM
[    53.103] (II) Initializing built-in extension XInputExtension
[    53.104] (II) Initializing built-in extension XTEST
[    53.104] (II) Initializing built-in extension BIG-REQUESTS
[    53.104] (II) Initializing built-in extension SYNC
[    53.104] (II) Initializing built-in extension XKEYBOARD
[    53.104] (II) Initializing built-in extension XC-MISC
[    53.104] (II) Initializing built-in extension SECURITY
[    53.104] (II) Initializing built-in extension XINERAMA
[    53.104] (II) Initializing built-in extension XFIXES
[    53.104] (II) Initializing built-in extension RENDER
[    53.104] (II) Initializing built-in extension RANDR
[    53.104] (II) Initializing built-in extension COMPOSITE
[    53.104] (II) Initializing built-in extension DAMAGE
[    53.104] (II) Initializing built-in extension GESTURE
[    53.159] (II) AIGLX: Screen 0 is not DRI2 capable
[    53.159] (II) AIGLX: Screen 0 is not DRI capable
[    53.162] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    53.162] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    53.304] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    53.335] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    53.335] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    53.335] (II) LoadModule: "evdev"
[    53.335] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    53.348] (II) Module evdev: vendor="X.Org Foundation"
[    53.348]     compiled for 1.9.0, module version = 2.3.2
[    53.348]     Module class: X.Org XInput Driver
[    53.348]     ABI class: X.Org XInput driver, version 11.0
[    53.348] (**) Power Button: always reports core events
[    53.348] (**) Power Button: Device: "/dev/input/event2"
[    53.348] (II) Power Button: Found keys
[    53.348] (II) Power Button: Configuring as keyboard
[    53.348] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    53.348] (**) Option "xkb_rules" "evdev"
[    53.348] (**) Option "xkb_model" "pc105"
[    53.348] (**) Option "xkb_layout" "us"
[    53.349] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    53.349] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    53.349] (**) Video Bus: always reports core events
[    53.349] (**) Video Bus: Device: "/dev/input/event4"
[    53.349] (II) Video Bus: Found keys
[    53.349] (II) Video Bus: Configuring as keyboard
[    53.349] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    53.349] (**) Option "xkb_rules" "evdev"
[    53.349] (**) Option "xkb_model" "pc105"
[    53.349] (**) Option "xkb_layout" "us"
[    53.351] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    53.351] (II) No input driver/identifier specified (ignoring)
[    53.351] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    53.351] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    53.351] (**) Sleep Button: always reports core events
[    53.351] (**) Sleep Button: Device: "/dev/input/event1"
[    53.351] (II) Sleep Button: Found keys
[    53.351] (II) Sleep Button: Configuring as keyboard
[    53.351] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    53.351] (**) Option "xkb_rules" "evdev"
[    53.351] (**) Option "xkb_model" "pc105"
[    53.351] (**) Option "xkb_layout" "us"
[    53.378] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    53.378] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    53.378] (**) AT Translated Set 2 keyboard: always reports core events
[    53.378] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    53.378] (II) AT Translated Set 2 keyboard: Found keys
[    53.378] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    53.378] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    53.378] (**) Option "xkb_rules" "evdev"
[    53.378] (**) Option "xkb_model" "pc105"
[    53.378] (**) Option "xkb_layout" "us"
[    53.379] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event5)
[    53.379] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    53.379] (**) TPPS/2 IBM TrackPoint: always reports core events
[    53.379] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event5"
[    53.379] (II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    53.379] (II) TPPS/2 IBM TrackPoint: Found relative axes
[    53.379] (II) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    53.379] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    53.379] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    53.379] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    53.379] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    53.379] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[    53.379] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse0)
[    53.379] (II) No input driver/identifier specified (ignoring)
[    53.382] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event6)
[    53.382] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    53.382] (**) ThinkPad Extra Buttons: always reports core events
[    53.382] (**) ThinkPad Extra Buttons: Device: "/dev/input/event6"
[    53.382] (II) ThinkPad Extra Buttons: Found keys
[    53.382] (II) ThinkPad Extra Buttons: Configuring as keyboard
[    53.382] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[    53.382] (**) Option "xkb_rules" "evdev"
[    53.382] (**) Option "xkb_model" "pc105"
[    53.382] (**) Option "xkb_layout" "us"
mozes@mozes:~$ clear

mozes@mozes:~$ cat /var/log/Xorg.0.log
[    45.045] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    45.045] X Protocol Version 11, Revision 0
[    45.045] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    45.046] Current Operating System: Linux mozes 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    45.046] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=deaeccd5-9890-4d2f-9df0-6a7db0281ca3 ro quiet splash
[    45.046] Build Date: 16 September 2010  05:39:22PM
[    45.046] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    45.046] Current version of pixman: 0.18.4
[    45.046]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    45.046] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    45.046] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  8 06:29:11 2010
[    45.152] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    45.152] (==) No Layout section.  Using the first Screen section.
[    45.152] (==) No screen section available. Using defaults.
[    45.152] (**) |-->Screen "Default Screen Section" (0)
[    45.152] (**) |   |-->Monitor "<default monitor>"
[    45.153] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    45.153] (==) Automatically adding devices
[    45.153] (==) Automatically enabling devices
[    45.153] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    45.153]     Entry deleted from font path.
[    45.153] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    45.153] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    45.153] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    45.153] (II) Loader magic: 0x81f8e00
[    45.153] (II) Module ABI versions:
[    45.153]     X.Org ANSI C Emulation: 0.4
[    45.153]     X.Org Video Driver: 8.0
[    45.153]     X.Org XInput driver : 11.0
[    45.153]     X.Org Server Extension : 4.0
[    45.154] (--) PCI:*(0:0:2:0) 8086:3582:1014:0562 rev 2, Mem @ 0xe0000000/134217728, 0xd0000000/524288, I/O @ 0x00001800/8
[    45.154] (--) PCI: (0:0:2:1) 8086:3582:1014:0562 rev 2, Mem @ 0xe8000000/134217728, 0xd0080000/524288
[    45.154] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    45.154] (II) LoadModule: "extmod"
[    45.308] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    45.308] (II) Module extmod: vendor="X.Org Foundation"
[    45.308]     compiled for 1.9.0, module version = 1.0.0
[    45.308]     Module class: X.Org Server Extension
[    45.308]     ABI class: X.Org Server Extension, version 4.0
[    45.308] (II) Loading extension MIT-SCREEN-SAVER
[    45.308] (II) Loading extension XFree86-VidModeExtension
[    45.308] (II) Loading extension XFree86-DGA
[    45.308] (II) Loading extension DPMS
[    45.308] (II) Loading extension XVideo
[    45.308] (II) Loading extension XVideo-MotionCompensation
[    45.308] (II) Loading extension X-Resource
[    45.308] (II) LoadModule: "dbe"
[    45.309] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    45.309] (II) Module dbe: vendor="X.Org Foundation"
[    45.309]     compiled for 1.9.0, module version = 1.0.0
[    45.309]     Module class: X.Org Server Extension
[    45.309]     ABI class: X.Org Server Extension, version 4.0
[    45.309] (II) Loading extension DOUBLE-BUFFER
[    45.309] (II) LoadModule: "glx"
[    45.309] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    45.309] (II) Module glx: vendor="X.Org Foundation"
[    45.309]     compiled for 1.9.0, module version = 1.0.0
[    45.309]     ABI class: X.Org Server Extension, version 4.0
[    45.310] (==) AIGLX enabled
[    45.310] (II) Loading extension GLX
[    45.310] (II) LoadModule: "record"
[    45.310] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    45.310] (II) Module record: vendor="X.Org Foundation"
[    45.310]     compiled for 1.9.0, module version = 1.13.0
[    45.310]     Module class: X.Org Server Extension
[    45.310]     ABI class: X.Org Server Extension, version 4.0
[    45.310] (II) Loading extension RECORD
[    45.310] (II) LoadModule: "dri"
[    45.311] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    45.311] (II) Module dri: vendor="X.Org Foundation"
[    45.311]     compiled for 1.9.0, module version = 1.0.0
[    45.311]     ABI class: X.Org Server Extension, version 4.0
[    45.311] (II) Loading extension XFree86-DRI
[    45.311] (II) LoadModule: "dri2"
[    45.311] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    45.311] (II) Module dri2: vendor="X.Org Foundation"
[    45.311]     compiled for 1.9.0, module version = 1.2.0
[    45.311]     ABI class: X.Org Server Extension, version 4.0
[    45.311] (II) Loading extension DRI2
[    45.311] (==) Matched vesa as autoconfigured driver 0
[    45.311] (==) Matched fbdev as autoconfigured driver 1
[    45.311] (==) Assigned the driver to the xf86ConfigLayout
[    45.312] (II) LoadModule: "vesa"
[    45.549] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    45.549] (II) Module vesa: vendor="X.Org Foundation"
[    45.549]     compiled for 1.8.99.905, module version = 2.3.0
[    45.549]     Module class: X.Org Video Driver
[    45.549]     ABI class: X.Org Video Driver, version 8.0
[    45.549] (II) LoadModule: "fbdev"
[    45.550] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    45.550] (II) Module fbdev: vendor="X.Org Foundation"
[    45.550]     compiled for 1.8.99.905, module version = 0.4.2
[    45.550]     ABI class: X.Org Video Driver, version 8.0
[    45.550] (II) VESA: driver for VESA chipsets: vesa
[    45.550] (II) FBDEV: driver for framebuffer: fbdev
[    45.550] (++) using VT number 7

[    45.590] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    45.590] (WW) Falling back to old probe method for vesa
[    45.590] (II) Loading sub module "fbdevhw"
[    45.590] (II) LoadModule: "fbdevhw"
[    45.591] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    45.591] (II) Module fbdevhw: vendor="X.Org Foundation"
[    45.591]     compiled for 1.9.0, module version = 0.0.2
[    45.591]     ABI class: X.Org Video Driver, version 8.0
[    45.591] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    45.591] (II) FBDEV(0): using default device
[    45.591] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    45.591] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    45.591] (==) FBDEV(0): RGB weight 888
[    45.591] (==) FBDEV(0): Default visual is TrueColor
[    45.591] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    45.591] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    45.591] (II) FBDEV(0): checking modes against framebuffer device...
[    45.591] (II) FBDEV(0): checking modes against monitor...
[    45.591] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    45.591] (**) FBDEV(0):  Built-in mode "current"
[    45.591] (==) FBDEV(0): DPI set to (96, 96)
[    45.591] (II) Loading sub module "fb"
[    45.591] (II) LoadModule: "fb"
[    45.591] (II) Loading /usr/lib/xorg/modules/libfb.so
[    45.591] (II) Module fb: vendor="X.Org Foundation"
[    45.591]     compiled for 1.9.0, module version = 1.0.0
[    45.591]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.705] (**) FBDEV(0): using shadow framebuffer
[    45.705] (II) Loading sub module "shadow"
[    45.706] (II) LoadModule: "shadow"
[    45.706] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    45.706] (II) Module shadow: vendor="X.Org Foundation"
[    45.706]     compiled for 1.9.0, module version = 1.1.0
[    45.706]     ABI class: X.Org ANSI C Emulation, version 0.4
[    45.706] (==) Depth 24 pixmap format is 32 bpp
[    53.092] (==) FBDEV(0): Backing store disabled
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.092] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.093] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.094] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.095] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    53.103] (==) FBDEV(0): DPMS enabled
[    53.103] (==) RandR enabled
[    53.103] (II) Initializing built-in extension Generic Event Extension
[    53.103] (II) Initializing built-in extension SHAPE
[    53.103] (II) Initializing built-in extension MIT-SHM
[    53.103] (II) Initializing built-in extension XInputExtension
[    53.104] (II) Initializing built-in extension XTEST
[    53.104] (II) Initializing built-in extension BIG-REQUESTS
[    53.104] (II) Initializing built-in extension SYNC
[    53.104] (II) Initializing built-in extension XKEYBOARD
[    53.104] (II) Initializing built-in extension XC-MISC
[    53.104] (II) Initializing built-in extension SECURITY
[    53.104] (II) Initializing built-in extension XINERAMA
[    53.104] (II) Initializing built-in extension XFIXES
[    53.104] (II) Initializing built-in extension RENDER
[    53.104] (II) Initializing built-in extension RANDR
[    53.104] (II) Initializing built-in extension COMPOSITE
[    53.104] (II) Initializing built-in extension DAMAGE
[    53.104] (II) Initializing built-in extension GESTURE
[    53.159] (II) AIGLX: Screen 0 is not DRI2 capable
[    53.159] (II) AIGLX: Screen 0 is not DRI capable
[    53.162] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    53.162] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    53.304] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    53.335] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    53.335] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    53.335] (II) LoadModule: "evdev"
[    53.335] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    53.348] (II) Module evdev: vendor="X.Org Foundation"
[    53.348]     compiled for 1.9.0, module version = 2.3.2
[    53.348]     Module class: X.Org XInput Driver
[    53.348]     ABI class: X.Org XInput driver, version 11.0
[    53.348] (**) Power Button: always reports core events
[    53.348] (**) Power Button: Device: "/dev/input/event2"
[    53.348] (II) Power Button: Found keys
[    53.348] (II) Power Button: Configuring as keyboard
[    53.348] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    53.348] (**) Option "xkb_rules" "evdev"
[    53.348] (**) Option "xkb_model" "pc105"
[    53.348] (**) Option "xkb_layout" "us"
[    53.349] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    53.349] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    53.349] (**) Video Bus: always reports core events
[    53.349] (**) Video Bus: Device: "/dev/input/event4"
[    53.349] (II) Video Bus: Found keys
[    53.349] (II) Video Bus: Configuring as keyboard
[    53.349] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    53.349] (**) Option "xkb_rules" "evdev"
[    53.349] (**) Option "xkb_model" "pc105"
[    53.349] (**) Option "xkb_layout" "us"
[    53.351] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    53.351] (II) No input driver/identifier specified (ignoring)
[    53.351] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    53.351] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    53.351] (**) Sleep Button: always reports core events
[    53.351] (**) Sleep Button: Device: "/dev/input/event1"
[    53.351] (II) Sleep Button: Found keys
[    53.351] (II) Sleep Button: Configuring as keyboard
[    53.351] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    53.351] (**) Option "xkb_rules" "evdev"
[    53.351] (**) Option "xkb_model" "pc105"
[    53.351] (**) Option "xkb_layout" "us"
[    53.378] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    53.378] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    53.378] (**) AT Translated Set 2 keyboard: always reports core events
[    53.378] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    53.378] (II) AT Translated Set 2 keyboard: Found keys
[    53.378] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    53.378] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    53.378] (**) Option "xkb_rules" "evdev"
[    53.378] (**) Option "xkb_model" "pc105"
[    53.378] (**) Option "xkb_layout" "us"
[    53.379] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/event5)
[    53.379] (**) TPPS/2 IBM TrackPoint: Applying InputClass "evdev pointer catchall"
[    53.379] (**) TPPS/2 IBM TrackPoint: always reports core events
[    53.379] (**) TPPS/2 IBM TrackPoint: Device: "/dev/input/event5"
[    53.379] (II) TPPS/2 IBM TrackPoint: Found 3 mouse buttons
[    53.379] (II) TPPS/2 IBM TrackPoint: Found relative axes
[    53.379] (II) TPPS/2 IBM TrackPoint: Found x and y relative axes
[    53.379] (II) TPPS/2 IBM TrackPoint: Configuring as mouse
[    53.379] (**) TPPS/2 IBM TrackPoint: YAxisMapping: buttons 4 and 5
[    53.379] (**) TPPS/2 IBM TrackPoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    53.379] (II) XINPUT: Adding extended input device "TPPS/2 IBM TrackPoint" (type: MOUSE)
[    53.379] (II) TPPS/2 IBM TrackPoint: initialized for relative axes.
[    53.379] (II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/input/mouse0)
[    53.379] (II) No input driver/identifier specified (ignoring)
[    53.382] (II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/input/event6)
[    53.382] (**) ThinkPad Extra Buttons: Applying InputClass "evdev keyboard catchall"
[    53.382] (**) ThinkPad Extra Buttons: always reports core events
[    53.382] (**) ThinkPad Extra Buttons: Device: "/dev/input/event6"
[    53.382] (II) ThinkPad Extra Buttons: Found keys
[    53.382] (II) ThinkPad Extra Buttons: Configuring as keyboard
[    53.382] (II) XINPUT: Adding extended input device "ThinkPad Extra Buttons" (type: KEYBOARD)
[    53.382] (**) Option "xkb_rules" "evdev"
[    53.382] (**) Option "xkb_model" "pc105"
[    53.382] (**) Option "xkb_layout" "us"

```

---

### Post by Closrapexa on 2010-11-07
[ChrisHartley]("http://ubuntuforums.org/member.php?u=762453"), I appreciate any help I can get, thanks for your input. I just don't get it, it worked flawlessly with all the inane desktop effects you can think of, up until 10.4. Is the ole' Thinkpad finally too outdated to use Ubuntu?

did your solution work?

---

### Post by ChrisHartley on 2010-11-08
Hi Closrapexa,

I don't think the issue is that the R50e is too old, just that the graphics card is not very well supported. In 10.04 your system was probably set to use the Intel driver. A lot of people, myself included, had system freezes with the Intel driver so in 10.10 they switched to using a more generic driver by default. The problem, in my understanding, is that when you use the generic driver less of the work is done by the graphic card and more is done by the system CPU - that is why the system stutters under heavy load. If the R50e had a faster CPU then maybe the system wouldn't stutter but the real solution here is to get the graphics card working with the right driver, then the CPU isn't trying to do the graphics stuff that it isn't good at. 

The official explanation is on the Maverick i8xx Status page here: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus) 

By using the updated Intel driver I was able to get smooth video but at the expense of system stability so it isn't a good solution. It did let me watch a movie but to switching between windows, moving the mouse, etc result in a bunch of strange video problems. I've disabled the Intel driver now. I think there are people working on this bug - there are lot of laptops out there with the same Intel graphics card so this bug is affecting a lot of people. Hopefully a fix will come, in the meantime I am going to try and learn enough about the system so I can contribute a useful bug report. 

If your system was working great with 10.04 then you might want to try re-enabling the Intel driver. To do this create the file /etc/X11/xorg.conf containing this:
```

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

```

You can create the file by running 'sudo gedit /etc/X11/xorg.conf' in a terminal, paste the text into the editor then save and close.

If your system becomes unstable you can just delete the /etc/X11/xorg.conf file and re-boot. Let me know if any of this helps. 

Chris H.

---

### Post by finite9 on 2010-11-10
im using a Thinkpad Edge 13 with Maverick 64bit and I have normal compiz effects enabled.  As far as im aware, im using the latest Intel driver mesa 7.9.  When I play any video in mplayer or totem its fine, but as soon as I switch compiz to full effects i get stutter.  I did not get stutter with full compiz effects in Ubuntu 10.04.  Only difference since doing clean install of 10.10 is that I use jfs as file system instead of ext3, but cannot see how that could possibly be related.

---

### Post by ChrisHartley on 2010-11-10
finite9 - It might be worth confirming that X11 is using the intel driver. In 10.10 they disabled the intel driver from autoloading, a big change from 10.04. It has to be manually loaded in /etc/X11/xorg.conf with something like this:
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

```

If your xorg.conf doesn't have those lines or you don't have an xorg.conf you will need to create one/add those lines before X11 will load the intel driver. 

You are correct that the switch from ext3 to jfs will not affect video but there were other big changes from 10.04 to 10.10 that might.

---

### Post by lidex on 2010-11-10
> **Closrapexa said:**
> [ChrisHartley]("http://ubuntuforums.org/member.php?u=762453"), I appreciate any help I can get, thanks for your input. I just don't get it, it worked flawlessly with all the inane desktop effects you can think of, up until 10.4. Is the ole' Thinkpad finally too outdated to use Ubuntu?

did your solution work?

Looks like you're using the i915 driver. Some work-arounds here:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Closrapexa on 2010-11-12
I tried enabling the Intel driver, and I got no mouse pointer, and a system crash before I could check if the video works. Well, like you said would happen. So, does that mean I have to either not watch video or hear audio, or downgrade back to 9.10?

---

### Post by Closrapexa on 2010-11-12
BTW, after doing this, as I write this, I updated, and it told me to upgrade xserver-xorg-video-intel, even though I had already deleted the Xorg file I had created. What does this mean? Does it have anything to do with it at all? It had no effect on the video or sound

---

### Post by zachsandberg on 2010-11-21
I also have an R50e with Ubuntu 10.10 and was experiencing the constant audio and mouse stuttering issues.

I completely fixed it following this article just installing the GTT Incoherency Patch [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by themvrck on 2010-11-24
> **zachsandberg said:**
> I also have an R50e with Ubuntu 10.10 and was experiencing the constant audio and mouse stuttering issues.

I completely fixed it following this article just installing the GTT Incoherency Patch [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I get this..... any ideas???

Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Closrapexa on 2010-11-24
Thanks, I'll that tomorrow, with all this going on, I went back to 9.10, the last version that worked for me.

---

### Post by Closrapexa on 2011-01-10
Very belated thanks, I finally got it to work with [ChrisHartley]("http://ubuntuforums.org/member.php?u=762453")'s workaround link, [this one]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") and although sometimes the screen just turns black for a second, but then goes back to normal, and even then, it's rare. So, I suppose that there are ways to go around it, but thats a-okay for me.

---

