---
title: "Ubuntu 10.10 incompatibility with Sony vaio cw series graphic card"
date: 2010-10-11
forum: Multimedia Software
---

### Post by praiser on 2010-10-11
Hi
I have a problem with installing ubuntu 10.10 in my vaio cw. when I boot it , it doesn't show  anything on my LCD but when I plug a monitor in , there would be an output. how can fix this problem? 

also I have the same problem with 10.04 version

---

### Post by iisdev on 2010-10-11
This sounds an awful lot like your issue?

Nvidia on Sony laptop:
[https://help.ubuntu.com/community/NvidiaOnSonyLaptop]("https://help.ubuntu.com/community/NvidiaOnSonyLaptop")

---

### Post by saliflo on 2010-10-12
It was working in Lucid but not my Maverick

---

### Post by praiser on 2010-10-13
> **saliflo said:**
> It was working in Lucid but not my Maverick

Yes he is right!

---

### Post by praiser on 2010-10-23
Hey I already have this problem can anybody help me?:(

---

### Post by SymmetryBreaking on 2011-01-08
Yo,

Sorry if this is already posted somewhere else in the forum, but this thread is the #1 result on google for "Vaio CW ubuntu 10.10" and pointed me in the right direction to eventually get my Vaio working so I thought I'd try to save others the trouble, if possible.  I've included as full a description as possible of what  didn't work as well; the resulting post being atrociously long.  Thus** I have bolded the essential info to save time for those to whom the details are not relevant,** such as [U]**those who went through all this in earlier versions of ubuntu only to have the known approaches fail when installing maverick.**
[/U] 
Background (+ what didn't work) - **I am running Ubuntu 10.10 Maverick Meerkat _with full graphics functionality_ on a Sony Vaio CW **(VPCCW21FX) with a **Nvidia GeForce 310m GPU and 1366x768 internal LCD**.  The default video on the install disk worked with my (so crappy I got it for free) ilo (mfd. by SHINCO) LCD TV through the HDMI port - better than many ppl's experience apparently.  However, even this was broken by using the "additional drivers" manager included w/ ubuntu, but booting in failsafe graphics mode after attemptind to install nvidia-current (260) DID work with the integrated LCD, though the nvidia drivers did NOT load, proper resolution was not detected, video was choppy, no 3d, HDMI no longer worked, etc. - but setting this as the default configuration allowed me to work within x and from a command line without loading x - if anybody wants to tell me how to figure out why so I can send a report & a copy of the config files to the ubuntu developers I'd appreciate it, as enabling this setting during install by default on Sony laptops is likely a trivial matter and would enable VAIO owners to install Ubuntu without an additional monitor or any software outside of the install disk.  This setting enabled me to boot to a command line on the internal monitor with and without nouveau enabled, btw.

After messing around with the various fixes and xorg.conf settings posted by others around the net, I eventually gave up on both the ubuntu approved nvidia-current and the current drivers from Nvidia's site.  having read that the 256.44 drivers worked without even the custom edid hack I gave the available .deb package a try.  After much more fruitless finagling, I gave up on the available 256.44 .deb as well and downloaded the 256.44 .run from Nvidia.

[B]Installing the nvidia 256.44 .run package (downloaded from their website) from the command line with a custom edid file (exported using Phoenix in win7) _worked!_ However, only with the_ "Option   "IgnoreABI" "True"_ line in the ServerLayout section of xorg.conf!

[/B]Oddly the nvidia-setttings config panel properly enabled my HDMI connected TV, though **I also had to dump the edid.bin from my HDMI connected LCD tv in windows to get any resolution above 640x480 - but that works flawlessly now as well.**

the only other thing I can think of is that **I still have the "nomodeset" option enabled in grub from my previous finagling, though this is probably not necessary** - nothing's broken now so I haven't bothered removing it.

**The nvidia-settings applet does not break my config as others had reported in lucid; twinview and multiple xscreens work with dynamic switching, my VGA port works, etc.**

**So, for anyone experiencing this problem, download and install 256.44 (sudo sh '/path/packagename.run') _after booting nouveau-free to a command prompt_, and follow the tutorial linked near the beginning of this thread regarding the edid files and xorg.conf edits, but in addition insert the ignoreABI option line into your xorg.conf as well.**  

A note for phoenix users - make sure you use "export edid" rather than "save edid as" in phoenix, and rename the file from the .hex it exports to .bin.  The .dat that results from using the "Save As" menu option is NOT a valid edid file!

 For good measure, I will now include the full text of my xorg.conf file and edid dump, which mush be renamed from sny.txt to sny.bin - I couldn't upload it with the .bin extension.

--------------------------


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "IgnoreABI" "True"
    Option         "Xinerama" "1"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony Nvidia Default Flat Panel"
    HorizSync       29.0 - 47.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DFP-1"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 310M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 310M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "ConnectedMonitor" "DFP-0,DFP-1,CRT"
    Option         "CustomEDID" "DFP-0:/etc/X11/sny.bin"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "CustomEDID" "DFP-0:/etc/X11/shinco.bin"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
-----------------------------------------------------------------------------------

---

### Post by josemald on 2011-02-10
Hi everybody, I also can't get my Sony Vaio CW series (vpccw17 model, Nvidia G210M video card) to show anything on the laptop screen. It works well with an external monitor through VGA port as well as an LCDTV through HDMI port (but with the TV watever should be in the screen borders is not shown up, like the tool bar).  

I'm booting Ubuntu from a flash drive, created with Casper RW creator. It has a persistent file of around 3GB.  Is there any way to configure the monitor to work? I've tried the above solutions but can't install drivers and can't copy anything into the /etc folder.  I tried changing my account into administrator, but didn't work either. 

BTW, I'm a complete rookie with linux and ubuntu, I'm trying to learn a bit by using it before actually installing it on my computer.  So please be as explicit as possible.

Thanks.

---

### Post by SymmetryBreaking on 2011-03-05
> **josemald said:**
> Hi everybody, I also can't get my Sony Vaio CW series (vpccw17 model, Nvidia G210M video card) to show anything on the laptop screen. It works well with an external monitor through VGA port as well as an LCDTV through HDMI port (but with the TV watever should be in the screen borders is not shown up, like the tool bar).  

I'm booting Ubuntu from a flash drive, created with Casper RW creator. It has a persistent file of around 3GB.  Is there any way to configure the monitor to work? I've tried the above solutions but can't install drivers and can't copy anything into the /etc folder.  I tried changing my account into administrator, but didn't work either. 

BTW, I'm a complete rookie with linux and ubuntu, I'm trying to learn a bit by using it before actually installing it on my computer.  So please be as explicit as possible.

Thanks.

Unfortunately recent Vaio laptops use a non-standars method for addressing several pieces of hardware which was apparently reverse-engineered from the way that windows expects rather than the way that the designers of the hardware intended, so they are not the best machines to learn linux for an absolute beginner.  

That said, I think that if you do get it working you will be hard pressed to return to the buggy, insecure m$ product that has become the de-facto standard through shady business pracrtices rather than merit.

The likely reason you can't access anything in the /etc folder is because of the inherant security in SUSE systems.  You need to be logged in as ROOT.  By trying to make your account an admin you had the right idea, though that step isn't necessary in linux, instead you need to take the extra authentication step of either running the commands from a root terminal or using sudo.

To move something to the etc folder open a terminal and type

sudo mv "source path" "destination path"

where the paths either begin from the system root /:

sudo mv /home/username/file.bin /home/username/Desktop/file.bin

or from the current folder, for example again moving a file from your home folder (assuming that the terminal is currently running in your home folder, which is the /home/"your username" and the default location when you start terminal) to your desktop

sudo mv file.bin Desktop/file.bin

Keep in mind that the directory and file names are case sensitive.

sudo will ask for your password then run whatever command as root.

to edit a file, for example xorg.conf, type:

sudo pico /etc/X11/xorg.conf

note that if pico opens a blank file when you think it shouldn't, check your typing as pico will create a new file with the path and name you gave it if the file dosen't already exist.

to run a file, for example the nvidia drivers packaged as a .run file:

sudo sh filename.run

and sh will execute the file.

Linux may seem to be a bit more difficult than windows or DOS at first, but once you get used to it you'll find that the extra steps are what makes it both far more secure and in the long run easier to configure and use.  

If I misread your problem and you already knew all this, feel free to PM me and I'll do what I can to help.

---

