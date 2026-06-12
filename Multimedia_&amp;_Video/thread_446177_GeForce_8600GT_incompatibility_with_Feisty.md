---
title: "GeForce 8600GT incompatibility with Feisty"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by jmeuf on 2007-05-16
I recently installed Feisty 7.04 and changed my X800XT ATI card for a GeForce 8600GT. I run on a X86 motherboard. I'm experiencing a hell of problems just to make my graphic card work. Let's start by the beginning:

  - System/Admin/Proprietary Driver Manager doesn't see the need to install any driver for my hardware
  - I installed glx_new, that crashed my X server (by the way, each time I replace "nv" by "nvidia" in my xorg.conf I get a crash of the X server)
  - I tried Envy, but it didn't recognize also my hardware
  - I manually installed with the .run script. I could finally setup the resolution and frequency, but the setting could not be saved and I had to set it up again at each session
  - nvidia-setting reports errors and doesn't offer more than a few check buttons

Between all these attempts I re-installed Feisty from scratch in order to have a clean starting point (specially after the .run attempt).

Any idea??
Thanks.

---

### Post by cubdukat on 2007-05-19
Looks like we may have to wait until nVidia gives us new drivers. It looks like the 8600 is sufficiently different from the 8800 series that the current drivers don't recognize it.

---

### Post by RawMustard on 2007-05-19
[Have you read this thread on nv forums?]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

---

### Post by =JoNaZ= on 2007-05-22
use these beta drivers.. works fine for me with 8600gt and a dell 30" 

