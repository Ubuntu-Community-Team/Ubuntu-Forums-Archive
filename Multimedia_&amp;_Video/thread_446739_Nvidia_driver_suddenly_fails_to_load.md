---
title: "Nvidia driver suddenly fails to load"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by Ublis on 2007-05-17
Running 64-bit 7.04 with a Geforce 7600GT, the nvidia driver stopped working after a reboot. I had installed VMWare and enabled visual effects, but had not updated the distro in that session. I am able to boot with GUI using nv instead of nvidia in xorg.conf.

Here's the partial error log:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Athena 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 17 15:04:00 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Philips 190X"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
....
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```
The failing configuration (which apparently worked):
```

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

```
This is what I get when trying to manually load the module:
```
# modprobe nvidia
FATAL: Error running install command for nvidia

```
I have tried:
- (re)installing nvidia-glx, nvidia-glx-new (both from Synaptic), the driver package from Add/Remove, the driver package from Automatix (I'm not sure which maps to which, so I just tried all of them)
- installing nvidia-glx after removing the nvidia-glx-new traces as described in [https://bugs.beta.launchpad.net/ubuntu/+bug/106217](https://bugs.beta.launchpad.net/ubuntu/+bug/106217)
- dpkg-reconfigure xserver-xorg (this got me a xorg.conf similar to above, but not working unless manually switched to nv again)
- nvidia-xconfig (which reset the Device setting, removing all but the Identifier and Driver part)
- updating the system (most important/low-level update seemed to be HAL)
- disabling the visual effects again
- purging vmware-server
- reboot, somewhere in the middle of it all

Any suggestions?

---

### Post by azidtripz on 2007-05-17
yeh mine wont auto load but i can manualy load it like this

modprobe -i nvidia

and then i can load gdm

its getting really annoying but because i have to run this ever reboot...

if anyone has any info i would be much appriceated.

---

### Post by avalez on 2007-05-19
+1 on  2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
but even 'modprobe nvidia' does not help - just nothing happens

---

### Post by azidtripz on 2007-05-20
> **avalez said:**
> +1 on  2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
but even 'modprobe nvidia' does not help - just nothing happens

"modprobe nvidia" did not work with me either i had to use "modprobe -i nvidia",
but if that doesn't do it for you it would be a completely different problem then mine, which i eventually fixed

---

### Post by tseliot on 2007-05-20
the command should be:
```
sudo modprobe nvidia
```

and try this:
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

---

### Post by morphious on 2007-05-21
I have similar problem. Few days ago, I downloaded the newest nvidia drivers, installed and built the kernel module. Everything went fine. Drivers was running ok (both the kernel module and drivers). 

After reboot, I couldn't start X (error message: drivers and kernel module wasn't exactly the same version). I checked lsmod, the kernel module nvidia was loaded. When I do:

```

sudo rmmod nvidia
sudo modprobe nvidia
```

and then:

```

startx
```

X is working correctly.

So I think, that the OLD nvidia module (from linux-restricted-modules) loads every boot.
I need linux-restricted-modules, because of my wireless network card - ipw3945.

But I do not want to load nvidia kernel module from this package.
What can I do?

Greetings, thx for help.

---

### Post by avalez on 2007-05-21
> **azidtripz said:**
> "modprobe nvidia" did not work with me either i had to use "modprobe -i nvidia",
but if that doesn't do it for you it would be a completely different problem then mine, which i eventually fixed

Well, it appeared, 'modprobe nvidia' worked, only after reboot with original xorg.conf, i.e. with nv driver for videocard, then nvidia does not load during boot time;  so yes, 'rmmod nvidia' does the trick, thanks tseliot, also!

So, I have the same issue, and clear, something goes wrong with loading nvidia driver at boot time, as it definitely works fine if (re)loaded afterward, thus right after installation it works fine too.

Meanwhile I've put rmmod, modprobe commands to /etc/rc.local, so gdm starts with second attempt.

True solution is still expected.

---

### Post by Ublis on 2007-05-24
Color me purple, I stumbled upon a solution. Well, it's the first time I boot, so it might still break down next time. Here's what I did (just posting a sequence, I'm not quite sure which step is the magic one):
- get nvidia-glx-new 
- switch back to nv in xorg.conf (this was basically my starting configuration)
- startx, then reboot
- Ctrl+Shift+F2 to go to a console. xorg.conf back to nvidia
- Ctrl+Shift+F7 to go back to the GUI. Kill it with Left-Shift+Left-Ctrl+Backspace. Will fail to load.
- as "sudo su": modprobe -i nvidia (fails, but in a new and interesting way claiming I might not have a nVidia GPU)
- switch back to nv in xorg.conf
- startx
- open a new console from Applications. Go "sudo su" and "modprobe nvidia". No problems, but no effect neither.
- try to switch on Desktop effects
- Ubuntu now wants to dload+install the nvidia drivers. Accept. It removes nvidia-glx-new and installs nvidia-glx. Wants to reboot, but refuse.
- sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
- now reboot

Then it worked. I think it might be related somewhere to rebooting at the right point in time. Interestingly enough, when I messed around with the drivers in non-GUI mode, it didn't offer to reboot. When I did so in GUI, it did offer.

By the way, I did have the restricted modules installed. For future reference, here is what I got from modprobe -i:
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
```

Of course, now it refuses to mount my NTFS partitions which worked perfectly fine before. Aaargh.

---

### Post by hsnart on 2007-05-28
i've got the same problem. (same reported x log and modprobe failing)
Seemingly following a system update (nvidia-glx was updated a few days ago too.)
sudo modprobe nvidia doesnt work. returning FATAL: Error running install command for nvidia

Is there any further diagnosis of the modprobe error i can do? (sorry, i'm new to a lot of this).

---

### Post by hsnart on 2007-05-31
solved my problem.

the update to nvidia-glx (2.6.20-16) had a dependency on linux-restricted-modules. But i only had linux-restricted-modules 2.6.20-15 installed.

i uninstalled nvidia-glx and linux-restricted modules (with -purge). then reinstalled, and also installed linux-restricted-modules 2.6.20-16. nvidia-glx works fine for me now.

---

