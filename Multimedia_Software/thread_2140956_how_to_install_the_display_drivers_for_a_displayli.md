---
title: "how to install the display drivers for a displaylink usb monitor in 13.04?"
date: 2013-05-01
forum: Multimedia Software
---

### Post by dysonsphere23 on 2013-05-01
how do i install the display drivers for a displaylink usb monitor?

the monitor connected with the displaylink device has the following messages on the display:
[   10.723468] usb 3-1.1: device descriptor read/8, error 110
[   13.853141] nouveau E[   VBIOS][0000:01:00.0] 0x8569[]: unknown opcode 0xc9

I am running ubuntu 13.04 on a new macbook pro with the NVIDIA GK107M [GeForce GT 650M Mac Edition] graphics card running on the open source Nouveau X.org X server display driver.

[http://libdlo.freedesktop.org/wiki/](http://libdlo.freedesktop.org/wiki/) has links to drivers and stuff but no guide for  ubuntu versions passed 9.10. i was able to install and test the monitor with libdlo from that page so i figure that it is possible but i do not understand how to install the proper x-drivers to get the display to work normally.

synaptic has no results for a search for displaylink.

---

### Post by spoons on 2013-05-18
I'd also be interested in a solution to this as my DL-195 adapter is not working.

Thanks.

---

### Post by spoons on 2013-05-20
Really hoping someone has a solution to this chaps.

---

### Post by Manthis on 2013-06-12
I'd be really interested in a solution too especially since the xserver-xorg-video-displaylink package is not available anymore under 13.04

---

### Post by jaws222 on 2013-06-18
Has anyone figured this out yet?

---

### Post by Lop3 on 2013-06-20
Please Display Port support!

I want to learn linux and use it as my main system. (So earnestly)
And so many good things will happen when I do, because I'm a developer and will do good things :-) (just not a driver guy)

But I can't switch to linux without running 3 monitors.
And to do that I need my displaylink monitors to work.
I have 2x AOC 15.6" e1649Fwu.
When I'm at home I run them in conjunction with an external full HD monitor.
When I'm out I use the USB monitors on the sides.

In windows when you plug in monitors they just appear in the display properties window.
In Linux there is all this X server stuff and configuration files etc. Which is great because thats the linux way.
But as a desktop thats not really what Ubuntu is aiming at. (more of a plug and play vibe)

I spent an entire day with my geekiest of linux friends to get it working, and we could not. We tried 12.04 and 12.10.
Strangely enough when I booted into some kind of recovery mode (can't remember) with a USB monitor connected, it initialized and worked almost perfectly, though everything was sideways or upside down or something. And after a while everything crashed, so it was not quite right. Inside the actual desktop environment we couldn't get anything working. We followed all the guides we could find.
It was really a tedious process, all the reboots and fiddling with complicated config files.
In the config files you had to explicitly specify every monitor, calculating the exact offsets of everything. Its a little bit crazy.
When you connect these monitors to a XP computer, they just show up. Inside the display properties you just drag them around with a mouse to where u want them. If you physically turn the monitor sideways, the driver automatically rotates the display.
Unfortunately the Mac and Windows 7 drivers don't do automatic rotation. And DisplayPort didn't bother making linux drivers.

For the moment when I want to run linux I run it in a VM.
Its kind of hard to make it my main OS that way.

Thanks for all the awesome improvements to Ubuntu.
peace

PS:
Maybe we should find out who the driver guy is at Ubuntu and make a kickstarter project to buy him a Displayport monitor? :)

---

### Post by dysonsphere23 on 2013-07-04
anyone?
i posted this question on askubuntu but it got removed for not being an appropriate use of that site.
any suggestions on where else to post this question to maybe get some help.
thanks

---

### Post by Lop3 on 2013-07-08
You would think if displaylink want to sell their technology they'd provide drivers...
I've tried complaining at displaylink.org forums. Nobody there seems to care.


Recently I heard Fedora has plug and play support for displaylink products since F18.
I've just tried this weekend with F19 x64 live desktop.
It gave me hope of success in the nearish future (maybe in a few releases time) but its completely unusable with my USB monitors.
[Fedora Forums]("http://www.forums.fedoraforum.org/showthread.php?t=292309")
The great thing is all this gave me a new idea for a solution to the problem.
Previously my solution was to run Windows 7 as my host operating system, then run Linux in a VM. (that worked great on all my monitors).
The problem with that is its not a good way for me to move to linux. I just tended to keep using windows.

Now I've had a much better idea.
Install Win XP in a VM. And connect the USB monitors to that VM. Then use [Synergy]("http://synergy-foss.org/") to transfer the mouse and keyboard input from the Linux host to the windows VM.
Thats the best solution I've been able to come up with.
I'll try it soon and give you feedback.
Note: I've read Windows 7 in a VM doesn't work with displaylink products.

---

### Post by baltee on 2013-07-19
Good Day All,  I've been working on this for a couple of days and my solution resulted in an upgrade of my kernel to 3.10.  After the upgrade and system reboot, it started working. On the first boot, I plugged it in to the USB port, while at the login screen and then continued to log in.  Not sure if this was relevant, but I also commented out the blacklist entry for it's framebuffer.  

Hope this helps!

---

### Post by thephi2 on 2013-09-01
> **baltee said:**
> Good Day All,  I've been working on this for a couple of days and my solution resulted in an upgrade of my kernel to 3.10.  After the upgrade and system reboot, it started working. On the first boot, I plugged it in to the USB port, while at the login screen and then continued to log in.  Not sure if this was relevant, but I also commented out the blacklist entry for it's framebuffer.  

Hope this helps!
Could you describe a bit more what you've done for the installation please? I would be really glad to have it working :)

"Not sure if this was relevant, but I also commented out the blacklist entry for it's framebuffer." :
You've edited /etc/modprobe.d/blacklist-framebuffer.conf, that's right?
what's inside?
```
blacklist udl
#blacklist udlfb
```

COuld you post your Xorg.conf file please? Mine is :
```
################### Default Stuff ###############################
 
Section "Device"
    Identifier      "Default Device"
    Driver          "intel"
EndSection
 
Section "Monitor"
    Identifier      "Default Monitor"
EndSection
 
Section "Screen"
    Identifier      "Default Screen"
    Monitor         "Default Monitor"
    Device          "Default Device"
    SubSection "Display"
            Depth   16            
    EndSubSection
EndSection
 
############### DisplayLink Stuff ###############
 
Section "Device"
    Identifier      "DisplayLinkDevice"
    driver          "fbdev"
    Option  "fbdev" "/dev/fb1"
EndSection
 
Section "Monitor"
    Identifier      "DisplayLinkMonitor"
EndSection
 
Section "Screen"
    Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
    Monitor         "DisplayLinkMonitor"
        SubSection "Display"
            Depth   16
        EndSubSection
EndSection
 
#################################################
  
Section "ServerLayout"
        Identifier      "Server Layout"
        Screen  0       "DisplayLinkScreen" 0 0
        Screen  1       "Default Screen" RightOf "DisplayLinkScreen"
        Option          "Xinerama" "Off"
EndSection
```

I've got Ubuntu 13.04 with Kernel 3.10.10
Thanks in advance!

---

### Post by thephi2 on 2013-09-01
Okay, I've understood the problem.
In fact, DisplayLink didn't make the effort to release a USB 3.0 version of the driver. When the USB 2.0 Displaylink was working very easily (even "out of the "box" with the 3.10 kernel), the USB 3.0 (which is on more and more devices) is stuck. 
What a shame! It's one year now and they didn't provide any solution. Only for windows (and not even for MAC) :(
[http://www.displaylink.org/forum/showthread.php?t=1748](http://www.displaylink.org/forum/showthread.php?t=1748)

---

### Post by Lop3 on 2013-09-13
Displaylink has not been good to the linux community at all.
So many of their customers have been sitting with Displaylink hardware for years that they have not been able to use.

check this out
[http://displaylinklinuxdriver.wordpress.com](http://displaylinklinuxdriver.wordpress.com)

---

### Post by seba2 on 2013-09-27
I would like to refresh this thread, however unfortunately I can't mark it as solved :(

I was also struggling for few days trying to bring up my 3rd monitor working and failed. The issue I encountering is that I can launch Xserver on only one of graph card. So I can start X on my nvidia OR displaylink. Together are not working. 
Eventually I stuck w/ situation where the screen on displaylink simply freeze on ubuntu loading page. And after CTRL+F1 it backs w/ console but them nvidia related monitors are shutdown.

Here you are what I manage to figured out and what my setting looks like maybe someone would be able to guide me.

ubuntu 13.04_x64
graph: GeForce 9500GT
kernel: 3.8.0-31-generic

I've tried following drivers:
- udlfb - oldest but only working for me
```
udlfb                  23016  1
fb_sys_fops            12703  1 udlfb
syscopyarea            12529  2 udl,udlfb
sysfillrect            12701  2 udl,udlfb
sysimgblt              12674  2 udl,udlfb
```
- udl/drm - not working due unable to find manufacturer:
```

udl                    24771  0
drm_usb                13134  1 udl
drm_kms_helper         49394  1 udl
drm                   286028  3 udl,drm_usb,drm_kms_helper
```

However it's find due dmsg shows that udlfb is good enough:
```
[    1.657389] usb 2-6: new high-speed USB device number 2 using ehci-pci
[    1.792981] usb 2-6: New USB device found, idVendor=17e9, idProduct=0141
[    1.792986] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.792989] usb 2-6: Product: USB Display Adapter (DVI)
[    1.792992] usb 2-6: Manufacturer: DisplayLink
[    1.792994] usb 2-6: SerialNumber: 0141-126440
[    5.988207] udlfb: DisplayLink USB Display Adapter (DVI) - serial #0141-126440
[    5.988211] udlfb: vid_17e9&pid_0141&rev_0003 driver's dlfb_data struct at ffff8802abeb6000
[    5.988213] udlfb: console enable=1
[    5.988214] udlfb: fb_defio enable=1
[    5.988215] udlfb: shadow enable=1
[    5.989093] udlfb: vendor descriptor not available (-32)
[    5.989128] udlfb: allocated 4 65024 byte urbs
[    5.989155] usbcore: registered new interface driver udlfb
[    6.027681] [drm] Initialized drm 1.1.0 20060810
[    6.078643] udlfb: 1680x1050 @ 59 Hz valid mode
[    6.078646] udlfb: 720x400 @ 70 Hz valid mode
[    6.078647] udlfb: 640x480 @ 60 Hz valid mode
[    6.078648] udlfb: 640x480 @ 67 Hz valid mode
[    6.078649] udlfb: 640x480 @ 72 Hz valid mode
[    6.078650] udlfb: 640x480 @ 75 Hz valid mode
[    6.078651] udlfb: 800x600 @ 56 Hz valid mode
[    6.078652] udlfb: 800x600 @ 60 Hz valid mode
[    6.078653] udlfb: 800x600 @ 72 Hz valid mode
[    6.078654] udlfb: 800x600 @ 75 Hz valid mode
[    6.078655] udlfb: 832x624 @ 75 Hz valid mode
[    6.078656] udlfb: 1024x768 @ 60 Hz valid mode
[    6.078657] udlfb: 1024x768 @ 70 Hz valid mode
[    6.078658] udlfb: 1024x768 @ 75 Hz valid mode
[    6.078659] udlfb: 1280x1024 @ 75 Hz valid mode
[    6.078660] udlfb: 1680x1050 @ 60 Hz valid mode
[    6.078662] udlfb: 1600x1200 @ 60 Hz valid mode
[    6.078663] udlfb: 1440x900 @ 75 Hz valid mode
[    6.078664] udlfb: 1440x900 @ 60 Hz valid mode
[    6.078665] udlfb: 1280x720 @ 60 Hz valid mode
[    6.078666] udlfb: 1280x960 @ 60 Hz valid mode
[    6.078667] udlfb: 1152x864 @ 75 Hz valid mode
[    6.078668] udlfb: 1280x1024 @ 60 Hz valid mode
[    6.078669] udlfb: Reallocating framebuffer. Addresses will change!
[    6.079750] udlfb: 1680x1050 @ 59 Hz valid mode
[    6.079753] udlfb: set_par mode 1680x1050
[    6.083658] udlfb: open /dev/fb0 user=0 fb_info=ffff8802b00e5000 count=1
[    6.084521] udlfb: set_par mode 1680x1050
[    6.102820] udlfb: set_par mode 1680x1050
[    6.105669] udlfb: DisplayLink USB device /dev/fb0 attached. 1680x1050 resolution. Using 6896K framebuffer memory
[    6.105732] udlfb: set_par mode 1680x1050
[    6.159719] udlfb: open /dev/fb0 user=1 fb_info=ffff8802b00e5000 count=2
[    6.755129] udlfb: set_par mode 1680x1050
[    7.372616] udlfb: open /dev/fb0 user=1 fb_info=ffff8802b00e5000 count=3
[    7.372620] udlfb: released /dev/fb0 user=1 count=2
[    9.110430] udlfb: released /dev/fb0 user=1 count=1
```

So I tried to configure X by /etc/X11/xorg.conf or /usr/share/X11/xorg.conf.d/10-monitor.conf here you are my file:
```

################################################################################
# LAYOUT
################################################################################
Section "ServerLayout"
    Identifier     "Layout0"
    #Screen      0  "Screen0" 0 0
    #Screen      1  "DisplayLinkScreen" RightOf "Screen0"
    Screen      0  "DisplayLinkScreen" 0 0
    Screen      1  "Screen0" LeftOf "DisplayLinkScreen"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "on"
    Option        "Clone" "off"
EndSection

################################################################################
# DEVICE & SCREEN
################################################################################
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +1680+0, CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       16
    EndSubSection
EndSection

Section "Device"
        Identifier      "DisplayLinkDevice"
        Driver          "displaylink"
        Option    "fbdev" "/dev/fb0"
        BusID        "USB:002"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        SubSection "Display"
                Depth   16
        Modes   "1600x1200" "1680x1050"
        EndSubSection
EndSection
################################################################################
# FILES
################################################################################
Section "Files"
EndSection

################################################################################
# INPUT
################################################################################
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

################################################################################
# MONITOR
################################################################################
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL U2412M"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 61.0
    Option         "DPMS"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
        ModelName          "Philips 220WS"
EndSection
```

I've also tried use steps from here [https://wiki.archlinux.org/index.php/DisplayLink](https://wiki.archlinux.org/index.php/DisplayLink). But:
- if Xinerama was enable them xrandr complaied about lack of moadules (RANDR or something)
- if Xinerama was disabled xrandr give me output like
-- for displayport:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1680 x 1050, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      60.0*
```
-- for nvidia:
```
Screen 0: minimum 8 x 8, current 3520 x 1200, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 470mm x 300mm
   1680x1050      60.0 +
   1600x1200      60.0* 
   1440x900       75.0     59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DVI-I-1 connected 1920x1200+1600+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      60.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)
```
unfortunately number of providers were in both cases 0, see:
```
xrandr --listproviders
Providers: number : 0

```
what can also be see here, I guess:
```
cat /proc/fb
0 udlfb
```

I don't see also any errors in Xserver log:
```
[     6.655] 
X.Org X Server 1.13.4
Release Date: 2013-04-17
[     6.655] X Protocol Version 11, Revision 0
[     6.655] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[     6.655] Current Operating System: Linux pl-byd-seba-desk.emea.int.genesyslab.com 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64
[     6.655] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-30-generic root=UUID=4a97d170-d173-400f-b41c-dbc35f6e2646 ro quiet splash
[     6.655] Build Date: 08 May 2013  02:34:03PM
[     6.655] xorg-server 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring (For technical support please see http://www.ubuntu.com/support) 
[     6.655] Current version of pixman: 0.28.2
[     6.655]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     6.655] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.655] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 27 12:14:04 2013
[     6.659] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.663] (==) No Layout section.  Using the first Screen section.
[     6.663] (==) No screen section available. Using defaults.
[     6.663] (**) |-->Screen "Default Screen Section" (0)
[     6.663] (**) |   |-->Monitor "<default monitor>"
[     6.663] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     6.663] (==) Automatically adding devices
[     6.663] (==) Automatically enabling devices
[     6.663] (==) Automatically adding GPU devices
[     6.664] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.664]     Entry deleted from font path.
[     6.664] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.664]     Entry deleted from font path.
[     6.664] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.664]     Entry deleted from font path.
[     6.664] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.664]     Entry deleted from font path.
[     6.664] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.664]     Entry deleted from font path.
[     6.664] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     6.664]     Entry deleted from font path.
[     6.664] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     6.664] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.664] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.665] (II) Loader magic: 0x7f9d32a2ad20
[     6.665] (II) Module ABI versions:
[     6.665]     X.Org ANSI C Emulation: 0.4
[     6.665]     X.Org Video Driver: 13.1
[     6.665]     X.Org XInput driver : 18.0
[     6.665]     X.Org Server Extension : 7.0
[     6.666] (--) PCI:*(0:2:0:0) 10de:0640:10b0:1401 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/524288
[     6.666] (II) Open ACPI successful (/var/run/acpid.socket)
[     6.667] Initializing built-in extension Generic Event Extension
[     6.667] Initializing built-in extension SHAPE
[     6.667] Initializing built-in extension MIT-SHM
[     6.667] Initializing built-in extension XInputExtension
[     6.667] Initializing built-in extension XTEST
[     6.667] Initializing built-in extension BIG-REQUESTS
[     6.667] Initializing built-in extension SYNC
[     6.667] Initializing built-in extension XKEYBOARD
[     6.667] Initializing built-in extension XC-MISC
[     6.667] Initializing built-in extension SECURITY
[     6.667] Initializing built-in extension XINERAMA
[     6.667] Initializing built-in extension XFIXES
[     6.667] Initializing built-in extension RENDER
[     6.667] Initializing built-in extension RANDR
[     6.667] Initializing built-in extension COMPOSITE
[     6.667] Initializing built-in extension DAMAGE
[     6.667] Initializing built-in extension MIT-SCREEN-SAVER
[     6.667] Initializing built-in extension DOUBLE-BUFFER
[     6.667] Initializing built-in extension RECORD
[     6.667] Initializing built-in extension DPMS
[     6.667] Initializing built-in extension X-Resource
[     6.667] Initializing built-in extension XVideo
[     6.667] Initializing built-in extension XVideo-MotionCompensation
[     6.667] Initializing built-in extension SELinux
[     6.667] Initializing built-in extension XFree86-VidModeExtension
[     6.667] Initializing built-in extension XFree86-DGA
[     6.667] Initializing built-in extension XFree86-DRI
[     6.667] Initializing built-in extension DRI2
[     6.667] (II) LoadModule: "glx"
[     6.671] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     6.886] (II) Module glx: vendor="NVIDIA Corporation"
[     6.886]     compiled for 4.0.2, module version = 1.0.0
[     6.886]     Module class: X.Org Server Extension
[     6.886] (II) NVIDIA GLX Module  304.108  Wed Jul 31 19:56:59 PDT 2013
[     6.886] Loading extension GLX
[     6.886] (==) Matched nvidia as autoconfigured driver 0
[     6.886] (==) Matched nouveau as autoconfigured driver 1
[     6.886] (==) Matched vesa as autoconfigured driver 2
[     6.886] (==) Matched modesetting as autoconfigured driver 3
[     6.886] (==) Matched fbdev as autoconfigured driver 4
[     6.887] (==) Assigned the driver to the xf86ConfigLayout
[     6.887] (II) LoadModule: "nvidia"
[     6.887] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     6.901] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.901]     compiled for 4.0.2, module version = 1.0.0
[     6.901]     Module class: X.Org Video Driver
[     6.906] (II) LoadModule: "nouveau"
[     6.909] (WW) Warning, couldn't open module nouveau
[     6.909] (II) UnloadModule: "nouveau"
[     6.909] (II) Unloading nouveau
[     6.909] (EE) Failed to load module "nouveau" (module does not exist, 0)
[     6.909] (II) LoadModule: "vesa"
[     6.909] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.911] (II) Module vesa: vendor="X.Org Foundation"
[     6.911]     compiled for 1.12.99.902, module version = 2.3.2
[     6.911]     Module class: X.Org Video Driver
[     6.911]     ABI class: X.Org Video Driver, version 13.0
[     6.911] (II) LoadModule: "modesetting"
[     6.911] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     6.912] (II) Module modesetting: vendor="X.Org Foundation"
[     6.912]     compiled for 1.13.3, module version = 0.7.0
[     6.912]     Module class: X.Org Video Driver
[     6.912]     ABI class: X.Org Video Driver, version 13.1
[     6.912] (II) LoadModule: "fbdev"
[     6.912] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.913] (II) Module fbdev: vendor="X.Org Foundation"
[     6.913]     compiled for 1.12.99.902, module version = 0.4.3
[     6.913]     Module class: X.Org Video Driver
[     6.913]     ABI class: X.Org Video Driver, version 13.0
[     6.913] (==) Matched nvidia as autoconfigured driver 0
[     6.913] (==) Matched nouveau as autoconfigured driver 1
[     6.913] (==) Matched vesa as autoconfigured driver 2
[     6.913] (==) Matched modesetting as autoconfigured driver 3
[     6.913] (==) Matched fbdev as autoconfigured driver 4
[     6.913] (==) Assigned the driver to the xf86ConfigLayout
[     6.913] (II) LoadModule: "nvidia"
[     6.913] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     6.913] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.913]     compiled for 4.0.2, module version = 1.0.0
[     6.913]     Module class: X.Org Video Driver
[     6.913] (II) UnloadModule: "nvidia"
[     6.913] (II) Unloading nvidia
[     6.913] (II) Failed to load module "nvidia" (already loaded, 32669)
[     6.913] (II) LoadModule: "nouveau"
[     6.914] (WW) Warning, couldn't open module nouveau
[     6.914] (II) UnloadModule: "nouveau"
[     6.914] (II) Unloading nouveau
[     6.914] (EE) Failed to load module "nouveau" (module does not exist, 0)
[     6.914] (II) LoadModule: "vesa"
[     6.914] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.914] (II) Module vesa: vendor="X.Org Foundation"
[     6.914]     compiled for 1.12.99.902, module version = 2.3.2
[     6.914]     Module class: X.Org Video Driver
[     6.914]     ABI class: X.Org Video Driver, version 13.0
[     6.914] (II) UnloadModule: "vesa"
[     6.914] (II) Unloading vesa
[     6.914] (II) Failed to load module "vesa" (already loaded, 0)
[     6.914] (II) LoadModule: "modesetting"
[     6.914] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     6.914] (II) Module modesetting: vendor="X.Org Foundation"
[     6.914]     compiled for 1.13.3, module version = 0.7.0
[     6.914]     Module class: X.Org Video Driver
[     6.914]     ABI class: X.Org Video Driver, version 13.1
[     6.914] (II) UnloadModule: "modesetting"
[     6.914] (II) Unloading modesetting
[     6.914] (II) Failed to load module "modesetting" (already loaded, 0)
[     6.914] (II) LoadModule: "fbdev"
[     6.914] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.914] (II) Module fbdev: vendor="X.Org Foundation"
[     6.914]     compiled for 1.12.99.902, module version = 0.4.3
[     6.914]     Module class: X.Org Video Driver
[     6.914]     ABI class: X.Org Video Driver, version 13.0
[     6.914] (II) UnloadModule: "fbdev"
[     6.914] (II) Unloading fbdev
[     6.914] (II) Failed to load module "fbdev" (already loaded, 0)
[     6.914] (II) NVIDIA dlloader X Driver  304.108  Wed Jul 31 19:36:56 PDT 2013
[     6.914] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     6.915] (II) VESA: driver for VESA chipsets: vesa
[     6.915] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     6.915] (II) FBDEV: driver for framebuffer: fbdev
[     6.915] (++) using VT number 7

