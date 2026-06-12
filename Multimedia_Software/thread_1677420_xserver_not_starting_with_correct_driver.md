---
title: "xserver not starting with correct driver?"
date: 2011-01-28
forum: Multimedia Software
---

### Post by bjrnfrdnnd on 2011-01-28
Hi, 

I am running ubuntu maverick 10.10 on x86_64.
I have already done what was proposed in  the
"recommended steps for ubuntu 10.10" in 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
and have installed the proposed upgrades.

The recommended way 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

```

proposed in this link just would not work in my case even though installation terminated without errors. For example, no xorg.conf file was created, and
completely wrong horizontal and vertical refresh rates were detected, and the maximum resolution allowed was 800x600, and there was no way ddcprobe would detect the correct rates, so there was no way for me to manually detect the correct refresh rates and correct resolutions.

I therefore had to do it the manual way, downloading the nvidia driver for my graphics card (nvidia quadro fx 570), which turns out to be this one: [http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/260.19.36/NVIDIA-Linux-x86_64-260.19.36.run&lang=us&type=GeForce](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/260.19.36/NVIDIA-Linux-x86_64-260.19.36.run&lang=us&type=GeForce) .

I successfully installed this driver, an xorg.conf file was created, but still the resolution was too low. 
I then followed all the suggestions in this thread:
[http://ubuntuforums.org/showpost.php?p=9211609&postcount=35](http://ubuntuforums.org/showpost.php?p=9211609&postcount=35)

I did not follow the grub modifications though, as I believe (how do I find that out?) that I am using grub2 and I believe that this thread addresses grub and I did not find any vga mode for my resolution 1680x1050.


Anyways, when I start up the machine, it goes straight to the graphical mode, the graphical login seems to be the right resolution, but after logging in, the resolution drops to 800x600.
I go to System->Preferences->Monitors, and a window pops up that
says:
"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?"
I can then just continue by choosing "yes", which open the nvidia settings, where I can choose the correct resolution for my screen, hit apply, and I get my native 1680x1050 resolution with hardware acceleration.

I did also open nvidia settings in su mode,
```
sudo nvidia-settings
```
and I then clicked the  "save to X configuration file" button.

I also checked that the x configuration xorg.conf has been changed (it has, with the resolution 1680x1050 now being present). 

I then restart, but the exact same thing happens again: after login, resolution of 800x600, and I have to change the resolution again running nvidia-settings
or going to System->Preferences->Monitors.

So, my question is, how do I tell ubuntu to continue with the correct settings from the xorg.conf file after login?
It is tedious to change the resolution after each startup.

Thanks for any hints!

---

### Post by BicyclerBoy on 2011-01-28
That recommended ppa X-swat will update your Xorg packages from 1.9 to 2.0.
This is bad & will break the current nvidia drivers.

I would remove the X-swat ppa & reload packages (synaptic).
Re-install Xorg1.9 if necessary.
Install the nvidia drivers from standard ubuntu repos.
Old drivers are fine/better for your video card.

---

### Post by lidex on 2011-01-29
To configure xorg.conf use this command:
```
sudo nvidia-xconfig
``` once your drivers are sorted out.

---

