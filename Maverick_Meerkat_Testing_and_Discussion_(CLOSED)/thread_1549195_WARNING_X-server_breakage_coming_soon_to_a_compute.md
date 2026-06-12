---
title: "WARNING: X-server breakage coming soon to a computer near you"
date: 2010-08-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-08-09
I got this email this morning:

> Summary for the impatient:
********************************************************************
A new X server is soon to be uploaded which requires all the
drivers to be rebuilt.  Be careful when upgrading in the next few
days.
********************************************************************

As promised earlier in the cycle, we've got the second X server
transition coming up.  This will take us to X server 1.9, which features
improvements to startup time, some memory usage improvements, and many
DRI2 fixes.

The 1.9 server has a new input and video ABI which means existing driver
packages will break.

The server needs to be uploaded first so the new drivers build against
the correct ABI, which means that there will be a period where safe
upgrades will have held-back packages.  The dependencies should ensure
that you won't accidentally get a non-working combination of X server
and drivers, but be careful if an upgrade wants to remove X packages.

Happy testing!

I went to do updates and was asked if I wanted to remove the current x-server plus more.

It may be time to use **apptitude safe-upgrade** until the issue is resolved.

---

### Post by kansasnoob on 2010-08-09
I just noticed ATM parsing the "partial upgrade" shows it will actually remove 'ubuntu-desktop' and most, if not all, of 'xorg'.

Hopefully no one accepts the partial :D

---

### Post by psyke83 on 2010-08-09
Thanks for the heads up. Perhaps it would be a good idea to sticky this thread until things calm down?

---

### Post by cariboo on 2010-08-09
Done

---

### Post by VMC on 2010-08-09
My nVidia GeForce 6150 SE fails miserably and I don't have the latest 1.9 xserver that your listing:
Mine:
xserver-xorg = Version1:7.5
xserver-xorg-core = Version 2:1.8.1.902-0ubuntu2

---

### Post by cariboo on 2010-08-09
I have 2 motherboards with 6150se chipsets, the only problem I've run into is to set nomodeset when booting from the Live CD. I have dedicated cards installed now, a 9400GS and a GT210, I do have to run **nvidia-xconfig** on both systems in order to get them to run properly.

---

### Post by andrewabc on 2010-08-09
I just got partial upgrade message, but not sure if related to this. So I guess I just won't update for several days until people say that the new drivers are uploaded. I never do partial upgrade, when I know it is safe and it still says it, I go into synaptic and 'mark all upgrades', then apply changes.

---

### Post by psyke83 on 2010-08-09
> **cariboo907 said:**
> I have 2 motherboards with 6150se chipsets, the only problem I've run into is to set nomodeset when booting from the Live CD. I have dedicated cards installed now, a 9400GS and a GT210, I do have to run **nvidia-xconfig** on both systems in order to get them to run properly.

Do you mean that the "nomodeset" isn't working with the free drivers anymore? At least for ATI cards, the command is no obsolete and you need to use "radeon.modeset=0". I have a feeling that you'll need to do something similar (nouveau.modeset=0).

Hmm, actually... IIRC, the nouveau drivers don't support non-KMS mode anymore. Shame.

---

### Post by linux18 on 2010-08-09
well it will certainly make me pay closer attention to upgrades, but at  least were getting some benefit once its all over, faster X server and  less memory usage.

---

### Post by VMC on 2010-08-09
I tried them all! Reported no valid modes:

F6 then added, one at a time, then added all at once, still the same effect, No X:

nouveau.modeset=0 or 1
nouveau.noaccel=1
nouveau.blacklist=true
xforcevesa

The above hints I got from Bug#539878

var/log/Xorg.0.log, has this to say:

```
[    98.455] (II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): <default monitor>: Using hsync range of 31.50--2011.39 kHz
(II) VESA(0): <default monitor>: Using vrefresh range of 56.00-61.74 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "2048x1536" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(WW) VESA(0): No valid modes left. Trying aggressive sync range...
(II) VESA(0): <default monitor>: Using hsync range of 31.50--2011.39 kHz
 (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-61.74 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "2048x1536" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(EE) VESA(0): No valid modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules/libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules/libvbe.so
[(EE) Screen(s) found, but none have a usable configuration.
 
Fatal server error:
 no screens found

```

I wonder if my monitor has anything to do with it. It will only display 1024x768. Usually when something tries otherwise I get the built in not valid screen display on my monitor. It appears above that it tried 1024x768, but failed.

```
$ lspci|grep VGA
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
```

---

### Post by psyke83 on 2010-08-09
> **VMC said:**
> I tried them all! Reported no valid modes:

F6 then added, one at a time, then added all at once, still the same effect, No X:
<snip>


Yes, I don't think it's a supported option anymore (or ever was... I haven't tested the nouveau driver for a long time).

This should give you the list of supported options:
```
$ modinfo nouveau
```

Also, you should try to remove the boot options "quiet splash" - that may help Xorg to initialize properly, or at least give more clues to the problem.

---

### Post by Starks on 2010-08-09
nomodeset causes the i945GM to boot to a blank screen. KMS works fine.

---

### Post by psyke83 on 2010-08-09
> **Starks said:**
> nomodeset causes the i945GM to boot to a blank screen. KMS works fine.

I think we're getting a bit off-topic (re: Xorg breakage), but you may need to check out the other thread re: Intel drivers to get UMS working (something about re-adding a different UMS codepath... my laptop with Intel graphics died, so I no longer test the Intel driver).

[http://ubuntuforums.org/showthread.php?t=1543787](http://ubuntuforums.org/showthread.php?t=1543787)

If KMS works fine, you have no need to go back to the old architecture anyway :)

---

### Post by cariboo on 2010-08-09
> **psyke83 said:**
> Do you mean that the "nomodeset" isn't working with the free drivers anymore? At least for ATI cards, the command is no obsolete and you need to use "radeon.modeset=0". I have a feeling that you'll need to do something similar (nouveau.modeset=0).

Hmm, actually... IIRC, the nouveau drivers don't support non-KMS mode anymore. Shame.

Strangely enough, it is really intermittent, sometime the Live CD will boot with no intervention, and at other times it will hang at the plymouth screen. I've had problems booting the Live CD with the 6000 series nvidia chipsets going back to 6.06 some times the Live CD will boot and other times it would need either safe graphics mode, or nomodeset. This is with three different systems and two different models of motherboards. The motherboards were all MSI if that makes a difference.

---

### Post by psyke83 on 2010-08-09
> **cariboo907 said:**
> Strangely enough, it is really intermittent, sometime the Live CD will boot with no intervention, and at other times it will hang at the plymouth screen. I've had problems booting the Live CD with the 6000 series nvidia chipsets going back to 6.06 some times the Live CD will boot and other times it would need either safe graphics mode, or nomodeset. This is with three different systems and two different models of motherboards. The motherboards were all MSI if that makes a difference.

I have the same problem when booting from a full installation, with a GeForce 6200 PCI card. Sometimes it hangs at Plymouth, sometimes not. But it always boots when I remove the "splash" boot option.

---

### Post by ranch hand on 2010-08-09
> **psyke83 said:**
> I have the same problem when booting from a full installation, with a GeForce 6200 PCI card. Sometimes it hangs at Plymouth, sometimes not. But it always boots when I remove the "splash" boot option.
I am on ATI here but  I can confirm that removing the "splash" instruction almost always allows you to boot.

On mine, if splash is enabled, the Live CD hangs trying to find several drives (memory card readers).  With out splash enabled it will get past that and boot.

Hitting escape with splash enabled will give you the messages.

Hitting escape with splash not enabled will give you the splash (with the hung up boot that goes with it).

---

### Post by VMC on 2010-08-09
I guess this is the X that's coming soon...```
The following packages have been kept back:
  gbrainy xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-i128 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-nv xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.

```I finally got the latest Maverick installed. A rather circuitous route I had to take. 

First booted singular, then used the *failsafex*, then it booted to livecd. 
Using terminal and type ubiquity, then after getting my location unplug Internet, and finish the questionnaire and wait for a dialog asking about wireless,  all the while ubiquity is still running and installing the system. Wait until it appears stopped, then from wireless dialog click forward. From then on it completes!

I can't wait until the above new X comes my way. Then again, it all may all go without a hitch. :)

---

### Post by andrewabc on 2010-08-10
Checked for updates, includes new xserver, and also includes drivers. No partial upgrade mentioned. So should be 'safe' to update since new xserver and drivers are showing up? Or wait for something else?

I got 93 updates available consisting of 1kb download (actual: 16.6mb) (they havn't fixed that bug yet?)

Also is it a bug that I have to enter password to check for updates, and also to install updates in update manager? I have to enter password twice in a row kinda sucks.

---

### Post by jppr on 2010-08-10
Jeps, new X run without problems, I have Nvidia 9400 Gt card but use nouveau-driver and that works fine too.

---

### Post by RTrev on 2010-08-10
> **andrewabc said:**
> Checked for updates, includes new xserver, and also includes drivers. No partial upgrade mentioned. So should be 'safe' to update since new xserver and drivers are showing up? Or wait for something else?

I tried the update this morning, and nothing works to get it past that final hump in the boot process.  Using an nvidia card and nvidia-current here.

---

### Post by andrewabc on 2010-08-10
I tried updating and got
"Upgrade operation failed", not sure if upgrade was the word used. Had a bunch of text in a window.

And "ubuntu software centre" crashed according to crash report that appeared. Since when do crash reports need password to access?

update manager doesn't have any files listed, so I assume it installed everything. I'm going to backup some stuff in case it fails.

EDIT:
Restarted and works fine for me.

intel atom n270, + i945

---

### Post by tad1073 on 2010-08-10
> **RTrev said:**
> I tried the update this morning, and nothing works to get it past that final hump in the boot process.  Using an nvidia card and nvidia-current here.

same here...ubuntu just stops at plymouth!

I have to boot into recovery mode then failsafe x.org

---

### Post by dino99 on 2010-08-10
even with "quiet splash" removed, no way to boot (nvidia 8500gt)

---

### Post by scradock on 2010-08-10
> **andrewabc said:**
> Checked for updates, includes new xserver, and also includes drivers. No partial upgrade mentioned. So should be 'safe' to update since new xserver and drivers are showing up? Or wait for something else?

I got 93 updates available consisting of 1kb download (actual: 16.6mb) (they havn't fixed that bug yet?)

Also is it a bug that I have to enter password to check for updates, and also to install updates in update manager? I have to enter password twice in a row kinda sucks.

I waited until Update Manager stopped offering a "Partial Update", then upgraded all waiting packages using Synaptic. That included xserver-xorg-core and the drivers.

The first boot worked, but the panel didn't have the shut-down button - had to add one manually!; the second boot hung, but after that it boots fine and everything seems to be working. I use the -video-ati and -video-radeon drivers, so there may still be problems with -nv/-nouveau.

The double password is standard; may be it will be changed before release, but I wouldn't bank on it. Sucks, but not a show-stopper.

---

### Post by plun on 2010-08-10
nVidia-owners....!

I am on the xorg-edgers ppa but its probably the same.

The challenge, from Xorg.0.log

```
[    24.520] (II) LoadModule: "nvidia"
[    24.521] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    24.522] (II) Module nvidia: vendor="NVIDIA Corporation"
[    24.522]     compiled for 4.0.2, module version = 1.0.0
[    24.522]     Module class: X.Org Video Driver
[    24.522] ================ WARNING WARNING WARNING WARNING ================
[    24.547] [B]This server has a video driver ABI version of 8.0 that this
driver does not officially support.  Please check
http://www.nvidia.com/ for driver updates or downgrade to an X
server with a supported driver ABI.[/B]
[    24.642] =================================================================
[    24.667] (EE) NVIDIA: Use the -ignoreABI option to override this check.
[    24.692] (II) UnloadModule: "nvidia"
[    24.692] (II) Unloading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    24.692] (EE) Failed to load module "nvidia" (module requirement mismatch, 0)
[    24.718] (EE) No drivers available.
[    24.745] 
Fatal server error:
[    24.796] no screens found
[    24.822] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    24.919] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    24.966]
```


Adding ignoreABI to xorg.conf solves this.  

```
Section "ServerFlags"
Option "ignoreABI" "True"
EndSection
```


But..... for the moment I must also use the driver downloaded from nVidia, I cannot enable it with the nvidia-current package.

The driver also broke after todays updates, and I must use a really dirty root-shell reinstall of the nvidia driver.

Just start with the ignoreABI nevertheless....;)  and of course on your own risk !!!

---

### Post by jppr on 2010-08-10
Nvidia owners... Why use Nvidia-current when nouveau-driver works fine. As before i said I have Nvidia 9400 Gt but I using nouveau-driver and that works fine without problems. I don´t need and use 3D systems and effects, so why use Nvidia-current driver... ? I have AMD 64 bit system and new X works fine too.

---

### Post by RTrev on 2010-08-10
> **jppr said:**
> Nvidia owners... Why use Nvidia-current when nouveau-driver works fine. As before i said I have Nvidia 9400 Gt but I using nouveau-driver and that works fine without problems. I don´t need and use 3D systems and effects, so why use Nvidia-current driver... ? I have AMD 64 bit system...

I thought it was wonderful that Nouveau worked so well, until I tried watching DVD videos with VLC.  At that point, moving to nvidia-current was, sadly, necessary.

---

### Post by plun on 2010-08-10
> **jppr said:**
> Nvidia owners... Why use Nvidia-current when nouveau-driver works fine. As before i said I have Nvidia 9400 Gt but I using nouveau-driver and that works fine without problems. I don´t need and use 3D systems and effects, so why use Nvidia-current driver... ? I have AMD 64 bit system and new X works fine too.

No Thanks !!!

---

### Post by IanW on 2010-08-10
> **RTrev said:**
> I thought it was wonderful that Nouveau worked so well, until I tried watching DVD videos with VLC.  At that point, moving to nvidia-current was, sadly, necessary.

^ This

---

### Post by amauk on 2010-08-10
> **jppr said:**
> Nvidia owners... Why use Nvidia-current when nouveau-driver works fine. As before i said I have Nvidia 9400 Gt but I using nouveau-driver and that works fine without problems. I don´t need and use 3D systems and effects, so why use Nvidia-current driver... ? I have AMD 64 bit system and new X works fine too.Anything using OpenGL is a no-go with Nouveau
(stock repo version - I know there's a PPA somewhere with 3D accelerated Nouveau, but I've not tried it)

---

### Post by RTrev on 2010-08-10
> **amauk said:**
> Anything using OpenGL is a no-go with Nouveau
(stock repo version - I know there's a PPA somewhere with 3D accelerated Nouveau, but I've not tried it)

Oh, didn't know about that.  Will go do some searching.  Thanks.

BTW, are you really still testing Karmic? :):):)

---

### Post by amauk on 2010-08-10
> **RTrev said:**
> BTW, are you really still testing Karmic?I'm very thorough

---

### Post by BobCFC on 2010-08-10
> **plun said:**
> nVidia-owners....!


Adding ignoreABI to xorg.conf solves this.  

```
Section "ServerFlags"
Option "ignoreABI" "True"
EndSection
```




I can confirm that installing 256.44 from the Nvidia website along with adding "ignoreABI" to xorg.conf fixed it for me using stock maverick (no ppa) 

Thanks **plun** :popcorn:

---

### Post by RTrev on 2010-08-10
> **plun said:**
> Adding ignoreABI to xorg.conf solves this.  


Hmm.  Didn't work with the nvidia-current in the repos.  I dropped back to nouveau (I always have to look up the spelling of that) and am wondering if I want to grab the driver from the nvidia site or wait for a newer one to show up in the repos.  The latter should be fairly soon, I would think, since they must know they just broke it for a lot of us.

Thanks for the tip!

---

### Post by philinux on 2010-08-10
After doing a safe-upgrade using chroot I removed nvidia-current and xorg.conf and it boots up fine.

I then reinstalled nvidia-current and it boots up fine.

---

### Post by plun on 2010-08-10
> **RTrev said:**
> Hmm.  Didn't work with the nvidia-current in the repos.  I dropped back to nouveau (I always have to look up the spelling of that) and am wondering if I want to grab the driver from the nvidia site or wait for a newer one to show up in the repos.  The latter should be fairly soon, I would think, since they must know they just broke it for a lot of us.

Thanks for the tip!

No I don't think it will be fixed until nVidia releases a new driver.

ignoreABI must be used until then.

I am not going to run the Nouveau driver, thats it !

---

### Post by mrbarletta on 2010-08-10
Current nvidia driver on their website is 256.44, do you suggest we open a ticket so they update the nvidia-current package? 

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by autocrosser on 2010-08-10
I play OpenGL games (namely Unreal Tournament 2004) & they will not work without the Nvidia current driver---I wish that nouveau would be good enough for that, but sadly not....

I'm waiting on the drivers to settle out--I could hand install but want to keep a "repo-only" system going--I had figured edgers would have had one by now--pity:(

---

### Post by TDK800 on 2010-08-10
same here, x-server broken after last upgrade... does this solution work for others also?

> 
After doing a safe-upgrade using chroot I removed nvidia-current and xorg.conf and it boots up fine.

I then reinstalled nvidia-current and it boots up fine. 


---

### Post by autocrosser on 2010-08-10
> **philinux said:**
> After doing a safe-upgrade using chroot I removed nvidia-current and xorg.conf and it boots up fine.

I then reinstalled nvidia-current and it boots up fine.

Hmmm--I'm at work right now---You say that the nvidia-current is now working with the new xorg stuff?????

---

### Post by TDK800 on 2010-08-10
> 
I can confirm that installing 256.44 from the Nvidia website along with adding "ignoreABI" to xorg.conf fixed it for me using stock maverick (no ppa)


can you share the command(s) for installing 256.44 from the Nvidia website?

---

### Post by RTrev on 2010-08-10
> **autocrosser said:**
> Hmmm--I'm at work right now---You say that the nvidia-current is now working with the new xorg stuff?????

Not for me.  Can't speak for anyone else.

---

### Post by philinux on 2010-08-10
> **autocrosser said:**
> Hmmm--I'm at work right now---You say that the nvidia-current is now working with the new xorg stuff?????

Yep. Well it is here. nVidia 8600 gt

---

### Post by caryb on 2010-08-10
I tried the ignoreABI & removed the nvidia-current package without luck with ny Nvidia chipset so I removed the xorg.conf & rebooted & now have basic graphics working again:p

Cary

---

### Post by kansasnoob on 2010-08-10
If someone hosed things doing a partial upgrade I have no answer for them, but using the US server I got the "full deal" now and all seems well with my Intel 82945.

This seems to rock! No hiccups at all with video.

---

### Post by cecilpierce on 2010-08-10
I've been fooling with this all day and finally got the 256.44 and 3d effects to work, all though I had to install it twice for some reason !!!
First time it worked fine, rebooted and no X, installed again, rebooted and it went well, go figure.

---

### Post by VastOne on 2010-08-10
> **TDK800 said:**
> can you share the command(s) for installing 256.44 from the Nvidia website?

I am interested in this as well.

---

### Post by autocrosser on 2010-08-10
OK--xorg-edgers fresh-swat PPA just posted a nvidia-current update that recommends all the xorg updates when checked---so I'm on it. Downloads are finished & it's installing---will know in 10 minutes or so if it's a good one.....................

---

### Post by autocrosser on 2010-08-10
Test#1--running a xorg.conf with ignoreABI--true works with the xswat PPA--My SLI setup is up & running....

I'll try without a xorg,conf next.........

---

### Post by autocrosser on 2010-08-10
Test#2--running without a xorg.conf is a dead fail--boots to the nv driver on my system...not very pleasant to work with, but at least it defaults to a GUI :p....

Reset the xorg.conf & all is back to normal--So my xorg looks like:```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "ServerFlags"
        Option "ignoreABI" "true"
