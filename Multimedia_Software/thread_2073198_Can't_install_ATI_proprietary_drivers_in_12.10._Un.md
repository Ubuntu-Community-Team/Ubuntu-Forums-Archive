---
title: "Can't install ATI proprietary drivers in 12.10. Unity is Missing"
date: 2012-10-19
forum: Multimedia Software
---

### Post by THPubs on 2012-10-19
I have a laptop with ATI Radeon 6770M HD Hybrid graphics card. In Ubuntu 12.04, I installed the fglrx driver through "additional drivers" and it worked. (I can even switch GPUs). But in the new Ubuntu 12.10, after installing, Unity won't load.

Only the mouse and the wallpaper. If I initialize the settings sudo aticonfig --initial then after rebooting it gives a warning saying I'm in low graphics mode! How to fix this?

PS : Even tried the drivers from AMD website (both the old 8.* and the new 9.* drivers)

PS 2 : Earlier i used software source to install the drivers. But when using the terminal, I got this warning : 

```
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
```

Full installation log :

> pubudu@lap1:~$ sudo apt-get install fglrx-updates
[sudo] password for pubudu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle-updates
The following NEW packages will be installed:
  fglrx-amdcccle-updates fglrx-updates
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 85.1 MB of archives.
After this operation, 254 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) quantal/restricted fglrx-updates amd64 2:9.000-0ubuntu3 [79.4 MB]
Get:2 [http://lk.archive.ubuntu.com/ubuntu/](http://lk.archive.ubuntu.com/ubuntu/) quantal/restricted fglrx-amdcccle-updates amd64 2:9.000-0ubuntu3 [5,747 kB]
Fetched 85.1 MB in 16min 38s (85.3 kB/s)                                       
Selecting previously unselected package fglrx-updates.
(Reading database ... 159905 files and directories currently installed.)
Unpacking fglrx-updates (from .../fglrx-updates_2%3a9.000-0ubuntu3_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from .../fglrx-amdcccle-updates_2%3a9.000-0ubuntu3_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up fglrx-updates (2:9.000-0ubuntu3) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
Loading new fglrx-updates-9.000 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Building initial module for 3.5.0-17-generic
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-17-generic/updates/dkms/

depmod.......

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:9.000-0ubuntu3) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


---

### Post by michales on 2012-10-19
Hi,

I've had the same problem. Please try this:

```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

sudo rm /etc/X11/xorg.conf

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri


sudo dpkg-reconfigure xserver-xorg

sudo reboot

```

It helps me but unity doesn't work well with default drivers.

Anyone help how to install ATI proprietary drivers in 12.10?

Thanks

---

### Post by Domovoi419 on 2012-10-19
Just had to say I upgraded 12.04 and was greeted to a nice wallpaper and cursor with no unity.


I have AMD 3870K APU with radeon HD 6550 built in. 

SO, I thought that upgrade failed so I installed 12.10 fresh and once it was up and running in software sources on the new tab where they moved the "additional drivers"  it said reboot to activate new drivers and I did and when it came back on I have desktop with mouse but no unity again.


Going back to 12.04 for a while I guess. this is strange.

---

### Post by THPubs on 2012-10-19
Got an error message while trying to install from the terminal "update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken". See the first post for the full installation log.

---

### Post by THPubs on 2012-10-19
Just filed a bug report : [https://bugs.launchpad.net/fglrx/+bug/1068661]("https://bugs.launchpad.net/fglrx/+bug/1068661")

---

### Post by alienfungi on 2012-10-19
I had to install linux-source and linux-headers-generic and then reinstall fglrx.  After that everything worked great.

---

### Post by THPubs on 2012-10-19
> **alienfungi said:**
> I had to install linux-source and linux-headers-generic and then reinstall fglrx.  After that everything worked great.

Did you install fglrx from the Ubuntu repo or used the driver from the AMD(ATI) website?

---

### Post by alienfungi on 2012-10-19
I installed fglrx-updates through synaptic package manager (the Ubuntu repo).  I didn't try the version from amd's site.

---

### Post by THPubs on 2012-10-19
> **alienfungi said:**
> I installed fglrx-updates through synaptic package manager (the Ubuntu repo).  I didn't try the version from amd's site.

I also tried but didn't work :( I faced a similar issue with my PC which have an Nvidia driver. For that, installing the kernel sources fixed the issue.

---

### Post by mwolfe on 2012-10-19
Personally, I had tried to install fglrx-updates by command line and afterwards compiz didn't load so when I logged in I had no unity bar or window borders. Turns out you need linux-headers-generic as well.

This is all you need to do:

```
sudo apt-get install linux-headers-generic fglrx-updates
```


If you've already installed some combination of the driver you can try installing linux-headers-generic and see if that fixes the issue. If not, uninstall everything like this:

```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

```

And then run the command above, reboot, and it should work. Note that I tried restarting lightdm after installing the driver and it didn't work right, I had to do a full reboot for it to work.

---

### Post by RedeyeJedi on 2012-10-19
> **mwolfe said:**
> Personally, I had tried to install fglrx-updates by command line and afterwards compiz didn't load so when I logged in I had no unity bar or window borders. Turns out you need linux-headers-generic as well.

This is all you need to do:

```
sudo apt-get install linux-headers-generic fglrx-updates
```


If you've already installed some combination of the driver you can try installing linux-headers-generic and see if that fixes the issue. If not, uninstall everything like this:

```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

```

And then run the command above, reboot, and it should work. Note that I tried restarting lightdm after installing the driver and it didn't work right, I had to do a full reboot for it to work.

This is what worked for me

Removed previous fglrx failed attempt
```
 sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* 
```

Then installing linux-source (not sure if this step is needed but it's what I did)
```
sudo apt-get install linux-source
```

Then install linux-headers-generic
```
sudo apt-get install linux-headers-generic
```

And finally install fglrx-updates
```
sudo apt-get install fglrx-updates
```

And restart
```
sudo reboot
```

I think you can put all the apt-get commands into one but I like to do separately so can keep an eye on em.

---

### Post by THPubs on 2012-10-20
> **RedeyeJedi said:**
> This is what worked for me

Removed previous fglrx failed attempt
```
 sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* 
```

Then installing linux-source (not sure if this step is needed but it's what I did)
```
sudo apt-get install linux-source
```

Then install linux-headers-generic
```
sudo apt-get install linux-headers-generic
```

And finally install fglrx-updates
```
sudo apt-get install fglrx-updates
```

And restart
```
sudo reboot
```

I think you can put all the apt-get commands into one but I like to do separately so can keep an eye on em.

Tried it... Even with a clean install... But still not working :( Anyway, thanks for the help :)

---

### Post by jesuscash on 2012-10-20
> **THPubs said:**
> Tried it... Even with a clean install... But still not working :( Anyway, thanks for the help :)
I'm having similar problems.
AMD here too.
I did an upgrade from 12.04 and experienced the EXACT same issues,
Got fed up and did a clean install of 12.10
all went well, by that I mean all the window borders were there and unity too
except now I cant activate proprietary drivers. (i really want my wiggly windows. Im assuming the lack of that option in compiz is because of the lack of the proprietary driver lol)
I tried the above commands and now im back to having no window borders or unity. sad is life.

---

### Post by dik23 on 2012-10-20
> **RedeyeJedi said:**
> This is what worked for me

Removed previous fglrx failed attempt
```
 sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* 
```

Then installing linux-source (not sure if this step is needed but it's what I did)
```
sudo apt-get install linux-source
```

Then install linux-headers-generic
```
sudo apt-get install linux-headers-generic
```

And finally install fglrx-updates
```
sudo apt-get install fglrx-updates
```

And restart
```
sudo reboot
```

I think you can put all the apt-get commands into one but I like to do separately so can keep an eye on em.

Yes, this has worked for me too.

It might seem like a crazy suggestion but if fglrx-updates requires linux-headers-generic and linux-source shouldn't they be dependencies and therefore automatically installed when using apt / synaptic / etc ?

---

### Post by Linuxisfast on 2012-10-20
You have to install linux-headers with output from uname -r

---

### Post by THPubs on 2012-10-20
> **Linuxisfast said:**
> You have to install linux-headers with output from uname -r

Yes I installed the right headers

---

### Post by YannB on 2012-10-21
Hi,

It seems that "older" generations of AMD chipsets (2000 to 4000 series) are no longer supported in the latest generation of drivers. If you have such a chipset you will need the legacy FGLRX drivers. Unfortunately the legacy drivers are not compatible with the new Xorg 1.13 which comes with Ubuntu 12.10. So you will need to downgrade to 1.12 of Xorg.

The good news is that someone set up a PPA for this purpose:
[ppa:makson96/fglrx]("https://launchpad.net/~makson96/+archive/fglrx")

You just need to install fglrx-legacy and fglrx-amdcccle-legacy.

More info to be found on [this post]("http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html").

My unity is now working fine

---

### Post by THPubs on 2012-10-21
> **YannB said:**
> Hi,

It seems that "older" generations of AMD chipsets (2000 to 4000 series) are no longer supported in the latest generation of drivers. If you have such a chipset you will need the legacy FGLRX drivers. Unfortunately the legacy drivers are not compatible with the new Xorg 1.13 which comes with Ubuntu 12.10. So you will need to downgrade to 1.12 of Xorg.

The good news is that someone set up a PPA for this purpose:
[ppa:makson96/fglrx]("https://launchpad.net/~makson96/+archive/fglrx")

You just need to install fglrx-legacy and fglrx-amdcccle-legacy.

More info to be found on [this post]("http://www.ubuntuvibes.com/2012/10/how-to-install-amd-catalyst-legacy.html").

My unity is now working fine

I have a 6000 series card :)

---

### Post by jasidog on 2012-10-21
> **dik23 said:**
> Yes, this has worked for me too.

It might seem like a crazy suggestion but if fglrx-updates requires linux-headers-generic and linux-source shouldn't they be dependencies and therefore automatically installed when using apt / synaptic / etc ?

Also worked for me. I'm not sure which part worked for me. I already had the latest headers installed so it was either "linux-source" or the "fglrx-updates" as previously i'd always tried the simpler sounding "fglrx" package after issues with the updates package in 12.04.

Anyway one or the other worked for me using a ATI 5870 on a clean 12.10 install.

It's solved my jet engined gpu fan sound effects and makes general performance seem more fluid.

---

### Post by mjhouska on 2012-10-21
im using ant ati HD3000 chipset on a biostar A780L3G mobo. does that mean i need to downgrade xrg too?

---

### Post by mjhouska on 2012-10-21
i got this[I][B] 
mjhouska@mjhouska-A780L3G:~$ sudo apt-get install fglrx-legacy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fglrx-legacy : Depends: xserver-xorg-core (>= 3:1.12) but 2:1.13.0-0ubuntu6 is to be installed
E: Unable to correct problems, you have held broken package
[/B][/I]

---

### Post by Unclean009 on 2012-10-22
These steps did not work for me. I have a laptop with a 6490M with switchable graphics. It'd be nice to get the proprietary drivers working because with the open source ones I only get roughly 1 hour of battery life...

---

### Post by Noccy on 2012-10-22
> **YannB said:**
> It seems that "older" generations of AMD chipsets (2000 to 4000 series) are no longer supported in the latest generation of drivers. If you have such a chipset you will need the legacy FGLRX drivers. Unfortunately the legacy drivers are not compatible with the new Xorg 1.13 which comes with Ubuntu 12.10. So you will need to downgrade to 1.12 of Xorg.

The good news is that someone set up a PPA for this purpose:
[ppa:makson96/fglrx]("https://launchpad.net/~makson96/+archive/fglrx")

This worked for me, following the instructions in the PPA descriptions. Thank you, you made my laptop usable again after the upgrade :) Was a few days away from re-installing 12.04.

(ATI Mobility Radeon HD4250)

---

### Post by spirosbond on 2012-10-23
> **Noccy said:**
> This worked for me, following the instructions in the PPA descriptions. Thank you, you made my laptop usable again after the upgrade :) Was a few days away from re-installing 12.04.

(ATI Mobility Radeon HD4250)

Well I have an ATI Mobility Radeon HD4650 and installing the fglrx-legacy didn't work for me... The resolution seems fixed but I don't have unity, window borders and the UI is laggy...

Do you know any way to fix this??

I am on linux image 3.5.0.17.19 with the linux image generic installed.

Cheers and thank you all.

EDIT: And btw AMD Catalyst Center works, but still...

---

### Post by Noccy on 2012-10-24
> **spirosbond said:**
> <Well I have an ATI Mobility Radeon HD4650 and installing the fglrx-legacy didn't work for me... The resolution seems fixed but I don't have unity, window borders and the UI is laggy...

Do you know any way to fix this??

Did you downgrade your X per the instructions in the PPA? Sounds like you got the patched kernel driver working (CCC working) but not the X driver (which is incompatible with the version of X shipped).

---

### Post by ayyala on 2012-10-25
Ubuntu 12.10 doesn't support AMD/ATI drivers (called fglrx). If you install them, Unity and xserver won't work!

If using AMD/ATI GPU drivers: Run the following command to remove them, and reboot:

```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

sudo rm /etc/X11/xorg.conf

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg

sudo reboot

```

Wait for AMD or Canonical or a PPA to release an update that sets the things right.Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4 are currently supported. 12.10 uses Kernel version 3.5.

Source: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

---

### Post by spirosbond on 2012-10-26
> **Noccy said:**
> Did you downgrade your X per the instructions in the PPA? Sounds like you got the patched kernel driver working (CCC working) but not the X driver (which is incompatible with the version of X shipped).

I only did that:

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy

how should I check if my X-server has downgraded? The repo here:

[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

does this automatically!?!?!

Cheers


> **ayyala said:**
> Ubuntu 12.10 doesn't support AMD/ATI drivers (called fglrx). If you install them, Unity and xserver won't work!

If using AMD/ATI GPU drivers: Run the following command to remove them, and reboot:

```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

sudo rm /etc/X11/xorg.conf

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg

sudo reboot

```

Wait for AMD or Canonical or a PPA to release an update that sets the things right.Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4 are currently supported. 12.10 uses Kernel version 3.5.

Source: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

Is there any way to use these drivers

[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

with kernel 3.2.0-32 which I have also installed at my 12.10? I tried booting with it but nothing changed.

Is there any other way to have my graphics working? Gnome doesn't work correctly either. I have the AMD Mobility 4650HD Graphics card btw.

Thank you



EDIT:
I did this
```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

sudo rm /etc/X11/xorg.conf

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg

sudo reboot

```

as suggested and I now have working unity and no lag at all. Thank you sir and lovely linux community

Cheers

---

### Post by rtimai on 2012-11-05
RS880M [Mobility Radeon HD 4200 Series]

I clean-reinstalled 12.10 and am running the OSS driver (and yes, cpu a little hotter.) Downgrading X.org and fglrx, and possible the kernel is all too scary for me, as I don't know how it will effect updates and the next ubuntu upgrade. 

All these video driver issues stem from Canonical's decision to transition from X.org to the new Wayland video server:

[https://wiki.ubuntu.com/Wayland](https://wiki.ubuntu.com/Wayland)

Not great news for those trying to hang on and keep older hardware running. I think I remember seeing somewhere that AMD was not planning to continue to support radeon 2xxx-4xxx in their fglrx driver. I may eventually have to switch to a more legacy-friendly distro.

---

### Post by DsXack on 2012-11-09
Solution for me:

1. remove current fglrx
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```
```
sudo apt-get remove --purge fglrx*
```

2. add ppa repository
```
sudo apt-add-repository ppa:andrikos/ppa
```

3. update packages list
```
sudo apt-get update
```

4. install packages
```
sudo apt-get install fglrx-updates
```

---

### Post by spirosbond on 2012-11-10
> **DsXack said:**
> Solution for me:

1. remove current fglrx
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```
```
sudo apt-get remove --purge fglrx*
```

2. add ppa repository
```
sudo apt-add-repository ppa:andrikos/ppa
```

3. update packages list
```
sudo apt-get update
```

4. install packages
```
sudo apt-get install fglrx-updates
```

Which card are you using? What cards does this ppa support?

Thank you

---

### Post by samsom63 on 2012-11-11
> **rtimai said:**
> RS880M [Mobility Radeon HD 4200 Series]

I clean-reinstalled 12.10 and am running the OSS driver (and yes, cpu a little hotter.) Downgrading X.org and fglrx, and possible the kernel is all too scary for me, as I don't know how it will effect updates and the next ubuntu upgrade. 

All these video driver issues stem from Canonical's decision to transition from X.org to the new Wayland video server:

[https://wiki.ubuntu.com/Wayland](https://wiki.ubuntu.com/Wayland)

Not great news for those trying to hang on and keep older hardware running. I think I remember seeing somewhere that AMD was not planning to continue to support radeon 2xxx-4xxx in their fglrx driver. I may eventually have to switch to a more legacy-friendly distro.

I run a compaq presario cq61 with a HD radeon 4200 and the open-source drivers. Occasionally Ubuntu 12.10 will not boot and I have to go to recovery mode. I then thought I should switch to the proprietary drivers, but because the legacy drivers are not supported in ubuntu 12.10, I followed the procedure highlighted above (with ppa:makson96/fglrx-legacy).
 
It did not work at all. The system would hang on a black screen when I tried to boot. The usual trick of setting radeon.modeset=0 would not work. I had to go to recovery mode, drop to root shell, purge the fglrx-legacy package and reinstall xorg to restore a working system.

At least, as a newbie in Ubuntu, this gave me a nice training opportunity!!

---

### Post by spirosbond on 2012-11-11
> **samsom63 said:**
> I run a compaq presario cq61 with a HD radeon 4200 and the open-source drivers. Occasionally Ubuntu 12.10 will not boot and I have to go to recovery mode. I then thought I should switch to the proprietary drivers, but because the legacy drivers are not supported in ubuntu 12.10, I followed the procedure highlighted above (with ppa:makson96/fglrx-legacy).
 
It did not work at all. The system would hang on a black screen when I tried to boot. The usual trick of setting radeon.modeset=0 would not work. I had to go to recovery mode, drop to root shell, purge the fglrx-legacy package and reinstall xorg to restore a working system.

At least, as a newbie in Ubuntu, this gave me a nice training opportunity!!

Sorry about the "newbie" question but, which are the open-source-drivers? I mean... where can I find them? Are they the pre-installed drivers of the Ubuntu distro?

Thank you

---

### Post by samsom63 on 2012-11-11
> **spirosbond said:**
> Sorry about the "newbie" question but, which are the open-source-drivers? I mean... where can I find them? Are they the pre-installed drivers of the Ubuntu distro?

Thank you

Yes, the open-source drivers are pre-installed. If you go to the software centre and select "software sources" and then the "additional drivers" tab, you'll see if there are more recent open-source drivers you can install.

---

### Post by dunkeld on 2012-11-15
I have tried downgrading x but it did not work. So I am using now drivers provided with Ubuntu 12.10 for my Mobility Radeon HD 4200. So far it works, just system tends to crash from time to time.

---

### Post by samsom63 on 2012-11-15
> **dunkeld said:**
> I have tried downgrading x but it did not work. So I am using now drivers provided with Ubuntu 12.10 for my Mobility Radeon HD 4200. So far it works, just system tends to crash from time to time.

Same for me: my system could not boot twice in past two weeks, and also suspend does not work properly.

---

### Post by mace2 on 2012-11-15
I ran into this exact problem on a clean install. 6000-series card.

Tried everything I could find... nothing worked. Reinstalled and am sticking with the open source driver for now. Unfortunately, my HDMI audio out is no longer working because of it.

---

### Post by ZzeCoOl on 2012-11-21
Having a legacy AMD  Card :  HD4890  running ubuntu 12.10 im doomed to use the fglrx-legacy driver with the serious performance loss plus the incompatibility with the recently released STEAM for linux 

But as i was searching for solutions i found that in Windows they managed to add support for the "legacy" cards to the latest driver ( even to the beta 12.11 ) 

Here is the link [http://forums.guru3d.com/showthread.php?t=370452](http://forums.guru3d.com/showthread.php?t=370452)   i hope that someone with the skills and knowledge to do the same for linux.

---

### Post by rtimai on 2012-11-22
The guru3d support is targeted at gamers, e.g. those running non-mission-critical systems. Gamers really are at the cutting edge of video, and are willing to mod their systems with lightly-tested drivers to gain an edge over their opponents in the virtual world.

Not so here! I'm playing it safe and staying with the recommended OSS driver. AMD/ATI may drop future development of fglrx for legacy video, but OSS development might yet continue, to at least to fix bugs (e.g., improve GPU usage to reduce load on the CPU.) 

Meanwhile, there is Ubuntu Community documentation of possible solutions for video issues, below. 

[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Keep in mind that procedures are model-specific. There are links to more specific information near the bottom of the page. The suggestions are not guaranteed to work, but at least they are written clearly and usually explain how to reverse the procedure. Probably worth bookmarking. Good luck to all.

rtimai
RS880M [Mobility Radeon HD 4200 Series]

---

### Post by ZzeCoOl on 2012-11-23
I think you missing the evolution ..

Linux is joining a new era , the era of Gaming. And all this because of the STEAM release and we going to see only advantages with this.

Nvidia allrdy released the version 310 drivers that Doubles the performance on many systems , AMD - ATi is a little back on this but STEAM said that they working together for a new driver to give great performance boost.


I have been waiting for this more than 10 years ! Now i rly hope for Adobe suite ~ peace

---

### Post by Teraspes on 2012-12-27
> **mwolfe said:**
> Personally, I had tried to install fglrx-updates by command line and afterwards compiz didn't load so when I logged in I had no unity bar or window borders. Turns out you need linux-headers-generic as well.

This is all you need to do:

```
sudo apt-get install linux-headers-generic fglrx-updates
```
If you've already installed some combination of the driver you can try installing linux-headers-generic and see if that fixes the issue. If not, uninstall everything like this:

```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

```And then run the command above, reboot, and it should work. Note that I tried restarting lightdm after installing the driver and it didn't work right, I had to do a full reboot for it to work.

Thanks, installing linux-headers-generic solved it for me. However, I installed the regular fglrx package. I'm running Ubuntu 12.10 64 bit with an AMD 6870.

---

### Post by spirosbond on 2013-01-05
For your information, I asked AMD if they plan to release an official update for the 4xxx and lower series, in order to support Ubuntu 12.10. This is the response:

[I]Thank you for contacting AMD!

I understand you are asking if Ubuntu 12.10 will be support for the Radeon HD4xxx Graphics solution.

Unfortunately, there isn&#8217;t any announcement in regards to Ubuntu 12.10 or driver releases. At the moment you will have to regress back to Ubuntu 12.04 or consider getting the Radeon HD5xxx series and above graphics solution.

[...]

Best regards,

AMD Global Customer Care[/I]

---

### Post by thecoolcat on 2013-01-08
In summary, for folks with older ATI cards (2xxx, 3xxx, 4xxx) there are two options:
1) Try Open source:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

sudo rm /etc/X11/xorg.conf

sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg

sudo reboot
```

or

2) Use legacy proprietary drivers:
```
sudo apt-get purge fglrx-amdcccle-legacy fglrx-legacy-dev fglrx-legacy
sudo rm -R /usr/lib/fglrx
sudo rm -R /usr/share/ati

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy
```

As for me, I'm using a motherboard with integrated 3xxx series graphics. I've been using option 2 for about a month and playing youtube or mp4 videos was not particularly smooth. Yesterday I moved to option 1 (open source) and from initially testing, I see that the videos play smoothly.

**Can anyone with experience or knowledge comment on the differences between these two options? For example, some folks on this thread are experiencing that the open source version runs hot and is not so good on performance (sucks battery). Mine is a desktop.**
Thanks!

---

### Post by WSAndrea on 2013-01-08
Hello everyone. I have similar problems with a ATI 6770M on HP dv6-6178sl. I tried to install fglrx and fglrx-updates from Software Sources and Unity disappears. I also tried manual installation of the 12.11 beta package but when I reboot the graphical server won't start at all. What can I do? I can't stick with OS drivers because with them I have poor battery life and the laptop heats a lot.

---

### Post by Ascurion on 2013-01-19
Hello everyone. I am having the same problem as I have a ATI RS880M [Mobility Radeon HD 4200 Series] graphic card on my laptop (Dell M301z) running 12.10. The open source drivers are working ok for me,  Unity, however, is responding relatively slowly and 3d games are very slow. 
I tried to install the  legacy proprietary drivers by using the makson96/fglrx repository as described above, but was left with a black screen after reboot. 

I am running the lowlatency kernel from, 

ppa:abogani/realtime

that is suggested by the  Ubuntu Studio site for low latency recording
[(help.ubuntu.com/community/UbuntuStudioPreparation]("http://help.ubuntu.com/community/UbuntuStudioPreparation")) and I suspect that this might influence the installation of the fglrx drivers. My question is if this is certain or if the  actual kernel used does not matter? If so the repository and downgrading of x.org does not work in my case.

---

### Post by blackangelpr on 2013-01-21
i had a ATI 5XXXX and the driver also have a bug i had filled a report so 12.10 ati driver still giving lots of problems  ... i should stay in 12.04 but was so stable that i get really boring of nothing breaking :) any way i had regret it since i cant play yet steam games ):P

---

### Post by blackangelpr on 2013-01-21
> **blackangelpr said:**
> i had a ATI 5XXXX and the driver also have a bug i had filled a report so 12.10 ati driver still giving lots of problems  ... i should stay in 12.04 but was so stable that i get really boring of nothing breaking :) any way i had regret it since i cant play yet steam games ):P

just read that ati had no plans so far to make a driver for cards lower than 5XXXX on ubuntu 12.10 so they recommend to stay in 12.04 hope this clear some questions...


as well any one had an error with 13 drivers of having a missing .h ?

---

### Post by v4mpiro on 2013-01-22
Legacy drivers 13.1 are out!

[http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip](http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip)

---

### Post by blackangelpr on 2013-01-22
i get this message window:

One or more tools required for installations cannot be found on the system.
Install the required tool before installing the fglrx driver. Optionally, run the 
installer with --force option to instal without the tools.  Forcing install will disable AMD hardware acceleration and may make your system unstable.
Not recommend.
See /usr/share/ati/fglrx-install.log for more details.



And inside that log it says:

Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/$
One or more tools required for installation cannot be found on the system. Inst$
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system$

any clue?

---

### Post by blackangelpr on 2013-01-23
In my case this is what it worked for me :

sudo apt-get install linux-headers-$(uname -r)

then installing the driver 

thanks to Xchat member on ubuntu channel PatrickDickey

---

### Post by bgood86 on 2013-02-04
****If you have a card<5000 use "fglrx-legacy" anything after that, try "fglrx" ****
****"fglrx-update" has posed problems for me.  I run WOW through wine, I have ATI Radeon HD 3400 and it runs very nicely for me. Also have no issues with TV hook up.

****For cards < 5000
sudo apt-get remove --purge xorg-driver-fglrx fglrx fglrx-update
sudo add-apt-repository ppa:makson96/fglrx 
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install fglrx-legacy
sudo aticonfig --initial
sudo shutdown now -rf

---

### Post by bgood86 on 2013-02-04
****for cards >=5000
sudo apt-get remove --purge xorg-driver-fglrx fglrx fglrx-update
sudo apt-get install fglrx
sudo aticonfig --initial
sudo shutdown now -rf

****I also have another notebook just upgraded to 12.10 running ATI Mobility 6620G HD and used this!!!****
All systems are go!

---

### Post by auxilium on 2013-02-07
```


sudo apt-get remove --purge xorg-driver-fglrx fglrx fglrx-update
sudo apt-get install fglrx
sudo aticonfig --initial
sudo shutdown now -rf


```

works for me too.

I had an update yesterday then after reboot I got black screen. I cant get Ctrl Alt F1. What I did was hard reset then press "shift" many times. Then go to the recovery console and access terminal. Use the code bgood86 adviced, system go go go!

---

### Post by dioioib on 2013-03-19
I have been experiencing issues with the driver install too. I am missing unity / gnome desktop but do have dual head (2 monitors displaying)

Does anyone have a resolution that could work for me. 

I tried re-installing xserve-xorg-core and gnome. Using an ATI5700 series card.

Spoke too soon: I corrected the issue using
 
sudo dpkg-reconfigure gdm

restarted then selected GNOME as the desktop environment

everything is working.

---

### Post by auxilium on 2013-03-28
Great!!!

---

### Post by LArchimonde on 2013-04-01
Try this ones, it worked for my ATI Radeon 4850HD. 
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

Hope this helps.

---

### Post by igor-iankovych on 2014-02-16
For all my rigs for some reason only fglrx-experimental-13 works

---

