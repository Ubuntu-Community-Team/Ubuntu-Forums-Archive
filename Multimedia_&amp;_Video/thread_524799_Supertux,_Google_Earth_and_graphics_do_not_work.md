---
title: "Supertux, Google Earth and graphics do not work"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by matogrosso on 2007-08-13
PLEASE HELP. I had these working before on the same hardware on other distributions

Supertux
As the name suggest, it was created for linux by linux users. It works fine on
windows, but both the sound and image are too slow on Ubuntu 7.04 Feisty.

Google-earth 
Crashes and causes Ubuntu to reboot. Works fine in the same computer, as long as
I use windows XP.

Supertuxkart
Same as supertux


Inconvenient truth:
Your grandma would probably be able to download and install these programs on
windows. She would give up using linux.


My System:

Software 7.04 Feisty Fawn Ubuntu

Hardware:
500 MB  Swap
Memory 979.6 MB
Intel Celeron CPU 2.00 GHz

Available disk space 3.9 GB
Used disk space 5.9 GB  (60%)
Total 10.3 GB

oscar@oscar-desktop:/media/hda4/oscar/LINUX$ 
oscar@oscar-desktop:/media/hda4/oscar/LINUX$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 Ethernet controller: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY (rev 31)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
oscar@oscar-desktop:/media/hda4/oscar/LINUX$ 

#### Trying to solve video google-earth problems, etc  ###############
gksudo gedit /etc/default/acpi-support
SAVE_VBE_STATE=false
POST_VIDEO=true
USE_DPMS=false



oscar@oscar-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.00GHz
stepping        : 7
cpu MHz         : 2000.184
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up
bogomips        : 4002.18
clflush size    : 64

oscar@oscar-desktop:~$

---

### Post by variona on 2007-08-14
Your video card's 3D capabilities are probably not supported by your x-server, all the applications you mentioned try to use them.
variona

---

### Post by matogrosso on 2007-08-14
Variona, Thanks for your reply. I've got dual boot. Supertux and Google earth work fine on Windows (same machine, same cards).  Please do you have any suggestions ?

---

### Post by RomeReactor on 2007-08-14
Hi. According to your lspci output, you have a SiS 661/741/760 integrated card. And [according to this site]("http://www.winischhofer.net/sisdri.shtml"), your card doesn't have [DRI]("http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure") support, meaning, no 3D rendering.

Sorry, looks like you either go without 3D games and applications, or get a new video card.

---

### Post by matogrosso on 2007-08-14
"Variona, Thanks for your reply. I've got dual boot. Supertux and Google earth work fine on Windows (same machine, same cards). Please do you have any suggestions ?"

RomeReactor,
Thank you, but I must disagree.

Actually I had supertux and google earth working before on Dapper. But I've changed my ethernet card and Dapper doesn't recognize it, so upgraded to Feisty. And as I mentioned below, these applications run 
on the same computer, as long as I use windows.

As I used these before, maybe they don't actually need DRI.

---

### Post by Gremlinzzz on 2007-08-14
I got a suggestion go play it on  xp windows its a great game emulator .

---

### Post by RomeReactor on 2007-08-14
> **matogrosso said:**
> "Variona, Thanks for your reply. I've got dual boot. Supertux and Google earth work fine on Windows (same machine, same cards). Please do you have any suggestions ?"

RomeReactor,
Thank you, but I must disagree.

Actually I had supertux and google earth working before on Dapper. But I've changed my ethernet card and Dapper doesn't recognize it, so upgraded to Feisty. And as I mentioned below, these applications run 
on the same computer, as long as I use windows.

As I used these before, maybe they don't actually need DRI.

That it does work in windows does not necessarily mean it will work on Linux; there's a problem with either the driver or OpenGL capabilities of your SiS card, at least in Linux; see [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/115609").

You're right, though; the card *might* work properly after all, but I've been searching and have not come up with the solution yet. Hopefully there's an answer out there.

---

### Post by matogrosso on 2007-08-15
RomeReactor,

Thanks for the Bug report. It does seem to cover my problem. I wonder when it is going to get fixed.

Cheers,
Matogrosso

---

