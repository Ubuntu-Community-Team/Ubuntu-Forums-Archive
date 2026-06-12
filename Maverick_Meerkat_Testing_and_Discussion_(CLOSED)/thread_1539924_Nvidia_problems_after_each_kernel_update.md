---
title: "Nvidia problems after each kernel update"
date: 2010-07-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-07-27
While I know that the default drivers are recommended rather than the proprietary Nvidia drivers, I prefer to enable a few effects from Compiz (0.8.x, not the new one) and so I need the closed source drivers to do this.

My question is.. Should I have to manage my video drivers after each kernel update? Have I configured this incorrectly, because I don't remember Ubuntu 10.04 updates giving me video problems this frequently.

I have the current version nVidia drivers with dual monitors configured through Nvidia Settings for TwinView setup. After I update the kernel and reboot I sometimes get a video failsafe menu and other times it seems to just work but warn me that the regular monitors configuration was unable to be used (or something along those lines).

I'd like to know the proper way to handle this on updates each time, or if my configuration is just corrupt...how can I purge everything video related and correct the problem?

I'm always able to get it working again, but the only method I know of is to remove the Nvidia driver, setup Nouveau so I can start X properly, reinstall Nvidia driver, run nvidia-xconfig, reboot, run nvidia-settings, restart X. I'm sure thats not the best way to handle it though.

Thanks in advanced.

EDIT:
I installed Nvidia driver via System -> Administration -> Hardware Drivers

---

### Post by P4man on 2010-07-27
You can install the closed source nvidia drivers from jockey (system > adminstration > hardware drivers). If you do it that way you should have no issue with kernel upgrades as the kernel modules will be rebuilt automatically. If you manually install nvidia drivers from the nvidia site you may get the issue you get.

I think you were  just confused about the ubuntu proposed drivers in jockey; they are not the opensource nouveau drivers; they are the binary nvidia drivers with working DKMS.

---

### Post by kyleabaker on 2010-07-27
> **P4man said:**
> You can install the closed source nvidia drivers from jockey (system > adminstration > hardware drivers). If you do it that way you should have no issue with kernel upgrades as the kernel modules will be rebuilt automatically. If you manually install nvidia drivers from the nvidia site you may get the issue you get.

I think you were  just confused about the ubuntu proposed drivers in jockey; they are not the opensource nouveau drivers; they are the binary nvidia drivers with working DKMS.

I may have been confusing, but I actually did install via Jockey, sorry. And I thought that it should update on its own, but every time I update the kernel, the video drivers fall behind.

Do you know how I can clean this out and restart with video configuration? As I said, I've removed the drivers via Jockey before and reinstalled them for each kernel update so far, so hopefully there is a better way. I'm hoping to avoid reinstalling 10.10 just get fix this. :D

---

### Post by P4man on 2010-07-27
Oh drat; I missed the fact this was posted in Maverick testing. i guess there is your problem and I dont know how to help :s

---

### Post by ronacc on 2010-07-27
I have been using the Nvidia driver from system>administration>hardware drivers (Nvidia current) and have had no problem with kernel update so far (just now upgrading from 2.6.35-10 to -11 ) .

edit:  The -11 kernel booted fine with the nvidia 256.35 driver and compiz with full effects.

---

### Post by kyleabaker on 2010-07-27
> **ronacc said:**
> I have been using the Nvidia driver from system>administration>hardware drivers (Nvidia current) and have had no problem with kernel update so far (just now upgrading from 2.6.35-10 to -11 ) .

I haven't had many issues with this in the past, but something isn't configured correctly to update anymore. Any idea how I can wipe the video configuration settings clean to start fresh (other than fresh 10.10 install)?

---

### Post by ronacc on 2010-07-27
try going to system>administration>hardware drivers and remove and then reinstall the nvidia driver .

---

### Post by wojox on 2010-07-27
Did you go to system > administration > hardware drivers or the Nvidia site when you installed them in 10.04?

---

### Post by ratcheer on 2010-07-27
> **ronacc said:**
> 

edit:  The -11 kernel booted fine with the nvidia 256.35 driver and compiz with full effects.

How did you do that?

Tim

---

### Post by kyleabaker on 2010-07-27
> **ronacc said:**
> try going to system>administration>hardware drivers and remove and then reinstall the nvidia driver .

As I've already stated above. I've already done that and have been for each update. The problem is that its not resolved correctly and I always have to modify things.

I even tried purging the nvidia drivers and restarting, but I don't think I was able to start with a clean configuration.

---

### Post by dino99 on 2010-07-27
which packages are installed ? (might be a meta package missing)

---

### Post by mc4man on 2010-07-27
> but I don't think I was able to start with a clean configuration.
Maybe you should try the manual method to return to nouveau, then after a restart go back to jockey and re-enable the drivers.

