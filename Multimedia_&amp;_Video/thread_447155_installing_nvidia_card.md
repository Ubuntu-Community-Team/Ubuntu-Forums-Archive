---
title: "installing nvidia card"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by collieman on 2007-05-17
I am a nooB.  I have this question.  I'm currently using an SIS 6328 video card.  It's the only one that worked allowing me to install Ubuntu.   The video is very slooooow and choppy.  I'm assuming it's because of not having 3D accel. drivers installed.  I want to upgrade a little with a good TNT2 Riva card.  I tried installing the nvidia glx legacy driver from the repository but when I physically intstalled  the TNT card an error message appears saying that a driver has not been installed and to reconfigure my x-server (whatever that is) and reboot.  It seems like I need to have the TNT card installed so it can be detected but installing it won't allow me to boot up.  A vicious circle.  How is this done?  Thank you, Collieman

---

### Post by Pollywoggy on 2007-05-17
> **collieman said:**
> I am a nooB.  I have this question.  I'm currently using an SIS 6328 video card.  It's the only one that worked allowing me to install Ubuntu.   The video is very slooooow and choppy.  I'm assuming it's because of not having 3D accel. drivers installed.  I want to upgrade a little with a good TNT2 Riva card.  I tried installing the nvidia glx legacy driver from the repository but when I physically intstalled  the TNT card an error message appears saying that a driver has not been installed and to reconfigure my x-server (whatever that is) and reboot.  It seems like I need to have the TNT card installed so it can be detected but installing it won't allow me to boot up.  A vicious circle.  How is this done?  Thank you, Collieman

Can you open a console?  ctrl-alt-f2  (or another f-key) should get you to a console.  Login and then do 'sudo dpkg-reconfigure xserver-xorg' and then answer the questions about your monitor and video card.  It will help if you have the spec sheet handy for the video card and monitor.

Once that is done restart gdm (sudo /etc/init.d/gdm restart).
If it does not start, post the error messages here.

I believe you are using the correct Nvidia package for your card (the legacy one).

---

### Post by collieman on 2007-05-17
I did ctrl+alt+f2 and it opened a black screen that looks like DOS and asked my for login and password.  I'm going to write down what you said to enter and will get back.

---

### Post by dxdemetriou on 2007-05-17
for this card I had a problem to find drivers even with windows for one computer I had to prepare
If it doesn't work even with the Restricted Drives Manager that is on Feisty repos, I think the only way is to try some very old drivers, if accepted with Kernel.
I have an mx440 geforce4 that works ok with nvidia-glx

---

### Post by collieman on 2007-05-17
I'm in trouble!!  You were right.  There were a lot of questions about the card, keyboard, mouse and monitor.  I had to fire up my XP rig to write  this.  It's  the first time I've used XP in 5 weeks.  Been trying hard to learn Ubuntu Linux.  I answered the questions the best that I could with monitor manual in hand.  I had nothing to use for the video card.  Answered the questions.  Entered the command for restart.  It did but now I only can see about the top 1/3 of my desktop and it looks like the reso is 800x600.  The lower 2/3 of the screen is white with what looks like very tiny lettering.  I rebooted and still the same.  I no doubt I answered something wrong. 
There were some choices for video cards right at the beginning with SIS, SISUSB  and a few others.   I'll bet I chose the wrong one.  I was kinda lost on that.  Now that I know how to reconfigure, I want to say x-server but not sure, I will try again AFTER "Googleing" a bit and getting some info on that TNT card.  What if I install that TNT card now.  Will it possibly work?  If I can get this to work I'm going to build a good, decent rig for Ubuntu with hardware that Ubuntu supports.  Am I going to have to reinstall Ubuntu?   No problem if I do.

---

