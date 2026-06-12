---
title: "Help Noob Install NVIDIA"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by brewbob on 2007-12-13
My eMachine has an NVIDIA GEForce 6100 GPU (NVIDIA Crush 51)

Since I installed Gutsy Gibbon the only choices for screen resolution are 800x600 and 640x480.  Not good enough.

So I went to Add/Remove programs and added the NVIDIA binary X.Org (new driver).  It added without any problem.

Now, how do I install this so the screen resolution preference includes other resolutions other than the two above?

I need a detailed explanation on this, as I'm a novice noob.  And, I would really appreciate your assistance!  :)

Thanks,
Bob

---

### Post by lswest on 2007-12-13
well, the best option to go with (least amount of work) and that should work would be to open a terminal and type ```
sudo apt-get install nvidia-settings
```
then, after it installs,
run it with ```
 nvidia-settings
``` in the terminal, which will open a control panel-like app, where you should set the resolution to "auto" so that it always gets put to the best resolution.

---

### Post by brewbob on 2007-12-13
isWest,

Thanks.  I did that and it apparently decided that the NVIDIA package I need is the Legacy version and it did its thing. But, I got some error messages:

***************************************************************************************
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  nvidia-glx-legacy
The following packages will be REMOVED:
  nvidia-glx-new
The following NEW packages will be installed:
  nvidia-settings
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 691kB of archives.
After unpacking 13.5MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted nvidia-settings 1.0+20070502-1ubuntu2 [691kB]
Fetched 691kB in 8s (86.3kB/s)                                                 
(Reading database ... 89145 files and directories currently installed.)
Removing nvidia-glx-new ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package nvidia-settings.
(Reading database ... 89097 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_1.0+20070502-1ubuntu2_i386.deb) ...
Setting up nvidia-settings (1.0+20070502-1ubuntu2) ...

brewbob@brewbob-desktop:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

brewbob@brewbob-desktop:~$ 
**********************************************************************************

When the NVIDIA control panel app opened, there was nothing to select "auto" available, due to the errors listed above?

:confused:

---

### Post by lswest on 2007-12-13
first off: the first letter of my name is an L but no worries^^ hmm, what seems to be the problem is that the nvidia driver isnt being used.  Check to see that in the xorg.conf file, open with ```
 sudo gedit /etc/X11/xorg.conf
``` has, and find ```
Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:0:18:0"
    Screen          0
EndSection
``` and make sure the driver is set to nvidia.  and if you want you can edit this bit ```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "1280x800@60"
    EndSubSection
EndSection
``` so that the only mode is the resolution you want, if the nvidia-settings doesnt work.

---

### Post by shavenlunatic on 2007-12-13
> **lswest said:**
> well, the best option to go with (least amount of work) and that should work would be to open a terminal and type ```
sudo apt-get install nvidia-settings
```
then, after it installs,
run it with ```
 nvidia-settings
``` in the terminal, which will open a control panel-like app, where you should set the resolution to "auto" so that it always gets put to the best resolution.


just to add to that.. don't you have to run

```


gksu nvidia-settings 
```
to let it write to xorg.conf, otherwise many of the changes won't be permanent..?

---

### Post by brewbob on 2007-12-13
I did the routine LS suggested, but not sure how to make the OS accept it.  When I check preferences, I still have the original two resolutions and not the one I edited in the screen section.  BTW, the modes in the screen section showed all possibles modes, not just the two defaults.

I did reboot Gutsy to see if the mode changed but no luck.

Shavenlunatic:  should I run what you suggested?  Can it hurt if it's not the right one?

---

### Post by shavenlunatic on 2007-12-13
> **brewbob said:**
> I did the routine LS suggested, but not sure how to make the OS accept it.  When I check preferences, I still have the original two resolutions and not the one I edited in the screen section.  BTW, the modes in the screen section showed all possibles modes, not just the two defaults.

I did reboot Gutsy to see if the mode changed but no luck.

Shavenlunatic:  should I run what you suggested?  Can it hurt if it's not the right one?


run what i said.. make your changes, click apply and then click "save to xorg.conf" (or whatever it is.. its ust near apply)..

give it a reboot and aslong as your password was accepted when you ran gksu nvidia-settings your settings should be saved...

---