There is also a ~/.nvidia-settings.rc you could remove before re-enabling the restricted drivers

manual - under the OR
[http://ubuntuforums.org/showthread.php?t=1423210](http://ubuntuforums.org/showthread.php?t=1423210)


dit: have myself had no issues with updates and nvidia - but am not using twinview

---

### Post by kyleabaker on 2010-07-27
> **ronacc said:**
> try going to system>administration>hardware drivers and remove and then reinstall the nvidia driver .

> **dino99 said:**
> which packages are installed ? (might be a meta package missing)

I'm not sure exactly how to check for all the necessary ones, but here are the ones installed (checking in Synaptic by searching Nvidia):

nvidia-current 256.35-0ubuntu2
nvidia-settings 256.35-0ubuntu1
nvidia-common 0.2.23
nvidia-173-modaliases 173.14.27-0ubuntu1
nvidia-96-modaliases 96.43.18-0ubuntu1
nvidia-current-modaliases 256.35-0ubuntu2
xserver-xorg-video-nouveau
xserver-xorg-video-nv
smartdimmer
jockey-common
jocky-gtk

Could the problem be that Nouveau and NV are still installed?

---

### Post by wojox on 2010-07-27
Try the 10.04 way [Install NVIDIA drivers manually on Lynx]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=nvidia+driver+Lynx")

---

### Post by ronacc on 2010-07-27
the nouveau and NV drivers shouldnt be a problem , take a look @ /etc/X11/xorg.conf and see what driver is listed .

@ratcheer what do you mean ? I have the nvidia current driver enabled and full visual effects enabled also the full compiz config settings manager not the "simple" and fusion icon .

---

### Post by kyleabaker on 2010-07-27
> **ronacc said:**
> the nouveau and NV drivers shouldnt be a problem , take a look @ /etc/X11/xorg.conf and see what driver is listed .

@ratcheer what do you mean ? I have the nvidia current driver enabled and full visual effects enabled also the full compiz config settings manager not the "simple" and fusion icon .

Here are the contents of my xorg.conf file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 256.35  (buildd@crested)  Tue Jun 29 04:06:55 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 LE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by ronacc on 2010-07-27
looks about the same as my entry except that I don't have twinview on that box .

---

### Post by ratcheer on 2010-07-27
> **ronacc said:**
> 
@ratcheer what do you mean ? I have the nvidia current driver enabled and full visual effects enabled also the full compiz config settings manager not the "simple" and fusion icon .

I just could not the  rev 11 kernel to boot. It stopped at the plymouth splash screen (there is another thread on it in this (Maverick Meercat Testing...) forum. I purged rev 11 and rev 10 still works. I am using the 256.35 nVidia driver, as are you.

Tim

---

### Post by ronacc on 2010-07-27
try removing quiet and splash from your grub boot line and see it it will boot -11 . I always do when I am using Ubuntu's grub ( which I'm not right now I am booting off the grub on another install (sabayon ) on another hd ) . I have a multi boot multi drive multi distro system .

---

### Post by caryb on 2010-07-27
I too am using the prop driver via jockey, mine installs correctly every time I get a new kernel but I always start with a dialog box *buntu is starting in low graphics mode, when I click through the error messages it comes to the logon in full graphics mode with all the effects. I'm at a loss on this one, it has ben this way since the 2.6.35 kernels.


Cary

---

### Post by plun on 2010-07-27
Well, I just reinstall the driver...........

```
sudo apt-get install --reinstall nvidia-current
```

Apparently something is broken when this occurs after every kernel update.

DKMS... ?

---

### Post by kyleabaker on 2010-07-27
I just thought of DKMS as well. I think that could be it...

Did your reinstall fix the issue?

EDIT:
I have dkms 2.1.1.2-3fakesync1 installed. Sounds odd.

---

### Post by kyleabaker on 2010-07-27
I just rebooted after the first boot into the new kernel and now the video drivers just aren't working at all, prompting me with the blank screen and driver setup window. None of the options work to configure it, so I'm forced to use the single session option with failsafe drivers to reconfigure everything.

I did a reinstall:
sudo apt-get install --reinstall nvidia-current

Then I configured X via:
sudo nvidia-xconfig

Then I rebooted and tried to configure the window settings:
sudo nvidia-settings

On reboot after configuring these settings, I get a black screen with a NotifyOSD message reading:
"Could not apply the stored configuration for monitors
X server does not support size requested"

The Xorg file is identical to the one that I was using before upgrading the kernel, yet now its telling me there is a resolution problem and I can't fix it...yet it continues to load just fine.

Screenshots to show you what I'm talking about. The first one is the first thing I see for a few seconds..

---

### Post by ronacc on 2010-07-27
just for grins , on the next kernel update remove twinview and drop back to a single screen before reboot and see what happens .

---