EndSection 
``` Good enough for me right now........


NOTE: I'm running x86-64, so I would guess that the regular x86 stuff will work as well--

---

### Post by keypox on 2010-08-10
> **TDK800 said:**
> can you share the command(s) for installing 256.44 from the Nvidia website?

they are on the driver download page labeled readme. 

sudo sh NVIDIA....package name

didnt work for me though maybei should try to install twice?  Running nvidia gtx 260.

---

### Post by VastOne on 2010-08-10
> **autocrosser said:**
> Test#2--running without a xorg.conf is a dead fail--boots to the nv driver on my system...not very pleasant to work with, but at least it defaults to a GUI :p....

Reset the xorg.conf & all is back to normal--So my xorg looks like:```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "ServerFlags"
        Option "ignoreABI" "true"
EndSection 
``` Good enough for me right now........


NOTE: I'm running x86-64, so I would guess that the regular x86 stuff will work as well--

I am running I'm running x86-64 as well and added the ignoreABI and I am running fine now

Server Vendor Version: 1.8.99.905 (10899905)

---

### Post by mrfuzzemz on 2010-08-10
Also working with "ignoreABI" option.
Thanks

---

### Post by keypox on 2010-08-11
> **mrfuzzemz said:**
> Also working with "ignoreABI" option.
Thanks

Working here now too.  

sudo gedit /etc/X11/xorg.conf

[https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=hardy](https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=hardy)

---

### Post by BobCFC on 2010-08-11
> **TDK800 said:**
> can you share the command(s) for installing 256.44 from the Nvidia website?

> **VastOne said:**
> I am interested in this as well.


Download the file such as **NVIDIA-Linux-x86_64-256.44.run** for 64bit

Choose recovery-mode at grub and drop to the command prompt as root (you can't install while X is running)

then run the file as root such as

```
sh Downloads/NVIDIA-Linux-x86_64-256.44.run
```

(Hint: type NV<TAB> for tab completion)

Answer yes to all the questions, except maybe the last one, you might want to keep your old xorg.conf if you made some changes.

Don't worry if it complains about a missing symbolic link or something. It takes maybe 60 secs while it builds.

The only trouble with installing by hand is that you have to redo it every time the kernel version changes, which happens a lot during the alpha/beta period

---

### Post by cariboo on 2010-08-11
Thanks guys, everything works using nvidia-current from xorg-edgers ppa and the xorg.conf posted in this thread. I had to chroot in to my install to make things work.

I've got another install to fix tomorrow. :)

---

### Post by pulpo69 on 2010-08-11
what about ati-card and fglrx? fglrx ?
Don't work till now.
I've only command line(netroot).

---

### Post by jfernyhough on 2010-08-11
> **pulpo69 said:**
> what about ati-card and fglrx? fglrx ?
Don't work till now.
I've only command line(netroot).This has been covered and you have the answer here: [http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872)

---

### Post by sinurge on 2010-08-11
am still getting the following error 

[   496.209]     ABI class: X.Org Server Extension, version 4.0
[   496.209] (II) Loading extension DRI2
[   496.209] (II) LoadModule: "nvidia"
[   496.209] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   496.210] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData
[   496.210] (EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
[   496.210] (II) UnloadModule: "nvidia"
[   496.210] (EE) Failed to load module "nvidia" (loader failed, 7)
[   496.210] (EE) No drivers available.
[   496.210] 
Fatal server error:
[   496.210] no screens found
[   496.210] 

output of my Xorg.conf file 
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nVidia"
    Option    "NoLogo"    "True"
EndSection

Section "ServerFlags"
    Option  "ignoreABI"    "True"
EndSection

---

### Post by cecilpierce on 2010-08-11
you could try Driver "nv" instead of Driver "nVidia"
works for me sometimes till you get the nvidia driver to work right.

---

### Post by ayates on 2010-08-11
> **sinurge said:**
> am still getting the following error 

[   496.209]     ABI class: X.Org Server Extension, version 4.0
[   496.209] (II) Loading extension DRI2
[   496.209] (II) LoadModule: "nvidia"
[   496.209] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[   496.210] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData
[   496.210] (EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
[   496.210] (II) UnloadModule: "nvidia"
[   496.210] (EE) Failed to load module "nvidia" (loader failed, 7)
[   496.210] (EE) No drivers available.
[   496.210] 
Fatal server error:
[   496.210] no screens found
[   496.210] 

output of my Xorg.conf file 
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nVidia"
    Option    "NoLogo"    "True"
EndSection

Section "ServerFlags"
    Option  "ignoreABI"    "True"
EndSection

I'm having the same problem and got bad news from Nvidia.
Check this: [http://www.nvnews.net/vbulletin/showthread.php?t=153963](http://www.nvnews.net/vbulletin/showthread.php?t=153963)

---

### Post by BobCFC on 2010-08-11
I switched from the 256.44 manual version to the stable PPA instead 

This stable PPA just provides the latest drivers whereas the bleeding edge PPA has all sorts of Xorg updates as well.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by TDK800 on 2010-08-11
> 
I switched from the 256.44 manual version to the stable PPA instead

This stable PPA just provides the latest drivers whereas the bleeding edge PPA has all sorts of Xorg updates as well.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)


So is it safe to do the upgrade now, or does the problem still exist?

---

### Post by pulpo69 on 2010-08-11
it seems the updates are all for ndivia-cards.
anybody knows when there will be updates for ati-cards?
since the breakage i can only use the command line in a failsafex boot.

---

### Post by autocrosser on 2010-08-11
> **TDK800 said:**
> So is it safe to do the upgrade now, or does the problem still exist?

Well----you pay your money (time) & take your chances--I went first to "test' if the PPA driver would even work, but this is testing after all....just have a LiveCD or be ready to recovery mode with exactly what you need to do in mind (PPA purge & be ready to run the nv driver to get to a GUI).......Or wait it out until a large number of people have taken the plunge...........

As for me---BRING ON THE BREAKAGE;););)

---

### Post by RTrev on 2010-08-11
Just my personal feeling, but I'd rather not go outside the repositories to get something to fix the problem.  I'd rather test what they give us.  I think it's great that you folks figured out a fix, because it will help the devs to create the actual fix which will be a part of Ubuntu.  But now that we know what will work, I'm inclined to wait and see how the developers want to handle it.

Does that seem reasonable?

---

### Post by TDK800 on 2010-08-11
I was able to fix the breakage with:

"sudo aptitude remove nvidia-current"


Hope this helps others.

---

### Post by autocrosser on 2010-08-11
> **RTrev said:**
> Just my personal feeling, but I'd rather not go outside the repositories to get something to fix the problem.  I'd rather test what they give us.  I think it's great that you folks figured out a fix, because it will help the devs to create the actual fix which will be a part of Ubuntu.  But now that we know what will work, I'm inclined to wait and see how the developers want to handle it.

Does that seem reasonable?

Everyone tests with a certain mindset, so unless your want is a Win7 clone---anything goes:D

I really like being on the edge & that's my poison--To me there is the brainwork of seeing what will "fix" the "problem" & the satisfaction of "victory" when it works--might be a bit of a hack to get there, but--------that's me:guitar:

Being on the razor-edge of stability is a VERY addictive place to be.

---

### Post by jppr on 2010-08-11
> **TDK800 said:**
> I was able to fix the breakage with:

"sudo aptitude remove nvidia-current"


Hope this helps others.

Easiest fix is that run system in Nouveau-driver, I don´t have any problem ;)

---

### Post by autocrosser on 2010-08-11
> **TDK800 said:**
> I was able to fix the breakage with:

"sudo aptitude remove nvidia-current"


Hope this helps others.

Interesting idea, but OpenGL games are a must--so having nvidia-current is a"need"

---

### Post by lidex on 2010-08-11
> **autocrosser said:**
> Test#1--running a xorg.conf with ignoreABI--true works with the xswat PPA--My SLI setup is up & running....

I'll try without a xorg,conf next.........
Just wanted to say thanks. ;)
Nvidia 8800 GTS up and running properly now with nvidia-current. 
I added Xorg-Edgers PPA, upgraded all packages, ran 'sudo nvidia-xconfig' and added this section to resulting xorg.conf:
```

Section "ServerFlags"
Option         "IgnoreABI" "true"
EndSection

```
After a reboot, all is well it seems. This is without 'quiet splash' in grub. I'll try with plymouth next boot.

---

### Post by zenarcher on 2010-08-12
> **lidex said:**
> Just wanted to say thanks. ;)
Nvidia 8800 GTS up and running properly now with nvidia-current. 
I added Xorg-Edgers PPA, upgraded all packages, ran 'sudo nvidia-xconfig' and added this section to resulting xorg.conf:
```

Section "ServerFlags"
Option         "IgnoreABI" "true"
EndSection

