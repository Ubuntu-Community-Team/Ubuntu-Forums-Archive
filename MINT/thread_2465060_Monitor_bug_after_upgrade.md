---
title: "Monitor bug after upgrade"
date: 2021-07-20
forum: MINT
---

### Post by Bewildered_Bob on 2021-07-20
Ubuntu 19.04 was successfully installed. But after upgrading to 20.04 the monitor went BERSERK !!  Some parts of the monitor screen were understandable but other parts were grossly distorted. After re-installing 19.04 the monitor works as advertised. Since there are no longer software patches for 19.04 what do I do next ?  Thanx.

Bewildered Bob

MORE - version 20.04 was installed on an oldie but goodie (until now) HP 505 desktop with an integrated Nvidia GeForce adapter. Does it make good financial sense to buy an inexpensive VGA card to replace the attachment to the motherboard and allow continued use of the desktop (which worked swell for 19.04) ??  If so any recommendations ??  Thanx

BB

---

### Post by grahammechanical on 2021-07-20
Are you using a proprietary video driver? How old is the video card? Over time Nvidia drops support for older Nvidia cards.

I think it is advisable before doing an online upgrade to take an installation back to its default condition and that includes changing to an open source video driver.

Run these commands to find out about the video card and available proprietary drivers.

```
ubuntu-drivers devices
ubuntu-drivers list
```

Use Software & Updates>Additional Drivers tab to deactivate the proprietary video driver. It occurs to me that this was an upgrade by means of a fresh install of 20.04. In that case do not tick the box to install non-free third party software. After installation you can try installing the proprietary video driver and also install ubuntu-restricted-extras to get the audio and video codecs you might need.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Regards

---

### Post by Bewildered_Bob on 2021-07-22
Mr Graham: Thanx for the quick reply. You shd know that I am a recovering Windows user and also Ub newbie so plz be **VERY SPECIFIC** abt cmds, etc.  Currently Ub _***19.04***_ is installed and apparently works as advertised but cannot be upgraded. If I understand you correctly the 2 ***ubuntu-drivers ***cmds shd provide devices & list while running 19.04. But (in my humble opinion) deactivating the proprietary Nvidia video driver shd be run in _***20.04***_ instead. However the monitor is so badly garbled that the on screen buttons, etc are not usable. Can your suggestion be followed while re-installing 20.04 from "scratch" ??  If not this procedure may not work on the desktop. Thanx.

BB
in the "colonies"

---

### Post by MAFoElffen on 2021-07-22
@grahammechanical:
He has a NVidia GeForce 6150 nforce 430 which works with NVidia driver package nvidia-304, which is still supported by the Graphics Team PPA...

Or if he purges the current NVidia druver, of whatever version he has, he would be covered by the opensource Nouveau driver. It is in the NV40 family, specifically is NV4C, so it is supported via Nouveau. While some chipsets only have 2D support by Nouveau, that specific chipset, does have 3D support with Nouveau.

---

### Post by grahammechanical on 2021-07-22
@bewildered_bob

You posted this in another thread which has now been closed. I copy it here.

> Ubuntu 19.04 works well on my HP 505 desktop with an Integrated NVIDIA  GeForce 6150SE Graphics adapter. But after installing Ub 20.04 the  monitor is WILDLY ERRATIC. So first step is to update the Nvidia driver  and test. But while trying to access Nvidia driver downloads an err msg  appears -"Nouveau kernel driver in use". What does this mean in plain  English ??  Is there a "work-around" to allow the Nvidia driver update  ??  If not, are there practical options (other than continue to run  19.04) ??

Nouveau is the open source video driver for Nvidia cards that is automatically activated if the Nvidia proprietary video driver is not activated.

If we go to Software & Updates>Additional Drivers tab and we are connected to the internet the utility will find a Nvidia driver for us. We can then activate it. Then when we reboot we will not be running on the Nouveau driver but the Nvidia driver.

You can use Ubuntu 19.04 to find out what Nvidia drivers are available for that hardware. Then when doing a fresh install of 20.04 do not tick the box to install non-free third party software. In this way when the installation is finished and Ubuntu 20.04 is restarted it will be running on Nouveau not the Nvidia driver.

All this is based on the opinion that the problem is caused by the Nvidia driver. The first thing is to get a working 20.04 desktop so that you can work in 20.04.

