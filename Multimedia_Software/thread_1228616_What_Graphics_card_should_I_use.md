---
title: "What Graphics card should I use?"
date: 2009-08-01
forum: Multimedia Software
---

### Post by jalfan on 2009-08-01
I have the following Graphics cards (note I am not using all of these at the same time... I only have one monitor):

1) Intel Corporation 82865G Integrated Graphics Controller (rev 02)
2) ATI Technologies Inc Rage 128 RE/SG
3) ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
4) nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

...I have collected these cards from my and my friends computers over the years.  I am trying to get one of them working with my system.  I have been all over the Web looking for information about how to configure my cards (or one of them) to use desktop effects.  I have been unable to get anything working the way it should (they do video and some games, but not compiz).

I have Ubuntu Jaunty on Linux Kernel 2.6.28-14-generic

I am using an Intel Processor on an Asus P5PE-VM Motherboard.  The Intel card above is integrated with an Intel Chipset for sound, graphics and other devices (networking, etc).

I had one of the ATI cards working on an older Ubuntu kernel, but can't seem to get it working on the new kernel (here, I though it would still be supported).

I need to know which of the above cards should work best with my system, and what packages I will need to get desktop effects working (Compiz and the cube switcher, etc.)

Thanks in advance, 


-jalfan

---

### Post by jalfan on 2009-08-01
I plugged in my Nvidia card and tried downloading the NVIDIA-Linux-x86-96.43.13 drivers from the Nvidia Website.

Installing these drivers allows me to enable desktop effects and compiz, but the window decorations went away... there are no borders on any windows and docks like AWN and Cairo only show a black white space at the bottom of the screen.

When I open a terminal window it just shows a white box.  
If I switch to a different terminal and type `emerald --replace`, i get the following error: 

(emerald:7250): Gtk-WARNING **: cannot open display:

I am continuing to search for answers while I am awaiting a reply to this thread...


Thank you for any help...

-jalfan.

---

### Post by jalfan on 2009-08-02
Well, as no one is adding input I will document my travels in this thread... if that is okay.

I still have not figure out what went on with the Compiz Window manager and why the window borders went away.

