---
title: "Unable to use nvidia driver"
date: 2008-10-01
forum: Multimedia Software
---

### Post by kramer2718 on 2008-10-01
I am about ready to tear my hair out ... I guess that wouldn't be helpful, would it?  Anyway...

I just got a snazzy new 1920x1200 LCD monitor and would actually like to take advantage of the resolution, but the default driver (didn't see anything about a driver under the default xorg.conf) won't work at that resoltoin.  So my first inclination was to install the nvidia driver.  So I did:

sudo apt-get install nvidia-glx

and it seemed to install just fine.  I used nvidia-xconfig in order to set up my xorg.conf, but then when I tried to startx, I got this:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux gloria 2.6.24-19-server #1 SMP Wed Aug 20 18:43:06 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM

        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  1 00:48:19 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) Module "ramdac" already built-in
FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

I thought that the preamble about x being unsupported was weird, but I'm running the latest version.  I then tried 

lsmod | grep nvidia
lsmod | grep glx

Neither returned any results ... so I did this:

modprobe nvidiafb

(it was the only video driver that looked likely)

But still no luck.  I got the same error message.

I was wondering if I should be using nvidia-glx, nvidia-glx-legacy, or nvidia-glx-new?  The docs I've found don't exactly match a gpu to a package very exactly.  My GPU, btw, is a GeForce 7050 PV onboard.  While I'm on the topic, my cpu is an Athlon 64 x2 5000 and I'm running Ubuntu Server 8.04 (kernel 2.6.24-19-server).  And I run KDE not Gnome.

I'm not opposed to using an opensource driver, but I've tested the default graphics drivers at that res and they seem to fail. (Any comment on that?  It seems that almost every GPU these days supports resolutions that high?  Why does the default driver seem to work at low res, but not high res?)

Any help would be much appreciated.

---

### Post by kpkeerthi on 2008-10-01
The correct way to install nvidia driver in Ubuntu is from System -> Admin -> Hardware Drivers

As for your case, you should have installed nvidia-glx-new.

1. Uninstall the driver:
```
sudo apt-get remove nvidia-glx
```

2. Edit your xorg.conf. Look for the line that highlighted below
```
sudo nano /etc/X11/xorg.conf
```
```

Section "Device"
  Identifier "nVidia Inc. GeForce2"
**  Driver     "nvidia"**
  VideoRam   65536
EndSection

```
Change it to
```

Section "Device"
  Identifier "nVidia Inc. GeForce2"
**  Driver     "nv"**
  VideoRam   65536
EndSection

```
3. Reboot.
4. Install the driver from System -> Admin -> Hardware Drivers

---

### Post by kramer2718 on 2008-10-01
But my xorg.conf doesn't look like that.  It looks like this:

```

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
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

```

I made the change to the device section as your suggested (and changed the identifier rerferenced in the Screen section).  starttx pooped itself:

```

...
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  1 09:28:57 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found

waiting for X server to begin accepting connections
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

modprobe -l nv

said that there was no module nv...

Another thing, when you suggest that I reboot, do I really have to reboot or is restarting X sufficient?

Also when you say, System -> Admin -> Hardware Drivers, I don't have those menu options.  I do have System -> Hardware Drivers Manager (and it gives no options whatsoever)...

What do those fancy linux driver managers do differently than manually installing the packages and loading the modules anyway? 

I'll refrain from manually installing nvidia-glx-new until I hear something here.  Would that work anyway?

Eagerly awaiting a reply...

---

### Post by Therion on 2008-10-01
Keeping it short, the instructions you have been given are explicit and are entirely correct.  

I suggest you follow them.

---

### Post by kramer2718 on 2008-10-01
WTF!?!?!

:confused:

I CAN'T follow them!

You told me to replace something in my xorg.conf that isn't there!!!!!!!!!!!!!!!!!!!!!!!!!!

If I was was going to be pedantic as you are suggesting that I should be, the operation <replace occurrences of X with Y in Z> leaves no occurrences of Y in Z if X was not first there!!!

So in that case, you suggestion would be a no-op.

Furthermore, the app that you told me to use isn't in my menu where you said it would be.

Besides, I come to these forums to fix my system and understand what is going on with my system.  I gave a ton of information about the problem and asked several pointed questions.

If you don't understand what's going on, ask more questions.

If you don't want to help, just say so and go to another thread.

---

### Post by Therion on 2008-10-01
> **kramer2718 said:**
> If I was was going to be pedantic as you are suggesting that I should be...

If you don't want to help, just say so and go to another thread.
You'll do well around here with that attitude.  

Oh, and I don't want to help you so I'm going to another thread.



Good luck!

---

### Post by Crafty Kisses on 2008-10-01
What are the results of this command?
```
glxinfo
```

---

### Post by kramer2718 on 2008-10-01
Look.  I tried to follow the directions given.  They didn't apply/didn't work AS I VERY CLEARLY COMMUNICATED.  If anyone else would like to help, I'd much appreciate it.

---

### Post by kramer2718 on 2008-10-02
```
$ glxinfo
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
bash: glxinfo: command not found
$sudo apt-get install mesa-utils
...
$glxinfo
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
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

---