[     6.916] (II) Loading sub module "fb"
[     6.916] (II) LoadModule: "fb"
[     6.916] (II) Loading /usr/lib/xorg/modules/libfb.so
[     6.918] (II) Module fb: vendor="X.Org Foundation"
[     6.918]     compiled for 1.13.4, module version = 1.0.0
[     6.918]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.918] (II) Loading sub module "wfb"
[     6.918] (II) LoadModule: "wfb"
[     6.918] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     6.920] (II) Module wfb: vendor="X.Org Foundation"
[     6.920]     compiled for 1.13.4, module version = 1.0.0
[     6.920]     ABI class: X.Org ANSI C Emulation, version 0.4
[     6.920] (II) Loading sub module "ramdac"
[     6.920] (II) LoadModule: "ramdac"
[     6.920] (II) Module "ramdac" already built-in
[     6.924] (WW) Falling back to old probe method for vesa
[     6.924] (WW) Falling back to old probe method for modesetting
[     6.924] (EE) open /dev/dri/card0: No such file or directory
[     6.924] (EE) open /dev/dri/card0: No such file or directory
[     6.924] (WW) Falling back to old probe method for fbdev
[     6.924] (II) Loading sub module "fbdevhw"
[     6.924] (II) LoadModule: "fbdevhw"
[     6.924] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.925] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.925]     compiled for 1.13.4, module version = 0.0.2
[     6.925]     ABI class: X.Org Video Driver, version 13.1
[     6.925] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     6.925] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     6.925] (==) NVIDIA(0): RGB weight 888
[     6.925] (==) NVIDIA(0): Default visual is TrueColor
[     6.925] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.925] (**) NVIDIA(0): Enabling 2D acceleration
[     8.267] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[     8.267] (II) NVIDIA(GPU-0):     Vision stereo.
[     8.315] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[     8.315] (II) NVIDIA(GPU-0):     Vision stereo.
[     8.317] (II) NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:2:0:0 (GPU-0)
[     8.317] (--) NVIDIA(0): Memory: 524288 kBytes
[     8.317] (--) NVIDIA(0): VideoBIOS: 62.94.3c.00.00
[     8.317] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     8.317] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     8.323] (--) NVIDIA(0): Valid display device(s) on GeForce 9500 GT at PCI:2:0:0
[     8.323] (--) NVIDIA(0):     CRT-0
[     8.323] (--) NVIDIA(0):     Philips 220WS (CRT-1) (connected)
[     8.323] (--) NVIDIA(0):     DELL U2412M (DFP-0) (connected)
[     8.323] (--) NVIDIA(0):     DFP-1
[     8.323] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[     8.323] (--) NVIDIA(0): Philips 220WS (CRT-1): 400.0 MHz maximum pixel clock
[     8.323] (--) NVIDIA(0): DELL U2412M (DFP-0): 330.0 MHz maximum pixel clock
[     8.323] (--) NVIDIA(0): DELL U2412M (DFP-0): Internal Dual Link TMDS
[     8.323] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[     8.323] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[     8.323] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     8.323] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[     8.323] (**) NVIDIA(0):     been enabled on all display devices.)
[     8.326] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     8.326] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[     8.326] (**) NVIDIA(0):     been enabled on all display devices.)
[     8.327] (==) NVIDIA(0): 
[     8.327] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     8.327] (==) NVIDIA(0):     will be used as the requested mode.
[     8.327] (==) NVIDIA(0): 
[     8.327] (II) NVIDIA(0): Validated MetaModes:
[     8.327] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select,CRT-1:nvidia-auto-select"
[     8.327] (II) NVIDIA(0): Virtual screen size determined to be 3600 x 1200
[     8.362] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[     8.362] (--) NVIDIA(0):     option
[     8.362] (II) UnloadModule: "vesa"
[     8.362] (II) Unloading vesa
[     8.363] (II) UnloadModule: "modesetting"
[     8.363] (II) Unloading modesetting
[     8.363] (II) UnloadModule: "fbdev"
[     8.363] (II) Unloading fbdev
[     8.363] (II) UnloadSubModule: "fbdevhw"
[     8.363] (II) Unloading fbdevhw
[     8.363] (--) Depth 24 pixmap format is 32 bpp
[     8.363] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[     8.372] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select,CRT-1:nvidia-auto-select"
[     8.474] Loading extension NV-GLX
[     8.585] (==) NVIDIA(0): Disabling shared memory pixmaps
[     8.585] (==) NVIDIA(0): Backing store disabled
[     8.585] (==) NVIDIA(0): Silken mouse enabled
[     8.586] (==) NVIDIA(0): DPMS enabled
[     8.586] Loading extension NV-CONTROL
[     8.587] Loading extension XINERAMA
[     8.587] (II) Loading sub module "dri2"
[     8.587] (II) LoadModule: "dri2"
[     8.587] (II) Module "dri2" already built-in
[     8.587] (II) NVIDIA(0): [DRI2] Setup complete
[     8.587] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     8.587] (--) RandR disabled
[     8.591] (II) SELinux: Disabled on system
[     8.592] (II) Initializing extension GLX
[     8.623] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.633] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     8.633] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.633] (II) LoadModule: "evdev"
[     8.633] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.635] (II) Module evdev: vendor="X.Org Foundation"
[     8.635]     compiled for 1.13.3, module version = 2.7.3
[     8.635]     Module class: X.Org XInput Driver
[     8.635]     ABI class: X.Org XInput driver, version 18.0
[     8.635] (II) Using input driver 'evdev' for 'Power Button'
[     8.635] (**) Power Button: always reports core events
[     8.635] (**) evdev: Power Button: Device: "/dev/input/event1"
[     8.635] (--) evdev: Power Button: Vendor 0 Product 0x1
[     8.635] (--) evdev: Power Button: Found keys
[     8.635] (II) evdev: Power Button: Configuring as keyboard
[     8.635] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     8.635] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     8.635] (**) Option "xkb_rules" "evdev"
[     8.635] (**) Option "xkb_model" "pc105"
[     8.635] (**) Option "xkb_layout" "pl"
[     8.637] (II) XKB: reuse xkmfile /var/lib/xkb/server-61818C6B46DD4F01AE1F641F27B555591612208F.xkm
[     8.638] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     8.638] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.638] (II) Using input driver 'evdev' for 'Power Button'
[     8.638] (**) Power Button: always reports core events
[     8.638] (**) evdev: Power Button: Device: "/dev/input/event0"
[     8.638] (--) evdev: Power Button: Vendor 0 Product 0x1
[     8.638] (--) evdev: Power Button: Found keys
[     8.638] (II) evdev: Power Button: Configuring as keyboard
[     8.638] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     8.638] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     8.638] (**) Option "xkb_rules" "evdev"
[     8.638] (**) Option "xkb_model" "pc105"
[     8.638] (**) Option "xkb_layout" "pl"
[     8.638] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/event2)
[     8.638] (**) Logitech USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[     8.638] (II) Using input driver 'evdev' for 'Logitech USB Laser Mouse'
[     8.638] (**) Logitech USB Laser Mouse: always reports core events
[     8.638] (**) evdev: Logitech USB Laser Mouse: Device: "/dev/input/event2"
[     8.638] (--) evdev: Logitech USB Laser Mouse: Vendor 0x46d Product 0xc069
[     8.638] (--) evdev: Logitech USB Laser Mouse: Found 12 mouse buttons
[     8.638] (--) evdev: Logitech USB Laser Mouse: Found scroll wheel(s)
[     8.638] (--) evdev: Logitech USB Laser Mouse: Found relative axes
[     8.638] (--) evdev: Logitech USB Laser Mouse: Found x and y relative axes
[     8.638] (II) evdev: Logitech USB Laser Mouse: Configuring as mouse
[     8.638] (II) evdev: Logitech USB Laser Mouse: Adding scrollwheel support
[     8.638] (**) evdev: Logitech USB Laser Mouse: YAxisMapping: buttons 4 and 5
[     8.638] (**) evdev: Logitech USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.638] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2/event2"
[     8.638] (II) XINPUT: Adding extended input device "Logitech USB Laser Mouse" (type: MOUSE, id 8)
[     8.638] (II) evdev: Logitech USB Laser Mouse: initialized for relative axes.
[     8.638] (**) Logitech USB Laser Mouse: (accel) keeping acceleration scheme 1
[     8.638] (**) Logitech USB Laser Mouse: (accel) acceleration profile 0
[     8.638] (**) Logitech USB Laser Mouse: (accel) acceleration factor: 2.000
[     8.638] (**) Logitech USB Laser Mouse: (accel) acceleration threshold: 4
[     8.639] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/mouse0)
[     8.639] (II) No input driver specified, ignoring this device.
[     8.639] (II) This device may have been added with another device file.
[     8.639] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event3)
[     8.639] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[     8.639] (II) Using input driver 'evdev' for 'HID 046a:0023'
[     8.639] (**) HID 046a:0023: always reports core events
[     8.639] (**) evdev: HID 046a:0023: Device: "/dev/input/event3"
[     8.639] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[     8.639] (--) evdev: HID 046a:0023: Found keys
[     8.639] (II) evdev: HID 046a:0023: Configuring as keyboard
[     8.639] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3/event3"
[     8.639] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 9)
[     8.639] (**) Option "xkb_rules" "evdev"
[     8.639] (**) Option "xkb_model" "pc105"
[     8.639] (**) Option "xkb_layout" "pl"
[     8.639] (II) config/udev: Adding input device HID 046a:0023 (/dev/input/event4)
[     8.639] (**) HID 046a:0023: Applying InputClass "evdev keyboard catchall"
[     8.639] (II) Using input driver 'evdev' for 'HID 046a:0023'
[     8.639] (**) HID 046a:0023: always reports core events
[     8.639] (**) evdev: HID 046a:0023: Device: "/dev/input/event4"
[     8.639] (--) evdev: HID 046a:0023: Vendor 0x46a Product 0x23
[     8.639] (--) evdev: HID 046a:0023: Found 1 mouse buttons
[     8.639] (--) evdev: HID 046a:0023: Found scroll wheel(s)
[     8.639] (--) evdev: HID 046a:0023: Found relative axes
[     8.639] (II) evdev: HID 046a:0023: Forcing relative x/y axes to exist.
[     8.639] (--) evdev: HID 046a:0023: Found absolute axes
[     8.639] (II) evdev: HID 046a:0023: Forcing absolute x/y axes to exist.
[     8.639] (--) evdev: HID 046a:0023: Found keys
[     8.639] (II) evdev: HID 046a:0023: Configuring as mouse
[     8.639] (II) evdev: HID 046a:0023: Configuring as keyboard
[     8.639] (II) evdev: HID 046a:0023: Adding scrollwheel support
[     8.639] (**) evdev: HID 046a:0023: YAxisMapping: buttons 4 and 5
[     8.639] (**) evdev: HID 046a:0023: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.639] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input4/event4"
[     8.639] (II) XINPUT: Adding extended input device "HID 046a:0023" (type: KEYBOARD, id 10)
[     8.639] (**) Option "xkb_rules" "evdev"
[     8.639] (**) Option "xkb_model" "pc105"
[     8.639] (**) Option "xkb_layout" "pl"
[     8.639] (II) evdev: HID 046a:0023: initialized for relative axes.
[     8.639] (WW) evdev: HID 046a:0023: ignoring absolute axes.
[     8.640] (**) HID 046a:0023: (accel) keeping acceleration scheme 1
[     8.640] (**) HID 046a:0023: (accel) acceleration profile 0
[     8.640] (**) HID 046a:0023: (accel) acceleration factor: 2.000
[     8.640] (**) HID 046a:0023: (accel) acceleration threshold: 4
[    10.061] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[    10.061] (II) NVIDIA(GPU-0):     Vision stereo.
[    10.061] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    10.061] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[    10.061] (**) NVIDIA(0):     been enabled on all display devices.)
[    10.111] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[    10.111] (II) NVIDIA(GPU-0):     Vision stereo.
[    10.111] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    10.111] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[    10.111] (**) NVIDIA(0):     been enabled on all display devices.)
[    10.591] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1920x1200 +1680+0"
[    10.660] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1920x1200 +1680+0, VGA-0: nvidia-auto-select @1680x1050 +0+0"
[    10.898] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[    10.898] (II) NVIDIA(GPU-0):     Vision stereo.
[    10.898] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    10.898] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[    10.898] (**) NVIDIA(0):     been enabled on all display devices.)
[    10.949] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[    10.949] (II) NVIDIA(GPU-0):     Vision stereo.
[    10.949] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    10.949] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[    10.949] (**) NVIDIA(0):     been enabled on all display devices.)
[    12.303] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[    12.303] (II) NVIDIA(GPU-0):     Vision stereo.
[    12.303] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    12.303] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[    12.303] (**) NVIDIA(0):     been enabled on all display devices.)
[    12.353] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[    12.353] (II) NVIDIA(GPU-0):     Vision stereo.
[    12.353] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    12.353] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[    12.353] (**) NVIDIA(0):     been enabled on all display devices.)
[    13.592] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[    32.842] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[    32.842] (II) NVIDIA(GPU-0):     Vision stereo.
[    32.842] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    32.842] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[    32.842] (**) NVIDIA(0):     been enabled on all display devices.)
[    32.893] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[    32.893] (II) NVIDIA(GPU-0):     Vision stereo.
[    32.894] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    32.894] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[    32.894] (**) NVIDIA(0):     been enabled on all display devices.)
[    64.182] (II) Open ACPI successful (/var/run/acpid.socket)
[    64.250] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1920x1200 +1680+0, VGA-0: nvidia-auto-select @1680x1050 +0+0"
[    90.046] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[    90.046] (WW) NVIDIA(0):     viewport height 1200; adjusting
[    90.048] (WW) NVIDIA(0): Specified panning domain width of 1280 is smaller than
[    90.048] (WW) NVIDIA(0):     viewport width 1920; adjusting
[    90.048] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[    90.048] (WW) NVIDIA(0):     viewport height 1200; adjusting
[    90.051] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[    90.051] (WW) NVIDIA(0):     viewport height 1200; adjusting
[   131.274] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[   131.274] (WW) NVIDIA(0):     viewport height 1200; adjusting
[   131.545] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select@1920x1200+1680+0,CRT-1:1600x1200@1600x1200+0+0"
[   139.432] (WW) NVIDIA(0): Specified panning domain width of 1280 is smaller than
[   139.432] (WW) NVIDIA(0):     viewport width 1920; adjusting
[   139.432] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[   139.432] (WW) NVIDIA(0):     viewport height 1200; adjusting
[   139.435] (WW) NVIDIA(0): Specified panning domain height of 720 is smaller than
[   139.435] (WW) NVIDIA(0):     viewport height 1200; adjusting
[   232.637] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[   232.637] (II) NVIDIA(GPU-0):     Vision stereo.
[   232.637] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   232.637] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[   232.637] (**) NVIDIA(0):     been enabled on all display devices.)
[   232.692] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[   232.692] (II) NVIDIA(GPU-0):     Vision stereo.
[   232.692] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   232.692] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[   232.692] (**) NVIDIA(0):     been enabled on all display devices.)
[   247.853] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[   247.853] (II) NVIDIA(GPU-0):     Vision stereo.
[   247.853] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   247.853] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[   247.853] (**) NVIDIA(0):     been enabled on all display devices.)
[   247.910] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[   247.910] (II) NVIDIA(GPU-0):     Vision stereo.
[   247.910] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   247.910] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[   247.910] (**) NVIDIA(0):     been enabled on all display devices.)
[   293.833] (II) NVIDIA(0): Setting mode "VGA-0: 1600x1200 @1600x1200 +0+0"
[   294.034] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1920x1200 +1600+0"
[   294.152] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @1920x1200 +1600+0, VGA-0: 1600x1200 @1600x1200 +0+0"
[  1458.018] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[  1458.018] (II) NVIDIA(GPU-0):     Vision stereo.
[  1458.018] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1458.018] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[  1458.018] (**) NVIDIA(0):     been enabled on all display devices.)
[  1458.076] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[  1458.076] (II) NVIDIA(GPU-0):     Vision stereo.
[  1458.076] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  1458.076] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[  1458.076] (**) NVIDIA(0):     been enabled on all display devices.)
[  9089.845] (II) NVIDIA(GPU-0): Display (Philips 220WS (CRT-1)) does not support NVIDIA 3D
[  9089.845] (II) NVIDIA(GPU-0):     Vision stereo.
[  9089.845] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  9089.845] (**) NVIDIA(0):     device Philips 220WS (CRT-1) (Using EDID frequencies has
[  9089.845] (**) NVIDIA(0):     been enabled on all display devices.)
[  9089.900] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[  9089.900] (II) NVIDIA(GPU-0):     Vision stereo.
[  9089.900] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  9089.900] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[  9089.900] (**) NVIDIA(0):     been enabled on all display devices.)
[ 13698.154] (II) evdev: HID 046a:0023: Close
[ 13698.154] (II) UnloadModule: "evdev"
[ 13698.154] (II) evdev: HID 046a:0023: Close
[ 13698.154] (II) UnloadModule: "evdev"
[ 13698.154] (II) evdev: Logitech USB Laser Mouse: Close
[ 13698.154] (II) UnloadModule: "evdev"
[ 13698.154] (II) evdev: Power Button: Close
[ 13698.154] (II) UnloadModule: "evdev"
[ 13698.154] (II) evdev: Power Button: Close
[ 13698.154] (II) UnloadModule: "evdev"
[ 13698.561] Server terminated successfully (0). Closing log file.

