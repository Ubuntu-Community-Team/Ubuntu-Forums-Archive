---
title: "[SOLVED] gksu nvidia-settings??? dual monitors"
date: 2008-08-26
forum: Multimedia Software
---

### Post by plnnightsky on 2008-08-26
I am trying to get dual monitors working. Being new to Ubuntu, I can't figure out where to start. I have search the groups and the web and have managed to mess my display up quite well. Fortunately I did have a back up and have been able to recover after each attempt. I have confirmed both monitors and outputs work from the the Nvida card. I did this by disconnecting each of the displays are reboot. The xorg.conf file seems to be the same for both displays.
Where may I find information, I can understand.

Below is the xorg.conf:
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
EndSection
Section "Module"
Load "glx"
EndSection


Here is the out put of lspci:
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
04:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e4 (rev a1)

One thing I keep noticing in the forums is to run "gksu nvidia-settings"  
When I do this as root nothing happens.  No error no pop up or message.  I don't think this is what is supposed to happen.

---

### Post by kagashe on 2008-08-27
After plugging second monitor you can use xrandr command to enable it with default mode:
> $ xrandr --auto

You can see what modes are available with:
> $ xrandr -q

and change the mode of VGA1 with
> $ xrandr --output VGA1 --mode 1024x768
This will change the mode to 1024x768

You can switch off VGA0 with
> $ xrandr --output VGA0 --off

kagashe

---

### Post by overdrank on 2008-08-27
> **plnnightsky said:**
> 
04:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e4 (rev a1)



Hi and welcome, kagashe gave good advice. I am just wondering what is the model of the graphics card as some one I was helping the other day had issues with the DVI output. I believe you also posted in that thread. 
You can update you pci ids with this command in the terminal
```
sudo update-pciids
```
Also you stated that when you run the nvidia settings command nothing happens? If so you may need to install them via synaptic manager.

---

### Post by plnnightsky on 2008-08-27
> **overdrank said:**
> Hi and welcome, kagashe gave good advice. I am just wondering what is the model of the graphics card as some one I was helping the other day had issues with the DVI output. I believe you also posted in that thread. 
You can update you pci ids with this command in the terminal
```
sudo update-pciids
```
Also you stated that when you run the nvidia settings command nothing happens? If so you may need to install them via synaptic manager.

The case of assuming got me in trouble again (since no error must be installed).  Thanks overdrank, I was missing the installation of nvida-settings.  I did a search and installed it then the command worked.  I only had to reinstall my xorg.conf once so far.  I do get pages of this type of error.  don't know if this is something I should be concerned about.

ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display connection).

It is not working the way I would like, but at least I have two displays working now.  It will take some time to figure it out.

The video card is Nvida Geforce 8400GS.

Thanks to both of you.

I'm impressed with what I can do, too many choices. :) 

When I have the monitors set to run with their own xwindows, how do I move applications between the monitors?  I'm sure it can be done because some of the configuration windows does it.

---

### Post by simonofsocal on 2008-08-28
> **plnnightsky said:**
> When I have the monitors set to run with their own xwindows, how do I move applications between the monitors?  I'm sure it can be done because some of the configuration windows does it.

You can't.  Sorry, but afaik you can only share apps like that when you have xinerama, or twinview enabled.  I prefer xinerama, it seems to handle fullscreen video a little better than twinview did for me.

---

### Post by plnnightsky on 2008-08-29
> **simonofsocal said:**
> You can't.  Sorry, but afaik you can only share apps like that when you have xinerama, or twinview enabled.  I prefer xinerama, it seems to handle fullscreen video a little better than twinview did for me.

I do have twinview enabled, I will switch to xinerama if this will help.  The way I have the monitors set-up is both work independent of each other.  This was one of the choices in nvida settings.

---

### Post by plnnightsky on 2008-09-19
Just an update:
The major problem was I did not have "nvidia-settings".  This was not apparent to when I tried to run "gksu nvidia-settings".  I thought it was a switch.  Once I ran "apt-get install nvidia-settings", I was able to configure the dual outputs.

The only thing I have not been able to figure out is how to move applications from one screen to the other.

---

