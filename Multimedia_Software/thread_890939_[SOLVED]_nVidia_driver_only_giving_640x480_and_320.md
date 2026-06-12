---
title: "[SOLVED] nVidia driver only giving 640x480 and 320x240"
date: 2008-08-15
forum: Multimedia Software
---

### Post by stromdal on 2008-08-15
On my MythBuntu box i have an nVidia Quadro 4 graphics card. I installed the restricted driver through Applications > System > Hardware Drivers and rebooted. Now I get two resolution options: 640x480 and 320x240. 

I tried installing envyng:

```
sudo apt-get install envyng-gtk
```

I had envyng installing the nVidia driver based on automatic hardware detection, and i rebooted. envyng removed the drivers installed by the Ubuntu Restricted Drivers application and instead installed another driver, but the end result was the same; only the two resolutions.

I installed the nVidia graphics control panel to see if that would change anything:

```
sudo apt-get install nvidia-settings
```

But no change - only the two resolution settings.

I tried installing, uninstalling and reinstalling the drivers using Ubuntu's Restricted HW tool and envyng several times, but so far all I've accomplished is losing the default Ubuntu driver, so now I can't get more than 640x480 even WITHOUT the nVidia driver (before installing nVidia driver I got 800x600 with the drfault driver). 

---------------------------------------

Some basic information:

```

~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

```

```

~$ uname -a
Linux mediBuntu-Frontend 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

```

```

~$lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV28GL [Quadro4 980 XGL] (rev a1)

```

My system is up to date.

The graphics card has two DVI outputs and I'm using a DVI->VGA adapter to connect to my monitor (a Philips 170B LCD monitor), so I'm guessing that corrupted EDID info is not the issue (since the  analog VGA monitor input doesn't send out any EDID info?).

---

### Post by LeetSpeak on 2008-08-15
Do you have internet connection? You need internet connection to install the packages needed.

---

### Post by stromdal on 2008-08-16
Yes, I have internet connection.

---

### Post by stromdal on 2008-08-26
Is there really noone out there who can help me with this?

---

### Post by overdrank on 2008-08-26
> **stromdal said:**
> Is there really noone out there who can help me with this?

Hi and you can try what PmDematagoda suggest here
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```

---

### Post by stromdal on 2008-09-09
Turns out there was nothing wrong with the graphics card driver. The computer was unable to determine what screen I was using and defaulted to a 640x480 "Plug 'n play" screen. 

I used the command:

```
gksudo displayconfig-gtk
```

to manually set the screen to a 1280x1024-capable generic screen.

BTW: when connecting the box to my 1920x1080 native LCD TV the resolution was automagically set correct without me having to lift a finger.

---

