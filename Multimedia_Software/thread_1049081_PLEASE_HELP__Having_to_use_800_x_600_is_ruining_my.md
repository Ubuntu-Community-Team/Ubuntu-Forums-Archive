---
title: "PLEASE HELP : Having to use 800 x 600 is ruining my ubuntu experience"
date: 2009-01-24
forum: Multimedia Software
---

### Post by whoney on 2009-01-24
Please can someone help me with this issue.

I am running Hardy Heron 8.04 and I can only set my screen resolution to a maximum resolution of 800 x 600 (and a refresh rate of 60Hz). I know for a fact that my setup is capable of running up to 1600 x 1200 (at a refresh rate of 100Hz) as I have tested this with Windows XP.

My monitor is an Iiyama Vision Master Pro 410 17" CRT and my graphics card is an nVidia Corporation NV10DDR [GeForce 256 DDR]. 

I believe that I have installed the correct NVIDIA driver for my graphics card but my monitor is being displayed as "Unknown" within the Monitor Resolution Settings screen.

I have tried adding a Mode Line to the Xorg.conf file but that did not make any difference.

Please help as this is really spoiling my ubuntu experience at the moment.

Thanks
Wayne

---

### Post by overdrank on 2009-01-24
Hi and have you tried using the nvidia-settings ```
gksu nvidia-settings
```

---

### Post by whoney on 2009-01-25
Thanks for the reply. :)

When I run the command: 

```
nvidia-xconfig
```

I get this:

```
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-xconfig
 * nvidia-glx
 * nvidia-glx-new
Try: sudo apt-get install <selected package>
```

So, I tried this:

```
sudo apt-get install nvidia-xconfig
```

But, was told that the following package would be REMOVED: nvidia-glx-legacy. Which, I know after much Googling is the driver that I need for my video card. So, decided not to continue at this stage. If I do this, is it likely to break my video completely?

---

### Post by overdrank on 2009-01-25
Hi and just try and install nvidia-settings. This should help.

---

### Post by whoney on 2009-01-25
It looks like I already have nvidia-settings installed.

---

### Post by overdrank on 2009-01-25
> **whoney said:**
> It looks like I already have nvidia-settings installed.

Ok have you tried to adjust resolution with the settings?

---

### Post by hamdi on 2009-01-25
or you can edit xorg.conf manually

---

### Post by whoney on 2009-01-25
Yes, but I get the following message when I try to run the NVIDIA X Server Settings application:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server."

When I run the command: 
```
nvidia-xconfig
```

I get this:
```
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-xconfig
 * nvidia-glx
 * nvidia-glx-new
Try: sudo apt-get install <selected package>
```

---

### Post by whoney on 2009-01-25
Is this really a problem with the video driver/settings or is this more likely due to the fact that my monitor type is currently "Unknown"?

I have tried manually adding a mode line for the monitor to the Xorg.conf file using some instructions that I found on the X Windows FAQ page but that has not helped.

---

### Post by overdrank on 2009-01-25
> **whoney said:**
> Is this really a problem with the video driver/settings or is this more likely due to the fact that my monitor type is currently "Unknown"?

I have tried manually adding a mode line for the monitor to the Xorg.conf file using some instructions that I found on the X Windows FAQ page but that has not helped.

It appears that your system is not using the nvidia drivers. So if you would uninstall the drivers then reboot. After reboot try and install the nvidia drivers again. This has been a issue for many users on Hardy 8.04.

---

### Post by steveneddy on 2009-01-25
I don't understand.

overdrank asked him to run

```
nvidia-settings

```and he keeps saying that he is running

```
nvidia-xconfig
```Are these the same commands or a simple failure to follow directions?

If more than one driver exists on the system the output of the Nvidia card will suffer.

Personally I would go to Synaptic and uncheck the drivers you don't need and make sure that the newest Nvidia driver is either installed or checked for installation, then install it.

---

### Post by overdrank on 2009-01-25
steveneddy whoney did and it is telling them that they are not using the nvidia driver. That is why they keep using the nvidia-xconfig :)
Post #8

---

### Post by whoney on 2009-01-25
> **overdrank said:**
> It appears that your system is not using the nvidia drivers. So if you would uninstall the drivers then reboot. After reboot try and install the nvidia drivers again. This has been a issue for many users on Hardy 8.04.

OK, I have just tried:

```
apt-get remove nvidia-glx-legacy
```

This successfully removed the package. 

Then I rebooted:

```
sudo reboot
```

ubuntu then came up in low-graphics mode with the following message:

"Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself."

Options were Configure, Shut Down or Continue, so I clicked on Continue.

Login came up OK.

Installed the nvidia-glx-legacy driver again from a terminal:

```
apt-get install nvidia-glx-legacy
```

Noticed the message: "Suggested package: nvidia-legacy-kernel-source" during install but have ignored this for now.

Then I rebooted again:

```
sudo reboot
```

ubuntu has come backup exactly the same as before and I still cannot select a screen resolution higher than 800x600 and cannot run the NVIDIA X Server Settings for exactly the same reasons as mentioned before.

I can see me having to buy either a new monitor or a new video card to fix this :(

---

### Post by overdrank on 2009-01-25
Ok you may try and use the xfix option when booting into recovery mode. Recovery mode is usually the second choice from the grub. Then choose the xfix option to correct the graphics. After this you should be given the choice of booting normally. Hope this works

---

### Post by rocket777 on 2009-01-25
Hey, thanks, I was having the same problem, couldn't go past 800x600. But I [COLOR="Red"]finally got it working[/COLOR], here's what I did.


I have a tnt legacy controller and a 1680x1050 AOC flat pannel. 

I tried a few things, by adding apps under the gui and searching for nvidia. I added the legacy and nothing seemed to happen. So, I eventually removed all the nvidia things that I had installed and did this:

```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

which I think is the legacy stuff. This seems to have created a minimal xorg.conf. 

Then I rebooted, and got the x fix screen, where I said do a manual configuration. Here I could not find my monitor, but could find adapters. I configured my adapter as a nvidia legacy, which it took.

The monitor, I had to choose the first option, I think it was generic or something like that, and then I got a bunch of choices that included lcd panel 1680x1050 which I chose. I then clicked on test which worked, and told it to use this. It did, but then when it finished coming up, it was still 800x600 with no larger choices.

But then before giving up, I [COLOR="Red"]rebooted, and KAZAAM, it worked[/COLOR]. I had read somewhere about rebooting, instead of restarting the xserver, which I had tried once before to no avail.

Here's my /etc/X11/xorg.conf that it produced,

```
Section "Device"
xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "NVIDIA Legacy"
        Busid           "PCI:1:0:0"
        Driver          "nv"
        Screen  0
        Vendorname      "NVIDIA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1680x1050"
        Horizsync       31.5-65.5
        Vertrefresh     56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1680x1050@60"  "1600x1024@60"  "1440x900@60"   "1280x800@60"   "1280x720@60"   "1280x768@60"   "800x600@60"    "800x600@56"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by whoney on 2009-01-25
> **overdrank said:**
> Ok you may try and use the xfix option when booting into recovery mode. Recovery mode is usually the second choice from the grub. Then choose the xfix option to correct the graphics. After this you should be given the choice of booting normally. Hope this works

I have just tried this and unfortunately it didn't work. I selected the xfix option and then chose resume booting and now the monitor is just sitting there with a black screen searching for a signal.

---