It is possible to download Nvidia drivers from their web site but in my opinion that will complicate things. Try Software & Updates>Additional Drivers first.

Regards

---

### Post by MAFoElffen on 2021-07-22
Sorry.

I agree. If you go to NVidia Drivers from them, then they are "PITA". The Ubuntu repo drivers are updated with other updates. The binaries from NVidia are a user driver manual affair and usually get wacked with just normal kernel updates. They are definitely more work to upkeep keep up on.

---

### Post by Bewildered_Bob on 2021-07-28
Linux Mint 20.2 is successfully installed but occasionally the original monitor screen display bug and associated system "freeze" occurs. I believe that the Nvidia driver is still installed but I am willing to try Nouveau instead. However since I am a Linux newbie VERY SPECIFIC INSTRUCTIONS are needed. Plz advise. Thanx.

Bewildered Bob

---

### Post by Bewildered_Bob on 2021-07-28
> **grahammechanical said:**
> @bewildered_bob

Nouveau is the open source video driver for Nvidia cards that is [U][I][B]automatically activated if the Nvidia proprietary video driver is not activated.
[/B][/I][/U]
If we go to Software & Updates>Additional Drivers tab and we are connected to the internet the utility will find a Nvidia driver for us. We can then activate it. Then when we reboot we will not be running on the Nouveau driver but the Nvidia driver.

You can use Ubuntu 19.04 to find out what Nvidia drivers are available for that hardware. Then when doing a fresh install of 20.04 do not tick the box to install non-free third party software. In this way when the installation is finished and Ubuntu 20.04 is restarted it will be running on Nouveau not the Nvidia driver.

All this is based on the opinion that the problem is caused by the Nvidia driver. The first thing is to get a working 20.04 desktop so that you can work in 20.04.

It is possible to download Nvidia drivers from their web site but in my opinion that will complicate things. Try Software & Updates>Additional Drivers first.

Regards

=========================================================================
Plz explain how the monitor functions if the only video driver (Nvidia) is not activated and Nouveau has not been installed. Thanx.
=========================================================================

---

### Post by tea for one on 2021-07-28
> **Bewildered_Bob said:**
> Plz explain how the monitor functions if the only video driver (Nvidia) is not activated and Nouveau has not been installed. Thanx.

I'm pretty sure that Nouveau is a default package included automagically during the installation process.
I do not have a Nvidia card but the nouveau package is present in my system.

```
edited@edited:~$ apt list xserver-xorg-video-nouveau
Listing... Done
xserver-xorg-video-nouveau/focal,now 1:1.0.16-1 amd64 [installed,automatic]
edited@edited:~$ 

```

---

### Post by Bewildered_Bob on 2021-07-29
Hello: In a post from "**Freedesktop.org**" the following appears - _***"There are two ways of installing Nouveau on your Linux computer. The most recommended way is to use your [distribution-provided packages]("https://nouveau.freedesktop.org/InstallNouveau.html#distro-packages"). If those are outdated or buggy, you may also [recompile Nouveau from source]("https://nouveau.freedesktop.org/InstallNouveau.html#recompilation").***__*** Nouveau is incompatible with NVIDIA's proprietary driver. If you want  to use Nouveau, you first need to remove the proprietary driver from  your system."***_
The post shows several distros but not Linux Mint which is installed on my HP desktop. I tried to install Nouveau using method (1) - distribution provided pkgs but cannot confirm if it is successfully installed since the bug is intermittent. Also there were no instructions provided (for a Linux newbee like me) to "remove proprietary Nvidia driver from system". 

Method (2) is to recompile Nouveau from source but it appears that the KERNEL contains the display adapter drive and must be re-complied (which, if true,  in my humble opinion is like the tail wagging the dog).  

Is there a method (3) - buy a VGA card so that the integrated display adapter is bypassed ?? It may be easier for a recovering Windows user like me.

still Bewildered Bob

---

### Post by QIII on 2021-07-29
Moved to MINT.

---

### Post by MAFoElffen on 2021-07-29
I'm not sure what that last person was referring to. xserver-xorg-video-nouveau is installed in Mint as well as most Debain Branched distros, by default. And I may be wrong, but as I remeber that card has a problem running Wayland, so you should be using Xorg XServer anyways.

---

