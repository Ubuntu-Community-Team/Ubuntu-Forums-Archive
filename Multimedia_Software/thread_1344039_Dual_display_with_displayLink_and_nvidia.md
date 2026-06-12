---
title: "Dual display with displayLink and nvidia?"
date: 2009-12-02
forum: Multimedia Software
---

### Post by trubshac on 2009-12-02
Hi

I hope that someone has already done what I'm trying to do, and can therefore help me.

I've just purchased a Rextron VCUA-20 which is a USB to VGA adapter using the displayLink system.  It appears in my system as:
```
Bus 001 Device 006: ID 17e9:0133 Newnham Research 
```

I also have a normal nvidia card:
```
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8400 GS] (rev a1)

```

This is my xorg.conf:
```
Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

Section "ServerLayout"
    Identifier     "Server Layout"
    Screen      0  "BigScreen" 0 0
    Screen      1  "SmallScreen" LeftOf "BigScreen"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "BigMonitor"
EndSection

Section "Monitor"
    Identifier     "SmallMonitor"
EndSection

Section "Device"
    Identifier     "BigDevice"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "SmallDevice"
    Option         "fbdev" "/dev/fb0"	
EndSection

Section "Screen"
    Identifier     "BigScreen"
    Device         "BigDevice"
    Monitor        "BigMonitor"
    SubSection     "Display"
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "SmallScreen"
    Device         "SmallDevice"
    Monitor        "SmallMonitor"
    SubSection     "Display"
        Modes      "1280x1024"
    EndSubSection
EndSection

```

I'm running Ubuntu 9.10 on an Intel Dual-Core E5400.

I am trying to get the desktop running across both displays, but have had little success yet.  My nvidia display (BigDisplay in xorg) runs the gnome desktop just fine.  My USB display (SmallDisplay in xorg) shows just a blank screen.  I do however know that appropriate USB drivers etc have been loaded because when I shutdown, the terminal display output appears on the USB display.

The only reference to displayLink I can find in dmesg is:
```
[   15.184409] DisplayLink device attached
[   15.184723] ret control msg 0: 4 0500fffffff0

```

The only reference I can find to the USB display within /var/log/Xorg.0.log is where it echoes the configuration that it is using:
```
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Server Layout"
(**) |-->Screen "BigScreen" (0)
(**) |   |-->Monitor "BigMonitor"
(**) |   |-->Device "BigDevice"
(**) |-->Screen "SmallScreen" (1)
(**) |   |-->Monitor "SmallMonitor"
(**) |   |-->Device "SmallDevice"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled

```

Does anyone have any suggestions as to what I might try changing to get this working please?

---

### Post by number nine on 2009-12-03
It's still early days for DisplayLink USB graphics support in Linux so you might have more luck posting to the libdlo mailing list where most of the developers are:

