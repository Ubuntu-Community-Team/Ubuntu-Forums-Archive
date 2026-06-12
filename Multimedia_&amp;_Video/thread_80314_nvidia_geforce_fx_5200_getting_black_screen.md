---
title: "nvidia geforce fx 5200 getting black screen"
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by jhong on 2005-10-21
I'd been playing games (RTCW-ET) with my 5200 for like a year, until a few months ago since nvidia released 7x.xx series drivers, my 5200 stopped working, all i can get is a black screen and i have to reset the box (oh wait, i have to power off/on)...  i have been googling this issue for a long time, but still can't find any solution that works for me, the last known working version of the driver is 66.29 but it doesn't compile with the new kernels...   I miss RTCW-ET so much, does anyone here have the same problem?

---

### Post by jerrygofixit on 2005-10-23
I also have the fx 5200 256mb, it's recommended that you stick w/ the 6779 drivers. google nvidia linux drivers, go to archive and install the 6779, you will probably have to edit your xorg.conf from console because i doubt it will find the card (didn't find mine and mines the same as yours). There's a document on the forums about it, i only saved a portion of it, here's what I have:

Ok, now let's begin:

1) uninstall nvidia-glx (if you don't have it just go to step 2)

2) remove the file manually:
sudo rm /etc/init.d/nvidia-glx

3) sudo apt-get install gcc

sudo apt-get install gcc-3.4

ctl-alt-f1 (so as to get to the command line, not a windowed terminal, but out of the graphical interface GUI)

login with your username and password (if required)

sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)

cd “directory where you have the nvidia installer”

CC=gcc-3.4

export CC

If you have Ubuntu 64bit type: **
sudo sh NVIDIA-Linux-x86_64-1.0-7667-pkg2.run

Otherwise if you have Ubuntu 32 bit type:
sudo sh NVIDIA-Linux-x86-1.0-7667-pkg2.run

If you have Ubuntu 64bit you can't install OpenGL32bit compatibility libraries, so when the installer asks whether to install it just answer no OR you may want to try a workaround which Draugen found but which I haven't tried myself (look at the PROBLEMS SECTION at the end of the guide: point 5).

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo nano /etc/X11/xorg.conf
scroll the file down until you find the line with “Modules” and comment out (by putting a "#" before the line) the 2 lines I put in blue and add Load "glx". It should look like the example below:


Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
#Load "dri"
#Load “GLcore”
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"

Then find the section Device and make sure the word I put in red is “nvidia”:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "nvidia"
BusID "PCI:1:0:0"


CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

sudo /etc/init.d/gdm start (or "kdm start" if you use KDE)

Now you have installed the new nvidia driver.

If you want a "control panel" which shows the settings of your card you might want to install "Nvidia-settings" (this part of the guide has been taken from the Unofficial Ubuntu Starter Guide) although they driver works fine also without it (the choice it's up to you).

Open Terminal or Konsole and type

sudo apt-get install nvidia-settings

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop (you can use "kate" instead of "gedit" in KDE)

Insert the following lines into the new file:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;


Save the file and exit.

Restart your computer

You will be able to see "Nvidia settings" in the menu (the one from which you launch all the applications)

Enjoy!

---

### Post by sirlancelot on 2005-10-23
I am using the 128mb version of the 5200 and have similar problems with GL enabled applications. However I can't find version 6779 of the drivers you say to find in the archives here: 
[http://www.nvidia.com/object/linux_display_archive.html]("http://www.nvidia.com/object/linux_display_archive.html")  
Is there another page that I am overlooking?

---

### Post by xsence on 2005-10-24
[QUOTE=sirlancelot]I am using the 128mb version of the 5200 and have similar problems with GL enabled applications. However I can't find version 6779 of the drivers you say to find in the archives here: 
[http://www.nvidia.com/object/linux_display_archive.html]("http://www.nvidia.com/object/linux_display_archive.html")  
Is there another page that I am overlooking?[/QUOTE]

Hi they mean the 7667 driver.

here's the link: [http://www.nvidia.com/object/linux_display_ia32_1.0-7667.html](http://www.nvidia.com/object/linux_display_ia32_1.0-7667.html)

and here for the full howto:

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=latest+Nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=latest+Nvidia+drivers)

---

### Post by sirlancelot on 2005-10-25
I have just tried those drivers and still experience the same problem, the GL program works for a short seemingly random period of time, then goes blank.

---

### Post by xsence on 2005-10-25
[QUOTE=sirlancelot]I have just tried those drivers and still experience the same problem, the GL program works for a short seemingly random period of time, then goes blank.[/QUOTE]

have you done this to your xorg.conf?

#Load "dri"
#Load “GLcore”

and has this system runned fine before? maybe its a hardware problem.

---

### Post by stefann on 2005-10-27
I'm having the same problem with a GeForce FX Go5200. Which version is supposed to work? Noone is speaking of the same...

---

### Post by sirlancelot on 2005-11-15
[QUOTE=xsence]have you done this to your xorg.conf?

#Load "dri"
#Load “GLcore”

and has this system runned fine before? maybe its a hardware problem.[/QUOTE]
Yes that was done automatically with my install of the new driver. After further diagnosis the GL-enabled app seems to simply stop drawing the 3D aspect, the canvas is still there but nothing is rendered.

---

### Post by stefann on 2005-11-20
I've now solved my problem. I compiled the older nvidia driver, 7667, and then it worked like a charm.

---

### Post by DaRiuX on 2006-09-13
I have an 5200 too and I can't install 6.06 LTS, after it boots from CD the screen goes blank with all resolutions. I even tried with another monitor and the same problem, what can I do?

---

### Post by bdk on 2006-09-14
I just reinstal Dapper after adding a FX 5200 and the regular install would cause X to crash, ](*,) so I used the Safe Video Mode to boot. :biggrin:  It should be the 2nd option down on the Live disc GUI when it first comes up.

I'm off to install the 7667 drivers now too because previously no openGL app would work, it would cause X to crash and restart... 

*-bdk*

> **DaRiuX said:**
> I have an 5200 too and I can't install 6.06 LTS, after it boots from CD the screen goes blank with all resolutions. I even tried with another monitor and the same problem, what can I do?

---

### Post by DaRiuX on 2006-09-15
Doesn't work...

---

### Post by dom on 2007-02-27
works out of the box for me on edgy with :

01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)

Anybody know whether to use the nvidia-glx or glx-legacy driver from synaptic ?

---

### Post by jrharvey on 2007-09-13
I have the same card but Ubuntu wont even boot. It just freezes in the boot screen for hours until I restart. All I have to do is switch to my Onboard video card and Ubuntu boots up fine but thats no fun. I want my video card back.

---

### Post by juststealthbabay on 2007-10-04
I was having the same problem myself.

Here's how I fixed it:
Under the "Screen" section of your /etc/X11/xorg.conf file, add the following line.
Option "NvAGP" "1"

Apparently there are problems with certain AGP graphics cards.
More information can be found [here]("http://en.opensuse.org/NVIDIA"). (under "Troubleshooting")

---

### Post by ariszlo on 2008-05-31
> **juststealthbabay said:**
> Under the "Screen" section of your /etc/X11/xorg.conf file, add the following line.
Option "NvAGP" "1"

Thanks a lot! With that option I can have 3D acceleration with Ubuntu's nvidia-glx.

---

### Post by cyclops-user on 2008-05-31
Could you tell us how did you manage to get the card working? I have the same card (FX52000) but i get a blank screen using the nvidia drivers.

Thanks

---

### Post by cyclops-user on 2008-05-31
I used this option:
Option       "NvAGP" "2"
and now the card is working!
Thanks!

---