### Post by dls156 on 2008-01-25
I am having the same problems. Before I start SuperTux or TuxRacer, my CPU looks normal, but as soon as I start one of the programs, the Xorg jumps through the roof. There is a screenshot attached. I am running a Toshiba Qosmio E15 with 2GB/ram, plenty of HD space, and a nVidia GeForce Riva TNT (128mb/ram). I just switched this computer to Ubuntu 7.10 from XP where both Tux's ran great. Being that these are two of my kids favorite games, and this is their computer, I would really appreciate someone smart helping us out here. Thanks.

---

### Post by RomeReactor on 2008-01-25
Hi. Do you have the restricted drivers enabled for the nVidia card? go to 'System->Administration->Restricted Drivers Manager' and make sure the box for your card is checked. Also, please post the output of:
```
glxinfo | grep rendering
```
and your xorg.conf:
```
cat /etc/X11/xorg.conf
```

---

### Post by dls156 on 2008-01-25
RomeReactor - Dude!!! Thanks!!! I spent about two hours today (I've been a die-hard linux user for all of 48 hours now) running command lines trying to figure this thing out. It is still a little catchy, but night and day over what it was - basically, not playable. Here is the other info you asked for, if you see anything I should edit in my xorg.conf, feel free to straighten me out - it's much appreciated.

dls@dls-qosmio:~$ glxinfo | grep rendering
direct rendering: Yes
dls@dls-qosmio:~$ cat /etc/X11/xorg.conf
# xorg.conf (xorg X Window System server configuration file)
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
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

#  Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "stylus"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "stylus"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#  EndSection

#  Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "eraser"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "eraser"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#  EndSection

#  Section "InputDevice"
#       Driver          "wacom"
#       Identifier      "cursor"
#       Option          "Device"        "/dev/input/wacom"
#       Option          "Type"          "cursor"
#       Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#  EndSection

Section "Device"
        Identifier      "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-51
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34M [GeForce FX Go5200 64M]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection

---

### Post by rosegarden78 on 2008-01-25
Last time Google Earth updated it would flicker when I moved my mouse over the screen, but before the update it worked fine, so I think the problem is with Earth.  I haven't tried it since yesterday's fresh install to activate compiz, though, but if it still flickers tomorrow I'll let you know. :)

---

### Post by RomeReactor on 2008-01-26
I don't see anything wrong with your xorg.conf, and you have direct rendering, so you *should* be able to run the game. It's not Compiz either, since in the screenshot you posted it showed Metacity running. How much RAM does your video card have? Try installing **nvclock** so we can get more information about your card:
```
sudo aptitude install nvclock
```
then:
```
nvclock -i
```
and post the output.

---

### Post by dls156 on 2008-01-26
Rome,

Thanks again. I looked up this computer online and found out it has a geForce FX go5200 which "supports up to 128 mb/ram", but then I looked at a system properties list I had printed out from XP device manager before upgrading to ubuntu and saw that I only had 64 mb.

Thanks again for helping with this, I am really excited about learning linux and troubleshooting is a good way to do it ;)  Here is the output you asked for:

-- General info --
Card:           nVidia GeforceFX Go 5200
Architecture:   NV34 B1
PCI id:         0x324
GPU clock:      199.125 MHz
Bustype:        AGP

-- Memory info --
Amount:         64 MB
Type:           128 bit DDR
Clock:          405.000 MHz

-- AGP info --
Status:         Enabled
Rate:           4X
AGP rates:      1X 2X 4X 
Fast Writes:    Disabled
SBA:            Unsupported

---

### Post by RomeReactor on 2008-01-26
I don't see what the problem might be, aside from the card not being very fast; does this problem happen with other applications/games besides those two? Are you able to run the desktop effects?

There are three nVidia drivers in the repositories; It might be that your using a driver that's not suited for your card. Please post the output of:
```
aptitude search nvidia-glx
```
Your card might need to use **nvidia-glx-legacy**; the driver you're currently using will be marked by the letter **i** instead of **p** or **c**.

---

### Post by dls156 on 2008-01-27
RR, here you go. Looks like you are right about the new driver - so how would I go about trying the legacy one, or finding out if I need to use the legacy one?

Thanks

dls@dls-qosmio:~$ aptitude search nvidia-glx
p   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
p   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
p   nvidia-glx-legacy               - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-legacy-dev           - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
i   nvidia-glx-new                  - NVIDIA binary XFree86 4.x/X.Org 'new' driv
p   nvidia-glx-new-dev              - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
dls@dls-qosmio:~$

---