[http://lists.freedesktop.org/mailman/listinfo/libdlo/](http://lists.freedesktop.org/mailman/listinfo/libdlo/)

Also:
[http://displaylink.org](http://displaylink.org)

---

### Post by trubshac on 2009-12-09
More information:

When I have booted up, and logged in, my normal gnome desktop is shown on my nvidia display, and my USB display is blank.
If I press <Ctrl>+<Alt>+0..6, then my nvidia display goes blank, and my USB display shows the relevant tty console where I can login and work normally.
When I press <Ctrl>+<Alt>+7, my USB display remains as it was, and my nvidia display restores the normal gnome desktop.
I'm unsure of the significance of this!  Does this information help anyone diagnose what may be wrong with my configuration?

I read in [http://ubuntuforums.org/showthread.php?t=1323155](http://ubuntuforums.org/showthread.php?t=1323155) that rectaganol thinks it may be a problem with fbcon taking over the device so that X cannot.  Can anyone help please?

---

### Post by pyro2927 on 2010-01-15
trubshac, did you ever figure out a solution?  I am having the exact same problem as you.

---

### Post by trubshac on 2010-01-16
No I haven't yet :-(  It's shelved for the moment, but please post what you did if you manage to get it working.

---

### Post by Mulchman on 2010-03-09
I've had some luck getting Ubuntu 9.04 (32 bit) & Ubuntu 9.10 (32 bit) to work my my Sewell USB External Video Card adapter.

I documented a lot of my progress on my [blog](http://mulchman.org/blog/?p=90).  You'll want udlfb from git (git clone [http://git.plugable.com/webdav/udlfb](http://git.plugable.com/webdav/udlfb)) and xf86-video-displaylink from [this package](http://projects.unbit.it/downloads/udlfb-0.2.3_and_xf86-video-displaylink-0.3.tar.gz).  (The latter package contains a udlfb library but it's old - you want the udlfb from git.)

The hardest part is putting together the xorg.conf... I can try and help with issues but am far from an expert in this matter.

---

### Post by trubshac on 2010-03-10
Many thanks Mulchman - I'll have another go myself now.  :D

---

### Post by Mulchman on 2010-03-10
I've been trying to get 3 screens up and running today on my desktop machine (the blog uses a simple laptop + additional screen which, to me, is far from an ideal use case as I want 3 screens running; anyway).

From some additional testing today I've found that I can't use the proprietary "nvidia" driver + the "displaylink" driver in the xorg.conf or I get a crash in randr.c:448 (RRFirstOutput).  The pScrPriv variable is always NULL on the return from dix/privates.c:159 (dixLookupPrivate) and causes a seg fault as there's no NULL check before accessing members of pScrPriv.  I'm trying to look into where these values get set in the dix/privates dictionary through some SSH gdb debugging of X but it's quite painful and slow.

Without the proprietary "nvidia" driver mentioned in the xorg.conf I can get all 3 of my screens to come up (DisplayLink + gfx cards' 2 DVI connected ones) but it's not ideal as the 2 DVI connected ones are mirrored.

Anyway, I mention this nvidia related issue as your xorg.conf from a while back has the driver mentioned (code snippet below) so you'll probably run into the same issue I'm hitting on my desktop machine when trying to use the nvidia driver.

```
Section "Device"
    Identifier     "BigDevice"
    Driver         "nvidia"
EndSection
```

---

### Post by niM_xaM on 2010-03-12
Hi Mulchman,

I've been trying to hook up an external monitor using displaylink usb adapter and your tutorial :
[http://mulchman.org/blog/?tag=displaylink](http://mulchman.org/blog/?tag=displaylink)

I followed every step exactly and managed to get the second monitor working (YAY!) Its running pretty smoothly and usable (i can run apps on it) .. however, it only works if I boot into Failsafe Gnome.. and the resolution is maxed at 1280x800.. 

When I boot in as normal Gnome, after entering the password the screen flicks and comes back to the login screen.. not able to get into the desktop.. (terminal mode also works)

The external monitor that I'd like to hook up is 1920x1080.. I've tried changing the resolution via the menus (System -> Preferences -> Display) but didnt see 1920x1080 option there.. I'm very new to Linux and not exactly sure how the xorg.conf work.. but here's my xorg.conf:

```

################ Original Video Settings ###############
Section "Screen"
    Identifier    "Default Screen"
    SubSection "Display"
        Depth    24
        Modes    "1920x1080"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    BusID           "PCI:01:00:0"
    Option    "NoLogo"    "True"
EndSection

##########################################################

Section "ServerLayout"
        Identifier      "Server Layout"
    Screen  0       "DisplayLinkScreen" 0 0 
        Screen  1       "Default Screen" LeftOf "DisplayLinkScreen"
    Option          "Xinerama" "off"
EndSection

###########################################################

Section "Files"
        ModulePath      "/usr/lib/xorg/modules"
        ModulePath      "/usr/local/lib/xorg/modules"
    ModulePath    "/usr/local/lib/xorg/modules/drivers"
EndSection

###################### DisplayLink Stuff ###################

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        SubSection "Display"
        Depth    24
        Modes    "1920x1080"
    EndSubSection
EndSection

```

I've put in Modes "1920x1080" for both monitors in the xorg.conf file and yet the monitor with the displaylink adaptor is running on 1280x800 .. Really appreciate if you can tell me what's wrong and advice on how to set the system up please.

Cheers! :)

---

### Post by Mulchman on 2010-03-13
The displaylink driver (xf86-video-displaylink) is still quite limited.  For instance, you can only do 16 bit depth (you have 24 in your xorg.conf) and there are some resolution limits.  You are probably hitting the resolution limit.

Btw, which version of the nvidia driver are you using?  (I'm using 185 and can't get the nvidia driver to work alongside the displaylink driver w/o crashing.)

Don't forget that there's also the libdlo mailing list - [http://lists.freedesktop.org/mailman/listinfo/libdlo](http://lists.freedesktop.org/mailman/listinfo/libdlo) - which has a lot more information on it (you can search the archives).

EDIT: When you do run into errors you can drop to another console (CTRL + ALT + F1-F6) and check the contents of /var/log/Xorg.0.log - it might show you error/warning information that is sometimes useful.

---

### Post by niM_xaM on 2010-03-16
Hi Mulchman, 


thanks for replying so soon. My nVidia driver version is 173.14.20 (on geforce FX 5200). 

I see.. at first i thought xf86 is the same with libdlo (or is one of the components of libdlo) .. so there are two different drivers for displaylink.. haha I'm a complete noob.. :p  I'll go and check out that forum then :) 

Cheers!

---

### Post by Mulchman on 2010-03-16
There are a couple of modules/libraries:

[list]
[*]libdlo: not used for anything
[*]udlfb: for framebuffer
[*]xf86-video-displaylink: X driver that uses udlfb
[/list]

Also, udlfb is shipped with certain Linux distros but the latest version lives in Git (and it's recommended to build your own from Git)

---

### Post by banoslo on 2010-03-27
Hi all,

I have got a displaylink adapter of lenovo (M01061), a laptop and two 1680x1050 res monitors. I wanted to use one monitor via vga-port and one monitor via displaylink adapter. The system is Ubuntu 9.10 (kernel 2.6.31-20-generic-pae).

Mulchman's description in his blog for Ubuntu 9.10 was used but I got stuck at some point. The monitor at vga-port was doing its job but not the displaylink one. My resolution was only 1280x1024..

I solved this way:
- unplugged displaylink from computer
- Start by updating the package list: ```
sudo apt-get update
```- Then download and install any package & system updates: ```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```- Then download some packages we&#8217;ll need later:```
sudo apt-get install build-essential xorg-dev libusb-dev git-core
```- Reboot
- removed old udlfb from directory ```

sudo rmmod udlfb
cd /lib/modules/`uname -r`/kernel/drivers/staging/udlfb/ && sudo mv udlfb.ko udlfb.ko.bak
sudo depmod -a

```- got latest udlfb: ```
cd $HOME/Desktop/ && git clone http://git.plugable.com/webdav/udlfb
```- made and installed it: ```
cd udlfb && make && sudo make install && sudo depmod -a 
```- got newest xf-video-udlfb: ```
cd $HOME/Desktop/ && git clone http://git.plugable.com/webdav/xf-video-udlfb
```- made and installed it: ```
cd xf-video-udlfb && ./configure && make && sudo make install
```- adding these three lines into /etc/gdm/Init/Default after the defintion of the gdmwhich() function:
```

XRANDR=`gdmwhich xrandr`
if [ "x$XRANDR" != "x" ] ; then
  $XRANDR -o 0
fi

```- (in a failsafed mode, restart computer) created a /etc/X11/xorg.conf file automatically: ```
Xorg -configure
```- changed xorg.conf file to
```


Section "ServerLayout"
    Identifier     "modified conf file: org by Xorg -configure"
    # added {
    Screen  0      "DisplayLinkScreen" 0 0
    Screen  1      "Screen0" LeftOf "DisplayLinkScreen"
    Option         "Xinerama" "off"
    # }
    # Screen  1      "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    # added {
    ModulePath   "/usr/local/lib/xorg/modules"
    ModulePath     "/usr/local/lib/xorg/modules/drivers"
    # }
     ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "glx"
    Load  "record"
    Load  "dri"
    Load  "dri2"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth   24
        Modes   "1680x1050"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

# added {
Section "Device"
    Identifier      "DisplayLinkDevice"
    driver          "displaylink"
    Option  "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
    Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
    Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
    Monitor         "DisplayLinkMonitor"
EndSection
#}


```Hope that help & cheers,
banoslo

---
Edited and fixed bugs in my description!

---

### Post by Ein2015 on 2010-04-19
banoslo, were you able to get it working doing that?

Mulchman, did we kill your blog? I can't get to it anymore!

I'm running 10.04, trying to get a 3rd monitor up using DL. So far I'm at the login screen, but I crash X whenever I try to login. I need to try what I've read here. :)

---

### Post by Mulchman on 2010-04-19
> **Ein2015 said:**
> Mulchman, did we kill your blog? I can't get to it anymore!

Don't know. It has been down for 2+ weeks now and I don't know why. I've sent some emails to the hosting company but they have not responded. Hopefully it's just a DNS issue.

---

### Post by robbychen on 2010-04-21
Hi,

I bought an UM-710S USB monitor that is DisplayLink compatible and am also looking for the solution to the Ubuntu 9.10 problem. I just found this thread. I'm glad to see this topic is still active :)

---

### Post by Ein2015 on 2010-04-24
robbychen,

When I finally get it working in 10.04 I'll try to post as much information as possible to help out.

---

### Post by Ein2015 on 2010-04-24
Sorry for double-post...

I've got the setup working (somewhat) on 10.04 now. I've followed the Mulchman 9.10 article with the installs and such except I installed the xf86-video-displaylink (or whatever it is close to that) through repos.

Here's my conf file...
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "DisplayLinkScreen" 0 0
    Screen      1  "Screen0" RightOf "DisplayLinkScreen"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "off"
EndSection

Section "Files"
    ModulePath     "/usr/lib/xorg/modules"
    ModulePath     "/usr/lib/xorg/modules/drivers"
    ModulePath     "/usr/lib/xorg/modules/extensions"
EndSection

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

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL E1909W"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1440+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

#### DisplayLink **** ####

Section "Device"
    Identifier     "DisplayLinkDevice"
    Driver         "displaylink"
    Option "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
    Identifier     "DisplayLinkMonitor"
    #VendorName     "Unknown"
    #ModelName      "DELL E1909W"
    #HorizSync       30.0 - 83.0
    #VertRefresh     56.0 - 75.0
    #Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "DisplayLinkScreen"
    Device         "DisplayLinkDevice"
    Monitor        "DisplayLinkMonitor"
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
EndSection
```

The displaylink monitor won't let me drag windows to and from it, but that's fine.

Now the only thing not working right is that the monitor running displaylink refuses to take a 1440x900 resolution (it's native one)... instead it only has 1280x1024. :\ Ideas?

---

### Post by robbychen on 2010-04-26
Ein2015: Thanks for the post. I tried to connect my DisplayLink monitor to my laptop running Ubuntu 9.10 yesterday with more dedication.:P This is what I've gotten so far (the config file is similar to yours):

[LIST]
[*]The DisplayLink screen displays the GNOME login screen after the start up.
[*]If I set the session to standard GNOME desktop, the X-Server will crash and return to the login screen.
[*]If I set the session to failsafe GNOME desktop, the desktop will load without problem.
[*]I already use dual-screen setup before adding the DisplayLink monitor, so the first two screens will combine into one screen when I attached the DisplayLink monitor and applied the modified xorg.conf file.
[*]As you wrote, the monitor also won't let me drag windows to and from it. This is perhaps because it runs in the two separate X-server. It looks like that it cannot setup as TwinView for two different graphic devices.
[/LIST]
Since then, I have given up and am waiting for Ubuntu 10.04 final next Thursday to see if I can get it working on the new version of Ubuntu. :(

---

### Post by Ein2015 on 2010-04-26
robbychen,

If I remember my X right, you're running the dual-monitor setup with Twinview and the single monitor with it's own X server. I've read that you can use Xinerama, but that it makes system performance go downhill fast.

I was originally running into the exact problem you were with the crashes. Post your Xorg.0.log file and I'll take a look.

---

### Post by robbychen on 2010-04-26
Hi, Ein2015:

Below is the content of my Xorg.0.log (note that I rebuilt my xorg.conf file once before with nvidia-xserver (I think this is the command, I don't remember) and reconfigured my graphics with nvidia-settings without DisplayLink device connected):

```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux robbyubtu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=0bf657de-d374-4469-8b70-bc468987f7b3 ro quiet splash
Build Date: 04 March 2010  09:57:23AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 26 18:44:46 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Nvidia-Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(**) ModulePath set to "/usr/lib/xorg/modules,/usr/local/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:06e9:1043:19b2 nVidia Corporation G98 [GeForce 9300M GS] rev 161, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:51:02 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1280x1024_75 +1280+0, DFP: 1280x800_60 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9300M GS (G98) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.98.38.00.07
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9300M GS at PCI:1:0:0:
(--) NVIDIA(0):     CMO CMC 19" AD (CRT-0)
(--) NVIDIA(0):     AUO (DFP-0)
(--) NVIDIA(0): CMO CMC 19" AD (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): AUO (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, DFP-0
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT:1280x1024_75+1280+0,DFP:1280x800_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "CRT:1280x1024_75+1280+0,DFP:1280x800_60+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Asus Laptop extra buttons
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Asus Laptop extra buttons: always reports core events
(**) Asus Laptop extra buttons: Device: "/dev/input/event7"
(II) Asus Laptop extra buttons: Found keys
(II) Asus Laptop extra buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device CNF7129
(**) CNF7129: always reports core events
(**) CNF7129: Device: "/dev/input/event8"
(II) CNF7129: Found keys
(II) CNF7129: Configuring as keyboard
(II) XINPUT: Adding extended input device "CNF7129" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event10"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device HID 062a:0000
(**) HID 062a:0000: always reports core events
(**) HID 062a:0000: Device: "/dev/input/event6"
(II) HID 062a:0000: Found 3 mouse buttons
(II) HID 062a:0000: Found x and y relative axes
(II) HID 062a:0000: Found scroll wheel(s)
(II) HID 062a:0000: Configuring as mouse
(**) HID 062a:0000: YAxisMapping: buttons 4 and 5
(**) HID 062a:0000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HID 062a:0000" (type: MOUSE)
(**) HID 062a:0000: (accel) keeping acceleration scheme 1
(**) HID 062a:0000: (accel) filter chain progression: 2.00
(**) HID 062a:0000: (accel) filter stage 0: 20.00 ms
(**) HID 062a:0000: (accel) set acceleration profile 0
(II) HID 062a:0000: initialized for relative axes.

```

---

### Post by ubootfanat on 2010-05-11
hi there!

having the same problem here.

ubuntu 10.04, nvidia-current (195....) from repos. xserver-xorg-video-displaylink 0.3 from repos.

I set up xorg.conf to start second xserver on displaylink device. This works but only in gnome safe mode. Seems that the nvidia driver is buggy. nv as well as vesa works (with limitations of course (cannot use my displayport screen)).

I will post details later.

any ideas in the meanwhile?

EDIT:
except from Xorg.0.log
```

(II) DL(0): EDID vendor "SAM", prod id 892
(II) DL(0): Using hsync ranges from config file
(II) DL(0): Using vrefresh ranges from config file
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) DL(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) DL(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) DL(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) DL(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) DL(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) DL(0): EDID vendor "SAM", prod id 892
(II) DL(0): EDID vendor "SAM", prod id 892
(II) DL(0): Using hsync ranges from config file
(II) DL(0): Using vrefresh ranges from config file
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) DL(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) DL(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) DL(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) DL(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) DL(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) DL(0): EDID vendor "SAM", prod id 892
(II) DL(0): EDID vendor "SAM", prod id 892
(II) DL(0): Using hsync ranges from config file
(II) DL(0): Using vrefresh ranges from config file
(II) DL(0): Printing DDC gathered Modelines:
(II) DL(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) DL(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) DL(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) DL(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) DL(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) DL(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) DL(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) DL(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) DL(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) DL(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) DL(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) DL(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) DL(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) DL(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) DL(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) DL(0): EDID vendor "SAM", prod id 892

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7fc7d0f3b000+0xf8f0) [0x7fc7d0f4a8f0]
3: /usr/bin/X (RRFirstOutput+0x1d) [0x4bf43d]
4: /usr/bin/X (ProcRRGetScreenInfo+0xc4) [0x4c7764]
5: /usr/bin/X (0x400000+0x30c3c) [0x430c3c]
6: /usr/bin/X (0x400000+0x261aa) [0x4261aa]
7: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7fc7cfc33c4d]
8: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address 0xa0

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

```

quite interesting. there is one and the same block three times in the logs just before crashing...
does anyone know, what is done in gnome standard mode and not in gnome safe mode? 

ubootfanat

---

### Post by HHGAG on 2010-05-15
I've not read all the posts but you should take a look at: [http://blogg.noonday.se/2010/01/28/linux-usb-video-adapter/](http://blogg.noonday.se/2010/01/28/linux-usb-video-adapter/)

alternatively is here an example for a xorg.conf:

[http://lkcl.net/displaylink/xorg.conf.displaylink.working.but.dissatisfactory](http://lkcl.net/displaylink/xorg.conf.displaylink.working.but.dissatisfactory)

You should note that:
 * Display Link has to be set as the main screen
 * DisplayLink supports currently only 16bit color depth, it must be configured according to all screens
 * DisplayLink screen has to begin the screen position on X-axis 0 and y-axis 0, ie the far left, otherwise there are problems with the mouse
 * DisplayLink supports only 1280x1024 as maximum resolution

---

### Post by samjam on 2010-05-26
> **HHGAG said:**
> I've not read all the posts but you should take a look at: [http://blogg.noonday.se/2010/01/28/linux-usb-video-adapter/](http://blogg.noonday.se/2010/01/28/linux-usb-video-adapter/)

alternatively is here an example for a xorg.conf:

[http://lkcl.net/displaylink/xorg.conf.displaylink.working.but.dissatisfactory](http://lkcl.net/displaylink/xorg.conf.displaylink.working.but.dissatisfactory)

You should note that:
 * Display Link has to be set as the main screen
 * DisplayLink supports currently only 16bit color depth, it must be configured according to all screens
 * DisplayLink screen has to begin the screen position on X-axis 0 and y-axis 0, ie the far left, otherwise there are problems with the mouse
 * DisplayLink supports only 1280x1024 as maximum resolution

I'm running my displaylink at 1680x1050 but it only works in 16 bit mode.

I have it as a 3 screen desktop with my ATI radeon having two of the monitors.

If I put it into 24 bit mode, then X segfaults when it adds the displaylink screen which sounds like it sort of "works" but maybe not at my resolution

Because there is no colour depth in common I have to have two separate desktops (no xinerama) until xrandr and some vga arbiter magic stuff makes it all work nicely maybe at meerkat time.

---

### Post by snoe on 2010-05-27
samjam, I'd be very interested to see your xorg.conf - when I start X, the maximum resolution I can get on the displaylink card is 1280x1024. I can see in the log that the higher resolutions are getting filtered out because of these messages:

```
(II) DL(0): Not using mode "1680x1050" (height too large for virtual size)
(II) DL(0): Not using mode "1600x1200" (height too large for virtual size)
(II) DL(0): Not using mode "1360x765" (width too large for virtual size)
(II) DL(0): Not using mode "1440x900" (width too large for virtual size)
(II) DL(0): Not using mode "1440x900" (width too large for virtual size)
(II) DL(0): Not using mode "1400x1050" (height too large for virtual size)
```

If I uncomment the Virtual line in my xorg.conf, I get a segfault
```
Section "ServerLayout"
    Identifier     "Layout0"
    #Screen       0 "Screen1"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard" 
    InputDevice    "Mouse0" "CorePointer"     
EndSection                                    

Section "Files"
        ModulePath      "/usr/lib/xorg/modules"     
        ModulePath      "/usr/local/lib/xorg/modules"
EndSection                                           

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection                       

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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown" 
    ModelName      "Apple"   
    HorizSync       30.0 - 75.0
    VertRefresh     60.0       
    Option         "DPMS"      
EndSection                     

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    #Driver         "nv"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400M"
    #BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: 1280x800 +2048+352, DFP-1: 2048x1152 +0+0"
    SubSection     "Display"
        Depth       16
    EndSubSection
EndSection

Section "Device"
        Identifier "DisplayLinkDevice"
        Driver "displaylink"
        Option "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
        Identifier "Monitor1" #SISUSBVGA
        #Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
EndSection

Section "Screen"
        Identifier "Screen0"
        Device "DisplayLinkDevice"
        Monitor "Monitor1"

        SubSection "Display"
                Depth   16
                #Virtual 1680 1050
        EndSubSection
EndSection
```

The segfault is the same as this one:
[http://lists.freedesktop.org/archives/libdlo/2009-June/000229.html](http://lists.freedesktop.org/archives/libdlo/2009-June/000229.html)

---

### Post by samjam on 2010-05-27
I'm not using nvidia.... but ati radeon.
My xorg.conf is

```

Section "ServerLayout"
        Identifier     "m123"
        Screen      0  "screen0" 0 0
        Screen      1  "ATI Screen" RightOf "screen0"
EndSection

Section "ServerLayout"
        Identifier     "m23"
        Screen      0  "ATI Screen" 0 0
#        Option "Xinerama" "off"
EndSection

Section "ServerLayout"
        Identifier     "m1"
        Screen      0  "screen0" 0 0
        Option "Xinerama" "off"
EndSection

Section "Screen"
	Identifier	"ATI Screen"
	Device	"ATI Device"
	Monitor "ATI Monitor"
        DefaultDepth     24
#	DefaultFbBpp	16
        SubSection "Display"
		Depth 24
                Viewport   0 0
                Virtual   3360 1050
        EndSubSection

EndSection

Section "Device"
	Identifier	"ATI Device"
	Driver "ati"
        BusID       "PCI:1:5:0"
        Option      "Monitor-DVI-0" "DVI-0"
#        Option      "Monitor-VGA-0" "VGA-0"
	Option      "Monitor-LVDS"  "LVDS"

EndSection

Section "Monitor"
        Identifier   "ATI Monitor"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
#        Option      "Position" "1680 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "DVI-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
        Option      "RightOf" "VGA-0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "LVDS"
        Option      "Disable" "true"
#	Option      "Ignore" "true"
EndSection

Section "Monitor"
        Identifier   "VGA-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
	Option      "Primary" "true"
EndSection

Section "Screen"
        Identifier "screen0"
        Device "dl0"
        Monitor "monitor0"
        DefaultDepth     16
	SubSection "Display"
		Depth 16
		Modes "1680x1050"
	EndSubSection
	Option "NoInt10" "true"
EndSection

Section "Device"
        Identifier      "dl0"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
        Identifier "monitor0"
	Mode "1680x1050"
	    # D: 146.263 MHz, H: 65.296 kHz, V: 59.960 Hz
	    DotClock 146.264
	    HTimings 1680 1784 1960 2240
	    VTimings 1050 1053 1059 1089
	    Flags    "+HSync" "-VSync"
	EndMode
	Mode "1024x768"
	    # D: 64.998 MHz, H: 48.362 kHz, V: 60.002 Hz
	    DotClock 64.999
	    HTimings 1024 1048 1184 1344
	    VTimings 768 771 777 806
	    Flags    "-HSync" "-VSync"    # Warning: XFree86 doesn't support accel
	EndMode
EndSection



```

---

### Post by random2001 on 2010-07-13
Has anyone figured this out? Xorg is still crashing when i try to use my displaylink on 10.04...Here is my xorg.conf:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "DisplayLinkScreen" 0 0
    Screen      1  "Screen0" RightOf "DisplayLinkScreen"
#    Screen 0       "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "off"
EndSection

Section "Files"
EndSection

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

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SUN GH18PS"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300 GE"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
  Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

############### DisplayLink Stuff ###############

Section "Device"
        Identifier      "DisplayLinkDevice"
        Driver          "displaylink"
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
                Modes   "1280x1024"
        EndSubSection
EndSection
``` In addition this is the error from Xorg.log.0:


```
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x79f410]
3: /usr/bin/X (ProcRRGetScreenInfo+0xae) [0x810ef0e]
4: /usr/bin/X (0x8048000+0xbe945) [0x8106945]
5: /usr/bin/X (0x8048000+0x2a477) [0x8072477]
6: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
7: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x34ebd6]
8: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address 0x68

Caught signal 11 (Segmentation fault). Server aborting
```

---

### Post by shotton on 2010-12-02
Did you every get this working I'm getting the exact same error. All three screens are working but GNOME won't start, it will not get passed the login screen and the nvidia seems to try and load twice. 

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux joel-shuttle 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=1855aa30-570a-41ea-beb7-829d08573bab ro quiet splash
Build Date: 10 November 2010  11:25:26AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Dec  2 14:26:27 2010
(++) Using config file: "xorg.test.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eaadb]
1: /usr/bin/X (0x8048000+0x610fd) [0x80a90fd]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x420410]
3: /usr/bin/X (ProcRRGetScreenInfo+0xae) [0x810afce]
4: /usr/bin/X (0x8048000+0xbd8f5) [0x81058f5]
5: /usr/bin/X (0x8048000+0x28eb7) [0x8070eb7]
6: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
7: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x216bd6]
8: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address 0x68

xorg.conf

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
    # HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Monitor"
    Identifier "MonitorUsbVga"
    VendorName "Monitor Vendor" # value does not matter
    ModelName "Monitor Model" # value does not matter
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 1280x1024 +1280+0"
    DefaultDepth    16    
    SubSection "Display"
        Depth       16
    EndSubSection
EndSection

Section "Screen"
    Identifier "ScreenUsbVga"
    Device "DeviceUsbVga"
    Monitor "MonitorUsbVga"
    DefaultDepth    16
    SubSection "Display"
        Depth   16
        Modes   "1280x1024"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    # generated from default
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
#        Screen      0  "Screen0" 0 0
    Screen      0  "ScreenUsbVga" 0 0
    Screen      1  "Screen0" RightOf "ScreenUsbVga"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    #    Option "AddARGBGLXVisuals" "False"
    #    Option "RenderAccel" "False"
    #    Option "AllowGLXWithComposite" "False"
    #    Option "backingstore" "False"
    #    Option "TripleBuffer" "False"
EndSection

Section "Device"
    Identifier "DeviceUsbVga"
    VendorName "Newnham Research" # Value does not matter
    BoardName "Newnham Research" # Value does not matter
    Option  "fbdev" "/dev/fb1"
    Driver    "displaylink"
EndSection

---

### Post by random2001 on 2010-12-02
> **shotton said:**
> Did you every get this working I'm getting the exact same error. All three screens are working but GNOME won't start, it will not get passed the login screen and the nvidia seems to try and load twice.

I haven't unfortunately. I just have my spare monitor blank next to me. If you end up figuring it out, could you let me know?

---