```
After a reboot, all is well it seems. This is without 'quiet splash' in grub. I'll try with plymouth next boot.

Thanks so much for this.  Worked for me, exactly per your instructions!

Cheers,
zenarcher

---

### Post by zenarcher on 2010-08-12
Confirmed to work on my second system, as well.

Thanks,
zenarcher

---

### Post by rbind on 2010-08-12
Hi there,

It seems my nvidia legacy driver (nvidia 173.14.27) is unable to catch up with the new xserver (nvidia FX5800: [http://www.nvnews.net/vbulletin/showthread.php?t=153963](http://www.nvnews.net/vbulletin/showthread.php?t=153963)). 

Do you think meerkat will ever allow 3D graphics on this card or should I consider (1) downgrading the xserver (2) downgrading ubuntu? 

I find it frustrating to give up meerkat, but giving the limitations of my hardware (yes, it is a pretty old graphics card), I do not want to wait for a new xserver 1.9 if I will end up having a low-graphics resolution and no compiz goodies...

Cheers

---

### Post by ratcheer on 2010-08-12
Well, I got a much nicer, new video card (see my sig) about a year ago for just $40. So, I would recommend a new card.

Tim

---

### Post by songochain on 2010-08-12
Cpu fan or gpu fan is always running? Anyone with this problem?

BR.

---

### Post by Baul on 2010-08-12
songochain

I think I have the same problem with these nouveau drivers - one thing that I did not ask in last comment - however there is a temp increase.

Before Ubuntu was really good temperature-wise compared to XP (how ever I am enjoying an alpha o/s - so I can't complain too much!).

Yet it is a problem -Nvidia drivers at this point appear cooler in terms of hardware usage - I'm sure that will change as the dev's approach the problem.

I just want to give them so many bugs and crashes as well as part of this process!

Hell it might lead to  a good O/S

---

### Post by ELD on 2010-08-13
Should this be the last major breakage since we are now in feature freeze?

---

### Post by nystire on 2010-08-13
songochain, I have the same problem. Using the OSS radeon drivers. Radeon Mobility 4600 series card in a Toshiba Satellite A500-138 laptop.

---

### Post by jppr on 2010-08-13
[https://launchpad.net/ubuntu/maverick/+source/nvidia-graphics-drivers/256.44-0ubuntu1](https://launchpad.net/ubuntu/maverick/+source/nvidia-graphics-drivers/256.44-0ubuntu1)

---

### Post by plun on 2010-08-13
> **jppr said:**
> [https://launchpad.net/ubuntu/maverick/+source/nvidia-graphics-drivers/256.44-0ubuntu1](https://launchpad.net/ubuntu/maverick/+source/nvidia-graphics-drivers/256.44-0ubuntu1)

> 
nvidia-graphics-drivers (256.44-0ubuntu1) maverick; urgency=low

<snip>

 * This release still doesn't report to be compatible with the
     new xserver ABI [B]but works fine if the ignoreABI option is
     set in xorg.conf.[/B]


[https://lists.ubuntu.com/archives/maverick-changes/2010-August/005672.html](https://lists.ubuntu.com/archives/maverick-changes/2010-August/005672.html)

Thanks for that....

---

### Post by ancleessen4 on 2010-08-13
As per earlier threads added xorg-edgers drivers PPA and added this to xorg.conf;

```
Section "ServerFlags"
Option         "IgnoreABI" "true"
EndSection
```

nvidia driver up and running again :guitar:

---

### Post by songochain on 2010-08-13
> **nystire said:**
> songochain, I have the same problem. Using the OSS radeon drivers. Radeon Mobility 4600 series card in a Toshiba Satellite A500-138 laptop.
So... there's a problem with xorg? I don't want crash my fan because It's always running.
BR.

---

### Post by cariboo on 2010-08-13
Read the first post in this thread.

---

### Post by mc4man on 2010-08-13
The new update to jockey and nvidia-current will allow it to be installed (from hardware drivers) and run.
Will automatically add the ignore line to a xorg.conf - though if you run nvidia-xconfig yourself afterwards then best to ck. the new xorg.conf and edit as needed.

---

### Post by songochain on 2010-08-13
I think I found a problem with powermizer, It always uses maximum performance :(
This [http://ubuntuforums.org/showpost.php?p=9394955&postcount=13](http://ubuntuforums.org/showpost.php?p=9394955&postcount=13) does not work.

BR.

---

### Post by sinurge on 2010-08-14
Sorry guys but still no go for my system. nvidia fx 6200 card. Even with the IgnoreABI option set to true it just wont come up.

am able to get to recovery but if i try startx then it just does not work and falls back to command prompt

---

### Post by woodrobin on 2010-08-14
> **ancleessen4 said:**
> As per earlier threads added xorg-edgers drivers PPA and added this to xorg.conf;

```
Section "ServerFlags"
Option         "IgnoreABI" "true"
EndSection
```nvidia driver up and running again :guitar:

This worked for me as well, both on my laptop running an nVidia 8xxx series, and on my desktop running an nVidia 9xxx series.

---

### Post by jonnybecker on 2010-08-14
Hi,

```
Section "ServerFlags"
Option         "IgnoreABI" "true"
EndSection
```

this didn't work for me with a GeForce FX Go 5300. My system wont come up.

Cheers
Jonny

---

### Post by plun on 2010-08-14
> **jonnybecker said:**
> Hi,

```
Section "ServerFlags"
Option         "IgnoreABI" "true"
EndSection
```

this didn't work for me with a GeForce FX Go 5300. My system wont come up.

Cheers
Jonny

The nvidia-current driver doesn't support older nvidia cards, the 173 driver cannot also not be used.

Use the nouveau-driver.....

---

### Post by sinurge on 2010-08-14
> **plun said:**
> The nvidia-current driver doesn't support older nvidia cards, the 173 driver cannot also not be used.

Use the nouveau-driver.....
What is the the workaround then. Can i keep xorg at 1.8 only so i can use 173... i dont want to fall back on noveau..its works but screen always get positions about 5 mm to the right and does not seem to have a way around that

---

### Post by mc4man on 2010-08-14
> What is the the workaround then. Can i keep xorg at 1.8 
I guess you could - I was hoping to continue to use the 195 on an agp system where I think it's better suited than the 256 drivers.
Ultimately decided that preventing an xserver upgrade was counter productive and will live with the 256 unless 195 becomes comp.

You could take this from the jockey changelog as an indication that possibly 173 will become avail. down the road, 

> 
jockey (0.5.9-0ubuntu2) maverick; urgency=low

  * data/handlers/fglrx.py, nvidia.py:
    - [COLOR="Blue"]Temporarily[/COLOR] disable fglrx, nvidia 96 and 173 and ignore the fact that nvidia
      current claims to be ABI incompatible with the new xserver.

---

### Post by Thomas Garman on 2010-08-15
Yes, I did upgrade to Alpha 3 and it completely destroyed my desktop and all but deleted xorg Xserver whatever.  Now I have nothing but a terminal.

On the "100 paper cuts" philosophy:  if you upgrade to an alpha 3 and it wipes out your desktop then there is no real paper cut sort of issue in play but rather it is like a giant chainsaw ripping your arms off and then the Linux Wizards humping your twitching corpse all weekend long.  Thanks guys.

I was thinking "hey, I will upgrade to Alpha 3 and then let the developers know how the icons look and whether I can use SAMBA and such..."  Ouch.

---

### Post by VastOne on 2010-08-15
> **Thomas Garman said:**
> Yes, I did upgrade to Alpha 3 and it completely destroyed my desktop and all but deleted xorg Xserver whatever.  Now I have nothing but a terminal.

On the "100 paper cuts" philosophy:  if you upgrade to an alpha 3 and it wipes out your desktop then there is no real paper cut sort of issue in play but rather it is like a giant chainsaw ripping your arms off and then the Linux Wizards humping your twitching corpse all weekend long.  Thanks guys.

I was thinking "hey, I will upgrade to Alpha 3 and then let the developers know how the icons look and whether I can use SAMBA and such..."  Ouch.

You did know going in that you were "upgrading" to an ALPHA!right?

Upgrade and Alpha/Beta should not be used in the same sentence on any machine that is used for any purposes other than to be rebuilt, IMHO.  

Meaning that it is expendable.

---

### Post by Thomas Garman on 2010-08-15
well of course it is "expendable" in the sense that I have two other computers and it really doesn't matter if in some vast cosmological sense the computer is basically turned into a brick by the so call ALPHA 3 and rendered useless.

But what is the point of testing at all if the OS does not even start a desktop session?  IS THERE ANYBODY who would be attracted to Ubuntu as an OS who wants to skip using the desktop and just do everything through a terminal or through recovery mode?  What exactly are they expecting people to test?

Yes, the terminal works.  Great job guys.  i think you can just wrap this one up and count it as a PERFECT 10!

Can't wait to see what the Beta release has going for it.

Incidentally I tested the Windows 7 RC for about 9 months before it was released and I can report that the desktop environment worked just fine from day 1.

At the very least, the packages and settings that work perfectly fine from 10.04 ought to continue to work perfectly fine in Alpha 3 or else there is absolutely no forward progress at all in your distribution.

And why release it for testing if there is literally nothing at all to test?

---

### Post by VastOne on 2010-08-15
> **Thomas Garman said:**
> 
And why release it for testing if there is literally nothing at all to test?

To expressly test for breakage just as you are describing. This is why we are here..

You are to be commended for your help in finding problems..


If you really want to help, figure out how to get your BUG info collected and report the BUG.

If you have a nVidia card you may want to read a little of this thread

---

### Post by Thomas Garman on 2010-08-15
I actually did get it into a bug on Launchpad once I got the terminal open then I reported that I cannot get anything with ALT+f2

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/618046](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/618046)

anyway I am not really sure what you guys think ALPHA 3 is for but not having any kind of desktop environment seems to me to be a lot bigger issue than what you would expect from an OS that is supposedly going to ship in less than 8 weeks.  whatever.

---

### Post by VastOne on 2010-08-15
> **Thomas Garman said:**
> I actually did get it into a bug on Launchpad once I got the terminal open then I reported that I cannot get anything with ALT+f2

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/618046](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/618046)

anyway I am not really sure what you guys think ALPHA 3 is for but not having any kind of desktop environment seems to me to be a lot bigger issue than what you would expect from an OS that is supposedly going to ship in less than 8 weeks.  whatever.

great job.

And for the 99.7% of us who are not having these issues on Alpha 3 we are confident in it making the 101010 deadline and ship, and just like every other release, with it's own share of problems.

---

### Post by lidex on 2010-08-15
> **Thomas Garman said:**
> well of course it is "expendable" in the sense that I have two other computers and it really doesn't matter if in some vast cosmological sense the computer is basically turned into a brick by the so call ALPHA 3 and rendered useless.

But what is the point of testing at all if the OS does not even start a desktop session?  IS THERE ANYBODY who would be attracted to Ubuntu as an OS who wants to skip using the desktop and just do everything through a terminal or through recovery mode?  What exactly are they expecting people to test?

Yes, the terminal works.  Great job guys.  i think you can just wrap this one up and count it as a PERFECT 10!

Can't wait to see what the Beta release has going for it.

Incidentally I tested the Windows 7 RC for about 9 months before it was released and I can report that the desktop environment worked just fine from day 1.

At the very least, the packages and settings that work perfectly fine from 10.04 ought to continue to work perfectly fine in Alpha 3 or else there is absolutely no forward progress at all in your distribution.

And why release it for testing if there is literally nothing at all to test?
Did you read the thread title? :wink:
I suspect your "upgrade" path was not ideal. Perhaps you should try wiping it and doing a clean install.

---

### Post by Dekrus on 2010-08-15
Never happened to me. :KS

---

### Post by VastOne on 2010-08-15
> **lidex said:**
> Did you read the thread title? :wink:
I suspect your "upgrade" path was not ideal. Perhaps you should try wiping it and doing a clean install.

Best advice for any approach to an Ubuntu install, especially when you couple it with a separate /home partition.

---

### Post by ranch hand on 2010-08-15
> **VastOne said:**
> You did know going in that you were "upgrading" to an ALPHA!right?

Upgrade and Alpha/Beta should not be used in the same sentence on any machine that is used for any purposes other than to be rebuilt, IMHO.  

Meaning that it is expendable.
I have considered that very concept.  It seems rather silly to call going from a stable OS to an unstable OS an upgrade.

I will admit that it does up your chances of FUN.

---

### Post by ranch hand on 2010-08-15
> **vastone said:**
> best advice for any approach to an ubuntu install, especially when you couple it with a separate /home partition.
+292

---

### Post by Thomas Garman on 2010-08-15
I would be very grateful for any suggestion at all that actually resulted in the desktop reappearing that does not involve merely wiping the HD and restarting.  Sheesh.

---

### Post by ranch hand on 2010-08-15
Well, if you are patient and run update/upgrades every day it will work eventually.  I had one install in 9.10-testing that went 10 days but it is usually much quicker than that.

---

### Post by Thomas Garman on 2010-08-15
and its still broken

---

### Post by ktp on 2010-08-15
> **Thomas Garman said:**
> I want my weekend back, please.  That's about 10 hours down the toilet.  When you call this "free" I would say that it is only free insofar as your time is worthless and the several hundred dollars you spent on the computer you just turned into a brick was play money.

WHY GOOD GOD WHY DID I EVER BOTHER WITH ANY OF THIS!??!!!

Well I don't think you are going to get the weekend back...but thanks for testing alpha software and reporting bugs in it.  Lets hope your experience saves few others from this bug.

Also, just guessing but, I think most of the people using this alpha code get bored if something like this does not happen.  Testing is boring if it just worked.  Good thing there is no such thing as bug free software.

---

### Post by sparker256 on 2010-08-15
> **Thomas Garman said:**
> I tried going to xorg and installing the ppa and doing upgrades all from the terminal but it is just not changing anything at all.  no desktop.  just a terminal.  tried generating my own xorg.conf but it will not actually recognize anything specific about my hardware.  I want my weekend back, please.  That's about 10 hours down the toilet.  When you call this "free" I would say that it is only free insofar as your time is worthless and the several hundred dollars you spent on the computer you just turned into a brick was play money.

WHY GOOD GOD WHY DID I EVER BOTHER WITH ANY OF THIS!??!!!

It is why most of us testing have more than one computer or A multi partition computer so we can boot to something that will work.

Bill

---

### Post by ranch hand on 2010-08-15
> **sparker256 said:**
> It is why most of us testing have more than one computer or A multi partition computer so we can boot to something that will work.

Bill
Oh come on Bill, who ever heard of such a thing.

I only have 10 installs on my test drive.  8 are variations of 10.10 (including Lubuntu) and 2 are stable installs.  Right now all my 10.10 installs are working pretty good.  The minimal install with the Gnome DE is a little slow to really get started but is fine after that.

Zenix 9.10  is the real back up in case all of them go down the tubes.

---

### Post by VastOne on 2010-08-15
> **ranch hand said:**
> Oh come on Bill, who ever heard of such a thing.

I only have 10 installs on my test drive.  8 are variations of 10.10 (including Lubuntu) and 2 are stable installs.  Right now all my 10.10 installs are working pretty good.  The minimal install with the Gnome DE is a little slow to really get started but is fine after that.

Zenix 9.10  is the real back up in case all of them go down the tubes.

Ranch, you are definitely the Legend in testing ... Poor guy cannot get one to install and you have 10 on 1 drive working...

You are my hero..

---

### Post by ranch hand on 2010-08-15
I only have that many because I am so good at screwing them up.  I need the extras to be there to take over.

I do seem to be falling down on the job screwing these up though.  This really has been a pretty calm cycle so far.

---

### Post by autocrosser on 2010-08-15
Recite after me...............BRING ON THE BREAKAGE:D:D:D 

I managed to b0rk up my backup testing install last night---it's been too long from the last time I logged in to it & the overdose of updates made it lie down & choke---guess that I might chroot in & fix it this evening---Shoot---I've been having more "drama" with upgrading my Buffalo router in the last month or so.......I'm running DD-WRT open source firmware on it (beta release of course!!!!!)  Nice to have linux on everything.....:popcorn:

---

### Post by andrewabc on 2010-08-15
> **ranch hand said:**
> This really has been a pretty calm cycle so far.
Yes, calm here as well, but it seems everyday random programs crash and generate crash reports. I don't remember testing other versions and having daily crash reports for different apps. The crashes don't seem to affect regular use, I just notice crash report icon all the time for different apps.

---

### Post by ktp on 2010-08-15
> **autocrosser said:**
> Recite after me...............BRING ON THE BREAKAGE:D:D:D 

I managed to b0rk up my backup testing install last night---it's been too long from the last time I logged in to it & the overdose of updates made it lie down & choke---guess that I might chroot in & fix it this evening---Shoot---I've been having more "drama" with upgrading my Buffalo router in the last month or so.......I'm running DD-WRT open source firmware on it (beta release of course!!!!!)  Nice to have linux on everything.....:popcorn:

off topic, but now i would never buy router which I can't put linux on...at least Buffalo router is going with DD-WRT as default factory firmware on some of their models now.

---

### Post by autocrosser on 2010-08-15
> **ktp said:**
> off topic, but now i would never buy router which I can't put linux on...at least Buffalo router is going with DD-WRT as default factory firmware on some of their models now.

Also OT---Yes--I bought a WZR-HP-G300NH because of the move to open-source firmware ( and 10/100/1000 ports)--but Buffalo was dragging their feet about the package, so I popped in the beta of DD-WRT &----WOW what a difference---all my fighting the router was over--may not install the "official" Buffalo firmware--DD-WRT is lightyears ahead.....


I just chroot'd my backup & "fixed" the xorg b0rk there--took quite a while to fix things--still a bit boring though......mixbox fixes---I do like a real puzzler every once in a while.........

---

### Post by Thomas Garman on 2010-08-16
still nothing

---

### Post by VastOne on 2010-08-16
> **Thomas Garman said:**
> 
update-manager -d

ought to be listed as malicious code since it is basically one of the few commands that will result in an absolutely useless computer under linux... and canonical promotes it everywhere in the forums.

You made a choice, you had a problem, you made another choice.

No one forces anyone here in the choices they make, no control mechanism's in place. 

We wish you better success in your future Alpha testing on any platform and thank you for your time and bug report. 

I really think you should spend more time understanding the stickies that clearly state - expect a brick at any time

---

### Post by autocrosser on 2010-08-16
> **Thomas Garman said:**
> Seriously, I have three computers all are dual dual boot with ubuntu and Vista Ultimate/XP/Windows 7 and the one little netbook I have that I tried the Ubuntu 10.10 Alpha 3 got bricked I mean who cares really tomorrow when I have some time I am going to put fedora 13 on it an walk away from this whole Ubuntu Alpha process but really it's been a laugh and thanks for the memories fellas.

By the way, I never did get a functioning xorg.conf file working so...

update-manager -d

ought to be listed as malicious code since it is basically one of the few commands that will result in an absolutely useless computer under linux... and canonical promotes it everywhere in the forums.


As Vast One said---you were the one that made the choice---almost all of us here UNDERSTAND that we live on a razors edge--and frankly---We like that.

If you can't work your way thru a very simple fix like this one was....well, I wish you luck wherever your feet happen to tread---Alpha-work is not for people that can't be bothered to read/think/look & be a TEAM player.

You need to help to be helped---not squirm as soon as things get the slightest bit hot.

---

### Post by Yumi on 2010-08-16
After sorting out the xorg.conf problem, 10.10 woerks unexpectetly well and fast for a Alpha release. And I like the "feeling" without being able to point to differeces to 10.04

Congratulations. Looking forward to a stable final release.

Michael

---

### Post by Thomas Garman on 2010-08-16
@autocrosser and vastone if you look at the forums you will see I spent about two days follwing detailed directions trying to get this issue fixed and nothing solved the problem AT ALL.

You act like I just just stumbled in and typed update-manager -d and then started complaining.

The only reason I found this sticky is googling for solutions AFTER updat-manager -d bricked the computer.

---

### Post by VastOne on 2010-08-16
> **Thomas Garman said:**
> @autocrosser and vastone if you look at the forums you will see I spent about two days follwing detailed directions trying to get this issue fixed and nothing solved the problem AT ALL.

You act like I just just stumbled in and typed update-manager -d and then started complaining.

The only reason I found this sticky is googling for solutions AFTER updat-manager -d bricked the computer.

Perhaps the lesson learned is to read the stickies before partaking on such a challenging adventure!

---

### Post by MarkieB on 2010-08-16
no longer participating in ubuntuforums.org

---

### Post by VastOne on 2010-08-16
> **MarkieB said:**
> +3

:)

so I'm seeing the new nvidia-current appearing now, are we clear that nvidia-current + xorg 1.9 works for everyone - providing you set xorg.conf to ignore ABI?

chances are I'll try before you write back either way :D

Working great for me...What nVid card are you using? I ask because I know older cards are not working...Anything newer "should: be fine..I Have a Geforce 9600

---

### Post by MarkieB on 2010-08-16
no longer participating in ubuntuforums.org

---

### Post by lonniehenry on 2010-08-16
I have kept updated and am now using nouveau again after trying nvidia-current. Wasn't able to get it to work and got back to nouveau and using Galleum. Everything works fine, except the screen appears to be larger than the laptops screen.  I use 1440x900 and the top panel fits the top of the screen.  The main screen appears to be larger than the physical screen and I have an area of the main screen to the right where I can put the cursor and some of the open windows, but that do not extend to the next desktop.  When I rotate the cube it shows about a screen and a third.  I don't know how to make it show only the screen that I actually see.  The resolution of the screen is 1440x900 and looks correct.

---

### Post by sinurge on 2010-08-16
> **MarkieB said:**
> +3
 
:)
 
so I'm seeing the new nvidia-current appearing now, are we clear that nvidia-current + xorg 1.9 works for everyone - providing you set xorg.conf to ignore ABI?
 
chances are I'll try before you write back either way :D
 
 
[LIST]
[*]Works well with "ignoreABI" if you have a new nvidia card.
[*]If you have an older card (like mine FX 6200) you must put it back to nouveau driver till 173 gets upgraded with the new changes done for 256 (current).
[/LIST] 
Hope this clears, cheers

---

### Post by Sam on 2010-08-16
> **Thomas Garman said:**
> @autocrosser and vastone if you look at the forums you will see I spent about two days follwing detailed directions trying to get this issue fixed and nothing solved the problem AT ALL.

You act like I just just stumbled in and typed update-manager -d and then started complaining.

The only reason I found this sticky is googling for solutions AFTER updat-manager -d bricked the computer.

I won't jump in the "you deserve what you did" sermon, but I have two things to say:

1) If it bricked your computer, you won't even be able to boot to anything.

2) If you cannot run X, try this: in /etc/X11/xorg.conf, Section Device, replace **Driver "whatever"** with **Driver "vesa"**. Then reboot. No hardware acceleration, but you should get a graphical environment.

---

### Post by autocrosser on 2010-08-16
> **Thomas Garman said:**
> @autocrosser and vastone if you look at the forums you will see I spent about two days follwing detailed directions trying to get this issue fixed and nothing solved the problem AT ALL.

You act like I just just stumbled in and typed update-manager -d and then started complaining.

The only reason I found this sticky is googling for solutions AFTER updat-manager -d bricked the computer.

Well--It looks like you should have done more investigation before you "went for the plunge"--You picked one of the worst times for a n00b to jump into a Alpha......And was noted--just using the "vesa" driver would have got you a GUI--what works in the rest of the forums has a 50/50 chance of working in the Alpha environment......

As I was told in college---Prior Planning Promotes Proper Performance......the 5P's

---

### Post by VMC on 2010-08-16
I noticed todays (16th) iso that I "zsync" was huge. the last "zsync" was on the 12th. todays "zync" was only 60% the same and it took about 1-hour to complete. It was worth it though. Ubiquity had some major overhaul.

I have an nVidia integrated chip - GeForce 6150 SE, and haven't looked at the PPA or any other nVidia drivers that everyone's using from this topic.

Once the CD/USB boots up it goes to a blank desktop without panels or anything else. I quick Ctrl+Alt+t gives a terminal. then "sudo ubiquity" starts the install process. It now works to completion and even with internet cable unplugged! Before it was hit and/or miss.

---

### Post by VMC on 2010-08-16
> **cariboo907 said:**
> I have 2 motherboards with 6150se chipsets, the only problem I've run into is to set nomodeset when booting from the Live CD. I have dedicated cards installed now, a 9400GS and a GT210, I do have to run **nvidia-xconfig** on both systems in order to get them to run properly.
Trying  **nvidia-xconfig**, I get command not found.  Did you install this from somewhere? 

edit...
I'm guessing that I need nvidia drivers installed first. :)

Searching the net gave me some indication of that. I was under the impression that you issues the command straight away without installing anything.

---

### Post by Thomas Garman on 2010-08-16
Hi everybody.  Yesterday those of you on this thread witnessed by breakdown and subsequent horrific outburst of frustration as my desktop disappeared and I lost my way.  After a few stern messages later about how I need to solve my own problems and not be such a whiner if I am going to test an Alpha 3 release and...

I completely removed xorg and then rebooted into recovery mode and then did install xserver-xorg and then install ubuntu-desktop and then an aptitude update and...

My desktop is back.  Thanks everyone.

---

### Post by VMC on 2010-08-16
> **Thomas Garman said:**
> Hi everybody.  Yesterday those of you on this thread witnessed by breakdown and subsequent horrific outburst of frustration as my desktop disappeared and I lost my way.  After a few stern messages later about how I need to solve my own problems and not be such a whiner if I am going to test an Alpha 3 release and...

I completely removed xorg and then rebooted into recovery mode and then did install xserver-xorg and then install ubuntu-desktop and then an aptitude update and...

My desktop is back.  Thanks everyone.

I know how you feel. We've all been there before. Having not seen your name on the testing section before, I thought that you just needed to relax and realize that this is testing. Things will break from time to time. That's why were're here.


[LIST]
[*]Ask questions and wait for reply's
[*]File bug reports at the Launchpad site
[*]Try alternate methods
[*]Wait for experience level to kick in
[/LIST]

With todays ISO, things have drastically improved.

---

### Post by VastOne on 2010-08-16
> **Thomas Garman said:**
> Hi everybody.  Yesterday those of you on this thread witnessed by breakdown and subsequent horrific outburst of frustration as my desktop disappeared and I lost my way.  After a few stern messages later about how I need to solve my own problems and not be such a whiner if I am going to test an Alpha 3 release and...

I completely removed xorg and then rebooted into recovery mode and then did install xserver-xorg and then install ubuntu-desktop and then an aptitude update and...

My desktop is back.  Thanks everyone.

Great news and by going through this your knowledge level has increased and more ppl will gain from your experiences.

---

### Post by autocrosser on 2010-08-16
Very Good!!!  Baptism by fire is nice after you are done with it.....As for the rest of it..

We are tucked away in the corner of the forum & every once in a while someone opens the slider & tosses food in for the "nutcases" within.....:p:p

You will learn quite a bit about the underpinnings of linux being here---working with code, working with others in a team-like environment---We snip & spat at each other every once in a while but it's here that the bugs are caught---Most of the long-term nutcases (inmates) know quite a bit about how things work & are more than happy to infect (teach) others...

I normally start as soon as the toolchain is uploaded & ride the wave from the first to the last---It's a fun & interesting time to be had & I really enjoy the hunt.


So a belated welcome to the testing group---We don't bite (much!!!!!);)

---

### Post by ktp on 2010-08-16
> **Thomas Garman said:**
> My desktop is back.  Thanks everyone.

Nicely done!! 

> **autocrosser said:**
> So a belated welcome to the testing group---We don't bite (much!!!!!);)

We don't bite much??  I am going to have to stop doing that then :lolflag:

---

### Post by autocrosser on 2010-08-16
> **ktp said:**
> Nicely done!! 



We don't bite much??  I am going to have to stop doing that then :lolflag:


Now--now--now---don't scare the nice n00b off........

---

### Post by ranch hand on 2010-08-16
> **Thomas Garman said:**
> Hi everybody.  Yesterday those of you on this thread witnessed by breakdown and subsequent horrific outburst of frustration as my desktop disappeared and I lost my way.  After a few stern messages later about how I need to solve my own problems and not be such a whiner if I am going to test an Alpha 3 release and...

I completely removed xorg and then rebooted into recovery mode and then did install xserver-xorg and then install ubuntu-desktop and then an aptitude update and...

My desktop is back.  Thanks everyone.
Please let me add my my welcome too.

I saw no reason to mention this before but now seems right.  You mentioned running a MS "beta" for 9 months.  Think how long the development of that OS went on before that.

Our dev cycle is 6 months, start to finish.  Comparing the 2 is not really possible.  When you consider the relative number of devs it becomes silly.  Most Linux OS' actually do work when released.

Several MS OS' have not been that good when released in spite of being well capitalised and over staffed.  Their PR and sales teams are very good though.

Make sure you fight your way to slider at feeding time.  We may not bite real hard but it can build up if really hungry.

---

### Post by Thomas Garman on 2010-08-17
@autocrosser as you will see from other posts I actually got it all back not that anyone on the forums provided a single useful suggestion by just completely removing xorg and then sudo apt-get xserver-xorg in recovery mode and so on and so forth.

I would like to see any of you do that when for two days straight I asked for suggestions and got zilch other than:

"It's your fault good luck just wipe the hard drive and start over and by the way what does your xorg.conf file say?"

Classy.

---

### Post by cariboo on 2010-08-17
Most of us didn't need to go as far as you did, the solution offered earlier in the thread worked for the majority of us. I would suggest your problem was a special case, as you did an upgrade, whereas most of us here have been using maverick since the toolchain was uploaded, and have probably done at least one complete install since then.

I know speaking for myself, I still have Lucid installed on all three systems I have maverick installed on, just in case. It's part of learning to run a testing version, when I first started running a testing version, I didn't have a fallback install. I paid for that by having an unusable system for several days.

Having a fallback install is also useful when repairing a broken system, you can always chroot the broken system and make repairs, while still being able to reference resources that help to solve the problem.

---

### Post by ranch hand on 2010-08-17
> **cariboo907 said:**
> Most of us didn't need to go as far as you did, the solution offered earlier in the thread worked for the majority of us. I would suggest your problem was a special case, as you did an upgrade, whereas most of us here have been using maverick since the toolchain was uploaded, and have probably done at least one complete install since then.

I know speaking for myself, I still have Lucid installed on all three systems I have maverick installed on, just in case. It's part of learning to run a testing version, when I first started running a testing version, I didn't have a fallback install. I paid for that by having an unusable system for several days.

Having a fallback install is also useful when repairing a broken system, you can always chroot the broken system and make repairs, while still being able to reference resources that help to solve the problem.
Don't forget the very important ability to listen to some tunes to soothe the beast.

---

### Post by autocrosser on 2010-08-17
> **Thomas Garman said:**
> @autocrosser as you will see from other posts I actually got it all back not that anyone on the forums provided a single useful suggestion by just completely removing xorg and then sudo apt-get xserver-xorg in recovery mode and so on and so forth.

I would like to see any of you do that when for two days straight I asked for suggestions and got zilch other than:

"It's your fault good luck just wipe the hard drive and start over and by the way what does your xorg.conf file say?"

Classy.

Well--I only caught the "spew" about hating Ubuntu--I realise that you were just venting (al least now I do), but I'm a old-timer around here & that was starting to sound a bit Troll-ish---which brought out what teeth I do have......I do apologise for taking what you posted a bit too close.....

So--are we square now?

As for the > I would like to see any of you do that when for two days straight I asked for suggestions and got zilch other than: You must realize that most of the people you are talking to here have had something similar to that happen several times in the past---I won't go "back in 2007 we had a xorg update that killed most of the testers computers"---that was real & the older group will remember that January.....but that is just one time in the past 5 years with Ubuntu for me---

I have nuked my systems multiple times over----and fixed them as many times...Back then we didn't have the support that we do now, so that's why the "join the club" talk.....

So take what you will & leave the rest.....I'm done now & will move on.

---

### Post by gnomefreak on 2010-08-17
i see it is trying to load VESA on the last post. if you remove /etc/X11/xorg.conf it should than default into nouveau.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/613458](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/613458)
try that see if it helps

---

### Post by Thomas Garman on 2010-08-17
@autocrosser Yes we are square and that's just how it is when its late at night and this simple little computer task you thought was going to take maybe an hour turns into a couple of late nights googling around various forums.  Sorry about that.
 
As for the next post about how if you delete xorg.conf the system reverts to nouveau...  if so, then it does not result in a useable desktop thats for sure but you can still open nautilus windows.

---

### Post by gnomefreak on 2010-08-17
> **Thomas Garman said:**
> @autocrosser Yes we are square and that's just how it is when its late at night and this simple little computer task you thought was going to take maybe an hour turns into a couple of late nights googling around various forums.  Sorry about that.
 
As for the next post about how if you delete xorg.conf the system reverts to nouveau...  if so, then it does not result in a useable desktop thats for sure but you can still open nautilus windows.

nouveau works fine as long as you do not expect #d accel. It is the default in Lucid and Maverick. it works normal even scales the screen res to a nice size. 

I dont understand what you mean by an unusable desktop.

---

### Post by MarkieB on 2010-08-18
no longer participating in ubuntuforums.org

---

### Post by VinDSL on 2010-08-18
> **MarkieB said:**
> quick update that nvidia-current is good for my card - 7 series [...]Indeed!

Working for me, as well!  :D

```
~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a2)