### Post by dxdemetriou on 2007-05-17
If you had a look at /etc/X11/xorg.conf, you would see that the command is:
sudo dpkg-reconfigure -phigh xserver-xorg
to not go to all those questions.
If you want, you can restore a backup that created when you had run the command
One easy solution is the Envy from:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
but I hadn't use it on Feisty as there is the Restricted Drivers Manager, and I don't know if can handle this type of card
If you are with Edgy yet and try to install manually the drivers maybe you will have trouble. This is the reason I used Envy.
Have a look here:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
and here:
[http://ubuntuforums.org/showthread.php?t=365388](http://ubuntuforums.org/showthread.php?t=365388)

---

### Post by collieman on 2007-05-17
GOT IT!!!!  Please excuse me if I did this wrong but it's a bit confusing for me.  I followed your instructions with the SIS card installed because I thought that if I installed the TNT card it wouldn't boot.  I shut the puter down, took out the SIS and installed the TNT.  Turned it on and it booted to desktop!!  A message appeared briefly saying that it was using restricted drivers.  I don't know if that's good or bad.  I think it's the latter. The desktop is 800x600 just by looking at it so I'll have to set the reso.  What do I do next?  Should I look for drivers for it on the Nvidia site.  I think I remember seeing Linux drivers there for the TNT2.  This is great!  I've finally got something to work...with your help.  I'm going to save and print your instructions for future reference.  I spent 3 weeks trying to get Xnview  (.rpm) to work but I didn't succeed.  This gives me a lift.  Thank you VERY much dxdemetriou.

---

### Post by dxdemetriou on 2007-05-17
You mean you have used the Restricted Drivers Managers and so are you using Feisty?
To make whatever you want with your graphic card there are a lot of guides, but you must be careful and to keep backups of xorg.conf
One good guide I follow up to now is [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
also search on forums and with Google friend
If you don't afraid about the command line you can play with xorg.conf, and nvidia-setings (gui)
If you used the Restr. program all will be ok (I don't know about the composite if is enable that needed for beryl and compiz)
The old way before the program was in terminal:
sudo nvidia-glx-config enable
to enable the 3d accel.
I had many headacne before too :)

---

### Post by collieman on 2007-05-17
Pollywoggy I forgot to thank you too for helping me get the TNT card installed.  I'm back on my Ubuntu puter.  The video is sooooo much faster now.  I got a little suprise when I went to change my reso.  The best I can get is 1024x768 which leaves the reso a little bigger than I wanted.  I wish I had selected a smaller reso in reconfig.   Is there a way to do that without going through all those questions again?

---

### Post by collieman on 2007-05-17
dxdemetriou, I am using Fiesty.   Not sure what you mean about using Restricted Drivers Manager.  I see it in system/administration but I never did anything with it.  Got to get to bed for work tomorrow morning.  Thanks guys for your help.

---

### Post by dxdemetriou on 2007-05-17
I had this trouble with resolution with my 440xm and 5500
My modified xorg.conf that from 1024x768 can reach 1280x1024 is:
> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "AIGLX" "off"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "DisableGLXRootClipping" "true"
    Option         "BackStoring" "True"
    Option         "AllowGLXWithComposite" "true"
    Option         "TripleBuffer" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection

If you can, play with it
you don't need to change everything, just some of the structure. If this file works is ok, but I have extra things needed for beryl.
I tried to add only the resolution in the file created initially, but didn't work for me, and I use this one now that I have from Dapper I think

---

### Post by md389 on 2008-01-02
Hey Guys, 
      My problem is similar to the original one. I am trying to install an old GeForce fx5200 PCI, but Im having quite a few problems. Firstly, I have already inserted the card into the pci slot in my comp, and then switched the VGA cable from the mobo to the video card. The monitor keeps telling me that theres no input; this is the first problem. At first I thought this was a card problem, but I installed the card on an old system just to make sure, and everything went peachy. So I figured maybe I needed to install the drivers before I could switch the VGA cable to the card. So I enable the nvidia restricted drivers in the Restricted Drivers Manager. I installed Envy and let it install new drivers and update xorg.conf. So I restarted my comp, and suddenly, I get an error saying that the comp is running in low-graphics mode. I went into the terminal and typed in: ```
sudo nvidia-glx-config enable
```

and got this:

```
 Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```

I typed in:

```
glxinfo | grep
```

and I get:

```
 Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I type in:

```
glxinfo
```

and I get:

```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

I prepared for the possibility that the pci slots on my mobo might be fried, but I checked Screen and Graphics in System => Administration, and it detects both the onboard and the nvidia card just fine. Someone PLEASE help me, cause I am stumped beyond belief. Also, although I check the nvidia drivers in Restricted Drivers Manager, it somehow seems to come unchecked. Im about to give up and reinstall Ubuntu. You guys are my last hope.

I forgot to mention, I have a 3.2GHz Intel Core-D with a gig of ram.

Oh and Im also running gutsy

---

### Post by Ummagumma on 2008-01-04
Something is broken in this release - it won't use the right nVidia driver (I have Riva TNT2), would get stuck at 640 x 480 or something like that, and after several evening of tweaking I only got it to go to high res but lost OpenGL and 3D in the process. 

I have given up on Ubuntu and nearly given up on Linux, however I tried Kanotix as a last reserve and voila - it got all my hardware right from the start ! The only problem is, fonts don't look too good, took some tweaking to get them to semi-acceptable level. Still, at least I _do_ have a working Linux install right now. Just wish Ubuntu developers would get their act together, v 6.xx had no problems with this graphic card.

Good luck to y'all !

---

### Post by Robynsveil on 2008-01-04
For those of you using nVidia card and can't get the Restricted Drivers Manager to work, you might try this - remember, no guarantees here: this is what I did, and it seemed to work:

If you have Envy, uninstall the default nVidia driver
Open Synaptic Package Manager and make sure all your repositories are active (Settings-> Repositories) including Proprietary drivers for restricted devices and software restricted by copyright or legal issues (multiverse). Under the Updates tab I also have Unsupported updates (Gutsy backports) ticked.
Do  a reload (important!)
Do a search for NVidia

Not sure what your Synaptic will tell you - your mileage may vary depending on your card, but mine let me uninstall old graphics manager apps and install linux-restricted-manager-14.386 (think that was the name - it was something like that - working from memory, here and my NVidia 6600 GT flies like a banshee (do banshees fly?) - anyway, works a treat.
HTH

---

