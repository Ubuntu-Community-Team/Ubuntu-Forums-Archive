---
title: "Nvidia Driver problem with KDE (kubuntu)"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by dercaS on 2007-04-03
Hello, I'm pretty new to Linux, so please be gentle with my somewhat lack of knowledge here.

I downloaded and installed a DVD distro of ubuntu 6.10 that came with Gnome as standard.
I then decided I wanted to try out KDE instead, and downloaded the required packages (with Synapsis I think), and installed KDE.
Edited /etc/X11/default-display-manager and made sure it contained /usr/bin/kdm

After a bit more tweaking here and there, was following some HOWTO that i googled to, I was finally running KDE.

Now, I wanted to install the nvidia drivers. The drivers in question are the 1.0-9755 version.
My system is a AGP Leadtek 6600GT 128 MB card on a ASRock k7v88 MB using the VIA KT880 Northbridge. CPU is a AMD Athlon Barton 3200@2200 Mhz. 400 FSB.
(Maybe excessive info here, but I just figured I should just cough it up right now)

The thing that happens when I install the drivers is that KDE starts up in 640x480@50 resolution. The login screen looks really ugly. Small and blurred letters. I manage to login in, but it all looks like I'm seeing the screen through a magnifying glass. I cannot in any way change the resolution. The only thing that can be changed is refresh rate. 50 or 56 Hz.

I have tried manually installing the drivers with 
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run.
I have also tried Envy.

Allways the same problem.

When viewing the xorg.conf file I see the following:

Section "Device"
  identifier "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
  boardname "NVIDIA GeForce 6 Series"
  busid "PCI:1:0:0"
  driver "nv"
  screen 0
  vendorname "NVIDIA"
EndSection

Section "Monitor"
  identifier "SyncMaster"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection
  
Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
  Monitor "SyncMaster"
  DefaultDepth 24
  SubSection "Display"
    depth 24 
    virtual 640 480
    modes "640x480@60"
  EndSubSection
EndSection

My monitor is a Samsung SyncMaster 913N LCD panel that should run at 1280x1024@75. 

I have looked at various guides, howtos and forums. But nothing that really has helped me. Also it's a drag to pick out hints from several sources and try to make things work. :( 

So, does anybody have any suggestions what I should do?
I'm not afraid to manually edit configuration files to get things working.

Oh and just a side note. When installing the nvidia drivers, the GUI fail to start when i boot up. I just get the TTY login screen, and then have to start X manually. Go go.
I am also currently downloading a DVD distro of Kubuntu and will have that just in case.

Sorry for a longwinded post, wasen't really sure how much information you would need.

---

### Post by tseliot on 2007-04-03
type:
```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you a few questions (Press ENTER whenever you don't know the answer to a question). At a certain point it will ask you about the resolution you wish to use (select it with the SPACEBAR). 

then log out and press CTRL+ALT+Backspace and log in

---

### Post by dercaS on 2007-04-03
Thanks for the tip. I tried it, and I managed to figure out what values to enter.
At the very beginning i choosed nvidia instead of nv as a display driver.
As name i set GeForce 6600 GT.
Then it was smooth sailing relativly untill i came to refresh rates settings.
I'm guessing that my monitor should have a fixed setting here, so I set 75 at both.
Instad of the 32-80 or whatever it was.

Logged out and restarted with CTRL-ALT-Backspace.

However upon examening System Settings -> Monitor & Display it now says I can choose between 50 and 51 Hz for refresh rates.
The Graphics Card is listed as a NVIDIA GeForce FX (generic)
Driver: nv

Shouldn't this be GeForce 6600 GT and driver: nvidia?

I'm a bit confused to be honest.

Good news is that I've got 1280x1024 though. :)

---

