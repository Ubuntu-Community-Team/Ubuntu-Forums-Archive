---
title: "Nvidia HELL (no boot screen or GUI)"
date: 2012-11-02
forum: Multimedia Software
---

### Post by Culito on 2012-11-02
Edited now since graphics are completely broken after fresh install.  See below.

---

### Post by TenPlus1 on 2012-11-02
Have you tried re-installing plymouth-label again ?

---

### Post by Culito on 2012-11-02
I did, no change.
I backed everything up already on to my secondary storage drive, so I think I'm going to do a clean install on my main drive.  It's probably time.

I'll report back.  I'm expecting to still be missing a boot screen and I'd really like to figure that out.

-C

---

### Post by Culito on 2012-11-02
The awesome news is that a new install of 12.10 is completely useless - noveau evidently doesn't work at all with my card and I get crazy graphics that lock up constantly while I'm trying to install Nvidia drivers from the command line...which is fun.

---

### Post by pqwoerituytrueiwoq on 2012-11-02
try booting using nomodeset in your kernel line

---

### Post by Culito on 2012-11-03
With or without nomodeset, the computer boots into low graphics mode. I can log in, and then I get a blank desktop with no launcher.  The only thing I can do is a Ctrl+Alt+T to get a terminal window.
If I run "unity", I just get Compiz errors and the computer locks up.
Any ideas?  I need my computer back!

---

### Post by Culito on 2012-11-03
I have been trying everything to install my nvidia drivers to no avail.
jockey-text -l
lists some drivers including kmod:nvidia_current.
jockey-text -e kmod:nvidia_current
fails with a message to view the jockey.log.  The last line:
/sys/module/nvidia_current/drivers does not exist.

I guess I might have to try the manual install here...?
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by pqwoerituytrueiwoq on 2012-11-03
```
sudo apt-get install nvidia-current linux-headers-$(uname -r)
```

---

### Post by Culito on 2012-11-03
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get install nvidia-current linux-headers-$(uname -r)
```

FANTASTIC!!

```
sudo apt-get install nvidia-current linux-headers-$(uname -r)
jockey-text -e kmod:nvidia_current
sudo nvidia-xconfig
reboot

```
Worked!
I have no boot screen, but I can live with that.
Everything appears stable so far.

Thanks very much.

---

### Post by pqwoerituytrueiwoq on 2012-11-03
google ubuntu boot resolution fix to fix plymouth

---

### Post by Culito on 2012-11-07
So I had to do the whole ```
sudo apt-get install nvidia-current linux-headers-$(uname -r)
``` again after a kernel upgrade by the Update Manager.
Is there any way for this to happen automagically?

---

### Post by BicyclerBoy on 2012-11-07
Install the meta-package that always points to the installed kernel matching package:
sudo apt-get install linux-headers-generic

The jockey install method should be triggering the headers package update & building nvidia kernel interface & loading by dkms.

I suspect your problems are caused by the jockey install not working & this is a consequence of having used the nvidia installer script.
The nvidia install script does have an "un-install" option.

---

### Post by Yougo on 2012-11-07
I ran into this problem aswell, and did 

```

sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall nvidia-expirimental-304

```

i understand that the second command wasn't necessary?

i also thought i had installed linux-headers-generic before, but am not sure, i might have installed the specific kernel headers back then. meh. no way to check now.

so, to be clear: 
**with linux-headers-generic installed, i will not run into this again at next kernel update?**


---------------
a tip for those running into this empty desktop stuff:

-if you have another DE or shell installed, and Lightdm/gdm/else loads into and odd resolution, load into a non-unity session, like gnome classic or xfce
-when you do load a not-working-unity session, pressing CTRL+ALT+T should give you a terminal, in which you could type
```
sudo apt-get install gnome-panel
gnome-panel
``` to get some gui even if it's just for logging out, or press CTRL+ALT+F1(to 6) to get to a VT and do your fixing from there

---

### Post by Culito on 2012-11-07
Good to know.
On my last install, I had a choice on which GUI (unity, unity2d, etc) now those choices aren't there.  Do I have to install those separately?

---

### Post by Yougo on 2012-11-08
Unity now only has 3d mode, with some special addition that sends the rendering through your CPU if your graphics card isn't up for the task. how well that works is up for debate.

unity 2d is not available anymore.

if you want a 2d experience, i do believe Gnome Shell has it's fallback mode
```
sudo apt-get install gnome-shell
```
the fallback mode is selectable at login (gnome classic), and loads if gnome-shell detects low graphics. the fallback mode will be gone at some point in the (near?) future, so for a long term solution, you might want to look at something else.
another option is to install another DE like lubuntu/lxde or xubuntu/xfce
```
sudo apt-get install lubuntu-desktop
or
sudo apt-get install xubuntu-desktop
```

and finally, you could resort to DE's from other distro's like Mate, Cinnamon, etc, but that requires adding repo's or even switching distro's

---

### Post by Culito on 2012-12-08
Well, I'm back after more battling with nvidia drivers.  My computer came off of screen saver, only to randomly reset to 640x480.

I followed all the directions that worked before, to no avail.

jockey-text -l lists nvidia_current enabled, but not in use. (I'm aware that this may be incorrect.  Xorg.conf lists "nvidia" as the display driver.)
I also tried re-installing nvidia-common.
The Displays dialog only lists 640x480 as an option, and the nvidia-xconfig doesn't list any options either.
The unity launcher still works, it's just huge...
I'm wondering if I just have some failing hardware here.

---

### Post by Culito on 2012-12-08
Well, my face is red.
The cable on the back of the monitor was loose, so it wasn't detecting properly.

Good times.

---