[http://www.nvidia.com/object/linux_display_ia32_100.14.06.html](http://www.nvidia.com/object/linux_display_ia32_100.14.06.html)

---

### Post by hongfai on 2007-05-25
> **=JoNaZ= said:**
> use these beta drivers.. works fine for me with 8600gt and a dell 30" 

[http://www.nvidia.com/object/linux_display_ia32_100.14.06.html](http://www.nvidia.com/object/linux_display_ia32_100.14.06.html)

I've tried this driver and it didn't work. It complains that it did not find a compatible GPU. Any ideas guys?

---

### Post by Pretzal on 2007-05-25
I tried this driver too. It seems to work ok after install but as soon as I reboot - my Xserver is broken. The only way I managed to get back into Ubuntu was to install the driver again from the command line. Restoring my xorg.conf file doesnt seem to work either. Please NVIDIA sort this out.

---

### Post by exc220 on 2007-05-27
> **Pretzal said:**
> I tried this driver too. It seems to work ok after install but as soon as I reboot - my Xserver is broken. The only way I managed to get back into Ubuntu was to install the driver again from the command line. Restoring my xorg.conf file doesnt seem to work either. Please NVIDIA sort this out.

Hey guys... I'm having this exact same problem! I've correctly installed the latest driver from the Nvidia website and right after I have installed it works flawlessly, even the Desktop Effects. However whenever I restart my PC I get problems with the Xserver...anyone have this card working? :(

---

### Post by schleppel on 2007-05-27
Try adding
```

rmmod nvidia

```
at the start of your /etc/init.d/gdm(or kdm for kubuntu users).
The X-Server will start, but the FAN of my 8600GT stops working and the PC crashes after 15 minutes or so. :(

---

### Post by heldal on 2007-05-27
[LIST=1]
[*]The current supported linux-driver from Nvidia that is included in Ubuntu doesn't support the 85xx and 86xx GPUs.
[*]For more recent hardware (8500/8600 and later) check Nvdia's website. Beta drivers may be the only option for the most recent hardware.
[*]8800GTS and GTX are supported with nvidia-glx-new, but the current version distributed with ubuntu (1.0.9755+2.6.20.5-16.28) is missing an extension to the x-server that is necessary for these GPUs
[*]Before you start installing Nvidia's driver make sure all traces of any ubuntu packages with "nvidia" in its name are completely removed. Especially important is to get rid of the files in nvidia-kernel-common that manipulates the behavior of modules (to differentiate between modules for the "legacy", current and "new" versions of the driver. Look for and remove /etc/devfs/conf.d/nvidia-kernel-nkc /etc/modutils/nvidia-kernel-nkc /etc/modprobe.d/nvidia-kernel-nkc /etc/default/nvidia-kernel and /etc/init.d/nvidia-kernel if you didn't completely remove them with the correct options from the package-manager.
[*]Scripts in Ubuntu's restricted-modules tools are putting files in /lib/linux-restricted-modules. These are not necessarily removed when changes are made. E.g. the installation of nvidia-glx-new leaves a file that has to be manually removed to be able to switch back to the default nvidia-glx package.
[/LIST]

---

### Post by fwilliams on 2007-05-27
A solution:

Use an alternate install disk (not the live cd) and install in text mode.

Do not add additional screen resolutions during install!

Use symatic (or whatever) to download the libc development libraries and headers (ie. libc6-dev).
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

It took a while to find the correct solution, so I wanted to post it here.

---

### Post by exc220 on 2007-05-28
> **heldal said:**
> [LIST=1]
[*]The current supported linux-driver from Nvidia that is included in Ubuntu doesn't support the 85xx and 86xx GPUs.
[*]For more recent hardware (8500/8600 and later) check Nvdia's website. Beta drivers may be the only option for the most recent hardware.
[*]8800GTS and GTX are supported with nvidia-glx-new, but the current version distributed with ubuntu (1.0.9755+2.6.20.5-16.28) is missing an extension to the x-server that is necessary for these GPUs
[*]Before you start installing Nvidia's driver make sure all traces of any ubuntu packages with "nvidia" in its name are completely removed. Especially important is to get rid of the files in nvidia-kernel-common that manipulates the behavior of modules (to differentiate between modules for the "legacy", current and "new" versions of the driver. Look for and remove /etc/devfs/conf.d/nvidia-kernel-nkc /etc/modutils/nvidia-kernel-nkc /etc/modprobe.d/nvidia-kernel-nkc /etc/default/nvidia-kernel and /etc/init.d/nvidia-kernel if you didn't completely remove them with the correct options from the package-manager.
[*]Scripts in Ubuntu's restricted-modules tools are putting files in /lib/linux-restricted-modules. These are not necessarily removed when changes are made. E.g. the installation of nvidia-glx-new leaves a file that has to be manually removed to be able to switch back to the default nvidia-glx package.
[/LIST]

I followed your directions and the nvidia driver seems to work!
I have one question though. Right now i have in the update manager a few available updates including: linux-headers-genric, linux-image-genric, linux-restricted-modules-common. I wanted to know if after I install these updates I have to reinstall the nvidia drivers.
thanks

---

### Post by tseliot on 2007-05-28
> **exc220 said:**
> I wanted to know if after I install these updates I have to reinstall the nvidia drivers.
thanks
Yes, you'll have to reinstall the driver.

---

### Post by exc220 on 2007-05-29
> **tseliot said:**
> Yes, you'll have to reinstall the driver.

Ok thanks for your help!

Is this new beta driver gonna be supported in your Envy application any time soon?

---

### Post by tseliot on 2007-05-29
> **exc220 said:**
> Ok thanks for your help!

Is this new beta driver gonna be supported in your Envy application any time soon?

It's in Envy 0.9.4. 

However you will have to follow point B of this page before you use Envy:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by canonbeck on 2007-05-29
Can anyone help me get my 8500gt working? I've tried everything read here and on the nvnews forum but nothing seems to work. The best I can do is to install the beta driver manually via envy and then restart X - at this point it does fire up. However, this only lasts until I reboot, at which point X fails to load complaining that it cannot find the video card... arrghhh!! - I'm tearing out what little hair I have left over this --- all I want is to display 1440x900....

Any help appreciated.

Cheers

---

### Post by Pretzal on 2007-05-30
I understand your frustration - I have the same problem with my 8600GT. I can install the NVIDIA beta drivers and get it to function - but as soon as I reboot - I have to install them again to get X going. From what I've read this is a very common problem and I am yet to find a solution anywhere.

---

### Post by Pretzal on 2007-05-30
Tseliot, I notice above that you say that the latest release of Envy supports the beta driver, but the latest one 100.14.06 is not yet supported in Envy as it is unable to detect my video card (8600GT). Is that going to be included sometime? Many thanks for your brilliant work on envy and helping countless NVIDIA users. Well Done!

---

### Post by exc220 on 2007-05-30
I have a 8600GT and I followed heldal's directions and then installed the Nvidia beta driver using tseliot's method 2 and everything seems to work fine even after I reboot.
Make sure you follow point 4 of heldal's directions :
> Before you start installing Nvidia's driver make sure all traces of any ubuntu packages with "nvidia" in its name are completely removed. Especially important is to get rid of the files in nvidia-kernel-common that manipulates the behavior of modules (to differentiate between modules for the "legacy", current and "new" versions of the driver. Look for and remove /etc/devfs/conf.d/nvidia-kernel-nkc /etc/modutils/nvidia-kernel-nkc /etc/modprobe.d/nvidia-kernel-nkc /etc/default/nvidia-kernel and /etc/init.d/nvidia-kernel if you didn't completely remove them with the correct options from the package-manager

---

### Post by Pretzal on 2007-05-31
Thanks I followed your instructions - took a leap of faith and removed nvidia-kernel-common and xserver-xorg-video-nv using synaptic then followed Tseliots method 2 and it seems to have worked.  

Im a little surprised my xorg.conf doesnt show my monitor and video card:

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


Does this look like a successful install of the nvidia driver?

---

### Post by canonbeck on 2007-06-01
i did the same and it hasnt worked for me - I'm giving up now :(

---

### Post by Julz_ET on 2007-06-01
> **exc220 said:**
> I followed your directions and the nvidia driver seems to work!
I have one question though. Right now i have in the update manager a few available updates including: linux-headers-genric, linux-image-genric, linux-restricted-modules-common. I wanted to know if after I install these updates I have to reinstall the nvidia drivers.
thanks

I followed these exact instructions and it worked, yay !

I installed the nvidia drivers from nvidia website.

---

### Post by messatsu on 2007-07-17
I used to have the problem where I could install the nvidia settings, but would crash on reboot like everyone else.  I got Envy and can't remember the steps I took, but it works minus one thing.  When rebooting, it stays in 1024x768.  I can change it manually on every boot now though.  I've screwed around with the xorg.conf file, but none of those show up in the GUI display settings.

current xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
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
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
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
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 60.0
    VertRefresh     43.0 - 74.0
    Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1920 1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920 1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920 1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920 1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920 1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920 1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by dabl on 2007-07-18
You need to change the Nvidia settings while you are in "Super User" mode, and then save them to xorg.conf.  Here is how:

Open a console window and enter ```
sudo nvidia-settings
```

Use the "detect display" button, then set the resolution and refresh rate that you would like for the default. Click the "Save To X Configuration File" button in the lower right of the panel.  Click "save" on the little window that opens.

Then you can restart the xserver with Ctrl-Alt-Backspace, and you should be able to login and have it come up in your default setting.

HTH :)

---

### Post by messatsu on 2007-07-18
Got it. [IMG]http://www.mugenguild.com/forumx/Smileys/mfg/hyo.gif[/IMG]

---

### Post by jadugartir on 2007-07-21
> **heldal said:**
> [LIST=1]

[*]Before you start installing Nvidia's driver make sure all traces of any ubuntu packages with "nvidia" in its name are completely removed. Especially important is to get rid of the files in nvidia-kernel-common that manipulates the behavior of modules (to differentiate between modules for the "legacy", current and "new" versions of the driver. Look for and remove /etc/devfs/conf.d/nvidia-kernel-nkc /etc/modutils/nvidia-kernel-nkc /etc/modprobe.d/nvidia-kernel-nkc /etc/default/nvidia-kernel and /etc/init.d/nvidia-kernel if you didn't completely remove them with the correct options from the package-manager.

[/LIST]


I was able to use synaptic to remove the part about nvidia-kernel-common that you said was important. the others, which are "/etc/devfs/conf.d/nvidia-kernel-nkc /etc/modutils/nvidia-kernel-nkc /etc/modprobe.d/nvidia-kernel-nkc /etc/default/nvidia-kernel and /etc/init.d/nvidia-kernel"

How do i remove these, i cant do it thruogh the file browser, maybe theres a terminal command?

---

### Post by messatsu on 2007-07-22
sudo rm <fiilename>

---

### Post by dabl on 2007-07-22
> **messatsu said:**
> sudo rm <fiilename>

Yep, that works, or ```
gksu nautilus
``` and use it to nuke your bad boy files. :popcorn:

---