```Here's my (working) xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 256.35  (buildd@vernadsky)  Tue Jun 29 00:38:43 UTC 2010

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
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "ServerFlags"
    Option    "IgnoreABI"    "True"
EndSection

```I had to add the "ServerFlags" Section, of course.  Otherwise, it boots into CLI......  ;)

---

### Post by VinDSL on 2010-08-18
> **gnomefreak said:**
> nouveau works fine as long as you do not expect #d accel. It is the default in Lucid and Maverick. it works normal even scales the screen res to a nice size.[...]Agreed!

I was quite satisfied with Nouveau.

Here is a snappy from two days ago (Standard Nouveau)...[INDENT][COLOR=Blue][http://vindsl.com/images/conky-10.10.png](http://vindsl.com/images/conky-10.10.png)[/COLOR]
[/INDENT]And, here is a snappy from a few minutes ago (nVidia 256.44 + Compiz)...[INDENT][COLOR=Blue][http://vindsl.com/images/ubu-10.10-nvidia-working.png](http://vindsl.com/images/ubu-10.10-nvidia-working.png)[/COLOR]
[/INDENT]Truthfully, I didn't see a lot of difference between the desktops!

---

### Post by teh603 on 2010-08-18
Speaking of vesa, on boot I'm getting some message about vesa and another driver conflicting and vesa getting removed or something and I think it might be related. I'll try to get a photo or something to post.

Course I'm also getting plymouth and ureadahead kill signal messages, so for all I know it could be normal.

---

### Post by violajack on 2010-08-18
I'm having the same nvidia issues, and I'm not sure what my best options are. I've been using Ubuntu for a long time on various machines, and it's been just working to the point where I've forgotten a lot of the diagnostic and fixy things to do.  

```

$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)

```

Does this mean it's too old for the nvidia-current driver?  I tried installing that package and it still wouldn't start x, even with the ignoreABI flag.  

The hardware drivers manager tells me I have nvidia_96 activated but not currently in use.

Should I wait until this driver is updated?  Should I try the nouveau driver?

I'm currently using the nv driver and I miss my spinny cube :(

---

### Post by VinDSL on 2010-08-18
> **violajack said:**
> I'm having the same nvidia issues, and I'm not sure what my best options are.[...]

The hardware drivers manager tells me I have nvidia_96 activated but not currently in use.

Should I wait until this driver is updated?  Should I try the nouveau driver?[...]I'll tell you what I did.  Maybe it will help.

I downloaded Ubu 10.10 Alpha 3 a week ago.  I'm dual-booting it with Ubu 10.04.

Every day, for 5 days, I did a fresh install of 10.10.  Everything worked fine, until I did an update.  Then, it would NOT go past Plymouth (see all the similar stories above).

Every night, after countless hours of futility, I would wipe the 10.10 partition, and start afresh the next morning.

Finally, I hit the right combination...


[LIST]
[*]I booted into 10.04, purged my entire GRUB2 setup, and reinstalled it.  This probably did nothing, but it made me happy.  :D
[*]I did (yet another) fresh install of 10.10 Alpha 3.  This time, I used the standard Nouveau drivers, instead of proprietary drivers, e.g. I didn't install ANY proprietary drivers via "Hardware Drivers" in the "Administration Menu".
[*]I installed Aptitude-GTK, and did a 'safe-upgrade'.
[/LIST]

Bingo!  My system booted with Linux 2.6.35-15-generic kernel, Gnome 2.31.6, and Nouveau drivers -- my first success!

I've been following this thread.  When I read *gnomefreak's* post (above) I decided to try a full-upgrade, and it worked.  I'm running nVidia 256.44 (current) with success.

As far as the Compiz "spinny cube" is concerned, it's working, but *Simple CompizConfig Setting Manager* crashes, when I try to invoke 'Enable Reflection'.  I just marked the bug as affecting me, in LaunchPad.

Anyway, they're getting there.  They always do...

---

### Post by pania on 2010-08-18
nvidia current 256.44 from normal repositories and GT 230M working fine here.

---

### Post by gnomefreak on 2010-08-20
> **teh603 said:**
> Speaking of vesa, on boot I'm getting some message about vesa and another driver conflicting and vesa getting removed or something and I think it might be related. I'll try to get a photo or something to post.

Course I'm also getting plymouth and ureadahead kill signal messages, so for all I know it could be normal.

its Vesa and Nouveau that you are seeing. and im guessing plymouth isnt loading? If not please confirm/comment on [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/598035](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/598035)

---

### Post by ranch hand on 2010-08-20
> **gnomefreak said:**
> its Vesa and Nouveau that you are seeing. and im guessing plymouth isnt loading? If not please confirm/comment on [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/598035](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/598035)
I am not using Nvidia (ATI) and using OSS drivers.

Your post interests me however as it deals with plymouth.

I read the bug report and thought you would like this bit of information.  One of the reasons, I believe, that plymouth is so funky is the lack of error logging.  Why would this be?

Plymouth is the boot manager, among its other job is the job of logging the process.  When plymouth fails there is no logging.

This is very handy if you want to claim that all faults in plymouth are user created and therefore do not exist.  There were a number of bugs marked invalid for that reason.

 I actually think that after this much time that the Ubuntu devs are actually taking this a little more seriously.  They seem to have gotten their heads around the fact the there may be a problem with the logging.

The problem has been that the thinking was that the only problem was in the graphic end of plymouth (the stuff you see, themes).  The real problem is with plymouth.d which does the real work.

Glad to see that report.  Gives me some hope for a fix for libplymouth2.

---

### Post by Wise Ferret on 2010-08-20
I have an Nvidia 9500m card, and I use nvidia-current drivers.

4 boots out of 5, I'm still getting a frozen plymouth (not even allowing moving to a tty) and the log message:
> This server has a video driver ABI version of 8.0 that this driver does not officially support.  Please check [http://www.nvidia.com/](http://www.nvidia.com/) for driver updates or downgrade to an X server with a supported driver ABI.

My xorg.conf includes the IgnoreABI option, but 80% of the time it doesn't seem to be recognised:
> Section "ServerFlags"
	Option		"IgnoreABI" "True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option  "FlatPanelProperties"  "Scaling = Aspect-Scaled"
	Option "OnDemandVBlankInterrupts" "true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
        Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"

EndSection

Is there any solution (not including moving to the handicapped nouveau)? If not, is there any bug report to join? It's nasty to be afraid to reboot my machine.

---

### Post by ranch hand on 2010-08-20
Welcome to the absolutely most wonderful boot manger in the history of the universe.

---

### Post by plun on 2010-08-20
> **Wise Ferret said:**
> 
Is there any solution (not including moving to the handicapped nouveau)? If not, is there any bug report to join? It's nasty to be afraid to reboot my machine.

Well, I also refuses to use Nouveau...... no way !

Try a driver reinstall:

```
sudo apt-get install --reinstall nvidia-current

```

---

### Post by dino99 on 2010-08-20
> **Wise Ferret said:**
> I have an Nvidia 9500m card, and I use nvidia-current drivers.

4 boots out of 5, I'm still getting a frozen plymouth (not even allowing moving to a tty) and the log message:


My xorg.conf includes the IgnoreABI option, but 80% of the time it doesn't seem to be recognised:


Is there any solution (not including moving to the handicapped nouveau)? If not, is there any bug report to join? It's nasty to be afraid to reboot my machine.

this xorg.conf is so tweaked that i doubt kernel agree with all that stuff: try without xorg.conf, rename this one if you want it later

sudo rm -f /etc/X11/xorg.conf

**** note: watch your logs about "glx" its already included into the kernel, so no need to add such stuff to disturb the boot process

---

### Post by sinurge on 2010-08-20
For some wierd odd reason post reinstalling nvidia current and adding the ignoreABI line to xorg.conf all seems to be well and X finally is working out for me.

Had a messed up X this morning without even any updates caused me to try our setting up nvidia current again.

btw am not sure it counts also updated via update-manager whatever updates it gave me before setting out to install 256 version of the driver.

---

### Post by cariboo on 2010-08-20
I just did a fresh install using nvidia-current from the repositories, I still had to use ignoreABI in order to start x.

---

### Post by ratcheer on 2010-08-20
> **cariboo907 said:**
> I just did a fresh install using nvidia-current from the repositories, I still had to use ignoreABI in order to start x.

Yes, it has not been fixed, yet. nVidia will have to fix their driver to be compatible with the new X server. It may just be a matter of a slight code change to communicate that it is compatible.

Tim

---

### Post by Wise Ferret on 2010-08-20
> **dino99 said:**
> this xorg.conf is so tweaked that i doubt kernel agree with all that stuff: try without xorg.conf, rename this one if you want it later

sudo rm -f /etc/X11/xorg.conf

**** note: watch your logs about "glx" its already included into the kernel, so no need to add such stuff to disturb the boot process

I tried moving the xorg.conf away, and it just booted with no 3d. I ran "sudo nvidia-xconfig", which created a simple nvidia xorg, and rebooted. Same problem: plymouth is stuck and freezes the entire system with it.

The current xorg.conf, created by nvidia-xconfig, is:> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.44  (buildmeister@builder103.nvidia.com)  Thu Jul 29 01:52:55 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Re-installing nvidia-current also didn't help. Any more ideas about how to start debugging this, or even solving it?

---

### Post by ranch hand on 2010-08-20
When you reboot and the menu comes up, hit  e  and edit the menu entry to remove "splash".

Hit Ctrl + x to boot with that edited entry.  This may work.  If it does edit your /etc/default/grub file to remove that "splash" command and then run "sudo update-grub".  The next time you boot it should do so without the "splash".

---

### Post by mc4man on 2010-08-20
If you install nvidia-current with jockey then you should get a simple xorg.conf that will work, just did so
(was using the nvidia site drivers, got tired of having to redo w/kernel updates.

Here's the plain xorg.conf it created - 
> Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option	"IgnoreABI"	"True"
EndSection


Obviously if one uses the previous xorg.conf or nvidia-xconfig then you'll need to add the "ServerFlags" section yourself.
( you may wish to mv your current xorg.conf to xorg.conf_old before using jockey, or the 'long' version - go ahead and return to nouveau, mv xorg.conf, reboot and  then use jockey

---

### Post by VinDSL on 2010-08-20
> **Wise Ferret said:**
> Re-installing nvidia-current also didn't help. Any more ideas about how to start debugging this, or even solving it?I would try this...

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig: version 256.44 (buildmeister@builder103.nvidia.com) Thu Jul 29 01:52:55 PDT 2010

Section "ServerLayout"
Identifier "Layout0"
Screen 0 "Screen0"
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
# generated from default
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
# generated from default
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "Unknown"
HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
EndSubSection
EndSection

######################
##  VERY IMPORTANT  ##
######################

Section "ServerFlags"
Option	"IgnoreABI"	"True"
EndSection


```

---

### Post by Wise Ferret on 2010-08-21
> **ranch hand said:**
> When you reboot and the menu comes up, hit  e  and edit the menu entry to remove "splash".

Hit Ctrl + x to boot with that edited entry.  This may work.  If it does edit your /etc/default/grub file to remove that "splash" command and then run "sudo update-grub".  The next time you boot it should do so without the "splash".

Oh thank you so much!
I found two cases when my driver would load normally. The first was when using recovery mode, choosing root shell, and typing "gdm". The second was removing the splash option from grub.
Now my original xorg.conf is playing happily.

Many thanks for all the other suggestions as well.

---

### Post by VinDSL on 2010-08-21
I noticed that Xorg was updated tonight.

```
$ Xorg -version

X.Org X Server 1.8.99.905 (1.9.0 RC 5)
Release Date: 2010-07-14
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux Zuul 2.6.35-17-generic #23-Ubuntu SMP Fri Aug 20 01:22:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-17-generic root=UUID=1246d3f2-f6ef-4dd9-a7b3-98d06080cda4 ro quiet splash
Build Date: 20 August 2010  09:08:12PM
xorg-server 2:1.8.99.905-1ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```

Initially, I was excited.  But when I rebooted, the display is now (best described as) fuzzy or blurry.

LoL!  I know that isn't a technical description.  It looks like the frequencies are off.

I'm going to go build a new xorg.conf and see if that helps.

---

### Post by dino99 on 2010-08-21
Due to my issues and what i've learn from forums, its better to let the system (lucid/maverick) to deal directly with X.
So, remove/purge xorg.conf as it often bring troubles: dont run proprio xconfig (nvidia/ati).

You might only need to tweak xorg.conf if you use very old hardware (monitor or/and graphic card) or too new ones, and need to insert settings.

---

### Post by ranch hand on 2010-08-21
> **Wise Ferret said:**
> Oh thank you so much!
I found two cases when my driver would load normally. The first was when using recovery mode, choosing root shell, and typing "gdm". The second was removing the splash option from grub.
Now my original xorg.conf is playing happily.

Many thanks for all the other suggestions as well.
Glad that works.   I can't boot 10.04 or 10.10 well with splash enabled.  10.10 is better, for me than 10.04.

You may well find that with out "splash" in there it shuts down about twice as fast too.

---

### Post by grifftel on 2010-08-22
> **BobCFC said:**
> I can confirm that installing 256.44 from the Nvidia website along with adding "ignoreABI" to xorg.conf fixed it for me using stock maverick (no ppa) 

Thanks **plun** :popcorn:
Fixed everything in one go for me, saved me a lot of misery, thank you v.much

---

### Post by Canislupus on 2010-08-22
I took it in the tailpipe on this one.  Fired up my XBMC box / file server for a night of movies with the family, and 6 hours later, they're disappointed and asleep and I'm editing my xorg.conf file on a 65" monitor...  

IgnoreABI didn't work for me.  My comp kept complaining that there was no display configured for the device.  Learned my lesson.  I'm typing this from my fresh 10.04 install.  No more Alpha's for me.

---

### Post by VastOne on 2010-08-22
> **Canislupus said:**
> I took it in the tailpipe on this one.  Fired up my XBMC box / file server for a night of movies with the family, and 6 hours later, they're disappointed and asleep and I'm editing my xorg.conf file on a 65" monitor...  

IgnoreABI didn't work for me.  My comp kept complaining that there was no display configured for the device.  Learned my lesson.  I'm typing this from my fresh 10.04 install.  No more Alpha's for me.

I am really sorry about your pain and the family movie night being lost, but if it is this critical to you, why would you have an alpha running anyway which in itself is almost guaranteed to fail at some point?

---

### Post by ranch hand on 2010-08-22
> **vastone said:**
> i am really sorry about your pain and the family movie night being lost, but if it is this critical to you, why would you have an alpha running anyway which in itself is almost guaranteed to fail at some point?
+3,459

---

### Post by DarkNovaGamer on 2010-08-22
I have an Intel E6750 with a GTX 260.

I have installed Maverick Alpha 3, updated completely, running XOrg 1.9.0 RC5 with nVidia's 256.44 drivers installed.

Adding the IgnoreABI ServerFlags to XOrg.conf allows full 3D effects and booting into Ubuntu (finally) with no issues. Just thought I'd share this information. :)

---

### Post by VMC on 2010-08-23
> **VastOne said:**
> I am really sorry about your pain and the family movie night being lost, but if it is this critical to you, why would you have an alpha running anyway which in itself is almost guaranteed to fail at some point?

My sentiments exactly ! (and now his families)

I see more and more people using the testing distro way before its time,  and on important programs only to have them all fail. It's just to easy to create an extra partition to test with. Leave mission critical programs with production systems.

---

### Post by autocrosser on 2010-08-23
Yes---I use the testing Distro in the HOPES that it will fail.....over half of the fun is fixing what breaks......It gets boring to have it just work (but that means we've done our job---yes?)....And before anyone goes with "well use Debian Sid then----", I test Ubuntu for the betterment of Ubuntu.....

Shoot--I'm using a beta on my router......works MUCH better that the stock firmware.

---

### Post by VinDSL on 2010-08-23
> **VMC said:**
> It's just to easy to create an extra partition to test with. Leave mission critical programs with production systems.Quoted for truth!  ;)

[IMG]http://vindsl.com/images/10.10-gparted.png[/IMG]

---

### Post by ranch hand on 2010-08-23
> **VinDSL said:**
> Quoted for truth!  ;)

[IMG]http://vindsl.com/images/10.10-gparted.png[/IMG]
Wow, brave guy.  Only one partition per OS.

I am way too good at screwing things up for that.

---

### Post by VinDSL on 2010-08-23
> **ranch hand said:**
> Wow, brave guy.  Only one partition per OS.[...]LoL!  Yeah, shared swap and everything.  :D 

I normally run a separate /home, et cetera, but... 

As *autocrosser* implied, failing is half the fun!

---

### Post by MarkieB on 2010-08-23
no longer participating in ubuntuforums.org

---

### Post by MarkieB on 2010-08-23
no longer participating in ubuntuforums.org

---

### Post by VMC on 2010-08-23
> **ranch hand said:**
> Wow, brave guy.  Only one partition per OS.

I am way too good at screwing things up for that.

That's how I've always done it. One partition per OS. If I was running a server maybe I would re-think the situation.

One reason I only use 1-partition for testing is almost on a daily basis I re-install. Another is , I clone and backup files. I've done this enough times to know what to expect.

I've never been convinced that having more than one partition (except swap) is any more safe than just using one partition. I've read all the arguments to the contrary, but if you lose a hard drive, it doesn't matter how many partitions your system has.

---

### Post by ktp on 2010-08-23
> **VinDSL said:**
> As *autocrosser* implied, failing is half the fun!

why else would you use alpha level "code" for? :lolflag:

---

### Post by ToxicBurn on 2010-08-24
> **cariboo907 said:**
> I got this email this morning:



I went to do updates and was asked if I wanted to remove the current x-server plus more.

It may be time to use **apptitude safe-upgrade** until the issue is resolved.


Why does Linux keep Going backwards and breaking drivers with each realease ?

the next feature i want to see in any Distro is to not have broken drivers after every update 

I know this can be done 
If Mac OSX can do it then i know other linux distros can do it.

The Xserver people need to get with it.

this is not moving forward if you ask me

---

### Post by VastOne on 2010-08-24
> **ToxicBurn said:**
> Why does Linux keep Going backwards and breaking drivers with each realease ?

the next feature i want to see in any Distro is to not have broken drivers after every update 

I know this can be done 
If Mac OSX can do it then i know other linux distros can do it.

The Xserver people need to get with it.

this is not moving forward if you ask me

What release? Once again, this is an Alpha for testing.  It's purpose is to make 10-10-10 a stable release.

Those X Server people are just like you and I, with families, jobs, schedules, commitments, and expectations.

On 10-11-10, if you have a complaint, there is process to report bugs for the release.

Prior to that, we all report bugs so those X people (and everyone else working towards the release) will know what is going on to fix it.  

That is the purpose of this process. There are still 7 weeks by my estimation to get it right.

I for one have faith it will be done.

---

### Post by pania on 2010-08-24
> **VastOne said:**
> What release? Once again, this is an Alpha for testing.  It's purpose is to make 10-10-10 a stable release.

Those X Server people are just like you and I, with families, jobs, schedules, commitments, and expectations.

On 10-11-10, if you have a complaint, there is process to report bugs for the release.

Prior to that, we all report bugs so those X people (and everyone else working towards the release) will know what is going on to fix it.  

That is the purpose of this process. There are still 7 weeks by my estimation to get it right.


I for one have faith it will be done.

+1 

I am new to testing and have 10.10 installed on it's own partition and have a number of stable OS' if something goes awry but it doesn't take the experienced tester's long to post ways to fix things anyway. This thread is an example of that.

---

### Post by VMC on 2010-08-24
> **ToxicBurn said:**
> 
I know this can be done 
If Mac OSX can do it then i know other linux distros can do it.

The Xserver people need to get with it.

this is not moving forward if you ask meiMac has one machine to get it right on. Linux has thousands.  Its not just ATI/nVidia/Intel, its how its implemented on those thousands.

---

### Post by VastOne on 2010-08-24
> **VMC said:**
> iMac has one machine to get it right on. 

Which is how I understand the Mac superiors wanted it, to have absolute control over the hardware..

Seems like that would be a very attainable controlled environment to release a cookie cut process, ergo, easy...

---

### Post by autocrosser on 2010-08-24
I was one of the beta-testers for OSX & yes--the hardware is EXTREMELY locked in....I ended up leaving the Mac world when Steve mandated the Intel arch--a very good portion of the ADC left within a week or two when that happened...I figured that I could build a Little-endian unit far cheaper---after all, the biggest reason Mac was better was due to the Big-endian arch (Long live the PowerPC!!!).

After the move there was little to keep me---the way the Linux/BSD clone that was/is Darwin covered all the good stuff & dumbed down the OS....well, you can see why I went to the Jedi Knights!!!!  Down with the Dark-Side!!!!


:lolflag:

---

### Post by teh603 on 2010-08-24
> **VastOne said:**
> Which is how I understand the Mac superiors wanted it, to have absolute control over the hardware..

Seems like that would be a very attainable controlled environment to release a cookie cut process, ergo, easy...Hell, they had it during the licensed clone program. One of the articles in MacWorld of the day was complaining about Apple's requirement that all clone manufacturers buy Apple-specific chips instead of less-expensive off-the-shelf ones. I'm particularly looking at the north bridge controller and floppy controller, both of which had to come directly from Apple.

About the only variation I can remember is a few of the old Power Computing clones that had a PC Parallel port in addition to the normal Mac ones. And that was freaking *needed* because at that time you could only get Mac printers from a few vendors who would tack on another $200 just for reshaping the serial port that was already there to mini-DIN 8 from DB-9.

---

### Post by VinDSL on 2010-08-25
Hope you don't mind me quoting myself...  :D

> **VinDSL said:**
> I noticed that Xorg was updated tonight.

Initially, I was excited.  But when I rebooted, the display is now (best described as) fuzzy or blurry.

LoL!  I know that isn't a technical description.  It looks like the frequencies are off.

I'm going to go build a new xorg.conf and see if that helps.

I don't know what they did, but today's update(s) got rid of all the fuzziness!

The odd thing is, it happened when the openoffice-core was updating.  Everything went white, and Boom!  It was all good again!

---

### Post by VinDSL on 2010-08-25
> **ktp said:**
> why else would you use alpha level "code" for? :lolflag:LoL!  It's like lifting dumbells.  It makes YOU stronger!  ;)

I chose the background (above) in 10.10 because it reminds me of The Valley of Baca (valley of weeping) in psalm 84 -- with Ubu 10.10.10 on the horizon.

Heh!  I'll NEVER give up testing software.  

What else is there?!?!?

---

### Post by MarkieB on 2010-08-25
no longer participating in ubuntuforums.org

---

### Post by VinDSL on 2010-08-25
> **MarkieB said:**
> that's a nice screenlet, Vin, is there an URL?Thanks, Mark!

I'm using Liberation Sans for my (various) fonts in 10.10 Alpha 3.  

The background is called Donau Sunrise.  It comes out of the EU (Austria).  It's from *Tienod* on deviantART.

The easiest way to D/L it is:  [Donau sunrise Wallpaper | Widescreen and high resolution wallpaper by eWallpapers.eu]("http://www.ewallpapers.eu/Nature/Photo-Manipulated/Donau-sunrise.html")

Or, are you talking about my Conky script?!?!?

Basically, it's a custom mix of Conky & ConkyForecast, with added fonts and so forth.

Too much to list here.  I don't want to hijack this thread.

I just wanted to show that X-server is working nicely on my GeForce 7600 GT now...

---

### Post by VastOne on 2010-08-25
> **VinDSL said:**
> 
LoL!  It's like lifting dumbells.  It makes YOU stronger!  ;)

I chose the background (above) in 10.10 because it reminds me of The Valley of Baca (valley of weeping) in psalm 84 -- with Ubu 10.10.10 on the horizon.

Heh!  I'll NEVER give up testing software.  

What else is there?!?!?

Where might I be able to find that background you have on your last post...

And indeed dumb bells is a good analogy in a lot of different ways

---

### Post by VinDSL on 2010-08-25
> **VastOne said:**
> Where might I be able to find that background you have on your last post...

And indeed dumb bells is a good analogy in a lot of different waysHi, *VastOne*.

The link is above, in #193.

The background is available in several different sizes...  ;)

---

### Post by VastOne on 2010-08-25
I just wanted to say and show that mine has never looked this crisp and clean before either...

---

### Post by VastOne on 2010-08-25
> **VinDSL said:**
> Hi, *VastOne*.

The link is above, in #193.

The background is available in several different sizes...  ;)

Thank you very much!

---

### Post by VinDSL on 2010-08-25
> **VastOne said:**
> I just wanted to say and show that mine has never looked this crisp and clean before either...Sweet!

10.10 is on a roll now!

The next thing you know, it will be exciting as brushing your teeth...  :D

---

### Post by teh603 on 2010-08-25
> **VinDSL said:**
> Sweet!

10.10 is on a roll now!

The next thing you know, it will be exciting as brushing your teeth...  :DThat's actually how it is for me. No matter how much normal use I put mine thru, things just won't break so I can bug report them. Then again, that's how it was for most of Lucid's testing phase once they got Plymouth, ureadahead, and all those broken pipes fixed.

---

### Post by jerrylamos on 2010-08-25
> **teh603 said:**
> That's actually how it is for me. No matter how much normal use I put mine thru, things just won't break so I can bug report them. Then again, that's how it was for most of Lucid's testing phase once they got Plymouth, ureadahead, and all those broken pipes fixed.

Maybe for you.  X-server breakage is what I get on ati Mobility 7500, black screens with external monitor (yes there's a launchpad bug, no action), ati Xpress 200 blackscreened with latest update (searching launchpad), int3el i845G sometimes it works sometimes not and never with the "legacy drive fix".

I get around it with various combinations of radeon.modeset=0, dropping back from Alpha 3 to Alpha 2, ...

So I thought O.K., let's try the latest 10.04 updates.  Wrong.  I was better off not updating....

Jerry

---

### Post by ranch hand on 2010-08-25
And plymouth is not fixed.

---

### Post by RTrev on 2010-08-25
> **ranch hand said:**
> And plymouth is not fixed.

Funny, I booted up something the other day, can't remember what it was, but on the screen appeared some plain text: "Booting, please wait."

Nothing ever looked so clean and professional, compared to what we've all been watching on every boot. :p

---

### Post by ktp on 2010-08-25
> **autocrosser said:**
> ---after all, the biggest reason Mac was better was due to the Big-endian arch (Long live the PowerPC!!!).

PowerPC that's where the Power is. =)

---

### Post by ktp on 2010-08-25
> **VinDSL said:**
> LoL!  It's like lifting dumbells.  It makes YOU stronger!  ;)

I chose the background (above) in 10.10 because it reminds me of The Valley of Baca (valley of weeping) in psalm 84 -- with Ubu 10.10.10 on the horizon.

Heh!  I'll NEVER give up testing software.  

What else is there?!?!?

The background speaks well...nicely done.

---

### Post by ktp on 2010-08-25
> **RTrev said:**
> Funny, I booted up something the other day, can't remember what it was, but on the screen appeared some plain text: "Booting, please wait."

Nothing ever looked so clean and professional, compared to what we've all been watching on every boot. :p

I would welcome seeing "Booting, please wait..." specially when it only takes about 10-15 seconds to boot.

---

### Post by aviramof on 2010-08-26
Ati just released ati Proprietary Display Driver 10.8 does it support xserver 1.8/1.9?
 
Thanks in advance.

---

### Post by MarkieB on 2010-08-26
no longer participating in ubuntuforums.org

---

### Post by aviramof on 2010-08-26
I tried the new fglrx from the x-swat ppa and it didn't worked so why is it not working now?

Thanks in advance.

---

### Post by VinDSL on 2010-08-26
> **ktp said:**
> The background speaks well...nicely done.Thanks!

I got the Compiz Fusion Extras working tonight.  :D

I *think* they've aced the X-server problems!

---

### Post by teh603 on 2010-08-26
> **ranch hand said:**
> And plymouth is not fixed.Well, fixed as we're going to get what with it being made a hard dependency for just about everything and mountall being changed to pretty much kill the boot process if its removed...

---

### Post by Claus7 on 2010-08-26
Hello,

> **violajack said:**
> I'm having the same nvidia issues, and I'm not sure what my best options are. I've been using Ubuntu for a long time on various machines, and it's been just working to the point where I've forgotten a lot of the diagnostic and fixy things to do.  

```

$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)

```

Does this mean it's too old for the nvidia-current driver?  I tried installing that package and it still wouldn't start x, even with the ignoreABI flag.  

The hardware drivers manager tells me I have nvidia_96 activated but not currently in use.

Should I wait until this driver is updated?  Should I try the nouveau driver?

I'm currently using the nv driver and I miss my spinny cube :(

just to fill in with my experience:

just upgraded from lucid a couple of hours ago, facing the same problems as stated in this thread, concerning the graphics environment.

I removed xorg.conf file, deactivated the nvidia driver via System-> Administration->Additional Drivers 

and I was able to boot without having to enter recovery mode and then logging in in low graphics mode.

Not the best resolution at the moment, yet it is working. Vesa, nouveau, nvidia-xconfig, nvidia-current, abi...

...seems to become more and more complicated the configuration of the graphics set up from version to version trying to find out the best combination. If it is just because of an alpha release, then it is ok with me.

Regards!

---

### Post by VinDSL on 2010-08-26
> **Claus7 said:**
> ...seems to become more and more complicated the configuration of the graphics set up from version to version trying to find out the best combination.[...]Normally, I leave the nVidia settings alone, but I had to crank up the DVC (Digital Vibrance Control) on 10.10 Alpha 3.

Definitely made a difference on my GeForce 7600 GT...  ;)

---

### Post by joecomstock on 2010-08-27
well so far nothing in the thread has helped me in particular, feel loathe to downgrade the xorg from 1.9.  Does anyone know a timetable for a fix of the nvidia driver?  It did not seem on the nvidia linux forums that they were going to release one soon.  Hopefully the problem will be fixed by the time of the beta freeze.

---

### Post by cariboo on 2010-08-27
Did you try the same xorg.conf file as autocrosser posted [here]("http://ubuntuforums.org/showpost.php?p=9704924&postcount=50"), he's running SLI too.

---

### Post by TunaCanTommy on 2010-08-28
I'm running a nVidia GeForce 6200, an older card. I got it running with the nVidia drivers by:
1. Disable the "splash" in grub.cfg - see post #162
2. Edit xorg.conf to add "IgnoreABI" "true" - see post #163
3. Reinstalled the nvidia-current driver - see post # 156
Solid as a rock so far . . .

---

### Post by IanW on 2010-08-29
New driver released, supporting xorg-server 1.9:-

[quote=NVNews.net]256.52 (prerelease) for Linux x86/x86_64 released

    * Fixed a bug that prevented XvMC from initializing in most cases.
    * Added support for xorg-server video driver ABI version 8, which will be included in the xorg-server-1.9 series of releases.
    * Fixed a bug that caused extremely slow rendering of OpenGL applications on X screens other than screen 0 when using a compositing manager.
    * Fixed a regression introduced after 256.35 that caused stability problems on GPUs such as GeForce GT 240.
    * Fixed a slow kernel virtual address space leak observed when starting and stopping OpenGL, CUDA, or VDPAU applications.
    * Fixed a bug that left the system susceptible to hangs when running two or more VDPAU applications simultaneously.

The 256.52 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86 is available for download via [[COLOR="Blue"]FTP[/COLOR]](ftp://download.nvidia.com/XFree86/Linux-x86/256.52/).
The 256.52 NVIDIA Accelerated Linux Graphics Driver Set for Linux/x86_64 is available for download via [[COLOR="Blue"]FTP[/COLOR]](ftp://download.nvidia.com/XFree86/Linux-x86_64/256.52/).

Please see the README ([[COLOR="Blue"]x86[/COLOR]](ftp://download.nvidia.com/XFree86/Linux-x86/256.52/README/index.html) / [[COLOR="Blue"]x86_64[/COLOR]](ftp://download.nvidia.com/XFree86/Linux-x86_64/256.52/README/index.html)) for more information about this release.

Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported
through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

Please also note: If you encounter any problems with the 256.52 NVIDIA Linux graphics driver release, please start a new thread and include a detailed
description of the problem, reproduction steps and generate/attach an [COLOR="Red"]nvidia-bug-report.log.gz[/COLOR] file (please see [[COLOR="Blue"]http://www.nvnews.net/vbulletin/showthread.php?t=46678[/COLOR]](http://www.nvnews.net/vbulletin/showthread.php?t=46678) for details).[/quote]

---

### Post by VinDSL on 2010-08-29
> **IanW said:**
> New driver released, supporting xorg-server 1.9:-LoL!  I KNEW this was going to be a mistake, but...

It worked out quite nicely!  Thanks!

---

### Post by donniezazen on 2010-08-29
Can anybody confirm if it is safe to upgrade? Last time i upgraded it broke my xorg and had to reinstall the whole system (on top of that startup disk creator and ISO have been acting funny).

Thanks.

PS:-I am using Dell E1505/6400.

---

### Post by VastOne on 2010-08-29
> **soham_1207 said:**
> Can anybody confirm if it is safe to upgrade? Last time i upgraded it broke my xorg and had to reinstall the whole system (on top of that startup disk creator and ISO have been acting funny).

Thanks.

PS:-I am using Dell E1505/6400.

No.  Alpha testing implies things are unstable and breakage is very possible. 

It is the risk of living and testing the edge..

The best thing you could do is to have a destructible test environment.

---

### Post by donniezazen on 2010-08-29
> **VastOne said:**
> No.  Alpha testing implies things are unstable and breakage is very possible. 

It is the risk of living and testing the edge..

The best thing you could do is to have a destructible test environment.

I understand the philosophy of alpha testing. With all due respect, it does not mean to intentionally break your system, I would rather wait a little for the known issues to be fixed. Thanks.

---

### Post by VastOne on 2010-08-29
> **soham_1207 said:**
> I understand the philosophy of alpha testing. With all due respect, it does not mean to intentionally break your system, I would rather wait a little for the known issues to be fixed. Thanks.

With all due respect, if it borked your system one time, and if your system is at all important to you, I would most definitely wait.

Did you ever find out what happened when it broke before?

---

### Post by youoh on 2010-08-29
removed the IgnoreABI Section with the new Driver and working like a charm.

---

### Post by VastOne on 2010-08-29
Has anyone gotten X 1.9.0 working on Lucid or is that strictly down the Maverick pipe?

---

### Post by VinDSL on 2010-08-29
> **soham_1207 said:**
> Can anybody confirm if it is safe to upgrade?[...]I cannot...

For instance:  I did a routine update 2 days ago, and it broke my custom theme -- both on the desktop, and in Plymouth.  Took 24 hours to fix it.  LoL!

I suppose it depends on the meaning of 'safe', but to my way of thinking, updating/upgrading 10.10 Alpha 3 is like tip-toeing through a minefield!

> **soham_1207 said:**
> [...]I would rather wait a little for the known issues to be fixed.I think that would be prudent -- wait for the Beta or RC.

You won't have to wait much longer... ;)

[LIST]
[*]Alpha 1 - June 3rd, 2010

[*]Alpha 2 - July 1st, 2010

[*]Alpha 3 - August 5th, 2010

[*]Beta - September 2nd, 2010

[*]Release Candidate - September 30th, 2010

[*]Final Release - SUNDAY - October, 10, 2010
[/LIST]

---

### Post by ranch hand on 2010-08-29
You guys are no fun at all.  Just upgrade the thing.  It is testing.  it is supposed to break.

Have FUN.  File some bugs.

---

### Post by VinDSL on 2010-08-29
> **youoh said:**
> removed the IgnoreABI Section with the new Driver and working like a charm.Works on my GeForce 7600 GT too.

Here's my current *xorg.conf*...

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.52  (buildmeister@builder103.nvidia.com)  Wed Aug 25 15:05:51 PDT 2010

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
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

I've also got the DVC in my nVidia X Server Settings boosted to 7.0 and it's never looked better!  :cool:

---

### Post by VinDSL on 2010-08-29
> **ranch hand said:**
> You guys are no fun at all.  Just upgrade the thing.  It is testing.  it is supposed to break.

Have FUN.  File some bugs.LoL!

My conkyForecast broke, after I removed the IgnoreABI Section in *xorg.conf*.

Does that count?!?!?!?  :D

---

### Post by ktp on 2010-08-29
> **VinDSL said:**
> LoL!

My conkyForecast broke, after I removed the IgnoreABI Section in *xorg.conf*.

Does that count?!?!?!?  :D

bug is bug...they all count =)

---

### Post by VinDSL on 2010-08-29
> **ktp said:**
> bug is bug...they all count =)Heh!

Well, I guess we're having FUN then...  :popcorn:

**EDIT**

Drat!  conkyForecast magically started working, on the last refresh...

Must have been a problem with the *weather.com* data feed.

LoL!  The Weather Channel is no FUN either!

This does bring up a quantum thought...

In the above case, to whom would one report the bug?!?!?

The leg bone's connected to the hip bone, you know?  ;)

Applying systemic rules, like "file some bugs", sounds great but, for whom does the bug toll?

In the end, I would judge, it tolls for thee...

---

### Post by zenarcher on 2010-08-29
I also removed the IgnoreABI section after the Nvidia driver update and all is working well here, too.  

Cheers,
zenarcher

---

### Post by cariboo on 2010-08-29
I can confirm that commenting out the ignoreABI section causes zero problems.

---

### Post by ratcheer on 2010-08-29
> **cariboo907 said:**
> I can confirm that commenting out the ignoreABI section causes zero problems.

What is the "comment" character for this file? Semicolon, pound sign, or something else?

Thanks,
Tim

---

### Post by freeball1 on 2010-08-29
> **ratcheer said:**
> What is the "comment" character for this file? Semicolon, pound sign, or something else?

Thanks,
Tim

pound sign is correct

---

### Post by ranch hand on 2010-08-29
#

---

### Post by ratcheer on 2010-08-29
> **freeball1 said:**
> pound sign is correct

Yes, thanks.

This was kind of weird, though. A week or so ago, when I added the IgnoreABI section, I had backed up the file before making the changes. Today, the backup file I had created was still there, but it only had 216 characters. The original had been over 1500 characters and I had verified that the real file and my backup were identical except for the IgnoreABI section after I made the change. Between then and now, something had totally messed up my backup file, and it was not I.

Anyway, I am back in business with the IgnogeABI section commented out.

Tim

---

### Post by VinDSL on 2010-08-29
For those of you that don't enjoy playing with RUN files...

256.52 is now available in the x-swat PPA via UM.  ;)

**EDIT**

N/M 

I just installed 256.52 in Lucid, and had to run the shell script from a console, just like usual.

It's the thought that counts, right?  :)

---

### Post by kentechy on 2010-08-29
I decided to upgrade my spare drive from 10.04 to 10.10 alpha.  After doing so the boot only goes to a prompt with not gnome desktop opening.  Any suggestions out there as to how to proceed?  Thanks.

---

### Post by VinDSL on 2010-08-29
> **VastOne said:**
> Has anyone gotten X 1.9.0 working on Lucid or is that strictly down the Maverick pipe?Not sure *exactly* what you're asking, but...

I just installed 256.52 on Ubu 10.04.  Works fine!  ;)

Poor Lucid!  This is the first time I booted into in 8 days.

---

### Post by lidex on 2010-08-29
I already like maverick more than lucid.
I purged x-swat and reverted to maverick xorg. 
Ran nvidia-xconfig to replace xorg.conf with new version (with no ignore abi) and all seems to be well with nvidia-current on GeForce 8800 GTS. Nice.

---

### Post by howefield on 2010-08-30
Post in the Maverick forum.

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

Can you login at your prompt ?

---

### Post by Sef on 2010-08-30
Moved to Maverick forum.

---

### Post by zacbarton on 2010-08-30
Is anyone else noticing that scrolling of large windows of text (terminal, firefox, gedit etc) results in high xorg cpu usage, it definitely seems worse than in lucid. I'm using the nvidia 256.44 (tried .52 also) drivers and the ambiance theme (tho any theme is the same).

GtkPerf 0.40

GtkEntry - time:  0.05
GtkComboBox - time:  0.86
GtkComboBoxEntry - time:  0.68
GtkSpinButton - time:  0.14
GtkProgressBar - time:  0.25
GtkToggleButton - time:  0.29
GtkCheckButton - time:  0.13
GtkRadioButton - time:  0.33
GtkTextView - Add text - time:  **3.36**
GtkTextView - Scroll - time:  **2.86**
GtkDrawingArea - Lines - time:  0.50
GtkDrawingArea - Circles - time:  0.58
GtkDrawingArea - Text - time: **11.59**
GtkDrawingArea - Pixbufs - time:  0.61

The 2 text tests peg my cpu to 100% and go so slow I can see the text being drawn.

---

### Post by VinDSL on 2010-08-30
I'm currently listening to streaming audio in Firefox and browsing in Google Chrome.

For comparison, here are my results:

GtkPerf 0.40 - Starting testing: Mon Aug 30 02:02:55 2010

GtkEntry - time:  0.06
GtkComboBox - time:  2.32
GtkComboBoxEntry - time:  1.79
GtkSpinButton - time:  0.42
GtkProgressBar - time:  0.64
GtkToggleButton - time:  0.54
GtkCheckButton - time:  0.20
GtkRadioButton - time:  0.28
GtkTextView - Add text - time:  1.32
GtkTextView - Scroll - time:  1.84
GtkDrawingArea - Lines - time:  1.65
GtkDrawingArea - Circles - time:  1.84
GtkDrawingArea - Text - time:  4.34
GtkDrawingArea - Pixbufs - time:  0.30
 --- 
Total time: 17.56

**EDIT**

To answer your question directly, no, I haven't noticed any slowness, or excessive CPU usage, except in Firefox -- which is why I don't use it for anything but Internet Radio.  But, this has been an ongoing issue for me, for the past few months.  It seems that Fx gets slower and more resource intensive with every release.

Overall, I am very pleased with the performance of Maverick...

I ran the test(s) several times, and took a snappy at the highest point of CPU usage.

Basically, the CPU usage ratchets up a little at a time, while the tests are running, and peaks during the final test(s).  However, it never pegs my meter in Conky (visible on right-side of desktop).

Check out the Top Processes too.  LoL!  Fx is using almost as many resources as xorg & compiz combined...  :)

---

### Post by dinamic1 on 2010-08-30
(Nvidia 7600 GS)
[http://i.imgur.com/ngnA7.png](http://i.imgur.com/ngnA7.png)

---

### Post by ranch hand on 2010-08-30
> **howefield said:**
> Post in the Maverick forum.

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

Can you login at your prompt ?
This is the question that needs answered first.

---

### Post by oasick on 2010-08-30
My graphic card is still not working :( . I have this card:

01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce FX 5900XT] (rev a1)

the worst thing is that since yesterday after attempting to install the driver manually I see everything with a very low resolution...:confused:

________________________________________________________________________________________________________________________________________________

I've fixed the resolution. I did it this way:

sudo rm /etc/modprobe.d/nvidia-installer-disable-nouveau.conf

But still I have no graphics acceleration ...

---

### Post by cariboo on 2010-08-30
Did you run:

```
sudo nvidia-xconfig
```

Then reboot, also nvidia-current only supports the 6 series and newer. I did see something somewhere that Alberto was working on new drivers for older video cards, but I don't know if he's done yet.

---

### Post by DeadlyWolf on 2010-08-30
> **VastOne said:**
> Has anyone gotten X 1.9.0 working on Lucid or is that strictly down the Maverick pipe?

Came today as an update from Ubuntu-x-swat for Lucid. (256.52 if that is what you are referring to)

---

### Post by VinDSL on 2010-08-31
> **DeadlyWolf said:**
> Came today as an update from Ubuntu-x-swat for Lucid.[...]Correctamundo!

Huge Inline Image: [http://vindsl.com/images/correctamundo.png](http://vindsl.com/images/correctamundo.png)  (HD / Visitors)

---

### Post by kentechy on 2010-08-31
> **ranch hand said:**
> This is the question that needs answered first.


Yes, I can login to the command line prompt

---

### Post by ranch hand on 2010-08-31
This is a good thing.  In that case you should get a prompt after you sign in.

Type   startx

This should take you to the desktop.  Run all update/upgrades.  Reboot and see if it has improved.

---

### Post by Yumi on 2010-09-01
Updated and new Headers 2.6.35-19 do not go to the graphical login, 2.6.35-15 boots normally.

Do I have that xorg.conf modification "ServerFlags ABI .... something" out again?

Michael

---

### Post by VastOne on 2010-09-01
> **Yumi said:**
> Updated and new Headers 2.6.35-19 do not go to the graphical login, 2.6.35-15 boots normally.

Do I have that xorg.conf modification "ServerFlags ABI .... something" out again?

Michael

Yes. That is what I had to do.

---

### Post by VastOne on 2010-09-01
> **VinDSL said:**
> Correctamundo!

Huge Inline Image: [http://vindsl.com/images/correctamundo.png](http://vindsl.com/images/correctamundo.png)  (HD / Visitors)

I might have to switch over to x-swat as I still have not received it from edgers.

---

### Post by Yumi on 2010-09-01
Edited xorg.conf, commented # "ServerFlags" out. -15 and -19 booting to command line.

---

### Post by coolcaseley67 on 2010-09-01
hi ,

My first problem was that jockey didn't show the 96nvidia driver  , i installed it by Synaptic package manager .


after a  reboot  Ubuntu no longer logs in  as it should ,it comes up with a Terminal asking be to log in .



how do i fix this ???

---

### Post by donatas_s on 2010-09-01
Hello, after install and update the ubuntu 10.10, the x server do not work, i give only console.
I found, that i can repare it by doing it:

1) wait until nvidia-current_256.44 gets updated
2) downgrade xorg-xserver to 1.8.2 (the maverick older version or even xorg-edgers lucid version)
3) try adding the following lines to xorg.conf (forcing nvidia drivers to obey) and reboot:
Section "ServerFlags"
Option "ignoreABI" "True"
EndSection

1) I install the newest nvidia drivers (256.52), but it is not helped.

3). I add this lines to xorg.conf, but it is not helped too, after restar, i give only console too.

How to do the second, i do not know. Can somebody write, how in console (or synaptec) dowgrade xserver-xorg 1.9 to xserver-xorg 1.8.2?

---

### Post by evilkastel on 2010-09-01
Probably won't work, i had the same issue and seemed to be about xorg 1.9 and nvidia/ati. As for now, if i update xorg, the system breaks and i have to do a couple of things to get the driver working again.

Probably this same issue:
[http://ubuntuforums.org/showthread.php?t=1561158](http://ubuntuforums.org/showthread.php?t=1561158)
[http://ubuntuforums.org/showthread.php?t=1549195&page=25](http://ubuntuforums.org/showthread.php?t=1549195&page=25)

---

### Post by whitehaint on 2010-09-01
Just do what I did, boot into recovery and pick boring safe mode.  I will enjoy my lame graphics until the fix comes out.  My first alpha test and what fun it is!!!!

---

### Post by whitehaint on 2010-09-01
I've got a similar issue with the nvidia stuff, startx did nothing so I am stuck in lame graphics mode via the recovery boot.  Oh well, beta release should be coming along soon enough!:popcorn:

---

### Post by whitehaint on 2010-09-01
I think this thread sums it up [http://www.uluga.ubuntuforums.org/showthread.php?t=1549195](http://www.uluga.ubuntuforums.org/showthread.php?t=1549195) .  In short, there are some issues and you are not alone!

---

### Post by cariboo on 2010-09-01
> **coolcaseley67 said:**
> hi ,

My first problem was that jockey didn't show the 96nvidia driver  , i installed it by Synaptic package manager .


after a  reboot  Ubuntu no longer logs in  as it should ,it comes up with a Terminal asking be to log in .



how do i fix this ???

Can you start X from the prompt? If it doesn't work, have a look at /var/log/Xorg.0.log, it should tell you what the problem is.

---

### Post by cariboo on 2010-09-01
We have a thread about this problem already, it is located [here]("http:///ubuntuforums.org/showthread.php?t=1549195"), there really isn't any sense in starting more threads about the same problem over and over again. Merged.

---

### Post by VMC on 2010-09-01
I think there's two separate problems here. 
The 1.9 breakage is one of them. 
What the OP here is describing is what I have also experienced with both Lucid and Maverick after installing nVidia drivers.

 It boots to a vt login prompt. startx boots up normally. The question is what is causing X not to start in the first place?

All logs point no where. Specifically .xession-errors log.

---

### Post by mc4man on 2010-09-01
>  Originally Posted by coolcaseley67  
hi ,

My first problem was that jockey didn't show the 96nvidia driver , i installed it by Synaptic package manager .


You may want to clarify, at least for youself, if whatever nvidia card you have can use the 256.XX drivers. If not, and you need the 96 drivers, then Atm I believe you are out of luck.
If that's the case, then return to using nouveau or lucid.

---

### Post by coolcaseley67 on 2010-09-01
hi ,

arr I've had this issue with fedora13 . 
> Can you start X from the prompt? If it doesn't work, have a look at /var/log/Xorg.0.log, it should tell you what the problem is.  

 I can go in to the recovery mode   , do not know the command to start the x sever .


> You may want to clarify, at least for youself, if whatever nvidia card  you have can use the 256.XX drivers. If not, and you need the 96  drivers, then Atm I believe you are out of luck.If that's the case, then return to using nouveau or lucid. 	 

Ok i will check the log & 256 

thanks !

---

### Post by coolcaseley67 on 2010-09-01
here is my log

this i is the big issue [B]Fatal server error:
[    16.158] no screens found
[    14.874] [/B]

```
_log :_
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.875] X Protocol Version 11, Revision 0
[    14.875] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    14.875] Current Operating System: Linux joseph-desktop 2.6.35-19-generic #28-Ubuntu SMP Sun Aug 29 06:36:51 UTC 2010 i686
[    14.875] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-19-generic root=UUID=bb593a9d-c1c6-4350-b294-3abe501e3fbf ro nomodeset
[    14.875] Build Date: 30 August 2010  03:27:10PM
[    14.875] xorg-server 2:1.9.0-0ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.889] Current version of pixman: 0.18.2
[    14.890]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    14.890] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.890] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep  1 09:50:06 2010
[    14.978] (==) Using config file: "/etc/X11/xorg.conf"
[    14.978] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.043] (==) ServerLayout "Layout0"
[    15.043] (**) |-->Screen "Screen0" (0)
[    15.043] (**) |   |-->Monitor "Monitor0"
[    15.044] (**) |   |-->Device "Device0"
[    15.044] (**) |-->Input Device "Keyboard0"
[    15.044] (**) |-->Input Device "Mouse0"
[    15.044] (==) Automatically adding devices
[    15.044] (==) Automatically enabling devices
[    15.108] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.108]     Entry deleted from font path.
[    15.140] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    15.140] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.140] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    15.140] (WW) Disabling Keyboard0
[    15.140] (WW) Disabling Mouse0
[    15.140] (II) Loader magic: 0x81f8e00
[    15.140] (II) Module ABI versions:
[    15.140]     X.Org ANSI C Emulation: 0.4
[    15.141]     X.Org Video Driver: 8.0
[    15.141]     X.Org XInput driver : 11.0
[    15.141]     X.Org Server Extension : 4.0
[    15.142] (--) PCI:*(0:1:0:0) 10de:0171:10b0:0002 rev 163, Mem @ 0xde000000/16777216, 0xd0000000/134217728, 0xddc80000/524288, BIOS @ 0x????????/131072
[    15.142] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    15.142] (II) LoadModule: "extmod"
[    15.265] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.278] (II) Module extmod: vendor="X.Org Foundation"
[    15.278]     compiled for 1.9.0, module version = 1.0.0
[    15.279]     Module class: X.Org Server Extension
[    15.279]     ABI class: X.Org Server Extension, version 4.0
[    15.279] (II) Loading extension MIT-SCREEN-SAVER
[    15.279] (II) Loading extension XFree86-VidModeExtension
[    15.279] (II) Loading extension XFree86-DGA
[    15.279] (II) Loading extension DPMS
[    15.279] (II) Loading extension XVideo
[    15.279] (II) Loading extension XVideo-MotionCompensation
[    15.279] (II) Loading extension X-Resource
[    15.279] (II) LoadModule: "dbe"
[    15.280] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.284] (II) Module dbe: vendor="X.Org Foundation"
[    15.284]     compiled for 1.9.0, module version = 1.0.0
[    15.284]     Module class: X.Org Server Extension
[    15.284]     ABI class: X.Org Server Extension, version 4.0
[    15.284] (II) Loading extension DOUBLE-BUFFER
[    15.284] (II) LoadModule: "glx"
[    15.284] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    15.999] (II) Module glx: vendor="NVIDIA Corporation"
[    16.009]     compiled for 4.0.2, module version = 1.0.0
[    16.009]     Module class: X.Org Server Extension
[    16.009] (II) NVIDIA GLX Module  96.43.18  Tue Jul 13 13:31:40 PDT 2010
[    16.009] (II) Loading extension GLX
[    16.009] (II) LoadModule: "record"
[    16.010] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.092] (II) Module record: vendor="X.Org Foundation"
[    16.092]     compiled for 1.9.0, module version = 1.13.0
[    16.092]     Module class: X.Org Server Extension
[    16.092]     ABI class: X.Org Server Extension, version 4.0
[    16.092] (II) Loading extension RECORD
[    16.092] (II) LoadModule: "dri"
[    16.093] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.095] (II) Module dri: vendor="X.Org Foundation"
[    16.095]     compiled for 1.9.0, module version = 1.0.0
[    16.096]     ABI class: X.Org Server Extension, version 4.0
[    16.096] (II) Loading extension XFree86-DRI
[    16.096] (II) LoadModule: "dri2"
[    16.096] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.098] (II) Module dri2: vendor="X.Org Foundation"
[    16.098]     compiled for 1.9.0, module version = 1.2.0
[    16.098]     ABI class: X.Org Server Extension, version 4.0
[    16.098] (II) Loading extension DRI2
[    16.098] (II) LoadModule: "nvidia"
[    16.099] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    16.158] dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData
[    16.158] (EE) Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so
[    16.158] (II) UnloadModule: "nvidia"
[    16.158] (EE) Failed to load module "nvidia" (loader failed, 7)
[    16.158] (EE) No drivers available.
[    16.158] 
Fatal server error:
[    16.158] no screens found
[    16.158] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    16.158] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    16.158] 
```


any thoughts ............ideas ???

---

### Post by coolcaseley67 on 2010-09-01
here is the log for the 256 ...
```
[    15.657] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    15.658] X Protocol Version 11, Revision 0
[    15.658] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    15.658] Current Operating System: Linux joseph-desktop 2.6.35-19-generic #28-Ubuntu SMP Sun Aug 29 06:36:51 UTC 2010 i686
[    15.658] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-19-generic root=UUID=bb593a9d-c1c6-4350-b294-3abe501e3fbf ro nomodeset
[    15.658] Build Date: 30 August 2010  03:27:10PM
[    15.658] xorg-server 2:1.9.0-0ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    15.658] Current version of pixman: 0.18.2
[    15.658]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    15.658] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.658] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep  1 22:37:34 2010
[    15.659] (==) Using config file: "/etc/X11/xorg.conf"
[    15.659] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.671] (==) ServerLayout "Layout0"
[    15.671] (**) |-->Screen "Screen0" (0)
[    15.671] (**) |   |-->Monitor "Monitor0"
[    15.672] (**) |   |-->Device "Device0"
[    15.672] (**) |-->Input Device "Keyboard0"
[    15.672] (**) |-->Input Device "Mouse0"
[    15.672] (==) Automatically adding devices
[    15.672] (==) Automatically enabling devices
[    15.701] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.701]     Entry deleted from font path.
[    15.719] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    15.719] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.719] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    15.719] (WW) Disabling Keyboard0
[    15.719] (WW) Disabling Mouse0
[    15.719] (II) Loader magic: 0x81f8e00
[    15.719] (II) Module ABI versions:
[    15.719]     X.Org ANSI C Emulation: 0.4
[    15.719]     X.Org Video Driver: 8.0
[    15.719]     X.Org XInput driver : 11.0
[    15.719]     X.Org Server Extension : 4.0
[    15.721] (--) PCI:*(0:1:0:0) 10de:0171:10b0:0002 rev 163, Mem @ 0xde000000/16777216, 0xd0000000/134217728, 0xddc80000/524288, BIOS @ 0x????????/131072
[    15.721] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    15.721] (II) LoadModule: "extmod"
[    15.740] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.741] (II) Module extmod: vendor="X.Org Foundation"
[    15.741]     compiled for 1.9.0, module version = 1.0.0
[    15.741]     Module class: X.Org Server Extension
[    15.741]     ABI class: X.Org Server Extension, version 4.0
[    15.741] (II) Loading extension MIT-SCREEN-SAVER
[    15.741] (II) Loading extension XFree86-VidModeExtension
[    15.741] (II) Loading extension XFree86-DGA
[    15.741] (II) Loading extension DPMS
[    15.741] (II) Loading extension XVideo
[    15.741] (II) Loading extension XVideo-MotionCompensation
[    15.741] (II) Loading extension X-Resource
[    15.741] (II) LoadModule: "dbe"
[    15.742] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.742] (II) Module dbe: vendor="X.Org Foundation"
[    15.742]     compiled for 1.9.0, module version = 1.0.0
[    15.742]     Module class: X.Org Server Extension
[    15.742]     ABI class: X.Org Server Extension, version 4.0
[    15.742] (II) Loading extension DOUBLE-BUFFER
[    15.742] (II) LoadModule: "glx"
[    15.743] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    17.237] (II) Module glx: vendor="NVIDIA Corporation"
[    17.237]     compiled for 4.0.2, module version = 1.0.0
[    17.237]     Module class: X.Org Server Extension
[    17.237] (II) NVIDIA GLX Module  256.52  Wed Aug 25 15:00:44 PDT 2010
[    17.237] (II) Loading extension GLX
[    17.237] (II) LoadModule: "record"
[    17.238] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.238] (II) Module record: vendor="X.Org Foundation"
[    17.238]     compiled for 1.9.0, module version = 1.13.0
[    17.238]     Module class: X.Org Server Extension
[    17.238]     ABI class: X.Org Server Extension, version 4.0
[    17.238] (II) Loading extension RECORD
[    17.238] (II) LoadModule: "dri"
[    17.239] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.244] (II) Module dri: vendor="X.Org Foundation"
[    17.244]     compiled for 1.9.0, module version = 1.0.0
[    17.244]     ABI class: X.Org Server Extension, version 4.0
[    17.244] (II) Loading extension XFree86-DRI
[    17.244] (II) LoadModule: "dri2"
[    17.245] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.246] (II) Module dri2: vendor="X.Org Foundation"
[    17.246]     compiled for 1.9.0, module version = 1.2.0
[    17.246]     ABI class: X.Org Server Extension, version 4.0
[    17.246] (II) Loading extension DRI2
[    17.246] (II) LoadModule: "nvidia"
[    17.246] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.287] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.287]     compiled for 4.0.2, module version = 1.0.0
[    17.287]     Module class: X.Org Video Driver
[    17.328] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    17.329] (EE) NVIDIA:     system's kernel log for additional error messages.
[    17.329] (II) UnloadModule: "nvidia"
[    17.329] (II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    17.329] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    17.329] (EE) No drivers available.
[    17.329] 
Fatal server error:
[    17.329] no screens found
[    17.329] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    17.329] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    17.329]
```

---

### Post by cariboo on 2010-09-01
From the output of the log, the nvidia driver isn't being loaded. In an earlier post you said you installed the nvidia-glx-96 driver. In synaptic it says it's a transitional package. Your log output states that it is trying to load nvidia-current 256.52 from edgers-xorg. What video card do you have, and what driver does it need?

Have you tried creating an /etc/X11/xorg.conf, the command is:

```
sudo nvidia-xconfig
```

---

### Post by whitehaint on 2010-09-01
Seems i have found a fix, well worked for me at least.  [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html) .  It uses the Nvidia 256.53 driver from the PPA, did it, rebooted and now I can cruise right into my 10.10 and I get a Nvidia splash screen on the way.  Compiz works and life is good!

---

### Post by splicerr on 2010-09-01
So I come to read about this X-server breakage and all I can see are posts about the nvidia binary drivers. Perhaps

```