```

Any ideas would be much appreciated! :)

---

### Post by ponsfrilus on 2014-02-07
One thing we can do is add our voice to [https://www.change.org/petitions/displaylink-support-linux-with-dl-3000-series-chips]("https://www.change.org/petitions/displaylink-support-linux-with-dl-3000-series-chips")...

---

### Post by igorsantos07 on 2014-10-11
Hello seba2!

Have you ever got your screen to work?
I've got an AOC screen and I'm trying hard to make it turn on... I could even see it working on TTY1, but on X it does not work at all.

I noticed you used driver "displaylink" on your DisplayLinkDevice on xorg.conf. Where did you got that module? If I do that X complains it could not find that module, and I have to use "fbdev" to make it shut up.

---

### Post by SimonHGR on 2015-05-02
Harumph. I too would like this to work. I just got an AOC USB monitor, and the odd thing is that for me, it seems to very nearly work. The device is recognized, and I can turn it on. What I get when I do is a rather manky pattern of dots, but if I move the mouse over it, the mouse leaves square blocks that show what the screen should be showing. If I do a screen capture on it, I see again what should be there.

In other words, it's working except that it's not being refreshed. Any change from the normal system does not get pushed to the display, but the updates caused by a mouse movement are written. Surely this must be so close to working as to be almost palpable, no?

BTW, I'm running Ubuntu 14.04.

Does anyone have any more ideas?

---

### Post by gordintoronto on 2015-05-03
When hardware doesn't work, I generally suggest the latest version of the operating system. You could at least boot from a Live USB and see what happens.

You might also say exactly which AOC USB monitor it is.

---

### Post by Lop3 on 2015-05-04
> **gordintoronto said:**
> When hardware doesn't work, I generally suggest the latest version of the operating system. You could at least boot from a Live USB and see what happens.
You might also say exactly which AOC USB monitor it is.

It might be worth trying live ISO's but if it doesn't work it doesn't mean it can't work. Also when it comes to displaylink support newer kernels are not always better. There have been regressions in Displaylink support more than once. If a live ISO works, then that's great, take note of what distro it is and the kernel version. But if it doesn't work, you might need to enable/disable a framebuffer (requires a reboot I think) or try a few different kernels (definitely requires a reboot) and you can't do that on a Live ISO.

-----------------------------

I've been reluctantly using Displaylink linux for the last 2 years and it has always been a struggle. Displaylink misrepresent their support of linux. Their linux support is non-existant. Last time I checked **they only provided a link** to a bunch of obsolete not-really-working methods created by independent linux hackers that sort of worked on outdated distros.
Now there is displaylink support integrated into the Linux Kernel. On Mint 16 I upgraded to one of the newer ubuntu kernels and I managed to run 2x 1920x1080 DL165 devices. But now I'm on Mint 17 and it's based on ubuntu 14.04 and the kernel support for displaylink has regressed. Now I can only run 1 displaylink at 1920x1080 and the other one at a pathetic 1024x768 and it acts up daily, often prevents my system from shutting down, often causes slow startup, or just outright kills my ability to see anything on any of my monitors forcing me to do a hard reboot.

In a nutshell Displaylink on linux SUCKS! And we should not even consider supporting their pathetic brand due to their disregard for linux users.
The only reason there is any linux is because some hacker took the time to [reverse engineer the windows XP displaylink driver]("https://www.youtube.com/watch?v=Ci8HbCRRZvM"). (and found they had violated the GPL also...)

While you might find some success the only suggestions I can make is you **try different kernels**. There is one change you can make, by **enabling or disabling some framebuffer blacklist** in one of your linux config files.
It's worth a try, but you're better off not buying or wasting your time trying to use Displaylink devices at all.

If you're ready to leave the Displaylink frustration behind. (when I find some time I will try these methods) ...
 There are better solutions, such as running a virtual monitor (aka framebuffer) on your PC and then connecting to it from a device with a VNC viewer.
This can be done with an Android phone/tablet, or an ipad, kindle, etc. (the benefit is these devices power themselves when you're on the road, instead of sucking power from your laptop) Or a RaspberryPi with a HDMI monitor.
Or a [Banana Pi]("http://www.bananapi.com/") with a LVDS screen.

Like this:
[http://askubuntu.com/a/613361/336308](http://askubuntu.com/a/613361/336308) (was given in response to) [http://askubuntu.com/a/240571/336308](http://askubuntu.com/a/240571/336308)

Interesting links:
[http://ubuntuforums.org/showthread.php?t=1327186](http://ubuntuforums.org/showthread.php?t=1327186)
[http://askubuntu.com/questions/28608/how-do-you-use-an-android-tablet-as-a-second-display/240571#240571](http://askubuntu.com/questions/28608/how-do-you-use-an-android-tablet-as-a-second-display/240571#240571)
x11vnc (i reckon this will hold the solution)
xinerama (old, not well maintained/supported, I would try this last)
[http://www.ccfe.ac.uk/news_detail.aspx?id=213](http://www.ccfe.ac.uk/news_detail.aspx?id=213)
[http://www.piwall.co.uk/](http://www.piwall.co.uk/)

---

### Post by SimonHGR on 2015-05-17
The one I was trying was: E1649FWU

Really weird the way it works except for actually "pushing" the update to the screen. That would seem to be easy to achieve relative to the more general questions, particularly since the mouse activity achieves this. Ah well.

Oh, and I did try a live boot of 15.04. No joy there, I'm afraid.

---

### Post by SimonHGR on 2015-05-17
Oh, now this looks interesting. I have an iPad mini, so I'll try to set up the framebuffer/vnc viewer idea. That sounds like it would serve my needs well. Thanks! Appreciate the input Lop3, I had no idea such a thing was possible!

---

### Post by kevinf2 on 2016-04-06
> **SimonHGR said:**
> Harumph. I too would like this to work. I just got an AOC USB monitor, and the odd thing is that for me, it seems to very nearly work. The device is recognized, and I can turn it on. What I get when I do is a rather manky pattern of dots, but if I move the mouse over it, the mouse leaves square blocks that show what the screen should be showing. If I do a screen capture on it, I see again what should be there.

In other words, it's working except that it's not being refreshed. Any change from the normal system does not get pushed to the display, but the updates caused by a mouse movement are written. Surely this must be so close to working as to be almost palpable, no?

BTW, I'm running Ubuntu 14.04.

Does anyone have any more ideas?

With my DL device (mimo magic touch), Xrandr reported 136**6**x768@**60** and I had your issue. I set this in xorg.conf with 136**8**x768@**59.9**, and the problem was solved. [https://wiki.archlinux.org/index.php/DisplayLink](https://wiki.archlinux.org/index.php/DisplayLink) 
> 
Section "Monitor"
     Identifier "DVI-1-0"
     Option "PreferredMode" "1368x768_59.90"
     Modeline "1368x768_59.90"  85.72  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
EndSection


---

