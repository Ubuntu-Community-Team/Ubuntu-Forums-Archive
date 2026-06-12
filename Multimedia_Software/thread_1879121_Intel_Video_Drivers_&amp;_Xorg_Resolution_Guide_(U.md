---
title: "Intel Video Drivers &amp; Xorg Resolution Guide (Ubuntu 10.04) [H67 Chipset Sandy Bridge]"
date: 2011-11-11
forum: Multimedia Software
---

### Post by own3mall on 2011-11-11
[CENTER]**Native Resolution Support Ubuntu?**
[/CENTER]

I had all sorts of problems trying to get my Ubuntu 10.04 Lucid installation to use the correct resolution on my widescreen monitor.  My native resolution didn't even show up in the display settings, and my monitor couldn't be detected.  It was shown as unknown. After following countless guides, I couldn't get it to detect my monitor or use its native resolution.  I installed intel drivers, but after installing them, they were not being used by Xorg.  I think it's because my system uses Sandy Bridge hardware, and as such, there are a few bugs in Ubuntu 10.04.  After spending 8+ hours, I got it to work.

This guide should work for motherboards using integrated intel video with the H67 chipset (sandy bridge)

My system specs just in case it is hardware related:

```

Intel i7 2600k CPU
ZOTAC H67ITX-C-E LGA 1155 Intel H67 Mini ITX Intel Motherboard
8GB of DDR3
1TB Hard Drive
Blu-ray Burner
Integrated Intel Graphics

```[CENTER]**Quick Note on Kernel Version**
[/CENTER]

Note, *you may need to download and use the latest Kernel for Ubuntu 10.04*.  You can do this by listing the newest kernels available:

```

apt-cache search linux-image

```To install the latest, use the following:

```

sudo apt-get install linux-image-[LATEST] linux-headers-[LATEST]
#Where LATEST = the most recent kernel version listed by using the above command.

```[CENTER]**Guide for Installing Video Drivers and Setting Resolution (Ubuntu 10.04)**
[/CENTER]
 
Add the following PPA to the system's software              sources by first loading the list:

```

sudo nano /etc/apt/sources.list

```Then, add the following lines to the bottom of the file:

```
[FONT=monospace]
[/FONT]deb http://ppa.launchpad.net/glasen/intel-driver/ubuntu lucid main 
deb-src http://ppa.launchpad.net/glasen/intel-driver/ubuntu lucid main 
 
```Save the file and exit.  Now run:

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 066ADE1D
sudo apt-get update
sudo apt-get upgrade

```Right, the intel drivers have been installed, but the vesa drivers are still in use.  

Before we restart your computer, let's get some information about the resolution mode we'll create later by running this command:

```

cvt [width] [height]  
# where width is your desired screen resolution width 
# where height is your desired screen resolution height.

```You should get a line that looks similar to:

```

eric@i7ubuserver:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

```All LCD monitors use a refresh rate of 60Hz by default.  However, we need the exact refresh rate for later... write down the resolution and the refresh rate (in my case it was 1440x900_60.00).

**[Following SECTION Assumes You Are Logged In as Root in Recovery Mode]**

Restart your system.  Boot up into recovery mode by getting the boot menu to show by holding down the Shift key.  Choose the kernel with (recovery) in parenthesis.  Once the "terminal" loads, you'll be logged in as root.  Now generate the Xorg.conf file by:

```

sudo Xorg -configure

```The xorg file is created and located here:

/root/xorg.conf.new

Edit the config:

```

sudo nano /root/xorg.conf.new

```By default, it should look similar to this:

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
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
    Load  "dri2"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "glx"
    Load  "dri"
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
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Sandy Bridge Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
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

```Make sure driver is set to intel in this section

```

Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Sandy Bridge Integrated Graphics Controller"
    BusID       "PCI:0:2:0"

```OK, that's done, but now we need to specify the resolutions that your monitor supports for each mode.

Add your monitor's supported resolutions to the xorg.conf file.  Make sure you use the resolution settings you received earlier when you ran the cvt command.  It should look like this:

```

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
EndSection

```As you can see, I added my resolution to the Modes line for each subsection.  You can add as many as you want (assuming your monitor will support that resolution).  Just separate them with a space as shown above.  All resolutions should be specified with the refresh rate appended to the end of the resolution by using "_" followed by the refresh rate you received from the cvt command.  If you omit the refresh rate, it will display a black screen and not display properly when we're done configuring a few more things.

My entire xorg config looks like this:

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
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
    Load  "dri2"
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "glx"
    Load  "dri"
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
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Sandy Bridge Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes        "1440x900_60.00" "1280x1024_60.00" "1024x768_60.00" "800x600_60.00"
    EndSubSection
EndSection

```Save your xorg file and quit nano.

Before we move the xorg file into the proper directory, we need to make a few more changes to different files.

Use this command to set the KMS mode for i915 (intel video only).

```
[I]
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
[/I]
```Then do:

```

update-initramfs -u

```Next, we're going to force the grub boot loader to use the i915 modeset by first editing the default/grub.conf file:

```

nano /etc/default/grub

```Find the line where it says:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```And replace it with:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"

```Now run the following command:

```

update-grub

```We did the above to force the i915.modeset because if we don't, our Xorg will not start properly and complain with a message similar to this when booting (which I received several times):

```

[   719.236] (--) using VT number 8
[   719.386] (EE) No devices detected.
[   719.386] 
Fatal server error:
[   719.386] no screens found
[   719.386] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org

```Let's copy the xorg file into the proper directory:

```

cp /root/xorg.conf.new /etc/X11/xorg.conf

```Restart your computer by using Control-Alt-Delete.

Your computer should boot into Linux and use your monitor's native resolution.  Your monitor should also be detected. If you are redirected to a terminal, rename the xorg file and restart to allow Ubuntu to choose the best settings, or edit the xorg.conf again using nano.  Make changes and reboot.  If you have any problems, I'd be happy to try and assist.  I hope this guide helps.  Please comment and I should be around to edit :)

It's a frustrating process, and I can't believe it's so hard to configure, change resolutions, and use the proper drivers in linux for the display.  Windows gets it right in about 2 seconds....  (still a linux fanboy, but come on!)

**References:**

[http://www.freebsd.org/doc/handbook/x-config.html](http://www.freebsd.org/doc/handbook/x-config.html)
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
[https://launchpad.net/~glasen/+archive/intel-driver]("https://launchpad.net/%7Eglasen/+archive/intel-driver")
[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

---

### Post by MoreOrLess on 2011-11-12
> **own3mall said:**
> Windows gets it right in about 2 seconds....

Probably not Windows 98, and not even XP without the right driver installed...
You're using hardware that's relatively new and much newer than the versions of the graphics stack components you're running. Ubuntu 11.10 probably would work "out of the box."

---

### Post by own3mall on 2011-11-13
> **MoreOrLess said:**
> Probably not Windows 98, and not even XP without the right driver installed...
You're using hardware that's relatively new and much newer than the versions of the graphics stack components you're running. Ubuntu 11.10 probably would work "out of the box."

I don't wish to use a version that's not LTS though, but I'd assume you're right.

---

### Post by own3mall on 2011-11-19
Tried Ubuntu 11.10, and it works great with my hardware.  Unfortunately, gnome 3 and Unity are the worst design fails I've ever seen in a GUI.  As such, if you'd like to use your older Linux versions with your newer Intel Sandy Bridge hardware and gnome 2, please compile and install the latest kernel for your Ubuntu version.

Here's a great guide here:

[http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/](http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/)

Just did the whole thing, and all of my hardware is working and was identified correctly.  It identifies all of my monitors and is using its native resolution.  No more Unity or gnome 3.  Welcome back gnome 2.  :KS  Using Ubuntu 10.04, and will probably use it for life until the whole Unity thing ends up in the trash along with gnome 3.  KDE worked OK, but it wasn't like gnome 2.  Sorry, I'm just frustrated with the way linux is going.  It's gonna be another XP vs 7 phase, and even Microsoft is being stupid with their latest Windows 8 GUI.  Please stop breaking things if they aren't broken.  I wish people would take remedial classes in design.

/rant

---

### Post by bmfloyd on 2012-02-03
[own3mall]("http://ubuntuforums.org/member.php?u=869862"), your guide not just worked for me, I've applied on 11.10 successfully and also it turned on effects after trying to turn on my NVidia card and crashed my Oneiric Ocelot.

Thank you very much for sharing your work.  It helped me a lot!

---

### Post by LuisVoid on 2012-05-12
Dear own3mall:  THANKS A LOT MATE!  After struggling for like a week reading tutorials, posts, etc... yours is the only one that has worked and believe me, I'm grateful man... so I've just created an account to let you know.  I've followed all your instructions (had to change some details since the distro I'm using names/keeps/reads its Xorg.conf differently) and let me assure you that if it wasn't for your guidance I would have probably punch my monitor hard enough to regret it the rest my life.  I got my laptop's native resolution right away and on top of that,  as soon as I plugged my HDMI display it also worked.  So THANKS AGAIN!  Luis

---

### Post by own3mall on 2012-05-16
> **LuisVoid said:**
> Dear own3mall:  THANKS A LOT MATE!  After struggling for like a week reading tutorials, posts, etc... yours is the only one that has worked and believe me, I'm grateful man... so I've just created an account to let you know.  I've followed all your instructions (had to change some details since the distro I'm using names/keeps/reads its Xorg.conf differently) and let me assure you that if it wasn't for your guidance I would have probably punch my monitor hard enough to regret it the rest my life.  I got my laptop's native resolution right away and on top of that,  as soon as I plugged my HDMI display it also worked.  So THANKS AGAIN!  Luis

Glad it worked for you!  I spent a lot time writing this guide, and I just noticed a few mistakes.  I'll probably go back and edit it.

---

### Post by leifharmsen on 2012-10-08
Still no luck.   It rebooted, and said in an X gui that I was running in low graphics mode and gave me some options.   I tried "reconfigure graphics" but no joy.   I tried to "rename xorg file" which I assume is the ../X11/xorg.conf file in order for "Ubuntu to choose..."  and I'm back where I started, with the same wrong screen resolution I began with and no option to change it to the right one.   Back to the drawing board, unless someone there has further instructions.  Thanks anyway - learned a little bit about what's inside there, anyway.

---

### Post by zenshot on 2012-10-14
Thank you!

The grub part was enough for me on precise 12.04 LTS.

It was very annoying to see that after upgrading from 10.04 to 12.04.1 LTS precise the boot process were apparently frozen on my Acer Aspire 5810T after "Battery state check"

Pressing the power button brought it to halt. 

As I debugged found out that it was because X did not start. Turned out I had to delete a small xorg.conf left there by the installer. After deleting /etc/X11/xorg.conf X started with VESA mode, only 1024x768 - bringing up a slow ugly screen.

For me this:

Code:

sudo Xorg -configure

ended in error - tried the grub part only and worked like charm, without generating a new xorg.conf file. 

I did from this part:

"Use this command to set the KMS mode for i915 (intel video only)."

until the last command:

Code:

update-grub
Very happy to see my laptop working after restart.

Best, zenshot

---

### Post by own3mall on 2012-10-15
> **leifharmsen said:**
> Still no luck.   It rebooted, and said in an X gui that I was running in low graphics mode and gave me some options.   I tried "reconfigure graphics" but no joy.   I tried to "rename xorg file" which I assume is the ../X11/xorg.conf file in order for "Ubuntu to choose..."  and I'm back where I started, with the same wrong screen resolution I began with and no option to change it to the right one.   Back to the drawing board, unless someone there has further instructions.  Thanks anyway - learned a little bit about what's inside there, anyway.

I would just compile the latest kernel then on whatever Ubuntu version you're using.

[http://www.howopensource.com/2011/08...-10-and-10-04/]("http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/")

Should work without you having to make any xorg changes.

---

### Post by johnaaronrose on 2012-11-16
> **own3mall said:**
> Tried Ubuntu 11.10, and it works great with my hardware.  Unfortunately, gnome 3 and Unity are the worst design fails I've ever seen in a GUI.  As such, if you'd like to use your older Linux versions with your newer Intel Sandy Bridge hardware and gnome 2, please compile and install the latest kernel for your Ubuntu version.

Here's a great guide here:

[http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/](http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/)

Just did the whole thing, and all of my hardware is working and was identified correctly.  It identifies all of my monitors and is using its native resolution.  No more Unity or gnome 3.  Welcome back gnome 2.  :KS  Using Ubuntu 10.04, and will probably use it for life until the whole Unity thing ends up in the trash along with gnome 3.  KDE worked OK, but it wasn't like gnome 2.  Sorry, I'm just frustrated with the way linux is going.  It's gonna be another XP vs 7 phase, and even Microsoft is being stupid with their latest Windows 8 GUI.  Please stop breaking things if they aren't broken.  I wish people would take remedial classes in design.

/rant
I have a Sandy Bridge graphics card. Instead of the boot splash screen, I get a blank screen after installing kernel 3.0 as per the guide. Any ideas on how to fix?

---