**[NVidia] **WARNING: X-server breakage coming soon to a computer near you

```would be a more suitable topic title. :rolleyes:

---

### Post by cariboo on 2010-09-01
For the most part the problem has been solved. So I should unstick this thread.

---

### Post by 23dornot23d on 2010-09-01
When was it solved ...... ?

Seems that this is the first time in the testing where I can actually know that it is going to crash because of the X-server breakage - which has now come to me ......

Nvidia ..... is everybody ok now from a clean install ..... should I do a fresh install

I have been doing safe upgrades ......

---

### Post by ranch hand on 2010-09-01
Nvidia is its own problem.  The problem with upgrading all the x stuff has been over for a while.

You could always use the OSS drivers.

---

### Post by ktp on 2010-09-01
> **cariboo907 said:**
> For the most part the problem has been solved. So I should unstick this thread.

I think this is good idea...this thread as "evolved" into more then what it was for.

---

### Post by VinDSL on 2010-09-01
> **whitehaint said:**
> Seems i have found a fix, well worked for me at least.  [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html) .  

It uses the Nvidia 256.53 driver[...] Woah!  Thanks, for that!

I didn't realize 256.53 was released (yesterday).  None of my PPAs picked it up...

Compiz looks fantastic now!!!

LoL!  I might as well wipe Lucid off this drive.  

I'll never use 10.04 again...  :p

**EDIT**

BTW, this is where I got 256.53:  [nVidia Drivers 256.53 Certified]("http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html")

> [LIST]
[*]Fixed a bug that prevented XvMC from initializing in most cases.
[*]Added support for xorg-server video driver ABI version 8, which will be included in the upcoming xorg-server-1.9 series of releases.
[*]Fixed a bug that caused extremely slow rendering of OpenGL applications on X screens other than screen 0 when using a compositing manager.
[*]Fixed a regression introduced after 256.35 that caused stability problems on GPUs such as GeForce GT 240.
[*]Fixed a slow kernel virtual address space leak observed whenstarting and stopping OpenGL, CUDA, or VDPAU applications.
[*]Fixed a bug that left the system susceptible to hangs when running two or more VDPAU applications simultaneously.
[/LIST]

Extra Credit:  [http://vindsl.com/images/256.53-compiz.png](http://vindsl.com/images/256.53-compiz.png)  (HD/Visitors)

---

### Post by 23dornot23d on 2010-09-01
I know it was a warning thread originally ..... so I held back on upgrading a little longer as my main job is graphics .....

Thinking that all the problems were now solved I did a safe upgrade .....

Its one system down - I guess here is the end of the road for me and Maverick.

Can anybody advise me which Graphic's card to look for in my next computer .....

Which one is the one that works 100% at the moment ..... Nvidia always was my choice with Linux ...... but after reading this ........ [Nvidia Open Source Drivers]("http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1") .... and advising vesa for what ? rendering 3D scenes .....  

I know that touch screen seems to be what is important at the moment ...... so does this mean that anybody with older Nvidia cards should forget about Maverick and think about buying either a new graphics card if its a desktop computer ...... or getting rid if its a laptop.

I missed from generic-14 ...... to generic-18 .......... and somewhere in that time frame
my computer graphics is now no longer supported ..........

What is ABI ...... all I keep seeing is that its some sort of a standard that Linux adheres to.

How many others does this ABI thing affect ...... or is it just me again ...... 

I lost surround sound in the latest upgrade and now have stereo ...... but losing the graphics when all my work is animation and 3D rendering ....... 

I guess I got left in the dust ....... you guys are going forward so fast.

---

### Post by ktp on 2010-09-01
it's hard to say which graphics card if you are going to be in testing world...no matter which card you use, there will be time (at least from my several years of using development releases) when your video card that will not work because something is always changing.

That being said I would still get nvidia over ati...because nvidia proprietary drivers are updated faster then ati.  And open source drivers are getting better and better, but they still need work for 3D and performance.

---

### Post by ktp on 2010-09-01
> **VinDSL said:**
> Woah!  Thanks, for that!

I didn't realize 256.53 was released (yesterday).  None of my PPAs picked it up...

Compiz looks fantastic now!!!

LoL!  I might as well wipe Lucid off this drive.  

I'll never use 10.04 again...  :p

**EDIT**

BTW, this is where I got 256.53:  [nVidia Drivers 256.53 Certified]("http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html")

sweet...i am upgrading as soon as I can.  I am also getting all your backgrounds. =)

---

### Post by VinDSL on 2010-09-01
> **23dornot23d said:**
> Can anybody advise me which Graphic's card to look for in my next computer .....

Which one is the one that works 100% at the moment .....My understanding is, you'll need a Series 6 card (or newer).

I'm running a nVidia 7600 GT and it works great!

If you're in doubt, you should check the Supported Products page on the nVidia site...  ;)

---

### Post by 23dornot23d on 2010-09-01
I have been running this graphics card ok all the way through. using the latest drivers with no problems - until now ...... so why the change ? and what's the change ?
Who needs it ..... how many users are you aiming it at ...... and how many older cards are
affected this Nvidia 9300M GS    

( I did not think was too bad a card and has worked well up to yesterday - but now it seems old hat )

[IMG]http://i55.tinypic.com/jub86c.jpg[/IMG]


So the other day when the ABI issue popped up  ......... I though no problem .... but now I am worried it is here to stay ........

Will the ABI issue be resolved then - its not a really old graphics card or computer, that I am using.

When I joined the testing - I did it in the hope of saving others from going through some of the tasks I have to do each time I upgrade and I used to be able to resolve most problems, and also for my own benefit too ....... this seems to be now working out the opposite of what I expected.

[B]I am not sure where this is heading - originally my system worked pretty well with Ubuntu 8.04 through to 10.04 ...... now after going through the testing of 10.10 

As someone has pointed out there are only 39 days to go to 10.10 
what are the chances of my system working ok. ?[/B]

It seems the main things that I used before ok are now not going to work. 

**The graphics card now crashes ..... the G-pen for drawing using GIMP etc does not work ...... the sound card now stereo instead of surround sound.**

What I am wondering is at the end of the next 39 days ....... will I have a big smile on my face :D or will I be sad :(. 

Am I jumping the gun - and my issues are going to be ok on release day .......

Is there a way to avoid being sad :( ...

This is my first time testing - do they somehow work out what works best for the majority
or are they targeting certain systems - like 64 bit ..... and touch screen ...... 

How do I get to see the full picture here , is there a video anywhere showing their objectives.


_______________________________________________________


Will this work for me then  [LINK]("http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html") ..... will try to see where the info is for the 9300 M GS


 
[LIST]
[*]Fixed  a bug that prevented XvMC from initializing in most cases.
[*]**[COLOR=Blue]Added  support for xorg-server video driver ABI version 8, which  will be included in the  upcoming xorg-server-1.9 series of releases.[/COLOR]**
[*]Fixed  a bug that caused extremely slow rendering of OpenGL  applications on X screens other  than screen 0 when using a compositing  manager.
[*]Fixed  a regression introduced after 256.35 that caused stability problems on GPUs such  as GeForce GT 240.
[*]Fixed  a slow kernel virtual address space leak observed whenstarting and stopping  OpenGL, CUDA, or VDPAU applications.
[*]Fixed  a bug that left the system susceptible to hangs when running two or more VDPAU  applications simultaneously.
[/LIST]
  


> 

Woah!  Thanks, for that!

I didn't realize 256.53 was released (yesterday).  None of my PPAs picked it up...

Compiz looks fantastic now!!!
If this works then I will be :grin: too ......

---

### Post by cariboo on 2010-09-01
I see that the xorg-edgers 256.52 driver only supports the 8 series and better. I've got a 6600GT AGP card, I have to put together a system, and see what driver it needs. I'm running the xorg-edgers driver on one system, and the driver from the repositories on two other systems, they all work quite well.

Cards used:

[list]
[*] 210GT
[*] 9400GT
[*] 8400GS
[/list]

---

### Post by 23dornot23d on 2010-09-01
Thanks guys .... 
(My Desktop System - I need a newer graphics card to run Maverick ... its a AGP Nvidia 5600)
But solved my problem for my Laptop with ..... no crash and no errors ..... great one ... thank you

[IMG]http://i53.tinypic.com/29uel3.jpg[/IMG]

Just the 2 problems now ..... the G-pen *(wizardpen) and the sound in Stereo .... instead of surround sound.
but I can live with these for the moment ..... as they run ok in my other systems .....

;) happy again ...

---

### Post by mc4man on 2010-09-02
> I see that the xorg-edgers 256.52 driver only supports the 8 series and better. I've got a 6600GT AGP card,

The 256.52 should support 6000 series and up - does on a 7800 agp here, though I still think the 195.XX where better suited for 6/7000 agp cards

---

### Post by coolcaseley67 on 2010-09-02
hi ,

my card is a GE Force4 Mx 440  its  nvidia 96.43.18 .


thanks !

---

### Post by mc4man on 2010-09-02
> my card is a GE Force4 Mx 440 its nvidia 96.43.18 .
Atm there is no restricted driver support for that card in maverick though there may be at some point - 
from jockey changelog
> jockey (0.5.9-0ubuntu2) maverick; urgency=low

  * data/handlers/fglrx.py, nvidia.py:
    - Temporarily disable fglrx, nvidia 96 and 173 and ignore the fact that nvidia
      current claims to be ABI incompatible with the new xserver.

and [nvidia site]("http://www.nvidia.com/object/IO_32667.html")
> The following GPUs are no longer supported in the regular NVIDIA Unified UNIX Graphics Driver. Instead, these GPUs will continue to be supported through special "Legacy GPU" drivers that will be updated periodically to add support for new versions of Linux system components (e.g., new Linux kernels, new versions of the X server, etc).

---

### Post by coolcaseley67 on 2010-09-02
hi

OK  I'll live with out it until **(if ever ) **an update appears to 96.43 !


:shock:
thanks !

---

### Post by plun on 2010-09-02
> **cariboo907 said:**
> I see that the xorg-edgers 256.52 driver only supports the 8 series and better. I've got a 6600GT AGP card, I have to put together a system, and see what driver it needs. I'm running the xorg-edgers driver on one system, and the driver from the repositories on two other systems, they all work quite well.

Cards used:

[list]
[*] 210GT
[*] 9400GT
[*] 8400GS
[/list]


Where did you see that  ??

> Please note: This NVIDIA Linux graphics driver release **supports GeForce 6xxx and newer NVIDIA GPUs**, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.


[http://www.nvnews.net/vbulletin/showthread.php?p=2309077](http://www.nvnews.net/vbulletin/showthread.php?p=2309077)


--

---

### Post by cariboo on 2010-09-02
I saw the support for 8 series and up in synaptic:

> The binary driver provide optimized hardware acceleration of OpenGL
applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
and flat panel displays are also supported.

This package also includes the source for building the kernel module
required by the Xorg driver, and provides NVIDIA's implementation of
the Video Decode and presentation API. The latter enables acceleration
for NVIDIA 8 and later series cards for h264 video.

GPUs such as GeForce series 6 or newer are supported.

See /usr/share/doc/nvidia-current/README.txt.gz for a complete list
of supported GPUs and PCIIDs

and a screenshot

**Edit** Oops looks like I misread, sorry for the confusion.

---

### Post by cariboo on 2010-09-02
It seems I mis-read things, I saw support for H264 for 8 series and up and assumed that the driver only supported the 8 series and up video cards.

---

### Post by philinux on 2010-09-02
8600gt.

From my chroot I deleted xorg.conf, purged nvidia-current. Rebooted and installed driver from jockey. Rebooted and all good. It put the ABI stuff in automagically. Plymouth not working though. 

Hope they get this all fixed up proper soon.

---

### Post by ktp on 2010-09-02
> **philinux said:**
> Plymouth not working though. 

Hope they get this all fixed up proper soon.

Me too, I haven't had proper plymouth boot for while...but enjoying the ~14 second boot.  I am thinking about going with blank boot screen to get another 1 or 2. =)

---

### Post by jerrylamos on 2010-09-02
Beta got GPU error on this i845G Intel video, so I booted a one day pre-Beta which I put Brian Roger's "shadow" fix on, see launchpad Bug #541492.  Note if I use his xorg.conf I get bootup crashes and hangs, but without the xorg.conf it works and has faster screen scroll than Beta.  Yes I've got launchpad entries.

Maybe I'll try the "shadow" fix on Beta....not sure how to back it off or how compatible it will be with the inevitable Maverick updates.

Jerry

---

### Post by ranch hand on 2010-09-02
I am enjoying the heck out of this thread but wouldn't it be better if it were  not a stickie?  We are trying to get noobs to read the stickies.  This one is not much use as a sticky, at least by that standard.

---

### Post by cariboo on 2010-09-02
I suggested this a couple of days ago. Done, unstuck.

---

### Post by PGHammer on 2010-09-03
> **psyke83 said:**
> Do you mean that the "nomodeset" isn't working with the free drivers anymore? At least for ATI cards, the command is no obsolete and you need to use "radeon.modeset=0". I have a feeling that you'll need to do something similar (nouveau.modeset=0).

Hmm, actually... IIRC, the nouveau drivers don't support non-KMS mode anymore. Shame.

I have had to use the last (radeon.modeset=0) whenever I use the FOSS drivers (HD5450=Evergreen=no KMS support unless latest drivers from git/Xorg-edgers are installed).  The only *other* option is Penguinista Catalysta 10.6 or newer ('buntu 10.04+, including all 10.10 builds to date) Xorg 1.9 follows the kernels (2.6.35+) in preferring KMS; hence the issues with FOSS radeon with Evergreen in particular.  If nouveau doesn't allow you to turn modesetting off...*ouch*.

---

### Post by jerrylamos on 2010-09-03
"i915.modeset=0" not working on Beta intel video i845G.  No gdm.  xsession-errors all kinds of complaints.  I've got dump info not sure if it is of interest?

with just "quiet" did boot.  There was a GPU lockup yesterday, let's see if it feels better today.

Jerry

---

### Post by philinux on 2010-09-05
Just got latest nvidia driver update to 256.53 and removed the abi stuff from xorg and all is well.

---

### Post by cloaknite on 2010-09-06
My ubuntu doesn't boot after updating to 10.10, i did a partial update before that, now i'm stuck with a tty1 terminal thing, can someone help? Thanks

---

### Post by recluce on 2010-09-06
> **philinux said:**
> 8600gt.

From my chroot I deleted xorg.conf, purged nvidia-current. Rebooted and installed driver from jockey. Rebooted and all good. It put the ABI stuff in automagically. Plymouth not working though. 

Hope they get this all fixed up proper soon.

Here is the fix I used to get Plymouth working with Lucid and Maverick in combination with Nvidia proprietary drivers:

[http://ubuntuforums.org/showthread.php?t=1558174](http://ubuntuforums.org/showthread.php?t=1558174)

---

### Post by cariboo on 2010-09-06
> **cloaknite said:**
> My ubuntu doesn't boot after updating to 10.10, i did a partial update before that, now i'm stuck with a tty1 terminal thing, can someone help? Thanks

If you can start in recovery mode, once at the menu select drop to a netroot prompt and type:

```
apt-get -f install
```

to see if that installs the missing packages.

Usually, when you upgrade this early in the process, 10.04 should be fully up-to-date, and should should uninstall any packages installed from a ppa, and disable the ppa's before attempting to upgrade.

---

### Post by cloaknite on 2010-09-06
> **cariboo907 said:**
> If you can start in recovery mode, once at the menu select drop to a netroot prompt and type:

```
apt-get -f install
```to see if that installs the missing packages.

Usually, when you upgrade this early in the process, 10.04 should be fully up-to-date, and should should uninstall any packages installed from a ppa, and disable the ppa's before attempting to upgrade.

No luck, I went to the menu and selected drop netroot. I wrote the command and then it says that there are no packages to be updated, installed or removed...I think I'm gonna format this thing :D

---

### Post by PGHammer on 2010-09-06
> **cloaknite said:**
> No luck, I went to the menu and selected drop netroot. I wrote the command and then it says that there are no packages to be updated, installed or removed...I think I'm gonna format this thing :D

Another issue is that *updating* Kubuntu 10.10 beta leaves KDE completely unusable (I now find myself having to use GNOME and GDM to have a desktop at all, as KDM/KDE 4.5.x is now useless).  The initial install went fine; it was the updates that broke things.

---

### Post by jerrylamos on 2010-09-07
i845G was running Beta with default intel drivers, KMS and all, yesterday.  Nice.

Today the "dread update" struck again with 2.6.35-20 and a bunch of other stuff.

No gdm no way.  Did some dumps for Launchpad Bug #541492.

Had to go back to driver "vesa".

Jerry

---