I installed my ATI Card, (#2 above, the ATI Rage 128 ) I installed the fglrx driver from ubuntu repositories.... after reboot I checked the xorg.conf file and it still said "nvidia" as the driver... I changed it to fglrx and rebooted... all kinds of problems arose and I had to plug the nvidia card back in and re-run the installation file for the nvidia driver that I downloaded from the nvidia web site.

Before doing this I had tried restoring the xorg.conf file that i had backed up and runing "xfix" from the repair boot options... none of these worked...

I downloaded the fglrx driver from the ATI web site, but they are in an RMP file.  I tried to make a deb package using "alien -d <packagename>.rpm" but got an error that it could not find the libc.so.6 file.

I did a locate and the file was located at /lib/libc.so.6.

If anyone has onformation about this error, please let me know... thanks.

I will continue to troubleshoot from here...

---

### Post by bobince on 2009-08-03
If you run compiz from the command line (‹compiz --replace›) you may get more information as to why it wouldn't start up. (If it kills the window manager, making the borders disappear, run ‹metacity› to get it back.)

For more information still, use [compiz-check](http://ubuntuforums.org/showthread.php?t=799070).

However, the graphics adapters you have listed are all pretty much useless. None of them would come close to running Aero, for example (Win Vista's equivalent of compiz).

> 1) Intel Corporation 82865G Integrated Graphics Controller (rev 02)

This is probably your best chance of getting compiz running, albeit with poor performance. Try compiz-check. You might be [blacklisted](http://ubuntuforums.org/showthread.php?t=765875) but it might be avoidable. Maybe. If you are lucky.

> ATI Technologies Inc Rage 128 RE/SG

Graphics card prehistory, fit only for the dustbin.

> 3) ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

Old ATI stuff is tricky, as the proprietary driver dropped support for previous cards when it was updated for the new xorg. Not sure what the open-source driver is like here.

> 4) nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

This is headed bin-ward with the Rage too really.

---

### Post by steefjeqv on 2009-08-04
Hi,

The ATI Radeon 9200 should work out of the box with Jaunty.
Do not install fglrx.
Jaunty loads the "ati" open source driver by default.

I'm using a 9600 which works perfectly (RV300).

I even updated my X with the xorgontheedge ppa :

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

Greetings,
Steven

---

### Post by jalfan on 2009-08-10
Thank you all for your advice.. I will try using my ATI with a New Jaunty install... but I am sticking with the Integrated Intel for now...

I will write later and let y'all know how it is going.   I am only using the Intel for the base graphics not for compiz as I still seem to have problems with it...

---

### Post by holstien on 2009-09-03
Yea. Keep the Rage for a server or for when everything else has flamed out.

From my own personal experience, I found an AGP Radeon 9200 SE to be a -slower- card than the integrated Intel 865 graphics on my Dell GX270. Compiz DID work on the Radeon, I think, at low resolutions, but something happened where there was nasty artifacts at high resolutions (like 2048x1152), where I usually work. Unfortunately, that computer sprayed sparks out the back and is no more.

Yes. fglrx didn't work, but the opensource ati driver does. It all autoconfigures nicely.

I'm currently using a PCI radeon 9200 SE in a Dell PIII 800. It's hard to believe that it's not software rendering sometimes.

If you have any money at all, i'd say you should do some research and ebay/buy a faster card if you really want compiz/3d performance.


This is an awesome page to compare the various ATI cards for your research:
[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)

---

### Post by AaronP_ on 2009-09-03
> **jalfan said:**
> I plugged in my Nvidia card and tried downloading the NVIDIA-Linux-x86-96.43.13 drivers from the Nvidia Website.

Installing these drivers allows me to enable desktop effects and compiz, but the window decorations went away... there are no borders on any windows and docks like AWN and Cairo only show a black white space at the bottom of the screen.

When I open a terminal window it just shows a white box.  

This is a bug in Compiz (or its window decorator) where it fails to gracefully handle the lack of 32-bit ARGB visuals that it wants to use for window decorations.  96.43.13 is old enough that you have to explicitly enable those with
```

  Option "AddARGBGLXVisuals"

```
in /etc/X11/xorg.conf.

---

### Post by jalfan on 2009-09-04
Thanks all for your posts... In response to <holstien>, I did try to install the opensource ATI driver from the manufacturer website, but when I try to trun it it says I don't have permissions.  I have tried to run it under my user using sudo, under root, and with and without GDM running...

The major error I get is that it says that it cannot find the X server and just quits.  When I try to run the script that tells me what X server I am using (X11 or FreeDesktop.org) I get the error that I do not have permissions to run the file... (I don't remember what the exact error is since I am not using my ATI card right now).

I had used the ATI card in the past on Ubuntu 8.04 with no problems... Why won't it work on Jaunty...? Of course I have not tried to "Out of the Box" Solution that <steefjeqv> suggested.  I had installed this version with My NVIDIA card installed.

Is there a way that I can keep my settings... (Firefox history, homepage, etc; currently installed programs, desktop background, et all)... but get a fresh install of Ubuntu Jaunty or newer? (I have not done this before, but I assume that backing up my /home directory would save my setting, but not the installed programs).. is there a way to get a list from my OS of what programs I have installed since I started using this version?

Please correct any information I have above that may be wrong.


(Note: the above information was not-double checked for spelling, wording or grammar... I am lazy today)


Peace...

--Jalfan

---

### Post by ad_267 on 2009-09-04
I would suggest you don't try to install drivers from the ATI/Nvidia websites, just use the default ones available from Ubuntu under System - Administration - Hardware Drivers. Usually everything works out pretty smoothly doing that.

---

### Post by jalfan on 2009-09-25
> **steefjeqv said:**
> Hi,

The ATI Radeon 9200 should work out of the box with Jaunty.
Do not install fglrx.
Jaunty loads the "ati" open source driver by default.



OK, I verified (using the USB Startup Disk Creator) that the ATI 9200 does work with the initial install...

The problem rmains, though, that my current setup (I have had fglrx installed in the past) doe snot work with it.  I believe it is trying to use the NVIDIA drivers for some reason.  

The xorg.conf file is not set to anything specific, it is the same default configuration that the USB Boot Drive has.

How do I reset my system so that it is not trying to use the wrong drivers?

Thanks to all for help...

---

### Post by markharding557 on 2009-09-25
i recomend that you use an nvidia card because nvidia drivers are better than the ones from ati

---

### Post by steefjeqv on 2009-09-30
Hi,

Sorry for the late reply, my phone connection has been broken for nearly a week.

You can uninstall fglrx (ATI) using this command :

sudo dpkg --purge fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

Uninstalling Nvidia : 

press ctrl alt f1 (this will switch you to a text based level)

sudo /etc/init.d/gdm stop

go to the downloaded nvidia dir

sudo ./NVIDIA-Linux your version of nvidia driver-pkg2.run --uninstall


Greetings,
Steven

---

