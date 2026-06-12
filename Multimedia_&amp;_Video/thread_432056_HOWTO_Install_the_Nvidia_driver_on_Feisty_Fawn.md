---
title: "HOWTO: Install the Nvidia driver on Feisty Fawn"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by tseliot on 2007-05-03
Hi, I've ported my guide about the Nvidia Drivers to Edgy Eft on the USDF.
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

OR try this mirror:

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)


--------------------------------------------------------------------
Application to make Method 2 faster

You can use Envy which you can find below (for automating Method 2 and solving problems of driver mismatch)

**NOTE: Envy is a 3rd party application and you should use it at your risk**

My application will download the ATI/Nvidia installer (and all the files the installer needs), build the packages you need and set the driver for you.

Get to the following website:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And follow the instructions you will find there.

---

### Post by dabl on 2007-05-03
GREAT to hear this!

Does it work on 64-bit?

Thanks for doing this!  :)

---

### Post by tommcd on 2007-05-03
tseliot, 2 questions:
1) What about this way from the wiki:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
It says system>administration>Restricted Devices Manager is now the 'recomended way'. Is that true?
2) When you install nvidia-glx-new in synaptic it says the command to enable the driver is now "sudo nvidia-glx-config enable". What is the difference between that and "sudo nvidia-xconfig", and what does the "--no-composite" switch do?

---

### Post by solarjeep on 2007-05-04
This (Envy) works.  I just did a clean install of Feisty for the first time on one of my secondary boxes.  I used the Envy package and it was flawless.   Using an nVidia GeForce4 MX 4000 AGP.
I'll update later if I run into any issues related to this method.

Nice job!

---

### Post by Rictus on 2007-05-04
Does this work for the 8800 series too?

---

### Post by John Azelvandre on 2007-05-04
I just downloaded and ran Envy, and it seemed to work, but I'm still not getting the hi-res my card is capable of.  But now direct rendering returns 'yes' whereas before it returned 'no.' Which I think is a good thing.  

I have: PCI Express nvidia GeForce Go 6600.

What do I try now?  This card is capable of doing something like 1680x1050

---

### Post by John Azelvandre on 2007-05-05
I got my card to work.  I guess Envy didn't quite do it in my case.  Fortunately, I had the old xorg.conf file from the previous vendor install handy, and I copied the relevant parts of it to get my card to work up to spec.  Here's what I needed to put in for my card:

```
Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	Option	    "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
#	Option     "TwinView" "On"
#	Option     "TwinViewOrientation" "Clone"
#	Option     "MetaModes" "CRT-0: 1680x1050, DFP-0: 1680x1050"
#	Option     "ConnectedMonitor" "CRT, DFP"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

Not really sure what this does, but it worked.

---

### Post by hessiess on 2007-05-08
i need to get the graphics drivers for a geforce go 7600 in ubuntu with no internet conection

the link dosant work, just infanatly loads

---

### Post by dnzz on 2007-05-08
Ok i installed the driver but I can NOT even play KAsteroids. Drivers are very slow.


I have Geforce 6200 go

Things i have tried:
1-Installing nvidia-glx-new, nvidia-glx-config enable, nvidia-xconfig
2-Installing drivers from [www.nvidia.com](www.nvidia.com)
3-This guide...
4-Using "nv" drivers (Hopelessly)


Any ideas?

---

### Post by Gang_Star on 2007-05-10
Wow! Amazing...

That's such a well written guide. Even a noob such as myself has no problem following it, it's done from the terminal to minimize error, and best of all it worked. Thanks!

I have what I have found to be not the easiest setup to get drivers running for but this was a synch. **My working setup:**
Geforce 6200 TurboCache
Kubuntu Feisty 7.04 (64 Version)

---

### Post by deesto on 2007-05-11
Would someone mind posting an alternative page, or the text from the link above?  It's timing out currently, and I can't get to the page to read the instructions.

I tried the Envy script, and it failed with the same errors that I got when I tried to install the drivers manually (can't load nvidia kernel drivers; I double-checked to ensure the kernel drivers were indeed installed).

I'm running 7.04 x86, and my video card is an integrated nvidia GeForce 6100 nForce 430.  X is running minimally with the video card driver set as "vesa".

Thanks!

---

### Post by tseliot on 2007-05-14
> **tommcd said:**
> tseliot, 2 questions:
1) What about this way from the wiki:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
It says system>administration>Restricted Devices Manager is now the 'recomended way'. Is that true?
Yes, I'll add it to this thread.

> **tommcd said:**
> 2) When you install nvidia-glx-new in synaptic it says the command to enable the driver is now "sudo nvidia-glx-config enable". What is the difference between that and "sudo nvidia-xconfig", and what does the "--no-composite" switch do?

"sudo nvidia-glx-config enable" should keep your xorg.conf compatible with debconf but will fail if you edited xorg.conf manually.

"nvidia-xconfig" is a tool created by Nvidia.

"--no-composite" disables the composite extension of the Xserver

---

### Post by tseliot on 2007-05-14
> **Rictus said:**
> Does this work for the 8800 series too?

Sure

---

### Post by tseliot on 2007-05-14
> **hessiess said:**
> i need to get the graphics drivers for a geforce go 7600 in ubuntu with no internet conection

the link dosant work, just infanatly loads

Try Method 1 offline

try this mirror:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

### Post by tseliot on 2007-05-14
> **deesto said:**
> Would someone mind posting an alternative page, or the text from the link above?  It's timing out currently, and I can't get to the page to read the instructions.

I tried the Envy script, and it failed with the same errors that I got when I tried to install the drivers manually (can't load nvidia kernel drivers; I double-checked to ensure the kernel drivers were indeed installed).

I'm running 7.04 x86, and my video card is an integrated nvidia GeForce 6100 nForce 430.  X is running minimally with the video card driver set as "vesa".

Thanks!

Can you post your /var/log/envy-installer.log and your /var/log/Xorg.0.log ?

---

### Post by rickdog on 2007-05-14
I had the Envy program setup my Nvidia driver for my AGP Geforce 6600 in 6.10, but it didn't work in Feisty. However, I did get the drivers installed using synaptic, so now I get that restricted driver item in the admin menu. Anyway, I'm wondering how to get the Nvidia settings gui again. I don't seem to have any way of adjusting the color and such with this new setup. Is there a version of Envy for 7.04? Is there a settings gui available? Thanks.

---

### Post by tseliot on 2007-05-14
> **rickdog said:**
> Is there a version of Envy for 7.04?
Sure (0.9.3), you can get it here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

> **rickdog said:**
> Is there a settings gui available? Thanks.
Envy will omstall it for you and create a link in you Applications Menu.

Or you might just type:
```
sudo nvidia-settings

```

---

### Post by deesto on 2007-05-14
> **tseliot said:**
> Can you post your /var/log/envy-installer.log and your /var/log/Xorg.0.log ?

Sure; please see attached archive.

---

### Post by Yaka on 2007-05-14
i have to say your envy app is great for my self ive switch 3 pcs from win2k to ubuntu and your app has worked flawlessly with install and configuring drivers its mad emy life easier and my friends who have switched to Ubuntu like me recently also use it too.

---

### Post by hpne on 2007-05-15
Thanks a lot, ENVY works great! I have Geforce 6600 and Feisty.

---

### Post by tseliot on 2007-05-15
> **deesto said:**
> Sure; please see attached archive.
type:
```
sudo dpkg-divert --rename --remove /usr/lib/xorg/modules/extensions/libglx.so
```

then use Envy's uninstall function and try the install function again.

---

### Post by mateuszbaranski on 2007-05-15
The Envy script is a really piece of nice script. 
I tried everything 
1) using synaptic nvidia-glx 
2) installing  nvidia driver from site
3) different kernels
I am in linux world for more that 3 years and have been using linux for audio/video production.  After fresh install of Feisty I spent more then week on this topic and almost went creazy.
 Nvidia driver is a MUST for me but I am not a driver specialist :-)

Finally I tried Envy script. It worked well for me. 
Thank you very much - you saved my time.

---

### Post by lummer on 2007-05-15
Hi, could you please tell me how to remove Envy and the nvidia drivers from the command line?

I just used envy 0.9.4 to install the drivers for my nvidia GO 7600 but upon restart i keep getting an error and it stays at the command line.

I clicked 0.9.4 without checking,  as I've been downloading 0.9.3 a few times recently and hadnt realised there was a new version out.

Thanks in advance!!!

---

### Post by agkbill on 2007-05-15
**Only 800x600 resolution**

Envy install the driver great but I only get one resolution to chose from 800x600. In Nvidia settings there is only a "Auto" mode to chose under resolution.

I have a new instalation of Feisty Fawn and I run envy in textmode, first I uninstalled all outher nvidia and then the instalation. I used  envy_0.9.3, 0.9.4 did not work.

I have a MSI  NX7600GS  256MB DDR2, TV-Out/Dual DVI  PCIe
Monitor is a CTR Nokia 920C

I would like to use 1280x1024 85Hz witch is the recomended for my monitor.

Thank you for a great script, I would just love to get it to work all the way. :) 

Best regards!
/Christer

---

### Post by samuele78 on 2007-05-16
please can you help me to install nvidia driver on ubuntu festy 7.04?
i've tried to use Envy scripts envy_0.9.3-0ubuntu5_all.deb but it doesn't work.
i have a geforce4 go 460 on toshiba 5200-801 laptop and i know that this card should work with nvidia driver 9631.
here there are envy.log,  xorg.conf and Xorg.0.log (i have restored nv driver because the nvidia module doesn't work ). thank you for any help

---

### Post by Cappy on 2007-05-16
The non-stable didn't work for me. X error and dropped me to a command line.

From my kernel log:
```

May 16 07:03:20 cappy kernel: [   42.983769] NVRM: API mismatch: the client has the version 1.0-9631, but
May 16 07:03:20 cappy kernel: [   42.983771] NVRM: this kernel module has the version 1.0-9755.  Please
May 16 07:03:20 cappy kernel: [   42.983773] NVRM: make sure that this kernel module and all NVIDIA driver
May 16 07:03:20 cappy kernel: [   42.983774] NVRM: components have the same version.
May 16 07:03:21 cappy kernel: [   43.630987] eth0: no IPv6 routers present
May 16 07:03:24 cappy kernel: [   47.024273] NVRM: API mismatch: the client has the version 1.0-9631, but
May 16 07:03:24 cappy kernel: [   47.024275] NVRM: this kernel module has the version 1.0-9755.  Please
May 16 07:03:24 cappy kernel: [   47.024277] NVRM: make sure that this kernel module and all NVIDIA driver
May 16 07:03:24 cappy kernel: [   47.024279] NVRM: components have the same version.
May 16 07:03:28 cappy kernel: [   51.080069] NVRM: API mismatch: the client has the version 1.0-9631, but
May 16 07:03:28 cappy kernel: [   51.080071] NVRM: this kernel module has the version 1.0-9755.  Please
May 16 07:03:28 cappy kernel: [   51.080072] NVRM: make sure that this kernel module and all NVIDIA driver
May 16 07:03:28 cappy kernel: [   51.080074] NVRM: components have the same version.

```

64-bit feisty, 7900GS. I had already downloaded the nvidia sh installer so I then ran it from the command line and it worked perfectly.
I had previously used the drivers that installed automatically with Feisty and I didn't uninstall them before I used Envy.

In the zip are my nvidia.log and envy.log

---

### Post by RocknrollNurse on 2007-05-16
I am unfortunate not to be able to get a driver with 3d acceleration running on Feisty. I'm running a fully updated and upgraded dist. on an AMD at 1050 mhz (slow), with a GeForce4 MX 4000 AGP card.  I'm not sure what else is distinct about my system, because everyone else seems to have been able to get NVIDIA cards working (even the same model), and I am at my wits end.  Using a manual install (aptitude) of the nvidia-glx driver, I was eventually able to get a working desktop -- I originally switched from NV because of extremely poor performance with simple programs like firefox and abiword (slow, despite about 460 ram).  However, this has been the greatest fruition of my hours and hours of labor.  A working GNOME Xwindows desktop that is fully satisfactory, but without any 3d acceleration whatsoever (no screensavers, desktop effects).  With Envy, I am unable even to overcome the problems with x windows that the manual install eventually got me past, and I have never been able to establish working 3d acceleration.  It is so frustrating.  I can give you any readouts, cat any config files, and inform about any hardware on the system -- can anybody help me?

---

### Post by Baboontu on 2007-05-16
Hello
I've  downloaded envy version 9.3.5 in order to install nvidia driver on Feisty , graphic card: nvidia mx 440. according to envy's site this ver. should have, by now, resolved the problems with my card.
I've installed it (verified that I didn't have any other version installed). then I rebooted to the generic kernel and nothing happened - only this *** black screen again. only restart could help me (no ctrl+alt+F1). even "safe mode" couldn't help me to revert to the last working xorg.conf I backed up.
so I booted to mandriva spring 2007 (which recognized my card automatically) to ask for help. 
when will I be able to run beryl on Ubuntu like I run it on Mandriva?
I attached xorg.log
please help me - I tried it so many time without any success.:( 
Thanks in advance

---

### Post by Cappy on 2007-05-16
Baboontu, you have to use the legacy nvidia drivers. 1.0-96xx. Ubuntu automatically installs these when you goto System-->Preferences-->Desktop Effects. You shouldn't need Envy.

---

### Post by Baboontu on 2007-05-16
Thanks Cappy . I've already tried that before to no avail , but I'll try again and post what happened.

---

### Post by SnoopDeVille on 2007-05-18
> **Cappy said:**
> The non-stable didn't work for me. X error and dropped me to a command line.

From my kernel log:
```

May 16 07:03:20 cappy-chan kernel: [   42.983769] NVRM: API mismatch: the client has the version 1.0-9631, but
May 16 07:03:20 cappy-chan kernel: [   42.983771] NVRM: this kernel module has the version 1.0-9755.  Please
May 16 07:03:20 cappy-chan kernel: [   42.983773] NVRM: make sure that this kernel module and all NVIDIA driver
May 16 07:03:20 cappy-chan kernel: [   42.983774] NVRM: components have the same version.
May 16 07:03:21 cappy-chan kernel: [   43.630987] eth0: no IPv6 routers present
May 16 07:03:24 cappy-chan kernel: [   47.024273] NVRM: API mismatch: the client has the version 1.0-9631, but
May 16 07:03:24 cappy-chan kernel: [   47.024275] NVRM: this kernel module has the version 1.0-9755.  Please
May 16 07:03:24 cappy-chan kernel: [   47.024277] NVRM: make sure that this kernel module and all NVIDIA driver
May 16 07:03:24 cappy-chan kernel: [   47.024279] NVRM: components have the same version.
May 16 07:03:28 cappy-chan kernel: [   51.080069] NVRM: API mismatch: the client has the version 1.0-9631, but
May 16 07:03:28 cappy-chan kernel: [   51.080071] NVRM: this kernel module has the version 1.0-9755.  Please
May 16 07:03:28 cappy-chan kernel: [   51.080072] NVRM: make sure that this kernel module and all NVIDIA driver
May 16 07:03:28 cappy-chan kernel: [   51.080074] NVRM: components have the same version.

```

64-bit feisty, 7900GS. I had already downloaded the nvidia sh installer so I then ran it from the command line and it worked perfectly.
I had previously used the drivers that installed automatically with Feisty and I didn't uninstall them before I used Envy.

In the zip are my nvidia.log and envy.log

I have the same card and im finding it rather difficult to install the drivers...main reason is that 
when i reboot my screen isnt configured properly in the xorg.conf so i always have to revert back with the backup .

Can u please tell me how you managed to install the driver ? I tried everything now , but with no avail :/

Desperate ! :)

---

### Post by Cappy on 2007-05-18
Sure, here is the process I used:
```

sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo apt-get install nvidia-glx-new

```
The nvidia-glx-new are the newest nvidia drivers. The legacy drivers for the older video cards are just "nvidia-glx".

X didn't startup correctly the first time so I had to run 
```

sudo apt-get install nvidia-glx-new
``` 
again once I was dropped to a command line.
In both cases where I used this in the last couple of days I already had nvidia-glx installed (automatically from System-->Administration-->Restricted Drivers Manager).

I ended up using this method because the nvidia's sh installer caused horrible FPS stuttering in my games.

---

### Post by SnoopDeVille on 2007-05-18
I succesfully installed it many times the problem was that my xorg.conf wasn't the same.
On the first look i think i saw the IdBus (2:0:0) under Device for nvidia card was missing...not sure if there was something else.

What did u mean by the X failed at start ? ...

Am i supposed to configure Xorg.conf myself if your solution won't work..or should i just re-backup it and leave it be :) ? 

Ty for the uber-fast reply! :P

P.s. Im Kinda used to it since dumb me tried Installing Ubuntu Edgy (amd64) when i didn't know anything about it :) 
Had it all working...but Feisty looked so promising i just had to try it ^__^..

P.s.s. do you see the Nvidia Logo at boot ? (just before u login) ?

Hm oky it didn't work , always the blue Xsever screen of death at boot :) 
What now ? :)

---

### Post by Jiroo on 2007-05-18
> **tseliot said:**
> 
"sudo nvidia-glx-config enable" should keep your xorg.conf compatible with debconf but will fail if you edited xorg.conf manually.

And how can I config glx once xorg.conf is edited...?
Thanks

---

### Post by tseliot on 2007-05-18
> **Jiroo said:**
> And how can I config glx once xorg.conf is edited...?
Thanks
```
sudo nvidia-xconfig
```

---

### Post by tseliot on 2007-05-18
> **samuele78 said:**
> please can you help me to install nvidia driver on ubuntu festy 7.04?
i've tried to use Envy scripts envy_0.9.3-0ubuntu5_all.deb but it doesn't work.
i have a geforce4 go 460 on toshiba 5200-801 laptop and i know that this card should work with nvidia driver 9631.
here there are envy.log,  xorg.conf and Xorg.0.log (i have restored nv driver because the nvidia module doesn't work ). thank you for any help

You need to solve a little problem first:
```
sudo dpkg-divert --rename --remove /usr/X11R6/lib/libGL.so.1
```

---

### Post by tseliot on 2007-05-18
> **agkbill said:**
> **Only 800x600 resolution**

Envy install the driver great but I only get one resolution to chose from 800x600. In Nvidia settings there is only a "Auto" mode to chose under resolution.

I have a new instalation of Feisty Fawn and I run envy in textmode, first I uninstalled all outher nvidia and then the instalation. I used  envy_0.9.3, 0.9.4 did not work.

I have a MSI  NX7600GS  256MB DDR2, TV-Out/Dual DVI  PCIe
Monitor is a CTR Nokia 920C

I would like to use 1280x1024 85Hz witch is the recomended for my monitor.

Thank you for a great script, I would just love to get it to work all the way. :) 

Best regards!
/Christer

You might want to ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by tseliot on 2007-05-18
> **Cappy said:**
> The non-stable didn't work for me. X error and dropped me to a command line.

From my kernel log:


Try Envy's Uninstall function and then the install function

---

### Post by Cappy on 2007-05-18
> **tseliot said:**
> Try Envy's Uninstall function and then the install function

It didn't work, I tried it once I installed from nvidia's sh script because it didn't work correctly. I used envy to uninstall and the install the nvidia drivers. It didn't work, same error.

---

### Post by Cappy on 2007-05-18
> **SnoopDeVille said:**
> I succesfully installed it many times the problem was that my xorg.conf wasn't the same.
On the first look i think i saw the IdBus (2:0:0) under Device for nvidia card was missing...not sure if there was something else.

What did u mean by the X failed at start ? ...

Am i supposed to configure Xorg.conf myself if your solution won't work..or should i just re-backup it and leave it be :) ? 

Ty for the uber-fast reply! :P

P.s. Im Kinda used to it since dumb me tried Installing Ubuntu Edgy (amd64) when i didn't know anything about it :) 
Had it all working...but Feisty looked so promising i just had to try it ^__^..

P.s.s. do you see the Nvidia Logo at boot ? (just before u login) ?

Hm oky it didn't work , always the blue Xsever screen of death at boot :) 
What now ? :)

There's nothing wrong with the xorg.conf changing during driver installation if your X is still working. 

I don't see the nvidia logo because it was automatically disabled in the xorg for me.
Here is that line in the /etc/X11/xorg.conf for enabling or disabling the logo.
```

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7900 GS]"
        Driver          "nvidia"
        Busid           "PCI:6:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

```

If you already have 3D acceleration, I say screw it unless you're trying to squeeze every ounce of power out of your video card. I notice Oblivion is a little smoother for me, but nothing too drastic. If installing nvidia-glx-new doesn't work, you could always reinstall nvidia-glx. Having a backed up xorg wouldn't hurt though.

Oh I didn't see you already tried it =P Try repeating the same process now that X won't start. I don't know why, but that did it for me.

---

### Post by SnoopDeVille on 2007-05-18
Thanks for your immense help ! 

After all i decided to edit my xorg.conf after a fresh install of the drivers.
Took some tweaking but i managed everything , even giving all the buttons to my G5 mouse ! :)

So it all looks fine now, but the main problem is .......don't laugh now ....seriously.......

How do i know if the drivers are actually working as intended  ?   ^___^
Times like these i wish i knew more about C++ programing...reverse engineering etc. :P 

P.s.    a big <3 for your Xorg.conf info u posted :)

---

### Post by rickdog on 2007-05-18
Do I need to uninstall the nvidia glx drivers that installed with 7.04 before running envy?

---

### Post by Cappy on 2007-05-18
> **SnoopDeVille said:**
> Thanks for your immense help ! 

After all i decided to edit my xorg.conf after a fresh install of the drivers.
Took some tweaking but i managed everything , even giving all the buttons to my G5 mouse ! :)

So it all looks fine now, but the main problem is .......don't laugh now ....seriously.......

How do i know if the drivers are actually working as intended  ?   ^___^
Times like these i wish i knew more about C++ programing...reverse engineering etc. :P 

P.s.    a big <3 for your Xorg.conf info u posted :)

```

glxinfo | grep rendering
```
That should return: "direct rendering: Yes"
The 3D screensavers (System-->Preferences-->Screensaver) should also be working.

---

### Post by SnoopDeVille on 2007-05-19
It works :) 3x Cheers ! ;) 

Envy is good also, still needs some tweaks tho :P

Thank you !

---

### Post by Fyrehardt on 2007-05-20
Thank You!!!!  I registered for these forums just so I could figure out how to get my video card working, and this guide was an absolute lifesaver for a complete noob like me.  Only problem I had was that my mouse pointer did indeed go missing, and I couldn't for the life of me remember how to edit xorg.conf....but some googling reminded me!  Thank you! \\:D/

---

### Post by tseliot on 2007-05-20
> **Cappy said:**
> It didn't work, I tried it once I installed from nvidia's sh script because it didn't work correctly. I used envy to uninstall and the install the nvidia drivers. It didn't work, same error.

Follow point B of the Frequently asked questions:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by Cappy on 2007-05-20
> **tseliot said:**
> Follow point B of the Frequently asked questions:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

Ah, I see. I should have used text mode. 
I was trying to make sense of [http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html), I didn't make it to the wiki.
If I could make a suggestion: maybe the FAQ link on the download page should be at the top of the envy page instead of at the bottom.

---

### Post by arthyko on 2007-05-20
hi, first of all sorry about my english.

got nvidia fx 5200 (128mb), fresh install feisty, downloaded and executed envy's stable script, reboot and ubuntu logo apears then the monitor turned off, tipped ctrl+alt+f1, logged and then ctrl+alt+f7, after that the monitor comes alive.

what's wrong?

thx

---

### Post by themis on 2007-05-21
Hi, I've been experiencing some problems ,trying to install the nvidia driver on my toshiba 5200-801,which uses NVidia GeForce4 460 Go.
First I used the restricted drivers manager,which results a grey screen.
Then I swithced to "nv",and then been trying the first method, which also results on the same grey screen,
again and again.
I've also used
       $sudo dpkg-divert --rename --remove /usr/X11R6/lib/libGL.so.1
suggested to samuele78,using the same laptop, a few posts before,but I get:
       No diversion `any diversion of /usr/X11R6/lib/libGL.so.1', none removed

What should I do?
Thanks!

---

### Post by dannyboy79 on 2007-05-21
> **tseliot said:**
> Follow point B of the Frequently asked questions:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

Just so you are aware, I believe there is a bug in the Envy Unstable script.

 I troubleshot the API mismatch for about 2 hours with the help of a forum user that goes by the screen name psyke83 or somethign very similar to that. HE was helping me thru gaim (IM). 

He tried to have me add blacklist nvidia_new to the /etc/modprobe.d/blacklist file, BUT that still didn't work, NO module was loading when we tried that and that fix DID work for psyke83 so we weren't sure why it didn't work on my machine? I also ensure that my /etc/defaults/linux-blah-blah-blah-common DID have the Disabled MOdules = "nv" within it and it STILL DIDN'T WORKL.

It turned out that the Envy unstable program had a bug and didn't do somethign correctly (if this is an untrue statement, I am only conveying the message that psyke83 informed me of. He said that he tried telling the author of Envy but the author of Envy said there was no bug. Then psyke83 even tried the unstable version on his own computer and tried to install 100.xx.xx and he got the same API mismatch error). 

So the soltuion was to add a hack to my rc.local file so that the correct nvidia kernel module would load. This is what I added BEFORE the exit 0 within the rc.local file:
find /lib/modules/`uname -r` | grep -i nvi | grep -v fb | grep nvidia.ko$ | xargs insmod
and finally the damn 100.xx.xx kernel module would load. BUT to no avail, random freezing is STILL OCCURING!!!! I have posted a million times in various threads about Fiesty freezing on simple tasks, like gedit, or various config dialog boxes opened thru System, Admin or Prefs. ANyway, I thoguht I'd at least let other know about the solution if they get teh dreaded API mismatch error when the nvidia driver is 100.xx.xx but the module being loaded was 9755 when they used Envy Unstable.

---

### Post by dannyboy79 on 2007-05-21
> **Cappy said:**
> The non-stable didn't work for me. X error and dropped me to a command line.

From my kernel log:
[CODE]
May 16 07:03:20 cappy-chan kernel: [   42.983769] NVRM: API mismatch: the client has the version 1.0-9631, but
May 16 07:03:20 cappy-chan kernel: [   42.983771] NVRM: this kernel module has the version 1.0-9755.  Please
May 16 07:03:20 cappy-chan kernel: [   42.983773] NVRM: make sure that this kernel module and all NVIDIA driver

Just so you are aware, I believe there is a bug in the Envy Unstable script.

 I troubleshot the API mismatch for about 2 hours with the help of a forum user that goes by the screen name psyke83 or somethign very similar to that. HE was helping me thru gaim (IM). 

He tried to have me add blacklist nvidia_new to the /etc/modprobe.d/blacklist file, BUT that still didn't work, NO module was loading when we tried that and that fix DID work for psyke83 so we weren't sure why it didn't work on my machine? I also ensure that my /etc/defaults/linux-blah-blah-blah-common DID have the Disabled MOdules = "nv" within it and it STILL DIDN'T WORKL.

It turned out that the Envy unstable program had a bug and didn't do somethign correctly (if this is an untrue statement, I am only conveying the message that psyke83 informed me of. He said that he tried telling the author of Envy but the author of Envy said there was no bug. Then psyke83 even tried the unstable version on his own computer and tried to install 100.xx.xx and he got the same API mismatch error). 

So the soltuion was to add a hack to my rc.local file so that the correct nvidia kernel module would load. This is what I added BEFORE the exit 0 within the rc.local file:
find /lib/modules/`uname -r` | grep -i nvi | grep -v fb | grep nvidia.ko$ | xargs insmod
and finally the damn 100.xx.xx kernel module would load. BUT to no avail, random freezing is STILL OCCURING!!!! I have posted a million times in various threads about Fiesty freezing on simple tasks, like gedit, or various config dialog boxes opened thru System, Admin or Prefs. ANyway, I thoguht I'd at least let other know about the solution if they get teh dreaded API mismatch error when the nvidia driver is 100.xx.xx but the module being loaded was 9755 when they used Envy Unstable.

---

### Post by stchman on 2007-05-21
> **tseliot said:**
> Hi, I've ported my guide about the Nvidia Drivers to Edgy Eft on the USDF.
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

OR try this mirror:

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)


--------------------------------------------------------------------
Script to make Method 2 faster

You can also use my Envy script which you can find below (for automating Method 2 and solving problems of driver mismatch)

NOTE: this might be dangerous and buggy

This script will download the Nvidia installer (and all the files the installer needs) and set the driver for you.

Get to the following website:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And follow the instructions you will find there.

I just used the Restricted Drivers in Administration.  It will install either Nvidia or ATI driver.  Reboot and done.  Now you need to install either sys-info or go to terminal and type nvidia-settings to get to the video card menu.

---

### Post by sab0403 on 2007-05-23
Hi,

I followed the guide to the letter, and while typing

> glxinfo | grep rendering

returns

> direct rendering: Yes

I can't get any resolution (higher or lower) besides 800x600, @50 Hz. They don't show up on the "Screen Resolution Preferences" Window, nor on the Nvidia tool.

I'm using a **GeForce4 MX 440 (AGP 4X**); I already followed Step 7 on the Problems section (and tried all three options).

Any guidance would be appreciated. Thanks.

---

### Post by zasf on 2007-05-24
Alberto,

what is the difference between envy and the [restricted driver manager]("https://launchpad.net/restricted-manager/")? sorry if this has been answered elsewhere, but I couldn't find it, still I believe this question deserves to be answered in Envy's FAQs.

To the best of my knowledge, I'll try to list the differences:
[LIST]
[*]envy takes care of graphics drivers only (nvidia and fglrx), not other drivers (wireless, etc) as r-d-m does
[*]envy, if updated, can install updated version of the drivers, while r-d-m sticks to what is available in repos (please confirm)
[*]r-d-m is supported by Ubuntu
[*]...
[/LIST]

Did I miss something?

Matteo

---

### Post by dannyboy79 on 2007-05-24
the only difference is that envy allows you to manually install a certain version of the driver whereas the restricted driver manager will install the latest stable driver for the card it detects. Meaning for recent Nvida Cards it would install the 9755 I believe, older ones would be the one previous and I am not an ATI person so I don't know what driver Envy installs for ATI. The envy you have the opportunity to install the latest beta driver from nvidia if you downloaded Envy 0.9.4 as well as the older ones from nvidia. Hope this answers you question and if I am missing something than I apologize, Tseliot would be the best person to answer this since he is the developer.
Obviously the other differences are also the ones that you mentioned above.

---

### Post by zasf on 2007-05-24
thanks for your reply that answered my question, the biggest difference is that envy downloads the latest version and builds the module, so this allows to have a more updated version than what is in repos, eventually built for a custom kernel.

Matteo

---

### Post by dannyboy79 on 2007-05-24
right on, I thought that's what I had stated.

---

### Post by deesto on 2007-05-24
> **tseliot said:**
> type:
```
sudo dpkg-divert --rename --remove /usr/lib/xorg/modules/extensions/libglx.so
```

then use Envy's uninstall function and try the install function again.

Thanks, but this resulted in:
```
No diversion `any diversion of /usr/lib/xorg/modules/extensions/libglx.so', none removed
```

---

### Post by KManZ on 2007-05-24
I too have the 7900 GS, and I am so lost on this.. :( I can't get it to install any driver... when I use Envy, I get the blue/gray screen that says the X server failed to start. I have downloaded nvidia-glx-new from Synaptic, and still it does nothing. How do I get it to show up in the Restricted Drivers Manager? I know when I fresh installed earlier a driver from nvidia was listed there. 

Someone just please help... walk me through from the beginning to the end so I can have some graphics. 

Honestly though.. Linux is great, but things like this put it LIGHTYEARS away from being adopted by the general public. :(

---

### Post by KManZ on 2007-05-25
Belay my last order :KS Somehow, someway, the drivers installed themselves.. by some alignment of the planets I now have everything enabled after 2 days of sheer torture sitting glued, behind my desk. I haven't smiled this big in a while! 

I don't remember exactly how I did it, but I know that it had something to do with the nvidia-kernel and the linux-restricted-modules being the same release number! Once I retried installing with Envy, the missing nvidia-kernel-2.6.20-16 appeared!

Lastly, Envy tried to install the nvidia-gxl driver. I was told to use the nvidia-gxl-new, so I uninstalled gxl and installed gxl-new. I then restarted, and BAM! SUCCESS! The driver is working, the Nvidia control panel is working. Life is good. I need sleep now.

---

### Post by fredramsey on 2007-05-25
Envy seemed to work great, but now the GUI will not launch. Tries to, but finally displays this error:

" Failed to start the X server (your graphical interface). It is likely it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

Ubuntu 7.04
7600 GTS
x86_64

Any immediate ideas? Any way to undo what Envy did from the command line?

Thanks!

:confused:

(Linux Newbie)

---

### Post by dannyboy79 on 2007-05-25
after X fails, and you get the cli, log in anyway and try out this command
dmesg | grep NVIDIA
and tell me if it says anything about API mismatch. THis is a very common issue. Have you added "nv" to the /etc/default/linux-restricted-modules-common file? (i may be off a little bit on the name but the file is definitely within the /etc/default/ folder and it's a long name and it has common at the end of it's name) After you edit that file and put the "nv" within the quotes, then save the file. Oh, you can use nano as the none gui text editor I feel it's the easiest but once you become more experienced vi (vim) is way more versatile. The common commands, find, save, close, etc etc are at the bottom of the nano screen if you're not sure how to save and close the file.

THen issue these commands

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
If you get to a gui login screen than it should be fixed. If X still fails than we have another issue. Which version of Envy did you install, and hten which version of the nvidia driver did you install or did you just chose the auto install within Envy?

---

### Post by fredramsey on 2007-05-25
Thanks, I will try that out this evening.

---

### Post by phoenix23 on 2007-05-25
> **dannyboy79 said:**
> after X fails, and you get the cli, log in anyway and try out this command
dmesg | grep NVIDIA
and tell me if it says anything about API mismatch. THis is a very common issue. Have you added "nv" to the /etc/default/linux-restricted-modules-common file? (i may be off a little bit on the name but the file is definitely within the /etc/default/ folder and it's a long name and it has common at the end of it's name) After you edit that file and put the "nv" within the quotes, then save the file. Oh, you can use nano as the none gui text editor I feel it's the easiest but once you become more experienced vi (vim) is way more versatile. The common commands, find, save, close, etc etc are at the bottom of the nano screen if you're not sure how to save and close the file.

THen issue these commands

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
If you get to a gui login screen than it should be fixed. If X still fails than we have another issue. Which version of Envy did you install, and hten which version of the nvidia driver did you install or did you just chose the auto install within Envy?

Hello.

I'm having a similar problem. I installed the Nvidia driver through Restricted Driver thing, and now I can't load the GUI. I don't see anything about an API error in dmesg grep, but I followed your steps and still can't get to the gui.

---

### Post by fredramsey on 2007-05-25
> **dannyboy79 said:**
> after X fails, and you get the cli, log in anyway and try out this command dmesg | grep NVIDIA

I finally had to re-install, but that's OK, I hadn't really installed anything yet.

I did NOT install the restricted NVIDIA drivers! Very Important! Future versions should check for that.

I ran Envy again, and all is well.

The only thing I can't really figure out is how to have it use the DVI side of my lcd all the time, so for now I have up and am using the analog connection.

But I did get my full 1920x1200 by adding it to the conf file.

Thanks!

:D

---

### Post by dannyboy79 on 2007-05-25
UPDATE FROM ME.
I originally thought this freezing may have been from the nvidia modules BUT
I am happy to inform everyone that a fresh install of Fiesty (no other hardware changes) has fixed the issue of the frozen commands when using gksu or gksudo which would eventually bring gnome-session and or X-server and or gnome-panel to it's knees. Meaning I could only exit to a tty or ssh into the box to restart it. So it obviously had something to do with something I installed along the way. Apps include pretty much everything in Automatix2, rkhunter, chkrootkit, tripwire, Exim4 and then sendmail, samba as a local master browser, and ssh. I can't think of much else I installed. Obviously the nvidia from the restricted modules manager, then the 100.xx.xx which both had this freeze. Then the freeze even occured in nv and vesa so who knows what the cause of it was I am just glad it's gone and I'll be sure to check it before and after every single I install!!!

There are 2 errors I am getting now that I am not applying any boot options like noapic or nolapic, they are:

[    2.937741] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df85989c), AE_BAD_HEADER
[    2.937854] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df8597fc), AE_BAD_HEADER

We'll see how it goes from here.

Fredramsey, what do you mean about using the dvi side of your lcd all the time, plug you computer into the dvi port and that should be it. I am not sure at all what you're referring to with this question.

---

### Post by RomeJones on 2007-05-26
Thanks Man,
This guide really helped me out.  I *gasp* almost switched back to windows for fear that I would never get my drivers right.  I had to go through a couple of extra steps that I'll outline below for any one with a similar setup to mine.

The Specs:
I've got a Dell 20" WideScreen monitor (I think it's an FPW 2005 or something) which has a recommended resolution of 1680x1050.  I'm running an Nvidia FX 5200.  They are connected via VGA.  

The Details:
Out of the box Ubuntu wasn't displaying correctly.  I went through the steps of your HOWTO and then X wouldn't come up.  Luckily, I managed to skip the step where you back up your xorg.conf.  So I had to make another (following your directions).  Well, this X displayed much better than the out of the box X (don't know why).  So i went through the steps again.  Well, I got the NVIDIA logo at boot so I new I was in business (I have no idea why it took this time).  However, when i went to change the screen resolution there wasn't an option for 1680x1050.  So I had to manually edit xorg.conf.  I put in "1680x1050" on every line under 'Screen'.  After that I rebooted X and everything looked great.  

Your howto is fantastic.  Thanks a bunch.

---

### Post by fredramsey on 2007-05-26
> **dannyboy79 said:**
> Fredramsey, what do you mean about using the dvi side of your lcd all the time, plug you computer into the dvi port and that should be it. I am not sure at all what you're referring to with this question.

I have both cables hooked up, so NVIDIA settings shows two screens.

Are you saying if I just have the one cable hooked up it should work?

---

### Post by dannyboy79 on 2007-05-26
> **fredramsey said:**
> I have both cables hooked up, so NVIDIA settings shows two screens.

Are you saying if I just have the one cable hooked up it should work?
I still don't understand? How many computers do you have hooked to your LCD? If it's just 1 than you shouldn't be using both the VGA and the DVI, that'll do you know good and I see no point in doing so. Just hook the dvi connector to the LCD and that's it. I still have to admit, I am very confussed on what your setup is and what you're trying to accomplish. 

My setup:
Only 1 17" FLat Panel LCD
2 Computers
1 KVM switch with audio, keyboard, mouse, and vga.
Since my LCD has 2 inputs, DVI and Analog, I have chosen to NOT use the KVM switch for the video and went straight from the Winbloz box which has a ATI AWI 9800 Pro DVI out to the DVI In on the LCD. Then my Ubuntu box has a GeForce 6200 128mb so I hooked that Analog straight to the LCD Analog in. So when I want to go back and forth between the boxes, I hit Scroll Lock 2 times which switches the audio, keyboard, and mouse, then I hit the Input Selector switch on the LCD Monitor to change it between Analog and Digital depending on whether I want to use Ubuntu or Winbloz. Hopefully this will clear up any confussion you may be having or maybe you can explain better what your setup is and what exactly you're trying to accomplish. Peace out.

---

### Post by fredramsey on 2007-05-26
> **dannyboy79 said:**
> I still don't understand?

Under Windows I always had both cables hooked up, that way I could switch between the two (a long time ago I ran into a game that didn't work well through the DVI - I kept it that way out of habit.

One PC. One Monitor.

So, at the risk of being repetitive, you think that having just the DVI cable hooked up should work? What about the existing configs?

---

### Post by eks on 2007-05-26
Hello,

Today I changed my graphic board from an ATI to an nVidia (Leadtek Winfast px8500, it's a 8500gt). The [change was smooth]("http://ubuntuforums.org/showthread.php?p=2726088"), until I tried to install nVidia proprietary drivers. First I tried Restricted Drivers Manager, which was accusing I didn't needed any restricted drivers. Then I went for Envy. When trying the automatic install, it gives this error in the log:

```

python pulse.py nvidia 
root@domub:/usr/share/envy# python pulse.py nvidia 
Ubuntu Feisty 64bit
ENVY ERROR: Envy does not recognise your card as compatible with any version of the driver.                    this might happen because either your card is not supported by the driver or Envy's hardware                    detection failed. You can try the manual installation at your risk.

```

I tried the manual install, which went smoothly. Until I enabled nVidia drivers on xorg.conf with nvidia-xconfig. When I try to reset X, it gives an error, something like:

```

Failed to load the nVidia kernel
/lib/modules/2.6.20-15-generic/nvidia/nvidia.ko

```

I went for that folder and it doesn't exist. I tried to re-install linux-restricted-modules-2.6.20-15-generic and still no /nvidia there. Even after also re-installing the drivers either with Envy or Synaptic.

Any ideas?

I'm attaching xorg.conf and Xorg.0.log.

I think I purged fglrx and ATI stuff from everywhere...


eks
PS: Btw, really thanks for the program! :)

---

### Post by Cappy on 2007-05-26
The 8500 needs the beta nvidia driver (100.14.03 I think). I've only seen the actual shell script from the nvidia website. I'm not sure if it is supported by envy yet.

---

### Post by dannyboy79 on 2007-05-26
that's supported by Envy Unstable. Then you do the manual install option. Good luck.

---

### Post by Baboontu on 2007-05-26
> **Cappy said:**
> Baboontu, you have to use the legacy nvidia drivers. 1.0-96xx. Ubuntu automatically installs these when you goto System-->Preferences-->Desktop Effects. You shouldn't need Envy.

Hi 
I installed through kubuntu kcontrol and it didn't work.
later I installed nvidia-glx in by the instruction of [[COLOR="DarkSlateBlue"]Latest nvidia feisty[/COLOR]]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#HOWTO:_Latest_NVIDIA_drivers") -method 1
I did cold reboot and then the notorious black screen again! oooff
what have I done to deserve this??
I will be  very grateful if someone  could examine the log file and my xorg.conf attached. 
thanks

---

### Post by rusyear04 on 2007-05-29
hello alltogether!

i'm having serious troubles with my nvidia driver/graphic card.
first i upgraded 6.10 -> 7.04 and tried to install "restricted drivers" for my nvidia card (supposingly FX 5600XT). this did result in a blank screen after booting. i srewed around a bit and found, that the gui (Xserver) only worked with the "nv" driver used (in xorg.conf).

since i read that there might be troubles with my previously installed proprietary drivers (6.10 worked almost fine) i screwed around more but did not reach anything.

thus i installed fesity from scratch (cd).
i then updated the software (another reboot) and then turned on the restricted driver" in system>admin
result: GUI did not work (with "nvidia" as driver in xorg.conf). a switch back to the "nv" driver and i get a display...

i now wanted to install by the HOWTO [http://doc.gwos.org/index.php/Latest_nvidia_feisty]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") but it says that method 1 requires a graphics card from the NOTES section... mine is not in it.

i am really growing desperate over this whole stuff... can somebody please help me?
thanx!

ps: is it normal that firefox is jerking/bucking when scrolling??? shouldn't be, or?? is there a possibility to remove this?

---

### Post by dannyboy79 on 2007-05-29
> **rusyear04 said:**
> hello alltogether!

i'm having serious troubles with my nvidia driver/graphic card.
first i upgraded 6.10 -> 7.04 and tried to install "restricted drivers" for my nvidia card (supposingly FX 5600XT). this did result in a blank screen after booting. i srewed around a bit and found, that the gui (Xserver) only worked with the "nv" driver used (in xorg.conf).

since i read that there might be troubles with my previously installed proprietary drivers (6.10 worked almost fine) i screwed around more but did not reach anything.

thus i installed fesity from scratch (cd).
i then updated the software (another reboot) and then turned on the restricted driver" in system>admin
result: GUI did not work (with "nvidia" as driver in xorg.conf). a switch back to the "nv" driver and i get a display...

i now wanted to install by the HOWTO [http://doc.gwos.org/index.php/Latest_nvidia_feisty]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") but it says that method 1 requires a graphics card from the NOTES section... mine is not in it.

i am really growing desperate over this whole stuff... can somebody please help me?
thanx!

ps: is it normal that firefox is jerking/bucking when scrolling??? shouldn't be, or?? is there a possibility to remove this?

oK, forget about the restricted module, I don't know why its not working for you, probably not identifying your card correctly and installing the wrong module. This is what you should do. first, make sure you remove and purge anything and everything related to nvidia THRU synaptic package manager. do a search for nvidia within synaptic and do  a COMPLETE removal of all of it all. 
Also, just so you are aware, I read the same link that you supposedly read and found this in the list of approved cards for the latest stable driver from nvidia, GeForce FX 5600XT and that's the one you have ([http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)). 
I think what you did was not realize that there was a link you should have clicked on the words "this page" but instead you scrolled to the bottom of the guide and saw the list of super old cards supported by the legacy driver and you didn't see your card and thought, "oh no, i can't use this driver". 

So all you have to do is follow step 1 BUT make sure that you also edit the /etc/default/linux-restricted-modules-common file and add "nv" in between the quotes so that the nv module doesn't get loaded, do that before you restart your x-server, you can do that by hitting ctrl-alt-backspace. good luck

---

### Post by rusyear04 on 2007-05-29
no luck so far...
i did follow your/the procedure. after a few drawbacks i am now so far, that i do hear the drums for login, but have no picture on my screen...
the problem solving related to this symptoms (from [http://doc.gwos.org/index.php/Latest_nvidia_feisty#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_nvidia_feisty#PROBLEMS_SECTION")) does not help.

i did follow *troubleshooting 10)* but still only the drums are there... monitor without a signal...

i don't know if that is normal/should be as it is:
my xorg.conf is finished after

```
Section "Screen"
 ...
EndSection

Section "Extensions"
 Option "Composite" "Disable"
EndSection
```

is this normal? shouldn't there be more entries??

---

### Post by dannyboy79 on 2007-05-30
if that's the only stuff in your xorg.conf file located within /etc/X11/ than yes, you have a problem. that's totally wrong!!!! If you're following method 1 and using the repo's than I don't understand what's occuring here? I just did this myself after the kernel upgrade. 

Ok, boot up your machine and when you here the drum roll, you should be able to hit ctrl-alt-f1 to get to a command line login. Login as usual and then do these commands (NOTE: if you can't get to a command line login using ctrl-alt-f1 than you may need to boot to recovery and edit your xorg.conf to use vesa right off the bat so you can work within a gui desktop environment. if the recovery mode doesn't work either, than boot to a live cd, mount your partition that contains your /etc/X11/xorg.conf and edit it thru the live cd)

```
sudo aptitude --purge remove nvidia-glx-new
```
```
sudo aptitude --purge remove nvidia-glx
```
```
sudo aptitude --purge remove nvidia-glx-legacy
```
(NOTE: these next 4 I don't think you have to do BUT if you try everything else and it still doesn't work than you can try all this over but using these next 4 steps as well)
```
sudo aptitude --purge remove nvidia-kernel-1.0.7184
```
```
sudo aptitude --purge remove nvidia-kernel-1.0.8774
```
```
sudo aptitude --purge remove nvidia-kernel-1.0.9631
```
```
sudo aptitude --purge remove nvidia-kernel-1.0.9755
```

after all that I want you to do this,
```
sudo dpkg-reconfigure xserver-xorg
```
this will run debconf (blue screen with questions etc etc. don't get intimidated!!!) and just pick the vesa driver which is the very first question. then all the following questions just answer to the best of your knowledge, keyboard layout etc etc. If you don't know an answer it's ok, just chose the default (i have to stress that, it's OK, just pick the default for anything you don't know!!!). then when that's done enter this command to ensure that before we restart nothing related to nvidia is being loaded. We need to edit the /etc/default/linux-restricted-modules-common file so that it has this in it DISABLED_MODULES="nv"
```
gksudo gedit /etc/default/linux-restricted-modules-common
```
put the **nv** within the quotes and save the file and exit. then issue this which will restart your entire machine from ground up.
```
sudo shutdown -r now
```
Now when your machine restarts you should have a gui login because it should be using the vesa driver which works on pretty much all hardware. If you type in this command
```
dmesg | grep NVIDIA
```
there better not be anything that returned from that referencing the nvidia driver because we removed and purged it all. If there is let me know and we'll have to talk some more. Also, when you do this
```
cat /etc/X11/xorg.conf | grep Driver
```
you should get back "vesa" at the end of the results which means that the xserver is using the vesa driver.
Now, basically just like method 1 says, do this
figure out your kernel by issuing these commands from a terminal
```
uname -r
```
Then whatever that resturns, whether it's -386 or whatever, then use that for the next command.
```
sudo aptitude install linux-generic
```
```
sudo aptitude install nvidia-glx-new
```
(NOTE: this is if your card is the FX5700
```
sudo nvidia-xconfig --no-composite
```
Using your favorite text editor, open the current xorg.conf located within /etc/X11/ using sudo and make that the Driver line reads nvidia instead of vesa. Ensure that you save the file before closing.
Also, there is a bug possibly with the FX5900 and FX5700 so we could maybe try this out to see if it helps since your card is pretty similar to those 2.  do these commands:
gksudo gedit /boot/grub/menu.lst
look for this line, #defoptions=quite splash
and remove the word splash so that it looks like this, #defoptions=quite
and also make sure that you scroll down and look for the lines that look like this,
kernel          /vmlinuz-2.6.20-16-generic root=UUID=522585f4-bbc8-4214-b6b4-a56504723995 ro quiet splash
and make sure that "splash" is also removed from ALL the lines that look like this, whether it's under recovery or not  or wherever, if it start with "kernel" than make sure splash is gone. You won't have a pretty splash screen anymore but if you want nvidia driver and 3d acceleration than that's the price to pay. NOW, we should be set. Issue this in the terminal
```
ctrl-alt-backspace
```
and you should be brought back to the gui login screen  and you should now be using the 9755 nvidia driver. If not, than I need to see the output of these commands
```
uname -r
```
```
lspci -v
```
```
cat /etc/X11/xorg.conf | grep Driver
```

---

### Post by Cappy on 2007-05-30
```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-*

```

is much shorter

---

### Post by dannyboy79 on 2007-05-30
thanks for your huge contribution in helping rusyear04's nvidia card to work.

---

### Post by Cappy on 2007-05-30
Thank you for being rude to me when all I did was point out a better way.

---

### Post by rusyear04 on 2007-05-31
first of all: thanx a lot for you efforts and help!

unfortunatelly i'm still not running NVIDIA as driver... i did as you told me.
with 2 small "problems/uncertanities":
1) after the command **dmesg | grep NVIDIA** i did recieve:
[B][   0.000000] ACPI: DSDT (v001 NVIDIA AWARDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[  40.282572] agpgart: Detected NVIDIA nForce2 chipset[/B]
as output... not sure if it's ok.

2) **uname -r** does return:
**2.6.20-16-generic**
i'm not sure whether this means i have to use **sudo aptitude install linux-generic** or something else containing the 2.6.20-16-generic. wouldn't know what ;)

finally before coming to your code-line **sudo nvidia-xconfig --no-composite** i still have vesa as driver in the xorg.conf
after execution -regardless whether with or without the **--no-composite** string i have nvidia as driver, but no **Section "ServerLayout"**.
and the gui is gone.

to answer your questions:
```

$ uname -r
2.6.20-16-generic

$ lspci -v
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel


00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
        Subsystem: nVidia Corporation Unknown device 0c17
        Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
        Subsystem: Giga-byte Technology Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: Giga-byte Technology Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at ec00 [size=32]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at e8002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at e8003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at e8004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000a000-0000dfff
        Memory behind bridge: e6000000-e7ffffff
        Prefetchable memory behind bridge: 70000000-700fffff

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Unknown device 5002
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

01:07.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at a000 [size=64]
        Capabilities: <access denied>

01:07.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at a400 [size=8]
        Capabilities: <access denied>

01:07.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e7008000 (32-bit, non-prefetchable) [size=2K]
        Memory at e7000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Giga-byte Technology GA-8I915ME-G Mainboard
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        I/O ports at a800 [size=256]
        Memory at e700b000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 70000000 [disabled] [size=64K]
        Capabilities: <access denied>

01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e700a000 (32-bit, non-prefetchable) [size=2K]
        Memory at e7004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600XT] (rev a1) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 9123
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at e5000000 [disabled] [size=128K]
        Capabilities: <access denied>


$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "vesa"

```

comments:
1) the splash stuff i didn't try yet... my card is the FX5600XT
2) i did save the xorg.conf before execution of** sudo nvidia-xconfig --no-composite**. i use this backup currently (to access the GUI :) )

thanx a lot!

---

### Post by tseliot on 2007-05-31
> **dannyboy79 said:**
> thanks for your huge contribution in helping rusyear04's nvidia card to work.
Every contribution is welcome.

The command which Cappy posted might be useful for the user to learn a faster way to remove things.

---

### Post by rusyear04 on 2007-05-31
yap... i'm really happy about every offer of help... :)

i just wanted to add two more things that i noticed:

1) i'm not able of changing my screen resolution (with the vesa driver). although i changed it in the xorg.conf i still don't have any choice in System>Preferences>ScreenResolution

2) under System>Administration>RestrictedDriversManager now i do get a message stating
> 
Your hardware does not need any restricted drivers.


don't know if both are normal... if not, i hope this somehow helps :-k

---

### Post by tseliot on 2007-05-31
> **rusyear04 said:**
> yap... i'm really happy about every offer of help... :)

i just wanted to add two more things that i noticed:

1) i'm not able of changing my screen resolution (with the vesa driver). although i changed it in the xorg.conf i still don't have any choice in System>Preferences>ScreenResolution

2) under System>Administration>RestrictedDriversManager now i do get a message stating


don't know if both are normal... if not, i hope this somehow helps :-k

did you follow the steps which Dannyboy79 suggested?

---

### Post by rusyear04 on 2007-05-31
yes.
as posted in #82 i encountered 2 "challenges" on the way... don't know whether they are important/wrong or not...

---

### Post by dannyboy79 on 2007-05-31
> **rusyear04 said:**
>  first of all: thanx a lot for you efforts and help!

unfortunatelly i'm still not running NVIDIA as driver... i did as you told me.
with 2 small "problems/uncertanities":
1) after the command **dmesg | grep NVIDIA** i did recieve:
[B][   0.000000] ACPI: DSDT (v001 NVIDIA AWARDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[  40.282572] agpgart: Detected NVIDIA nForce2 chipset[/B]
as output... not sure if it's ok.

this is fine, I wanted to make sure it wasn't loading a module for the nvidia driver or the nvidia kernel or whatever it's called.
> **rusyear04 said:**
>  

$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "vesa"

so after you rebooted and found that your x-server was using the vesa driver, did you follow the next steps?
sudo aptitude install nvidia-glx-new
and then go from there???? After you do those steps, your xorg.conf should be automatically changed, are you saying that after you follow all my steps that your xorg.conf is still using vesa?
> **rusyear04 said:**
>  
comments:
1) the splash stuff i didn't try yet... my card is the FX5600XT
2) i did save the xorg.conf before execution of** sudo nvidia-xconfig --no-composite**. i use this backup currently (to access the GUI :) )

thanx a lot! 
1) that's fine, it prbably isn't related to that if you see your splash screen when booting up.
2) that's fine, but the xorg.conf that you're backing up should already contain the "nvidia" instead of the "vesa" one so I am not sure what steps you're not performing?

I have to be honest, I can't for the life of me beleive that you're having this much trouble doing this????????
Ok, 1 more time. Please go thru all the steps carefully BUT this time since you showed me the output  of uname -r, just do exactly what I told you for that command and don't worry about -386 or anything else:
```
sudo aptitude install linux-generic
```

Just make sure you follow what I have written down exactly and don't miss anything and post back when you've done that.

---

### Post by dannyboy79 on 2007-05-31
> **Cappy said:**
> Thank you for being rude to me when all I did was point out a better way.

well I took your comments as a way to "show me up" and I felt that it could've been worded differently than the way you worded it which would've avoided this misunderstanding or perception of your post. If that's not the case than I apologize and I thank you for the comment. I informed him the way I did so that nothing is overlooked as he is obvioulsy having a very difficult time with this which he shouldn't be.

---

### Post by Mikimike on 2007-05-31
If someone wouldn't mind having a look, I posted yesterday in another thread the troubles I'm having with my Geforce4 440 Go card on my dell laptop.  I found this thread afterward.  Anyway here's the link, any help is appreciated.  I really don't want to start over from a fresh install if at all possible.

Thread [http://ubuntuforums.org/showthread.php?t=459365](http://ubuntuforums.org/showthread.php?t=459365)

Thanks

Miki

---

### Post by eks on 2007-06-01
> **Cappy said:**
> The 8500 needs the beta nvidia driver (100.14.03 I think). I've only seen the actual shell script from the nvidia website. I'm not sure if it is supported by envy yet.

Man! Thanks for the tip!! The beta drivers worked. :)

But I had to install it manually, and follow the instructions [from here]("http://www.nvnews.net/vbulletin/showthread.php?t=72490"). Which are:

> 
    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx or /etc/init.d/nvidia-kernel does not exist.

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv"


Might be usefull if someone is having the same problem I had: after installing the drivers X would only load with nv, loading with nvidia would only give me a black screen. For some reason (??), you need to uninstall the restricted modules or disabled it manually (on the above quote it says to do both things, but if you uninstall the restricted modules there is no /etc/default/linux-restricted-modules file).


eks

---

### Post by dannyboy79 on 2007-06-01
> **tseliot said:**
> Every contribution is welcome.

The command which Cappy posted might be useful for the user to learn a faster way to remove things.

Tseliot, may I ask why you post back regarding such a trivial thing but when people post questions about envy or whatnot, you don't post back? I am not trying to cause any camotion, I am only trying to find out where I should post bugs that I think Envy has?

---

### Post by tseliot on 2007-06-01
> **dannyboy79 said:**
> Tseliot, may I ask why you post back regarding such a trivial thing but when people post questions about envy or whatnot, you don't post back? I am not trying to cause any camotion, I am only trying to find out where I should post bugs that I think Envy has?

You can post here or report a bug on launchpad.

Here you will find further instructions:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by esme on 2007-06-01
Thank you,

I decided to install Ubuntu 7.04 Fiesty Fawn 64 bit as a dual boot with XP on my laptop, mainly because wild horses are not going to get me to use Vista and also so I could check out this OS I'd been hearing good things about

Initially it installed with a VGA driver at 800x600 so I looked for a solution to my lack of graphics

I originally followed the instructions in the community doc FixVideoResolutionHowto to try and sort out my graphics problem which improved the situation as I now had a resolution of 1280x1024 but then I found Envy

The auto install failed to detect the card probably as it's fairly new, nVidia GeForce Go 9750 GTX, but the manual install worked fine and I now have blisteringly fast graphics again

Thanks again, you are a star

---

### Post by dannyboy79 on 2007-06-01
> **tseliot said:**
> You can post here or report a bug on launchpad.

Here you will find further instructions:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

Ok, thank you. Since I took at look at your blog, it appears as though you fixed the issue of the API mismatch problem and it was because the envy script wasn't properly uninstalling something because it couldn't determine the OS type, is that right?

SInce you are adimately involved with the nvida driver situation I was curious if a kernel update is suppose to make the x-server crash if I had installed the nvidia driver (nvidia-glx-new) thru the command line using aptitude? Because I am pretty sure that when the 16 kernel update rolled out, my x server crashed. Is the nvidia-glx-new part of the restricted modules and that's why it crashed? because it needed to use the new restricted modules that are compiled against the new kernel? If that's true, I believe there needs to be way more communication for the average user that kernel updates will crash the xserver. Why wouldn't there be a warning within the kernel update info that stated something along the line of, "If you are using restricted modules, you'll have to uninstall them first before the kernel update, then reinstall them after the kernel update otherwise severe crashes will occur?" I know that may be extreme BUT people will follow what it says wouldn't they?

What are you thoughts?

---

### Post by tseliot on 2007-06-02
> **dannyboy79 said:**
> Ok, thank you. Since I took at look at your blog, it appears as though you fixed the issue of the API mismatch problem and it was because the envy script wasn't properly uninstalling something because it couldn't determine the OS type, is that right?
That happened on Debian

> **dannyboy79 said:**
> SInce you are adimately involved with the nvida driver situation I was curious if a kernel update is suppose to make the x-server crash if I had installed the nvidia driver (nvidia-glx-new) thru the command line using aptitude? Because I am pretty sure that when the 16 kernel update rolled out, my x server crashed. Is the nvidia-glx-new part of the restricted modules and that's why it crashed? because it needed to use the new restricted modules that are compiled against the new kernel? If that's true, I believe there needs to be way more communication for the average user that kernel updates will crash the xserver. Why wouldn't there be a warning within the kernel update info that stated something along the line of, "If you are using restricted modules, you'll have to uninstall them first before the kernel update, then reinstall them after the kernel update otherwise severe crashes will occur?" I know that may be extreme BUT people will follow what it says wouldn't they?

What are you thoughts?
If you installed nvidia-glx-new and you're using linux-generic (in theory) you shouldn't experience an xserver crash, since the restricted-modules for your new kernel will be automatically installed after a kernel upgrade.

[COLOR="Red"]Take the following words with a grain of salt since I don't work for Canonical and I'm not an Ubuntu developer[/COLOR]
I *think* that sometimes the Servers containing the repositories may get the new kernel before the restricted modules (I suppose it's a matter of upload times and bandwith). In this case (if you attempt a system update) only your kernel would be updated however I think that APT would complain.


Now, why the Xserver crashes and when?
if you type:
```
ls /lib/linux-restricted-modules
```
you will see that each kernel has its own folder in which it stores its restricted-modules.

therefore if your kernel is upgraded from 2.6.20-**15**-generic to 2.6.20-**16**-generic and the restricted-modules for the new kernel are not installed (e.g. for the reasons I listed above) no "/lib/linux-restricted-modules/2.6.20-16-generic" folder will be found and the modules won't be loaded a boot thus causing a Xserver crash.

---

### Post by fabertawe on 2007-06-04
Hi there,

I'm having the API mismatch problem with the Envy 0.9.4-0ubuntu5. I need an Nvidia driver over 100* as I have an 8600GT card arriving in a couple of days. I'm currently running a 5700LE (my 6800 died :().

I've also tried the driver from the Nvidia site (100.14.06) and whilst this installs I'm getting an odd situation on reboots. On booting I get the API mismatch error but if I relaunch the Nvidia installer script and exit when it tells me the driver is already installed then I can restart GDM successfully! Any ideas please?

And many thanks for the Envy script, it's made installing the driver a breeze :)

Paul

---

### Post by Bruegger on 2007-06-04
Hi tseliot,
Let me congratulate you first for making the painful process of installing nvidia drivers so easy for new linux users.
Been using envy for my dapper install and it has always come to my rescue.
Now coming to the present..i have done a fresh install of feisty fawn on my old machine and the nvidia driver install has me against the wall.
have tried manual install, through aptitude, through the nvidia site , through restricted driver manager and finally also through envy.
but still not able to get it running.
Ubuntu only loads when i change nvidia to nv.
Have checked the products supported list and my ancient geforce2 mx integrated cpu (device id 1X1A0) is suppoted by 9631 and also the 9639.
But i cant get it running no matter what. sometimes it runs and most other times it just crashes x.
Posting this through my windows dual boot. 

Is there any way the 9631 or 9639 can be made to work with my card?Dont wanna invest in a new card at the moment.And yes i want the 9631 0r 9639 drivers only for the card no 7184 or patched 8774 please.
I want to use glx effects and beryl in feisty like i used to in dapper.

Any help will be really great.

Any one able to run 9631 0r 9639 drivers with nvidia geforce 2 mx integrated gpu please help out a fellow noob.

Thx

---

### Post by dannyboy79 on 2007-06-04
> **tseliot said:**
> Now, why the Xserver crashes and when?

therefore if your kernel is upgraded from 2.6.20-**15**-generic to 2.6.20-**16**-generic and the restricted-modules for the new kernel are not installed (e.g. for the reasons I listed above) no "/lib/linux-restricted-modules/2.6.20-16-generic" folder will be found and the modules won't be loaded a boot thus causing a Xserver crash.
Yeap, that's exactly what had happened to me, I noticed that when I saw an update, there was only 2 thing, the kernel and something along with that BUT I know it wasn't the restricted modules so that makes more sence. Now I know to not update the kernel until I see that the Restricted Modules are there to.
Thanks for the info.

---

### Post by dannyboy79 on 2007-06-04
> **fabertawe said:**
> Hi there,

I'm having the API mismatch problem with the Envy 0.9.4-0ubuntu5. I need an Nvidia driver over 100* as I have an 8600GT card arriving in a couple of days. I'm currently running a 5700LE (my 6800 died :().

I've also tried the driver from the Nvidia site (100.14.06) and whilst this installs I'm getting an odd situation on reboots. On booting I get the API mismatch error but if I relaunch the Nvidia installer script and exit when it tells me the driver is already installed then I can restart GDM successfully! Any ideas please?

And many thanks for the Envy script, it's made installing the driver a breeze :)

Paul

Yes, I have tried telling Tseliot about this but he told another user that was trying to help me that there wasn't a problem. I had to put in a long find comment within my rc.local file so that the newest 100.xx.xx nvidia driver would work when I used the Unstable version of Envy, was it 0.94? The fix is post number 51 within this very thread!!! That's the only way we could get it to work without getting the API mismatch. It's kind of a hack but nothing would work, I worked with another gentlemen over IM and after an hour, he gave up trying to fix and he said that it was a problem with Envy and or something else and that this was the only way to get it to work?

---

### Post by fabertawe on 2007-06-04
> **dannyboy79 said:**
> Yes, I have tried telling Tseliot about this but he told another user that was trying to help me that there wasn't a problem. I had to put in a long find comment within my rc.local file so that the newest 100.xx.xx nvidia driver would work when I used the Unstable version of Envy, was it 0.94? The fix is post number 51 within this very thread!!! That's the only way we could get it to work without getting the API mismatch. It's kind of a hack but nothing would work, I worked with another gentlemen over IM and after an hour, he gave up trying to fix and he said that it was a problem with Envy and or something else and that this was the only way to get it to work?

Turns out it was /lib/modules/`uname -r`/volatile/nvidia_new.ko

I blacklisted (and deleted) the little monkey and no more API mismatch ;) This is with the Nvidia installer, not tried Envy since.

Cheers ... Paul

---

### Post by joekarl on 2007-06-04
Every time I have done a clean install of Ubuntu, Envy has worked a treat. It is the only program I know that sets up an Nvidia card so that OpenGL works properly, essential if you want JDoom or Freespace Open to work.

---

### Post by mokos on 2007-06-07
> **Bruegger said:**
> Hi tseliot,
Let me congratulate you first for making the painful process of installing nvidia drivers so easy for new linux users.
Been using envy for my dapper install and it has always come to my rescue.
Now coming to the present..i have done a fresh install of feisty fawn on my old machine and the nvidia driver install has me against the wall.
have tried manual install, through aptitude, through the nvidia site , through restricted driver manager and finally also through envy.
but still not able to get it running.
Ubuntu only loads when i change nvidia to nv.
Have checked the products supported list and my ancient geforce2 mx integrated cpu (device id 1X1A0) is suppoted by 9631 and also the 9639.
But i cant get it running no matter what. sometimes it runs and most other times it just crashes x.
Posting this through my windows dual boot. 

Is there any way the 9631 or 9639 can be made to work with my card?Dont wanna invest in a new card at the moment.And yes i want the 9631 0r 9639 drivers only for the card no 7184 or patched 8774 please.
I want to use glx effects and beryl in feisty like i used to in dapper.

Any help will be really great.

Any one able to run 9631 0r 9639 drivers with nvidia geforce 2 mx integrated gpu please help out a fellow noob.

Thx


same card, same problems: it all went fine with feisty and envy, then I upgraded kernel to -16 and nothing went right (nor older kernel would work). The former configuration I was able to use was by manual install of legacy drivers (7184) and get my 3d acc. working, even if tseliot's note page lists my card in the second group. now I've tried both with 9631 and 7184 but had no results for 3d acc. wait for someone to help us!

---

### Post by dannyboy79 on 2007-06-07
> **mokos said:**
> same card, same problems: it all went fine with feisty and envy, then I upgraded kernel to -16 and nothing went right (nor older kernel would work). The former configuration I was able to use was by manual install of legacy drivers (7184) and get my 3d acc. working, even if tseliot's note page lists my card in the second group. now I've tried both with 9631 and 7184 but had no results for 3d acc. wait for someone to help us!

well, if you have that old of a card, I would merely use the Restricted Modules Manager BUT you'll have to ensure that you remove AND PURGE anything related to nvidia-glx* within synaptic. That's most likely your problem, what happens is that something lays around and then you get the API mismatch error and it's because the Nvidia Module doesn't match the kernel module or somethign like that. Have you tried to use Envy BUT only to completely remove all nvidia drivers? I would do that, then change your driver to vesa for the time being, then do a complete restart of yoru machine. THen when you reboot, you'll be using the vesa driver, then simply go to the Restricted MOdules MAnager and click it, and it should install teh correct driver for your card, which is the 9631. I have a similar card in my Dell Dimension 8200 (GeForce4 MX 420 0x0172 ), I used the Restricted Modules Manager myself, and it worked like a treat. BUT this was because I didn't install anything else first which is normally the problem. Have you followed my post a couple pages before this one about remove and purging?

---

### Post by Bruegger on 2007-06-07
Hi Mokos,
Seem to have made some headway with both 9631 and 9639 on the -16 generic kernel.But screens still lags meaning windows leave their frames behind when minimised or closed.Think it doesnt refresh fast enough. Dunno if its my monitor or my xorg.conf causing this.Will fix it later. But atleast have workable 3d and gl.
Maybe this will help you out.
I deleted all instances of nvidia from /lib/linux-restricted-modules/.Mine had nvidia-glx-legacy and nvidia-new in it left behind from my previous trials.
Then ran the nvidia installer for 9639 from the terminal( necessary to close gdm before doing this i am told) and a restart and you are on!
Lemme know if you need more detailed help.

Goddd, its tough to get help for old cards..and they seem to run like a charm on windows.
Wish they were better supported on linux. Linux makes the card seem from stone ages whereas in windows it still packs quite a mean punch with 3d games.

Cheers!

---

### Post by Cappy on 2007-06-07
> **Cappy said:**
> Sure, here is the process I used:
```

sudo apt-get --purge remove nvidia-glx nvidia-glx-new nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`

```
The nvidia-glx-new are the newest nvidia drivers. The legacy drivers for the older video cards are just "nvidia-glx".

X didn't startup correctly the first time so I had to run 
```

sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`
``` 
again once I was dropped to a command line.
In both cases where I used this in the last couple of days I already had nvidia-glx installed (automatically from System-->Administration-->Restricted Drivers Manager).

I ended up using this method because the nvidia's sh installer caused horrible FPS stuttering in my games.

I just reinstalled my nvidia drivers and I found out that when I removed my nvidia-glx it also removed the restricted modules and that needed to be reinstalled. I used "sudo dpkg-reconfigure xserver-xorg" (selected the nv driver) and once I got in Ubuntu and went to (System-->Administration-->Restricted Drivers Manager) and it told me I needed that. The error I got for this was "Nvidia Module not found!". Works now and I added the correct command onto my quoted post.

Question though: when reconfiguring xserver-xorg how do you check boxes, like say, for resolution? I don't know what key to use. I did it once GDM started up with sudo nvidia-settings but I would like to know how to do it with the xserver-xorg too.

---

### Post by dannyboy79 on 2007-06-08
> **Cappy said:**
> Question though: when reconfiguring xserver-xorg how do you check boxes, like say, for resolution? I don't know what key to use. I did it once GDM started up with sudo nvidia-settings but I would like to know how to do it with the xserver-xorg too.

I believe it's the space bar.

---

### Post by dannyboy79 on 2007-06-08
> **Bruegger said:**
> Hi Mokos,
Seem to have made some headway with both 9631 and 9639 on the -16 generic kernel.But screens still lags meaning windows leave their frames behind when minimised or closed.Think it doesnt refresh fast enough. Dunno if its my monitor or my xorg.conf causing this.Will fix it later. But atleast have workable 3d and gl.
Maybe this will help you out.
I deleted all instances of nvidia from /lib/linux-restricted-modules/.Mine had nvidia-glx-legacy and nvidia-new in it left behind from my previous trials.
Then ran the nvidia installer for 9639 from the terminal( necessary to close gdm before doing this i am told) and a restart and you are on!
Lemme know if you need more detailed help.

Goddd, its tough to get help for old cards..and they seem to run like a charm on windows.
Wish they were better supported on linux. Linux makes the card seem from stone ages whereas in windows it still packs quite a mean punch with 3d games.

Cheers!
I believe you still have something incorrect in your xorg.conf as you shouldn't be having these issues with the 9631. Have you removed any reference to DRI? I don't think you can use both dri and xgl modules.

---

### Post by mokos on 2007-06-08
I did it! purged and removed everything (wtf in lib/linux-restricted.. I even had something of glx.new that's nothing to do with me!) then installed linux restricted modules for my architecture -16.386 and now I do have my "yes"  for direct rendering...but I have those annoying scroll problems in firefox, black lines over the desktop and some sporadic gdm crashes. I changed that section in xorg.conf "load DRI 0666" with option composite disable (even tried with Enable")maybe I have to attach my xorg.conf file and let you see it...for now, many thanks folks now I can go back fragging!!!!

---

### Post by Bruegger on 2007-06-11
Hi Dannyboy79,
I am using the 9639 drivers and not the 9631
Thanks for the lovely tip. Seemed to set a lotta things rite. I deleted the " AllowGLXWithComposite" option and Section  Composite Extensions from my xorg.conf and things seem a whole lot better.
Still have the occasional "painting the screen with mouse" problem but this is definetely much much better. Able to get about 492 FPS from the card.
Posting my xorg.conf here. Maybe it will help some spot the problem to perfect it to a T or help a fellow Noob set up the latest nvidia-glx driver on geforce2 cards.

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Samsung SyncMaster 753s"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
    Driver         "nvidia"
    Busid	   "PCI:2:0:0"
    Option	   "UseDisplayDevice"	"DFP"
    Option	   "Edid"	"False"
    Option	   "UseEdid"	"False"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
    Monitor        "Samsung SyncMaster 753s"
    DefaultDepth    24
    Option         "NvAGP" "1"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "UseDisplayDevice" "DFP"
    Option         "Edid" "False"
    Option	   "UseEdid"	"False"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section	"DRI"
	Mode	0666
EndSection

---

### Post by viejo on 2007-06-12
This is a great thread!

Installed the drivers via method 1 for a GeForce 4. I rebooted and the computer freezes at the ubuntu splash screen. It sits for a short time, then reverts back to busybox! /bin/sh: can't access tty; job control turned off

So, naturally, I try to boot into Windows, but it won't but and always reverts back to the blue screen of death! :( I have no idea why this would have happened. Aside booting from a Windows XP disc to reset everything, I'm lost. BTW, I would rather not start from scratch, lots of work on there...

---

### Post by dannyboy79 on 2007-06-12
> **Bruegger said:**
> Hi Dannyboy79,
I am using the 9639 drivers and not the 9631
Thanks for the lovely tip. Seemed to set a lotta things rite. I deleted the " AllowGLXWithComposite" option and Section  Composite Extensions from my xorg.conf and things seem a whole lot better.
Still have the occasional "painting the screen with mouse" problem but this is definetely much much better. Able to get about 492 FPS from the card.
Posting my xorg.conf here. Maybe it will help some spot the problem to perfect it to a T or help a fellow Noob set up the latest nvidia-glx driver on geforce2 cards.

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Samsung SyncMaster 753s"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
    Driver         "nvidia"
    Busid	   "PCI:2:0:0"
    Option	   "UseDisplayDevice"	"DFP"
    Option	   "Edid"	"False"
    Option	   "UseEdid"	"False"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics]"
    Monitor        "Samsung SyncMaster 753s"
    DefaultDepth    24
    Option         "NvAGP" "1"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "UseDisplayDevice" "DFP"
    Option         "Edid" "False"
    Option	   "UseEdid"	"False"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section	"DRI"
	Mode	0666
EndSection

i could be wrong but I don't see a need for the DRI section at the bottom when you're not even loading the DRI module within the modules section towards the top. May or may not have any effect and as I said, I am not sure about this and only really using logical thinking.

---

### Post by Trew on 2007-06-16
hello, i tryed methode 1 and 2 and envy, but i always get the following error messages:

(EE) NVIDIA(0): The interrupt for NVIDIA graphics device PCI:0:5:0
(EE) NVIDIA(0):      appears to be edge-triggered. Please see the COMMON
(EE) NVIDIA(0):      PROBLEMS section in the README for additional information.

so i read the README from NVIDIA and found the followeing:

Currently, the NVIDIA driver will attempt to detect edge triggered interrupts and X will purposely fail to start (to avoid stability issues). This behavior can be overridden by setting the "NVreg_RMEdgeIntrCheck" NVIDIA Linux kernel module parameter. This parameter defaults to "1", which enables the edge triggered interrupt detection. Set this parameter to "0" to disable this detection.

now i have to set the paramet to "0"...but i wouldnt know how

---

### Post by dannyboy79 on 2007-06-16
I woulld use the NV forums here: [http://www.nvidia.com/page/support.html](http://www.nvidia.com/page/support.html)
you;ll obviously have to compile the nvidia module yourself AFTER you set that paramter.

---

### Post by Trew on 2007-06-16
do you know what this means:

(WW) NVIDIA: No matching Device section for instance (BUSID PCI:0:10:3) found

gr trew

---

### Post by steevc on 2007-06-16
I tried using Envy to get my Geforce 6150 on-board graphics working better. I told it to install and it did all sorts of stuff. I told it to update my xorg.conf, but the new one was unchanged, still using nv. The xorg-configure program did not offer me the nvidia driver.

I've also tried installing nvidia-glx-new, but that complains when I modprobe nvidia about a lack of 

/lib/modules/2.6.20-16-generic/nvidia/nvidia.ko

I tried making a link to the one I found at

/usr/src/modules/nvidia-kernel/debian/nvidia-kernel-2.6.20-16-generic/lib/modules/2.6.20-16-generic/nvidia/nvidia.ko

but that just crashes modprobe as well.

So no glxgears for me so far :(

---

### Post by dannyboy79 on 2007-06-18
> **steevc said:**
> I tried using Envy to get my Geforce 6150 on-board graphics working better. I told it to install and it did all sorts of stuff. I told it to update my xorg.conf, but the new one was unchanged, still using nv. The xorg-configure program did not offer me the nvidia driver.

I've also tried installing nvidia-glx-new, but that complains when I modprobe nvidia about a lack of 

/lib/modules/2.6.20-16-generic/nvidia/nvidia.ko

I tried making a link to the one I found at

/usr/src/modules/nvidia-kernel/debian/nvidia-kernel-2.6.20-16-generic/lib/modules/2.6.20-16-generic/nvidia/nvidia.ko

but that just crashes modprobe as well.

So no glxgears for me so far :(

well it sounds like you're having a conflict, you need to completely remove and purge everything Nvidia, change your xorg.conf to use "vesa" temporarily, then make sure you purge and remove again just in case, Then, restart again making certain you're using the vesa driver, then use synaptic to install the nvidia-glx-new driver, I am not aware if this updates your xorg.conf file or not, so check it and make sure it's driver is "nvidia", then go to this file and edit it using sudo: "/etc/default/linux-restricted-modules-common"
make sure you enter this within the quotes;
DISABLED_MODULES="nv"
then save and close that file. then restart your x-server using this "ctrl-alt-backspace", your screen should go black and you should greeted with the login window of gdm again, you did it! if your xserver fails to load, then you still have conflicts and you should have created that symlink or whatever it is you did to try  to make that nvidia.ko file be seen. good luck

---

### Post by dannyboy79 on 2007-06-18
> **Trew said:**
> do you know what this means:

(WW) NVIDIA: No matching Device section for instance (BUSID PCI:0:10:3) found

gr trew

can you please show us the output of the following commands entered seperately into a terminal session (command line):

cat /etc/X11/xorg.conf | grep Device

cat /etc/X11/xorg.conf | grep PCI

lspci -v

then I can maybe help you

---

### Post by steevc on 2007-06-18
> **dannyboy79 said:**
> well it sounds like you're having a conflict, you need to completely remove and purge everything Nvidia, change your xorg.conf to use "vesa" temporarily, then make sure you purge and remove again just in case, Then, restart again making certain you're using the vesa driver, then use synaptic to install the nvidia-glx-new driver, I am not aware if this updates your xorg.conf file or not, so check it and make sure it's driver is "nvidia", then go to this file and edit it using sudo: "/etc/default/linux-restricted-modules-common"
make sure you enter this within the quotes;
DISABLED_MODULES="nv"
then save and close that file. then restart your x-server using this "ctrl-alt-backspace", your screen should go black and you should greeted with the login window of gdm again, you did it! if your xserver fails to load, then you still have conflicts and you should have created that symlink or whatever it is you did to try  to make that nvidia.ko file be seen. good luck

I just tried some stuff I found elsewhere. I ran
```

sudo apt-get remove linux-restricted-modules-2.6.20-16-generic nvidia-kernel-common nvidia-glx-new --purge
```

and then re-installed it all and that got the driver working. For some reason installing the nvidia stuff required the 2.6.20-15 kernel stuff, even though I'm running 2.6.20-16.

I can now run Google Earth again. glxgears gives rates of anywhere from 200 to 3000 fps.

My remaining issue is that I can am offered a maximum refresh of only 55Hz at 1280x1024. The monitor will do 160Hz and is set up for it in xorg.conf. What do I need to do to fix this?

Thanks

---

### Post by dannyboy79 on 2007-06-18
> **steevc said:**
> I just tried some stuff I found elsewhere. I ran
```

sudo apt-get remove linux-restricted-modules-2.6.20-16-generic nvidia-kernel-common nvidia-glx-new --purge
```

and then re-installed it all and that got the driver working. For some reason installing the nvidia stuff required the 2.6.20-15 kernel stuff, even though I'm running 2.6.20-16.

I can now run Google Earth again. glxgears gives rates of anywhere from 200 to 3000 fps.

My remaining issue is that I can am offered a maximum refresh of only 55Hz at 1280x1024. The monitor will do 160Hz and is set up for it in xorg.conf. What do I need to do to fix this?

Thanks

you could try installing nvidia-settings and then using that to get a better res but I've never heard of such a high res before.

---

### Post by steevc on 2007-06-18
nvidia-settings was already installed as part of nvidia-glx-new. That allowed me to set a higher refresh rate (85Hz). That's much better.

Thanks again/.

---

### Post by dannyboy79 on 2007-06-18
> **steevc said:**
> nvidia-settings was already installed as part of nvidia-glx-new. That allowed me to set a higher refresh rate (85Hz). That's much better.

Thanks again/.

glad I could be of service. just pay it forward!

---

### Post by ballison on 2007-06-20
Thankyou :D

---

### Post by steevc on 2007-06-23
Still got a slight problem with the refresh rate. I can set it to 85Hz in nvidia-settings, but it does not stick for the next time I log in. System Settings still only offers 50-56Hz.

nvidia-settings had a button to write stuff to xorg.conf, but that didn't seem to help.

---

### Post by Cappy on 2007-06-23
Did you try
```
gksudo nvidia-settings
```
?
(And then use the option to save to the xorg)

---

### Post by Luke Davis on 2007-06-23
Just wanted to say thank you to tseliot for his envy script. Worked a charm. :). Especially good as the latest nvidia fixed an issue with my ati motherboard rs480.

---

### Post by drobvice on 2007-06-23
Another thanks here.  I haven't been able to boot the newest linux kernel thanks to the nvidia driver.  I messed around trying to install and uninstall nvidia stuff in synaptic and finally managed to break X for both kernels I have in 7.04.  I contemplated just using my windows partition but I remembered reading about envy and it worked like a charm.  Shame that ubuntu could not perform this upgrade on it's own.  I had pretty high hopes after seeing the restricted driver manager.

---

### Post by dabl on 2007-06-23
I just installed the latest Nvidia driver with the Envy script -- worked like a charm, as always.  Thank you tseliot!  I noticed a nice speedup on my GeF 7900GS card with glxgears, too.  I was getting about 17,000 fps with the -9755 driver -- here's what I'm getting with the new driver:

```
dibl@feisty:~$ glxgears
99922 frames in 5.0 seconds = 19984.284 FPS
99885 frames in 5.0 seconds = 19976.876 FPS
99889 frames in 5.0 seconds = 19977.625 FPS
99855 frames in 5.0 seconds = 19970.836 FPS
99885 frames in 5.0 seconds = 19977.000 FPS
99888 frames in 5.0 seconds = 19977.492 FPS
99897 frames in 5.0 seconds = 19979.236 FPS
99878 frames in 5.0 seconds = 19975.588 FPS
99901 frames in 5.0 seconds = 19980.184 FPS
99878 frames in 5.0 seconds = 19975.520 FPS

```

Of course, once I turn on Beryl that drops to 12,000 real fast!

---

### Post by Vodkayum on 2007-06-24
Ok I was using ubuntu and had some issues, a friend has been using kubuntu and recommended it to me. I installed and it resolved my sound issue I was having on ubuntu yet Envy will not work under kubuntu. I tried the add/remove option and it does not seem to work and I tried to run the .run file I d/l'ed from Nvidia but it said it was unable to update the kernal. Please help me.
 
 P.S. please do not tell me to go back to windows I desperately never want to use windows again and have been flamed at quite a few linux forums.

---

### Post by thejam on 2007-06-24
> **dabl said:**
> I just installed the latest Nvidia driver with the Envy script -- worked like a charm, as always.  Thank you tseliot!  I noticed a nice speedup on my GeF 7900GS card with glxgears, too.  I was getting about 17,000 fps with the -9755 driver

Does envy install the new 100.14.11 driver?  Does the fps for glxgears drop after a suspend or hibernate?  Does virtual console (ctl-alt-f1, etc) work after suspend or hibernate?  I'm running the Restricted Drivers Manager version (nvidia-glx 9631) with a Nvidia 7900 GS on amd64 (Mac Pro 8-core) and I get problems on resume: glxgears becomes ~2100fps from ~15800fps before hibernate and window resizing slows a lot too.  Also virtual consoles don't work on resume from suspend too.

---

### Post by thejam on 2007-06-24
> **thejam said:**
> Does envy install the new 100.14.11 driver?  Does the fps for glxgears drop after a suspend or hibernate?  Does virtual console (ctl-alt-f1, etc) work after suspend or hibernate?  I'm running the Restricted Drivers Manager version (nvidia-glx 9631) with a Nvidia 7900 GS on amd64 (Mac Pro 8-core) and I get problems on resume: glxgears becomes ~2100fps from ~15800fps before hibernate and window resizing slows a lot too.  Also virtual consoles don't work on resume from suspend too.
I just tried envy.  I first uninstalled the Restricted Drivers Manager version via the gnome menu, then rebooted into "nv" driver, then ran envy gui.  It seemed to install 100.14.11 driver.  But X crashed on reboot, saying that the nvidia kernel module wasn't there (/dev/nvidactl couldn't be opened).  So I tried "sudo modprobe nvidia", but lsmod didn't show any nvidia.  I also tried "sudo /etc/init.d/nvidia-kernel restart", but gdm restart still fails.  Please help!

---

### Post by dabl on 2007-06-24
Yes, since the 22 June release, it installs ver. 100.14.11.

I have not observed any problem with the text console (Ctrl-Alt-F1 - F7) after hibernation.

I'm on an Intel motherboard and CPU, so it is possible that chipset/BIOS issues are different with your AMD platform.

I deleted /etc/init.d/nvidia_everything, and linux-restricted-modules, and packages nvidia-glx-everything, before I downloaded and ran Envy.  I made sure I had my linux-headers and build-essential packages.  Also Envy needs some python packages that I didn't have (python-glade2 and pt3) and also fakeroot and another package I can't remember (gh-make, maybe), so you have to install those before it will run.  I was previously running the nvidia-glx-new packaged driver (-9755).

---

### Post by thejam on 2007-06-24
Thanks.  Well I just got mine to work: instead of attempting to be clever and uninstalling nvidia via the Restricted Drivers Manager [RDM] (which failed from my prev. post), I reinstalled nvidia using RDM & rebooted so that I had the older version of nvidia running fine (without envy).  Then I used envy  to installed the newer nvidia 100.14.11, which then rebooted me and voila, working X!  I got fast fps on glxgears and working console after hibernate!  However, after suspend my virtual console goes blank (but I can still switch back to X with ctl-alt-f7), but glxgears is fast.  So I'm going to stick with suspend even though virtual console is still broken.

Based on this experience, I think envy has a bug with the case where someone deactivates nvidia under the ubuntu Restricted Drivers Manager, reboots under "nv" driver, then tries envy.  I noticed in the messages that were flying by during the kernel module compile something about ia32 (even though I'm on amd64); but that could be irrelevant.

Cheers.

---

### Post by gkiller on 2007-06-24
Thanks tseliot for the Howto on USDF how to install the newest binary driver. It followed it and had it running in no time without any problems for my GF 8800 GTS.

One thing I noticed immediately with the new 100.14.11 driver compared to the one in Ubuntu (97.55) is that the slow/sluggish scrolling in Opera and Firefox is gone when Beryl/Compiz is active! The difference is extreme, surfing feels fast again :)

(At least I hope that it's because of the new driver... but I wouldn't know what else I changed.)

---

### Post by Mark228 on 2007-06-25
I can't seem to get any drivers to work for me, but that might be because I am a total newbie. :( I tried RDM and restarted X but it wouldn't start (got errors) and sent me to a command line. I didn't save info from that and just reinstalled Ubuntu as I haven't a clue what to do from that command line to get the GUI working again. After second install I found ENVY and it appeared to install everything ok but when I restarted X the exact same thing happened as my previous attempt. So again, I reinstalled (lol) and this time tried installing using the Applications/Add-Remove and it said it installed ok, but yet again I restart X and get the following errors which look the same as previous ones:

Failed to start the X server etc
(ww) Nvidia : no matching device section for instance (BusID PCI:1:0:0)
(EE) No devices detected
Fatal server error
No screens found

I'm on LiveCD atm and any help would be much appreciated! I can get to a command line but don't know what I can do from there to remedy my problems.

During the last attempt using A/A-R it said I could revert to backup using this command:

cp /var/backups/xorg/xorg.conf.2007-06-25-08:13:01 /etc/x11/xorg.conf

but when I try it I just get:

cp: cannot create regular file 'etc/x11/xorg.conf' : no such file or directory

Go easy on me guys I'm a total newb to Linux.

edit: 8800 gts graphics card, Core Duo conroe etc.

---

### Post by Bruegger on 2007-06-25
Dannyboy,
Still not able to correct the problem. The " painting screen with mouse pointer clicks" still persists. 
Using the 9639 drivers on geforce2 mx in fiesty fawn.
Anyone any suggestions how i solve it?

Bruegger

---

### Post by dannyboy79 on 2007-06-25
I don't have any other suggestions sorry.

---

### Post by l-fever on 2007-06-25
Awesome! I used your ENVY script to install the nvidia driver on my HP-DV6327cl laptop and worked like a charm! Got Beryl installed and looking good! Thanks! Great Stuff!

Steve

---

### Post by steevc on 2007-06-26
Re my issues with refresh rates. Here's the appropriate bits from by xorg.conf. I think nvidia-settings added the "1280x1024_85 +0+0;" bit, but System Settings only offers 50-56Hz.

```

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Iiyama"
    HorizSync       31.5 - 112.5
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024 +0+0; 1280x1024_85 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by Mark228 on 2007-06-26
Just reporting back, I re-installed Ubuntu again and saw that ENVY had been labled "stable" within the past 24 hours so gave it another try. It installed everything fine like last time except this time I have no crashed X :D:D:D I'm now on Ubuntu with screen resolution 1680x1050 and a very happy chappy! Thanks a lot for making this program, tseliot, I'll use Ubuntu for a while and see how I go but I certainly don't mind making a small donation for saving me all the pain of installing these drivers. Well done! =D>

---

### Post by TXBDan on 2007-06-26
just used Envy on my new Feisty install and my Quadro FX3500

worked perfectly!

quick dumb question. whats a quick/easy way to check what drive version i'm running?


oh and glxgears is showing around 8300fps. woo

---

### Post by mseewald on 2007-06-27
Hi all,

For me the solution did not work. I could compile the module successfully, but it was never loaded. 

I found out, that there is a bug causing the following line to appear in /etc/modprobe.d/lrm-video
```
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
```

When this line is removed, the module loads successfully and works.

I can only speculate, that other packages (nvidia-glx-new?) were incompletely removed and left over this line in this file.

See also:
[http://www.nvnews.net/vbulletin/showpost.php?p=1285625&postcount=43](http://www.nvnews.net/vbulletin/showpost.php?p=1285625&postcount=43)
[http://ubuntuforums.org/showthread.php?p=2666152](http://ubuntuforums.org/showthread.php?p=2666152)

Regards,
Michael

---

### Post by tseliot on 2007-06-27
> **TXBDan said:**
> just used Envy on my new Feisty install and my Quadro FX3500

worked perfectly!

quick dumb question. whats a quick/easy way to check what drive version i'm running?


oh and glxgears is showing around 8300fps. woo
Quick way:
```
glxinfo | grep version | grep NVIDIA
```

easy way:
use nvidia-settings

---

### Post by tseliot on 2007-06-27
> **mseewald said:**
> Hi all,

For me the solution did not work. I could compile the module successfully, but it was never loaded. 

I found out, that there is a bug causing the following line to appear in /etc/modprobe.d/lrm-video
```
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
```

When this line is removed, the module loads successfully and works.

I can only speculate, that other packages (nvidia-glx-new?) were incompletely removed and left over this line in this file.

See also:
[http://www.nvnews.net/vbulletin/showpost.php?p=1285625&postcount=43](http://www.nvnews.net/vbulletin/showpost.php?p=1285625&postcount=43)
[http://ubuntuforums.org/showthread.php?p=2666152](http://ubuntuforums.org/showthread.php?p=2666152)

Regards,
Michael
Thanks for reporting.

This is something I can add to Envy.

---

### Post by tseliot on 2007-06-27
> **Mark228 said:**
> I can't seem to get any drivers to work for me, but that might be because I am a total newbie. :( I tried RDM and restarted X but it wouldn't start (got errors) and sent me to a command line. I didn't save info from that and just reinstalled Ubuntu as I haven't a clue what to do from that command line to get the GUI working again. After second install I found ENVY and it appeared to install everything ok but when I restarted X the exact same thing happened as my previous attempt. So again, I reinstalled (lol) and this time tried installing using the Applications/Add-Remove and it said it installed ok, but yet again I restart X and get the following errors which look the same as previous ones:

Failed to start the X server etc
(ww) Nvidia : no matching device section for instance (BusID PCI:1:0:0)
(EE) No devices detected
Fatal server error
No screens found

I'm on LiveCD atm and any help would be much appreciated! I can get to a command line but don't know what I can do from there to remedy my problems.

During the last attempt using A/A-R it said I could revert to backup using this command:

cp /var/backups/xorg/xorg.conf.2007-06-25-08:13:01 /etc/x11/xorg.conf

but when I try it I just get:

cp: cannot create regular file 'etc/x11/xorg.conf' : no such file or directory

Go easy on me guys I'm a total newb to Linux.

edit: 8800 gts graphics card, Core Duo conroe etc.
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
cd /etc/X11/
```
```
ls
```
you'll see xorg.conf and other backup files (e.g. xorg.conf_backup_200703022015)

replace xorg.conf with a backup:
```
sudo cp name_of_your_backup_file xorg.conf
```

then reboot by typing:
```
reboot
```

---

### Post by tseliot on 2007-06-27
> **steevc said:**
> Re my issues with refresh rates. Here's the appropriate bits from by xorg.conf. I think nvidia-settings added the "1280x1024_85 +0+0;" bit, but System Settings only offers 50-56Hz.

If I were you I wouldn't trust System Settings.

Launch nvidia-settings and see what it says

---

### Post by steevc on 2007-06-27
> **tseliot said:**
> If I were you I wouldn't trust System Settings.

Launch nvidia-settings and see what it says

nvidia-settings offers me 60, 75 and 85Hz. If I accept the latter and tell it to write to xorg.conf I get the results in my earlier post

[http://ubuntuforums.org/showpost.php?p=2917984&postcount=138](http://ubuntuforums.org/showpost.php?p=2917984&postcount=138)

System Settings doesn't pick up on the higher frequency. Can you see anything wrong with the file?

Thanks for all your good works.

---

### Post by tseliot on 2007-06-27
> **steevc said:**
> nvidia-settings offers me 60, 75 and 85Hz. If I accept the latter and tell it to write to xorg.conf I get the results in my earlier post

[http://ubuntuforums.org/showpost.php?p=2917984&postcount=138](http://ubuntuforums.org/showpost.php?p=2917984&postcount=138)

System Settings doesn't pick up on the higher frequency. Can you see anything wrong with the file?

Thanks for all your good works.

What I was trying to say is that system settings is not as reliable as Nvidia-settings.

On my computer System settings says that I'm using 50Hz and Nvidia-settings claims it is 60Hz.

You shouldn't worry about what System settings says.

---

### Post by Skneepa on 2007-06-27
Hi, thanks to your guide I managed to get the NVIDIA drivers working. Everything seems ok, however when I try to enable desktop effects I get the following message: "the composite extension is not available"...In the guide you suggest to add the command 
sudo nvidia-xconfig --no-composite
Why do we have to add this no-composite line? Is this somehow related with my issue? How can I work the problem out? Sorry if my question is silly but I make my first steps in linux and try to figure out how stuff works. Thanks in advance! :)

My graphics card is an Nvidia GF7600GS 256MB if that helps!

---

### Post by steevc on 2007-06-28
> **tseliot said:**
> What I was trying to say is that system settings is not as reliable as Nvidia-settings.

On my computer System settings says that I'm using 50Hz and Nvidia-settings claims it is 60Hz.

You shouldn't worry about what System settings says.

The thing is that when I log in I can see that the refresh rate is too low. I can change it with nvidia-settings to 85Hz, which is much easier on the eyes, but it will revert back next time. I just need to know how to make the change permanent.

Thanks again

---

### Post by tseliot on 2007-06-28
> **Skneepa said:**
> sudo nvidia-xconfig --no-composite
Why do we have to add this no-composite line? Is this somehow related with my issue? How can I work the problem out? Sorry if my question is silly but I make my first steps in linux and try to figure out how stuff works. Thanks in advance! :)

My graphics card is an Nvidia GF7600GS 256MB if that helps!

That's necessary only for legacy cards (and your card is not a legacy card).

Maybe I need to edit my guide

---

### Post by tseliot on 2007-06-28
> **steevc said:**
> The thing is that when I log in I can see that the refresh rate is too low. I can change it with nvidia-settings to 85Hz, which is much easier on the eyes, but it will revert back next time. I just need to know how to make the change permanent.

Thanks again

type:
```
sudo nvidia-settings
```

set the refresh rate

then press the button to save your settings

---

### Post by steevc on 2007-06-28
> **tseliot said:**
> type:
```
sudo nvidia-settings
```

set the refresh rate

then press the button to save your settings

Okay, so I run that, set it to 85Hz, hit Apply and hit Save to X Configuration File. All looks nice.

Then I log out and back in, run nvidia-settings again and I'm back to 60Hz.

I'm not clear on where the user resolution and refresh are saved. It looks like something is not getting saved properly. Would I find any help in some log file?

I can see all sorts of messages in .xsession-errors, but nothing obvious.

---

### Post by tseliot on 2007-06-28
> **steevc said:**
> Okay, so I run that, set it to 85Hz, hit Apply and hit Save to X Configuration File. All looks nice.

Then I log out and back in, run nvidia-settings again and I'm back to 60Hz.

I'm not clear on where the user resolution and refresh are saved. It looks like something is not getting saved properly. Would I find any help in some log file?

I can see all sorts of messages in .xsession-errors, but nothing obvious.

Did you launch "nvidia-settings" with "sudo" as I suggested?

If yes, then read point 15 of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION)

---

### Post by Schuenemann on 2007-06-28
Hi, I have an old Geforce 256 32 MB. I had it working nicely in Edgy, but I can't configure it in Feisty.

I installed the required packages "sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings"

Then, the text says to run "sudo nvidia-xconfig --no-composite", but I get this error:

> nvidia-xconfig: unrecognized option: "--no-composite"

Invalid commandline, please run `nvidia-xconfig --help` for usage information.

Edit: using Kubuntu.

What should I do?

Thanks

---

### Post by steevc on 2007-06-29
> **tseliot said:**
> Did you launch "nvidia-settings" with "sudo" as I suggested?

If yes, then read point 15 of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#PROBLEMS_SECTION)

I ran it as sudo. Next time I started I ran

nvidia-settings --load-config-only

Still at 60Hz. So it looks like it is not saving properly. Ho hum.

I don't think I mentioned that a while back I had some issues when I installed an old nvidia MX400 card in my PC. I managed to break X for a while. I can't remember the exact details, but various things have been not quite right since then. Perhaps some files got left behind that are clashing. Any suggestions on where to look?

---

### Post by dannyboy79 on 2007-06-29
> **steevc said:**
> I ran it as sudo. Next time I started I ran

nvidia-settings --load-config-only

Still at 60Hz. So it looks like it is not saving properly. Ho hum.

I don't think I mentioned that a while back I had some issues when I installed an old nvidia MX400 card in my PC. I managed to break X for a while. I can't remember the exact details, but various things have been not quite right since then. Perhaps some files got left behind that are clashing. Any suggestions on where to look?
all you have to do is see if xorg.conf is being saved by nvidia-settings by checking the date stamp. just cd to the /etc/X11/ directory and then do:
ls -la
and it'll show if it saved it within that last minute. You're making sure that you hit "save xorg.conf" within nvidia-settings correct? Also, i noticed that if hit save more than once, it will save it. good luck

---

### Post by dannyboy79 on 2007-06-29
> **Schuenemann said:**
> Hi, I have an old Geforce 256 32 MB. I had it working nicely in Edgy, but I can't configure it in Feisty.

I installed the required packages "sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings"

Then, the text says to run "sudo nvidia-xconfig --no-composite", but I get this error:



Edit: using Kubuntu.

What should I do?

Thanks

you can always manually edit your xorg.conf. Open it with sudo, it's located within /etc/X11/, then at the very end of the file make it look like this

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
then make sure you save it and close it, then restart X with ctrl+alt+backspace

---

### Post by kantarell on 2007-06-29
Could somebody help me, I have installed Envy as it is described here, and also tried with other things like the examples on this page: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) - however I have not gotten Envy to work with my Geforce 6150 graphic card and M2NPV-VM motherboard.

I uninstalled the Nvidia driver, and Envy from my computer. But even though I have ran "sudo dpkg-reconfigure xserver-xorg" the highest resolution I can use ends up with 1280x1024, and this after I have switched to "vesa" in the xorg.conf file. The resolution I get with "nv" is not that high and it doesn't show the whole screen on my Samsung LCD-TV (LE19R) which is capable of 1440x900 (recommended resolution. It is a widesdcreen monitor so it would be better with this resolution.

Attached is my xorg.0 file, well I can't attach this so I'll quote it here:

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 29 14:34:37 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SAMSUNG LCD"
(**) |   |-->Device "nVidia Corporation C51PV [GeForce 6150]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7
...
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 2.0.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	..
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	Quadro FX 5600, Quadro FX 4600
(II) Primary Device is: PCI 00:05:0
(--) Chipset GeForce 6150 found
...
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) NV(0): Initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6150"
(**) NV(0): Depth 16, (--) framebuffer bpp 16
(==) NV(0): RGB weight 565
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xFC000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): SAMSUNG LCD: Using hsync range of 30.00-81.00 kHz
(II) NV(0): SAMSUNG LCD: Using vrefresh range of 56.00-75.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
...
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(--) NV(0): Virtual size is 1440x1024 (pitch 1440)
(**) NV(0): *Default mode "1440x900": 108.8 MHz, 56.9 kHz, 60.2 Hz
(II) NV(0): Modeline "1440x900"  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync
(**) NV(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
etc.
(==) NV(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
	[8] -1	0	0xfdbff000 - 0xfdbff7ff (0x800) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[10] -1	0	0xfe024000 - 0xfe027fff (0x4000) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c807 (0x8) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000cc0f (0x10) IX[B]
	[25] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[26] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[27] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[28] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000f400 - 0x0000f40f (0x10) IX[B]
	[35] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[36] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xd0000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

---

### Post by Schuenemann on 2007-06-29
> **dannyboy79 said:**
> you can always manually edit your xorg.conf. Open it with sudo, it's located within /etc/X11/, then at the very end of the file make it look like this

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
then make sure you save it and close it, then restart X with ctrl+alt+backspace
Hi, thanks for your answer.

I tried as you suggested, but when I tried to restart X, I got a black screen with a white cursor blinking. I could type letters, but couldn't enter a command. My only option was to hit Ctrl + Alt + Delete and restart.
I got the same screen, so I had to enter safe mode and replace xorg.conf by the older version.

I noticed the driver in the xorg.conf said 'nv' instead of 'nvidia'. So I changed to 'nvidia' and inserted again the Section Extensions. I got the same result.

As a last attempt, I changed to 'nvidia', but left the Section Extensions out. This time X was restarted and the nvidia logo appeared, but I had a horrible 800x600 resolution and there wasn't any bigger one available at the display settings. Also, I couldn't run glxinfo or glxgears.

What can I do now? (I'd like to say again that I did it in Edgy, so even that old card has to work in Feisty :).

Thanks

---

### Post by adc on 2007-06-29
Hello.

I have a Geforce2 Integrated GPU(really old motherboard :) ) and I'm having problems when I try to install the nvidia drivers. 
I've tried using Envy and it doesn't work. I've tried installing the driver manually(using nvidia-glx-legacy) and I get the same problem: an error screen before login.
If you need any additional info please reply and I shall try to get it. Any help is welcome.

By the way: the --no-composite option used in nvidia-xconfig doesn't work in my case.

---

### Post by TXBDan on 2007-06-30
i just installed ubuntu on my gf's computer which had a crappy ol ATI card that was choking to death on compiz fusion, etc.

i upgraded it to an old nvidia FX5200 i had around. i was a little weary about swapping drivers, etc, but i used envy and it worked like a champ.

brilliant!

---

### Post by steevc on 2007-07-01
> **dannyboy79 said:**
> all you have to do is see if xorg.conf is being saved by nvidia-settings by checking the date stamp. just cd to the /etc/X11/ directory and then do:
ls -la
and it'll show if it saved it within that last minute. You're making sure that you hit "save xorg.conf" within nvidia-settings correct? Also, i noticed that if hit save more than once, it will save it. good luck

It's definitely being updated. The results can be seen back in post #138. Can someone look at that or post your own version for me to compare. I still wonder if something is conflicting and causing the settings not to be used, but I have no idea what it could be.

This is a frustrating issue, but at least I can use the PC. I just run nvidia-settings each session and fix the refresh, but this is trickier for other family members who use the PC.

Cheers

---

### Post by banelos on 2007-07-01
A strong suggestion for all Linux newcomers who has a Geforce 8800 GTS as me.
If you can't get the nvidia drivers included in Feisty Fawn to work do this:

**Go to Alberto Milone's website and run Envy** ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

I tried removing all nvidia related and installing nvidia-glx-new, I tried manually compiling the newest drivers from Nvidia but neither with any success.. Only after trying this simple script did I succeed in getting it to work.

---

### Post by Schuenemann on 2007-07-01
Well, after almost a week I did it.

I had to insert this line -> Option "AllowGLXWithComposite" "True" <- in section device.

That allowed me to use GLX, but at 800x600 only. So I changed my monitor config and that allowed to use 1024x768, but without GLX.
I noticed that that line was removed, so I inserted it back again and everything finally worked fine.

My final xorg.conf is at [http://paste.ubuntu-nl.org/28166/](http://paste.ubuntu-nl.org/28166/) if anyone cares.

Thanks

---

### Post by AvalonSkies on 2007-07-03
Envy works!

I had to tweak a setting or two, and run the nvidia config app as su to get it to save xorg.conf properly. But it works. Thanks a lot!

(Jeez... one day most Linux tasks are probably going to have automation like this. And that will be awesome.)

---

### Post by bsmith1051 on 2007-07-03
I nominate "Envy" as _the_ _best_ 3rd-party tool!  Considering how critical -- and sensitive -- the video drivers are in Linux, this tool is like magic.

Now, what will it take for X server, in general, to become more robust?  I mean, I just installed the latest "Ubuntu" updates and didn't notice there was a kernel upgrade included.  Rebooted today and BOOM no video.  Even Windows (cough hack) handles video better than that, i.e., it smoothly falls-back to VGA mode if necessary.

---

### Post by MindFlayer on 2007-07-04
First of all, huge thanks to tseliot! Envy was the only way I could get my drivers to work without black magic. :)

The only problem I've encountered was trying to install the package 'nvidia-glx-dev'. 
It spew out the following messages:
...
Errors were encountered while processing: 
/var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
...

Apparently, the packages are too old/misversioned in the ubuntu repository so it couldn't be installed. I've also tried to install the package from debian unstable but it had some conflicts as well. I'm clueless now and I really need the package for OpenGL development. :(

---

### Post by Billybobplr on 2007-07-04
> **tseliot said:**
> Hi, I've ported my guide about the Nvidia Drivers to Edgy Eft on the USDF.
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

OR try this mirror:

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)


--------------------------------------------------------------------
Script to make Method 2 faster

You can also use my Envy script which you can find below (for automating Method 2 and solving problems of driver mismatch)

NOTE: this might be dangerous and buggy

This script will download the Nvidia installer (and all the files the installer needs) and set the driver for you.

Get to the following website:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And follow the instructions you will find there.

I have 1 day of experience with linux a friend helped me on my laptop. now im trying to set up on home comp. i have 8800 gts video. i tried the above and get what is equal to a blue screen in windows i guess i dont see my problem in problems section and dont know what info you need from blue screen. i am trying to run 7.04

---

### Post by miceagol on 2007-07-05
> **Billybobplr said:**
> I have 1 day of experience with linux a friend helped me on my laptop. now im trying to set up on home comp. i have 8800 gts video. i tried the above and get what is equal to a blue screen in windows i guess i dont see my problem in problems section and dont know what info you need from blue screen. i am trying to run 7.04

I just tried setting up Ubuntu 7.04 on my computer with an 8800 GTS. The first thing I tried was installing the nvidia-glx-new package, but that leads to an X server crash. Then I tried to install the newest nVidia drivers (100.14.11) manually several times, but still I just got the "blue screen" when I restarted X. In the end I tried using the Envy script, but I only got the same results.

What you need to do to get the 8800 GTS to work in Feisty is to install the older [97.55 drivers]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html") manually. Those are the drivers I use now, and they work perfectly.

---

### Post by tseliot on 2007-07-06
> **miceagol said:**
> I just tried setting up Ubuntu 7.04 on my computer with an 8800 GTS. The first thing I tried was installing the nvidia-glx-new package, but that leads to an X server crash. Then I tried to install the newest nVidia drivers (100.14.11) manually several times, but still I just got the "blue screen" when I restarted X. In the end I tried using the Envy script, but I only got the same results.

What you need to do to get the 8800 GTS to work in Feisty is to install the older [97.55 drivers]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html") manually. Those are the drivers I use now, and they work perfectly.

Yep, it's a well-known bug in the package of the driver in Ubuntu :-(

---

### Post by tseliot on 2007-07-06
> **Billybobplr said:**
> I have 1 day of experience with linux a friend helped me on my laptop. now im trying to set up on home comp. i have 8800 gts video. i tried the above and get what is equal to a blue screen in windows i guess i dont see my problem in problems section and dont know what info you need from blue screen. i am trying to run 7.04

did you try Envy?

If you want to get back to the Desktop Environment boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vesa" instead of "nv" and try again.

---

### Post by larryh on 2007-07-06
Kubuntu Feisty with an XFX GeForce 7100 GS
I installed the nVidia drivers via synaptic without too much difficulty thanks to all the postings in this forum and the howto here:  

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty) 

Unfortunately I haven't been able to get to any resolutions above 640x480.  Found numerous tips regarding editing the xorg.conf file (again the forums) from users with similar problems but nothing worked for me so I posted to nVidia's Linux forum and got a quick but confusing response:
------------------------------------------
1.0-9755 is no longer supported. If this problem persists with 100.14.11, please start X with the following command:
startx -- -logverbose 6

and then generate and attach an nvidia-bug-report.log.
-------------------------------------------
The bug report I generated with their script does show me to be using 1.0-9755.  Why would the driver I got from the Ubuntu repository be unsupported?  I figured I would try Envy next but I'd really like to understand how I ended up with an unsupported driver first.  Did I mess something up?

---

### Post by raymondx on 2007-07-08
I tried Envy and it didn't work.  I keep on getting the "Fatal Server Error: No Screens Found" Message.  Here are my logs....

---

### Post by puppetj on 2007-07-08
my install on the driver when all to hell, ok i have a geforce fx go5600, in my hp laptop, after do the install i cant get back into x now, i tried sudo dpkg-reconfigure -phigh xserver-xorg, and i picked vesa but i can log in but my desktop is all blank white/tan no menus or icons, i try vga or nv and i just get the blue screen telling my x is messed up

---

### Post by dannyboy79 on 2007-07-09
if you used envy, then you should have a backup of xorg.conf. just go to the directory, /etc/X11/ and look for one of the xorg.conf dates that are before the latest one or the one that has something like _backup on it. then simply delete the file called xorg.conf (because you say it doesn't work), then rename the one that says backup so that it's named xorg.conf and you will be back to the original xorg settings. You can do this from the command line or you can pop in a live cd and mount the partition that contains your /etc/.

---

### Post by puppetj on 2007-07-09
i do not have a back in there, and when & how i get back up running how do i get these drivers installed with Evny so this doesnt happen again?

---

### Post by raymondx on 2007-07-10
Looks like my Geforce 6600 doesnt want to run on anything linux.  I tried Debian Etch and Fedora 7 and i get the same xserver error.  I even downgraded my Ubuntu to Breezy Badger and it still doesnt work.  Tried gdm kdm and xdm...same result.  But it works perfectly in Windows XP.

---

### Post by puppetj on 2007-07-10
> **dannyboy79 said:**
> if you used envy, then you should have a backup of xorg.conf. just go to the directory, /etc/X11/ and look for one of the xorg.conf dates that are before the latest one or the one that has something like _backup on it. then simply delete the file called xorg.conf (because you say it doesn't work), then rename the one that says backup so that it's named xorg.conf and you will be back to the original xorg settings. You can do this from the command line or you can pop in a live cd and mount the partition that contains your /etc/.



so i'am i out of luck, do i need to reinstall, this becoming similar sounding to a windows response, heheheh

---

### Post by dannyboy79 on 2007-07-11
> **raymondx said:**
> Looks like my Geforce 6600 doesnt want to run on anything linux.  I tried Debian Etch and Fedora 7 and i get the same xserver error.  I even downgraded my Ubuntu to Breezy Badger and it still doesnt work.  Tried gdm kdm and xdm...same result.  But it works perfectly in Windows XP.
The 6600 is MORE than compatible with X-Org. VESA works fine and if you want accelerated graphics, use nvidia-glx-new from the Ubuntu Extra Repositories. You can enable them using this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---

### Post by dannyboy79 on 2007-07-11
> **puppetj said:**
> so i'am i out of luck, do i need to reinstall, this becoming similar sounding to a windows response, heheheh
No you're not out of luck and there's almost NEVER EVER a reason to reinstall Ubuntu if that's what you're asking.


I thought I have already explained what you need to do. Log into the terminal if you're saying that you don't have an xserver (meaning gui desktop). then use the following commands from the command line

```
sudo envy -t
```
that should start envy in text mode, use it to uninstall Nvidia drivers. it may or may not remove the xorg.conf that you have that doesn't work and put back the original but I am not sure. Once it's done running, you can exit it, then run this command to give your xserver a try
```
sudo /etc/init.d/gmd stop && sudo /etc/init.d/gdm start
```
**use kdm instead of gdm IF you're using Kubuntu I think (i don't use Kubuntu)
that should get you to a gui login window IF envy put back your original xorg.conf file IF NOT, perform the below steps.


If you want to do these steps below than that means that you tried to login again to your gui desktop and xserver still failed. you should be back at the command line and logged in, if you're not logged in, than log into the command line and do these steps.
```
cd /etc/X11/
```
```
ls -la
```
this should show several files within the /etc/X11/ directory. among them you should see xorg.conf and something along the lines of xorg.conf_somethingorother OR xorg.conf.somethingorother. MAKE sure you chose the one with the OLDEST date to ensure that it's the original xorg.conf file before you changed anything in it.   (that merely means that I am not exactly sure what envy renames the original xorg.conf but I know it does make a backup of the original xorg.conf, which is the config file that the xserver uses) IF you don't see an xorg.conf file other than the main one, meaning xorg.conf, then there is no backup and we'll have to try another way but for now I am guessing there's a backup because you stated you used Envy.
```
sudo mv xorg.conf xorg.conf_notworking
```
this will rename the xorg.conf that isn't working for you and rename it to what I put, you can use anyname that you want, but make sure it's not the same as any other file in the directory. The sudo password is the same password that you chose when you installed Ubuntu. If you don't remember that password than you can find the solution within these forums but I am guessing that since you installed Envy, you know the sudo password
```
sudo mv xorg.conf_somethingorother xorg.conf
```
What the above command is saying is you need to chose whatever that backed up xorg.conf filename is and rename it to xorg.conf. SO, you should now have the original xorg.conf file back in place, so we can try to log in again. so do this again:
```
sudo /etc/init.d/gmd stop && sudo /etc/init.d/gdm start
```
now if the xserver fails again, then we can try this after you relogin into the command line if you're aren't already logged into it.
sudo dpkg-reconfigure xserver-xorg
now it will ask you ton's of questions, the important one is in the begining, I want you to chose VESA as the driver. then answer all the rest of the questions to the best of your knowledge and any you don't know what to do, then just chose the default, it will be ok. Make sure that the resolutions are the ones that are applicable to your graphics card as well. then when that's done. you can then again try to login to your gui deskop with this again:
```
sudo /etc/init.d/gmd stop && sudo /etc/init.d/gdm start
```
If that doesn't get you in, then please post back and tell me exactly what the output from the following command, paste the results into a website called [www.pastebin.com](www.pastebin.com).

cat /var/log/Xorg.0.log

this will be a very large file with lots of contents, that's why I want you to paste it at pastebin, it's a website to store text data online to share with others. good luck

---

### Post by Beatbreaker on 2007-07-11
Hi, i installed the NVIDIA drivers with Envy now i can't boot up and get this message after the Ubuntu loading screen has completed:

```
(EE)NVIDIA(0): Failed to initialize the NVIDIA kernel module! 
please ensure that there is a supported NVIDIA GPU in this system and the the NVIDIA device files have been created properley 

**aborting**
Screen(s) found bu none have a usable configuration
Fatal server error:
No screens found
```


what have i done here?

i'm going to try "sudo dpkg-reconfigure xserver.xorg"  

i'll post my error log, but would like to know what i've done wrong with it all too.

---

### Post by dannyboy79 on 2007-07-11
here's the solution: [http://ubuntuforums.org/showthread.php?t=443846&highlight=Envy+No+screens+found](http://ubuntuforums.org/showthread.php?t=443846&highlight=Envy+No+screens+found)

Please use search feature in forum, it'll save you time from having to post a question that's already been asked and answered.

---

### Post by raymondx on 2007-07-11
> **dannyboy79 said:**
> The 6600 is MORE than compatible with X-Org. VESA works fine and if you want accelerated graphics, use nvidia-glx-new from the Ubuntu Extra Repositories. You can enable them using this guide: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

I got back to feisty and reinstalled nvidia-glx-new, this removed nvidia-glx.   But when i tried to enable it using the restricted drivers manager...it tries to bring back nvidia-glx again and remove nvidia-glx-new so i cancelled it right away.  I did a sudo nvidia-glx-config enable and restarted, this brought me back to the xserver error.  Adding "nv" to the DISABLED_MODULES" gives me a blank screen (PC just crashed).

---

### Post by puppetj on 2007-07-11
"I thought I have already explained what you need to do. Log into the terminal if you're saying that you don't have an xserver (meaning gui desktop). then use the following commands from the command line

Code:

sudo envy -t"



yes i thought i mentioned that i did to the envy t, text menu, to unistall, didnt help, i cleaned, i reinstalled now luck.

but i'll try these steps.

---

### Post by dannyboy79 on 2007-07-12
you guys are not following the guides properly (maybe you are but it's also possible that you used the restricted module manager and it doesn't properly flush out old drivers) and your having conflicts with the various nvidia drivers. follow these steps if you have any card towards the top of this list ([http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)), then use the nvidia-glx-new (which is the 9755 driver within in the repos), any card in the middle section on this list use nvidia-glx, and then at the bottom use nvidia-glx-legacy. These are all in the repo's. NO need for Envy and or restricted module manager as it didn't pick the correct one for me, then I had the API mismatch problem.

Follow the steps in post number 78 here ([http://ubuntuforums.org/showthread.php?t=432056&page=8](http://ubuntuforums.org/showthread.php?t=432056&page=8)) for your specific card and driver.

---

### Post by kurian on 2007-07-12
Me using a nvidia graphics card :**Nvidia Geforce2 integrated GPU** , using the restricted driver manager i installed the driver necessary for the graphics card but after restarting a portion of the screen appears and the remaining is black... everything looks awkward.

I was not having any problem when i used the dapper drake. How can i correct this problem... When i searched the net many users who uses the Nvidia Geforce2 integrated GPU suffers the same problem.... But not any reply gives a satisfactory solution how to overcome this problem

Kindly reply with a good solution as soon as possible so that i could enjoy feisty fawn with all its feisty...

---

### Post by dannyboy79 on 2007-07-12
> **kurian said:**
> Me using a nvidia graphics card :**Nvidia Geforce2 integrated GPU** , using the restricted driver manager i installed the driver necessary for the graphics card but after restarting a portion of the screen appears and the remaining is black... everything looks awkward.

I was not having any problem when i used the dapper drake. How can i correct this problem... When i searched the net many users who uses the Nvidia Geforce2 integrated GPU suffers the same problem.... But not any reply gives a satisfactory solution how to overcome this problem

Kindly reply with a good solution as soon as possible so that i could enjoy feisty fawn with all its feisty...

try the post immediately before yours and let us know how that goes!

---

### Post by raymondx on 2007-07-12
> **dannyboy79 said:**
> you guys are not following the guides properly (maybe you are but it's also possible that you used the restricted module manager and it doesn't properly flush out old drivers) and your having conflicts with the various nvidia drivers. follow these steps if you have any card towards the top of this list ([http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)), then use the nvidia-glx-new (which is the 9755 driver within in the repos), any card in the middle section on this list use nvidia-glx, and then at the bottom use nvidia-glx-legacy. These are all in the repo's. NO need for Envy and or restricted module manager as it didn't pick the correct one for me, then I had the API mismatch problem.

Follow the steps in post number 78 here ([http://ubuntuforums.org/showthread.php?t=432056&page=8](http://ubuntuforums.org/showthread.php?t=432056&page=8)) for your specific card and driver.

Your guide must be missing something because doing a CTRL+ALT+Backspace immediately after installing the nvidia-glx-new just reloaded the vesa.  So I tried doing a "nvidia-glx-config enable again".  I knew i got it right  because the change registered in the restricted drivers manager.  But then...restarting my PC brought me to another xserver error.  It said something like this....

(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
No screens found.

---

### Post by dannyboy79 on 2007-07-12
> **raymondx said:**
> Your guide must be missing something because doing a CTRL+ALT+Backspace immediately after installing the nvidia-glx-new just reloaded the vesa.  So I tried doing a "nvidia-glx-config enable again".  I knew i got it right  because the change registered in the restricted drivers manager.  But then...restarting my PC brought me to another xserver error.  It said something like this....

(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
No screens found.
Well it sounds like your xorg.conf is missing a section! What does this return?
lspci -v | grep nV
It should be similar to this:
01:00.0 VGA compatible controller: nVidia Corporation
The very begining means it's at PCI BusID 01:00.0. So the error is saying that you have a device there, but there's no config info for it within your xorg.conf.

Make sure that your xorg.conf has a Device section like this example:
Section "Device"
        Identifier      "nVidia Corporation NV44A [GeForce 6200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Sorry about the missing part of the instructions. Good catch! I just updated it. I added this just prior to the bug info regarding the 5700.

Using your favorite text editor, open the current xorg.conf located within /etc/X11/ using sudo and make that the Driver line reads nvidia instead of vesa. Ensure that you save the file before closing.

---

### Post by raymondx on 2007-07-13
> **dannyboy79 said:**
> Well it sounds like your xorg.conf is missing a section! What does this return?
lspci -v | grep nV
It should be similar to this:
01:00.0 VGA compatible controller: nVidia Corporation
The very begining means it's at PCI BusID 01:00.0. So the error is saying that you have a device there, but there's no config info for it within your xorg.conf.

Make sure that your xorg.conf has a Device section like this example:
Section "Device"
        Identifier      "nVidia Corporation NV44A [GeForce 6200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Sorry about the missing part of the instructions. Good catch! I just updated it. I added this just prior to the bug info regarding the 5700.

Using your favorite text editor, open the current xorg.conf located within /etc/X11/ using sudo and make that the Driver line reads nvidia instead of vesa. Ensure that you save the file before closing.

doing this command...

lspci -v | grep nV

gives me this message ....

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2) (prog-if 00 [VGA])

so i did a "sudo nano /etc/X11/xorg.conf" and i found this section ....

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        BusID           "PCI:0:5:0"
EndSection

Changing the BusID to  "PCI:1:0:0" gives me a black screen and crashes my pc.  Will it make any difference if i change the identifier?

---

### Post by raymondx on 2007-07-13
continuation....

changing the BusID "PCI:0:5:0" to BusID "PCI:1:0:0" gives me a black screen.  I restarted my PC in recovery mode so i could retrieve the Xorg.0.log file (see attachment)

It seems to say that it's missing a Module "wfb".  How can i solve this?

---

### Post by Beatbreaker on 2007-07-14
> **dannyboy79 said:**
> 
```
dmesg | grep NVIDIA
```
there better not be anything that returned from that referencing the nvidia driver because we removed and purged it all. If there is let me know and we'll have to talk some more. Also, when you do this
```
cat /etc/X11/xorg.conf | grep Driver
```
you should get back "vesa" at the end of the results which means that the xserver is using the vesa driver.


ok when i get up to this step i get this - does it mean that i've still got some Nvidia stuff installed on my system that i haven't removed yet? i think it's because of the chips on my motherbard though and has little to do with the GPU that i'm using. - i'll plough ahead anyway and see what happens - but just in case it's relevant i'll post it here:

```
XXXXX@XXXXX-desktop:~$ dmesg | grep NVIDIA
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
XXXXXX@XXXXXX-desktop:~$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "vesa"

```

---

### Post by Beatbreaker on 2007-07-14
ok well that worked - I've even got a "NVIDIA X-Server settings" button in my system tools now.

my Compiz Fusion has stopped working now though, which is odd because it was working before when i was using the restricted drivers compiz installed by default.  

if i type compiz in the terminal now i get this error message

```
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

---

### Post by Sockerdrickan on 2007-07-14
Why be so difficult when you can just get it from [www.nvidia.com](www.nvidia.com) and install it?





sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start

---

### Post by raymondx on 2007-07-14
I think i'm making progress here.... i got rid of the missing Module "wfb" error by running the latest Envy version but i hit another snag......

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c5d91]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by Beatbreaker on 2007-07-14
> **Tux0r said:**
> Why be so difficult when you can just get it from [www.nvidia.com](www.nvidia.com) and install it?





sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start

this did it - man you're a genius!!! I tried everything to get this thing working!

---

### Post by raymondx on 2007-07-15
> **Tux0r said:**
> Why be so difficult when you can just get it from [www.nvidia.com](www.nvidia.com) and install it?





sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start

I followed your instructions religiously using the latest driver (NVIDIA-Linux-x86_64-100.14.11-pkg2.run)  and this is what i got....

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x6d) [0x48282d]
1: /lib/libc.so.6 [0x2b371b241d40]
2: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv001082X+0x36) [0x2b371d902eb6]

Fatal server error:
Caught signal 11.  Server aborting

I stored the xserver log file and its detailed copy when i did a "startx -- -logverbose 5" in the attachments below.......i'm beginning to think that there's something wrong with the card or i shouldnt be using the latest drivers but everything worked just fine on XP.

---

### Post by larryh on 2007-07-16
I didn't have any luck with what was in the Ubuntu repositories getting my GeForce 7100 GS working so I tried Envy.  My problems continued so I turned to the nVidia forum at nvnews.net.  They will only assist if you attach a log file created by their nvidia-bug-report.sh script.  Does Envy install this script or will I only have access to it if I install the drivers directly from nVidia?

---

### Post by dannyboy79 on 2007-07-16
> **Tux0r said:**
> Why be so difficult when you can just get it from [www.nvidia.com](www.nvidia.com) and install it?





sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start
It's not difficult if people hadn't played around with the RMM (Restricted Modules Manager) and tried other things before just simply using the Ubuntu Repositories to begin with as I have suggested. Your way ASSUMES that they aren't using the RM's for their WIFI (Athero's chip for example), so you should really tell people that before you tell them to remove the restricted modules package.

---

### Post by pjrettin on 2007-07-17
> **dabl said:**
> I just installed the latest Nvidia driver with the Envy script -- worked like a charm, as always.  Thank you tseliot!  I noticed a nice speedup on my GeF 7900GS card with glxgears, too.  I was getting about 17,000 fps with the -9755 driver -- here's what I'm getting with the new driver:

```
dibl@feisty:~$ glxgears
99922 frames in 5.0 seconds = 19984.284 FPS
99885 frames in 5.0 seconds = 19976.876 FPS
99889 frames in 5.0 seconds = 19977.625 FPS
99855 frames in 5.0 seconds = 19970.836 FPS
99885 frames in 5.0 seconds = 19977.000 FPS
99888 frames in 5.0 seconds = 19977.492 FPS
99897 frames in 5.0 seconds = 19979.236 FPS
99878 frames in 5.0 seconds = 19975.588 FPS
99901 frames in 5.0 seconds = 19980.184 FPS
99878 frames in 5.0 seconds = 19975.520 FPS

```

Of course, once I turn on Beryl that drops to 12,000 real fast!

I have a 7800GS and I'm lucky if I get 1500-7000.

---

### Post by dannyboy79 on 2007-07-18
> **pjrettin said:**
> I have a 7800GS and I'm lucky if I get 1500-7000.

well then you don't have 3d accelerated graphics working I would have to say. WHat does glxinfo | grep Di OR glxinfo | grep di

NOTE: I forget whether it's Direct Rendering = yes or direct rendering = yes so I am having you try both. If that's not set to yes, then something is wrong. Also, you can check this

dmesg | grep nV

It should return that the Nvidia driver is being loaded.

---

### Post by SerialSniper on 2007-07-19
I am still having trouble installing the drivers for my XFX 8800GTS 320MB


Using METHOD 1 - It seems to take but then after I ctrl+Alt+backscape I get I message saying xserver could not load. Do I want to see the log file. In the log files it says something along the lines about the driver could not be loaded and no screen/display found.

To get xserver back up I have to 

dpkg-reconfigure -phigh xserver-xorg.

So I tried METHOD 2 - and I get to the point were you actually install the nvida.run file but it complains that  I do not have libc header files installed on my system.

btw it is a completely new install of 7.04. I did the updates only then tried to install the driver.

Thanks.

---

### Post by pjrettin on 2007-07-19
> **dannyboy79 said:**
> well then you don't have 3d accelerated graphics working I would have to say. WHat does glxinfo | grep Di OR glxinfo | grep di

NOTE: I forget whether it's Direct Rendering = yes or direct rendering = yes so I am having you try both. If that's not set to yes, then something is wrong. Also, you can check this

dmesg | grep nV

It should return that the Nvidia driver is being loaded.

It reports directing rendering is on.

---

### Post by FenrirVII on 2007-07-20
This stuff is hilarious sometimes, Great work on the guide.  But for me.. i finished it all right yet It was bugged somehow.  Instead of a list off of the Glxinfo, it just gave me about 9 lines of small mixxed codes and errors.  Basically It couldnt find anything or such.  Well I went into my "Im not going to remember what im about to do because im going to severely #$%@ it up " mode, where i do anything that is possible to make the code work.. and somehow i did.. Something to do with the xorg backup though.  Glx works fine somehow,  

Im just wondering if Getting a bug, and then doing some massive changes in the xorg backup and other various files could have some hidden disastrous effects? Again my glxgears is running, direct rendering and all the works are in order.. I just am worried there could be something behind it all thats messing up that glxgears couldnt catch?

---

### Post by bwallum on 2007-07-27
Hello

I've done a silly.

I got Envy up and running and it was great. Configured the nVidia driver, great too. I then looked at screen resolution in Ubuntu's default top menu (I'm running on a Windows box at the moment and can't precisely remember the Ubuntu setup). It hadn't changed from the very basic options. I thought this might conflict with Envy so I removed the (what i perceived to be the earlier) nVidia driver with the restricted packages manager.

So here I am with command line only, no idea of what to do, and very, very little knowledge of Linux. I presume I have blown up X something or other GUI. 

Any way back with this or do I have to re-install Ubuntu?

Regards
Bob

---

### Post by blackjackel on 2007-07-27
I used envy to install the driver and it works, though it dosent have sli enabled, and I've tried the command to enabled it with no luck.... I can't find a howto on how to get SLI enabled anywhere...

---

### Post by aum11 on 2007-07-27
Have ati mobility radean x1400 and am supposed to have screen resolution of 1920x1200, but cannot get offered more than 1280x1024..  Even when I add in 1920x1200 to xorg.conf, the gdm fails and returns to login screen and finally returns with 1280x1024 eventually.

Just ran envy and still no change.

Can you offer any help?

Thanks.

---

### Post by serfcx on 2007-07-27
> **bwallum said:**
> Hello

I've done a silly.

I got Envy up and running and it was great. Configured the nVidia driver, great too. I then looked at screen resolution in Ubuntu's default top menu (I'm running on a Windows box at the moment and can't precisely remember the Ubuntu setup). It hadn't changed from the very basic options. I thought this might conflict with Envy so I removed the (what i perceived to be the earlier) nVidia driver with the restricted packages manager.

So here I am with command line only, no idea of what to do, and very, very little knowledge of Linux. I presume I have blown up X something or other GUI. 

Any way back with this or do I have to re-install Ubuntu?

Regards
Bob

You can run envy from the command line

sudo envy -t

---

### Post by dannyboy79 on 2007-07-27
as I have pasted more than once, please follow this:

Follow the steps in post number 78 here ([http://ubuntuforums.org/showthread.php?t=432056&page=8](http://ubuntuforums.org/showthread.php?t=432056&page=8)) for your specific card and driver.

---

### Post by bwallum on 2007-07-27
Hole in one!

Heres a big wet sloppy kiss! mmmmmmmmmmmmmmmmmmHHHH! 

It just worked!

At the command prompt type in username and password (when prompted) then use serfcx's  code

```
sudo envy -t
```

Enter your password when prompted again.

Then choose the menu number to install appropriate driver (nVidia or ATI)

Then watch the alien scrolls as goodness knows what happens.

Follow the defaults when prompted and hey presto! Ubuntu's back in glorious technicolour!

"Never; in the field of human endeavour ......." have so many thanks been given for so few words!

Kindest Regards
Bob

---

### Post by bgh10788 on 2007-07-31
Just so you know, I am a complete Linux noob so sorry if this is a really dumb post.  

I have a laptop with an 8400M GS graphics card.  I downloaded the latest drivers on the nVidia site and then followed Method 2 to install them.  Everything installed and looked fine except there were no shutdown or restart buttons in the turn off options (just log out, suspend, switch user,etc).

I had to ctrl+alt+f1 and then push ctrl+alt+del to get the thing to restart.  I figure this is where my problems start.   Once the computer restarts, I get the "no screens found" error and the xserver won't start.  I have to reconfigure the xorg.conf to use the vesa driver.  With this setting, I can restart no problem.  

Another thing, if I reinstall the drivers (using either method 2 or the nvidia installer) it will start everytime, but I can't get it to restart appropriately and work on the restart.

Thanks in advance for your help.

---

### Post by mikko_i on 2007-07-31
Method 2 works beautifully with ACER Aspire 5920G / NVIDIA GeForce 8600M GT. Requires driver version 100.14.09 from nvidia.com.

Thank you!

---

### Post by PhenixRising on 2007-08-02
Thanks for writing this script.  It really made my life easier. Now if only someone could help me fix my sound problem.

---

### Post by tseliot on 2007-08-02
> **bgh10788 said:**
> Just so you know, I am a complete Linux noob so sorry if this is a really dumb post.  

I have a laptop with an 8400M GS graphics card.  I downloaded the latest drivers on the nVidia site and then followed Method 2 to install them.  Everything installed and looked fine except there were no shutdown or restart buttons in the turn off options (just log out, suspend, switch user,etc).

I had to ctrl+alt+f1 and then push ctrl+alt+del to get the thing to restart.  I figure this is where my problems start.   Once the computer restarts, I get the "no screens found" error and the xserver won't start.  I have to reconfigure the xorg.conf to use the vesa driver.  With this setting, I can restart no problem.  

Another thing, if I reinstall the drivers (using either method 2 or the nvidia installer) it will start everytime, but I can't get it to restart appropriately and work on the restart.

Thanks in advance for your help.
If you're looking for a quick way to solve the problem you might want to try Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

**NOTE: Envy is a 3rd party application and you should use it at your risk**

If you decide to use Envy you will have to install it by following point "A" of the instructions:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

then try point "B" (starting from step 3)

and finally install the driver through Envy

---

### Post by tseliot on 2007-08-02
> **blackjackel said:**
> I used envy to install the driver and it works, though it dosent have sli enabled, and I've tried the command to enabled it with no luck.... I can't find a howto on how to get SLI enabled anywhere...
try with:
```
sudo nvidia-xconfig --sli=Auto
```

---

### Post by tseliot on 2007-08-02
> **bwallum said:**
> Hello

I've done a silly.

I got Envy up and running and it was great. Configured the nVidia driver, great too. I then looked at screen resolution in Ubuntu's default top menu (I'm running on a Windows box at the moment and can't precisely remember the Ubuntu setup). It hadn't changed from the very basic options. I thought this might conflict with Envy so I removed the (what i perceived to be the earlier) nVidia driver with the restricted packages manager.

So here I am with command line only, no idea of what to do, and very, very little knowledge of Linux. I presume I have blown up X something or other GUI. 

Any way back with this or do I have to re-install Ubuntu?

Regards
Bob
maybe run Envy and install the driver again?

---

### Post by tseliot on 2007-08-02
> **aum11 said:**
> Have ati mobility radean x1400 and am supposed to have screen resolution of 1920x1200, but cannot get offered more than 1280x1024..  Even when I add in 1920x1200 to xorg.conf, the gdm fails and returns to login screen and finally returns with 1280x1024 eventually.

Just ran envy and still no change.

Can you offer any help?

Thanks.
You should start a new thread since this one is about the Nvidia driver.

---

### Post by tseliot on 2007-08-02
> **SerialSniper said:**
> I am still having trouble installing the drivers for my XFX 8800GTS 320MB


Using METHOD 1 - It seems to take but then after I ctrl+Alt+backscape I get I message saying xserver could not load. Do I want to see the log file. In the log files it says something along the lines about the driver could not be loaded and no screen/display found.

To get xserver back up I have to 

dpkg-reconfigure -phigh xserver-xorg.

So I tried METHOD 2 - and I get to the point were you actually install the nvida.run file but it complains that  I do not have libc header files installed on my system.

btw it is a completely new install of 7.04. I did the updates only then tried to install the driver.

Thanks.
please, follow these instructions:
[http://ubuntuforums.org/showpost.php?p=3120577&postcount=214](http://ubuntuforums.org/showpost.php?p=3120577&postcount=214)

---

### Post by Terry of Astoria on 2007-08-02
I only want to say that I somehow got my kernel modules and drivers mismatched by using the restricted drivers manager and then Automatix  (It's too easy to mess up with both options there . . .) to manage my driver for my Geforce FX 5200 and man, it would not get straight for a while even though I tried everything I could think of a read of.  Then I came upon this HOWTO and method one failed, but man, ol' Envy sure did the trick.  Props to you, tseliot and thanks to you and everyone else who works together on these good projects. Thanks again!

---

### Post by eazybeet on 2007-08-03
Hey many thanks this software is awesome - it istalled my Nvidia 8800 gts card when all else failed:)

---

### Post by NoThanksM$ on 2007-08-08
What an amazing program!  I have years of experience as a Windows administrator and just recently jumped into using Linux at home.  I tried various sets of instructions but could not get the nVidia driver working with my 8600GTS, I kept getting the API Mismatch error.  I tried Envy and it worked perfectly the first time.  I only wish I knew what it did that I didn't do.  Thank you!

---

### Post by chrisstankevitz on 2007-08-08
Will someone please answer my three questions:

1. Why would someone use this instead of "restricted device manager" which worked for me in 32 bit ubuntu?
2. Does the "envy" technique work in 64 bit Ubuntu?
3. Why does 64 bit ubuntu report "no hardware found" while 32 bit ubuntu's RDM gets my nvidia up and running?  (Same machine)

Thanks,

Chris

---

### Post by benjr06 on 2007-08-09
> **tseliot said:**
> ...

Or you might just type:
```
sudo nvidia-settings

```

Thanks a ton for the code.  I've been looking for this command.  I knew my drivers were installed, but I just couldn't figure out how in the world to change the screen resolution.

---

### Post by tseliot on 2007-08-09
> **chrisstankevitz said:**
> Will someone please answer my three questions:

1. Why would someone use this instead of "restricted device manager" which worked for me in 32 bit ubuntu?
If you need the latest driver you can use Envy (at your own risk). It also works with recompiled kernels (provided that paravirtualisation is disabled in the kernel)

> **chrisstankevitz said:**
> 2. Does the "envy" technique work in 64 bit Ubuntu?
Sure

> **chrisstankevitz said:**
> 3. Why does 64 bit ubuntu report "no hardware found" while 32 bit ubuntu's RDM gets my nvidia up and running?
Honestly, I have no idea. I know that RDM takes the list of the supported cards from the driver (or something like that). I didn't write RDM therefore I can't be sure of what can be causing your problem.

Maybe you should report the bug on Launchpad

---

### Post by dannyboy79 on 2007-08-09
> **chrisstankevitz said:**
> Will someone please answer my three questions:

1. Why would someone use this instead of "restricted device manager" which worked for me in 32 bit ubuntu?
2. Does the "envy" technique work in 64 bit Ubuntu?
3. Why does 64 bit ubuntu report "no hardware found" while 32 bit ubuntu's RDM gets my nvidia up and running?  (Same machine)

Thanks,

Chris

1. the restricted module didn't work for me! it kept chosing the 9631 driver and giving me a API mismatch.
2. you'd have to read tseliot's webpage, not sure.
3. not sure, don't mess with 64bit despite having a core2duo. to much messing around with firefox and other programs when it's a marginal gain in performance.

---

### Post by dannyboy79 on 2007-08-09
> **NoThanksM$ said:**
> What an amazing program!  I have years of experience as a Windows administrator and just recently jumped into using Linux at home.  I tried various sets of instructions but could not get the nVidia driver working with my 8600GTS, I kept getting the API Mismatch error.  I tried Envy and it worked perfectly the first time.  I only wish I knew what it did that I didn't do.  Thank you!

if you want to know how it works, take a look at the code. just scroll along and see what the command are.

---

### Post by dartmusic on 2007-08-09
This is making me crazy!

I can't get the nvidia drivers to load properly.  I've tried EVERY possibility listed in these forums, but to no avail.  

Now, finally trying Envy for about the 10th time, I'm once again getting an error when the script tries to build nvidia-kernel-source, with no explanation.

Help...please!! :)

---

### Post by tseliot on 2007-08-10
> **dartmusic said:**
> This is making me crazy!

I can't get the nvidia drivers to load properly.  I've tried EVERY possibility listed in these forums, but to no avail.  

Now, finally trying Envy for about the 10th time, I'm once again getting an error when the script tries to build nvidia-kernel-source, with no explanation.

Help...please!! :)

post your /var/log/envy-installer.log

I'm sure there is an explanation to your problem

---

### Post by dartmusic on 2007-08-10
Here you go...and thanks!

```
python pulse.py nvidia 
root@rickstone-desktop:/usr/share/envy# python pulse.py nvidia 
Ubuntu Feisty 32bit
Your graphic card has been detected as a GeForce 6200
Your graphic card is supported by the latest driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
Package nvidia-kernel-2.6.20-16-386 is not installed, so not removed
Package nvidia-glx-dev is not installed, so not removed
Package nvidia-kernel-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not installed, so not removed
E: Couldn't find package nvidia-new-kernel-2.6.20-16-386
E: Invalid operation nvidia-new-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not installed, so not removed
Package nvidia-legacy-kernel-source is not installed, so not removed
Package nvidia-settings is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx-control is not installed, so not removed
E: Couldn't find package fglrx-kernel-2.6.20-16-386
output is ['']
lenoutput is 1
An installer has been detected
md5new: af434d27f9b089ac1cb216f55f9b0f33
md5sumold: af434d27f9b089ac1cb216f55f9b0f33
dpkg-buildpackage: source package is nvidia-graphics-drivers
dpkg-buildpackage: source version is 1:100.14.12
dpkg-buildpackage: source changed by Alberto Milone (tseliot) <albertomilone@alice.it>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 100.14.12
debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp build-kernel-stamp configure-stamp
dh_clean
rm -fr NVIDIA-Linux-x86-100.14.11-pkg0  nvidia-kernel-source.tar.gz
 debian/rules build
rm -f debian/nvidia-kernel-source.README.Debian debian/control debian/copyright debian/nvidia-glx.links debian/nvidia-glx-dev.links debian/nvidia-glx.override debian/nvidia-glx.docs debian/nvidia-glx.examples debian/nvidia-glx.postrm debian/nvidia-glx.init debian/nvidia-glx-ia32.override debian/nvidia-glx-ia32.links debian/nvidia-kernel-source.docs debian/nvidia-glx-dev.preinst || true
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-kernel-source.README.Debian.in > debian/nvidia-kernel-source.README.Debian
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/control.in > debian/control
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/copyright.in > debian/copyright
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-glx.links.in > debian/nvidia-glx.links
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-glx-dev.links.in > debian/nvidia-glx-dev.links
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-glx.override.in > debian/nvidia-glx.override
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
< debian/nvidia-glx.docs.in > debian/nvidia-glx.docs
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-glx.examples.in > debian/nvidia-glx.examples
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-glx.postrm.in > debian/nvidia-glx.postrm
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
< debian/nvidia-glx.init.in > debian/nvidia-glx.init
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-glx-ia32.override.in > debian/nvidia-glx-ia32.override
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
< debian/nvidia-glx-ia32.links.in > debian/nvidia-glx-ia32.links
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-kernel-source.docs.in > debian/nvidia-kernel-source.docs
perl -p \
        -e 's{#BASE_VERSION#}{}g;' \
        -e 's{#RELEASE#}{100.14.11}g;' \
        -e 's{#VERSION#}{100.14.11}g;' \
        -e 's{#NEXTVER#}{100.14.12}g;' \
        -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-100.14.11-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-100.14.11-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
        < debian/nvidia-glx-dev.preinst.in > debian/nvidia-glx-dev.preinst
dh_testdir
./NVIDIA-Linux-x86-100.14.11-pkg0.run --extract-only
Creating directory NVIDIA-Linux-x86-100.14.11-pkg0
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 100.14.11..................................
...........................................................................................
if test -d /usr/share/envy/nvidia-graphics-drivers/patches; \
        then \
                pwd; \
                ls -al; \
                cd NVIDIA-Linux-x86-100.14.11-pkg0/usr/src/nv; \
                for i in /usr/share/envy/nvidia-graphics-drivers/patches/*; \
                        do patch -p3 <$i; \
                done; \
        fi
sed 's/^nvidia-graphics-drivers/nvidia-kernel/g'  debian/changelog > debian.binary/changelog
touch configure-stamp
touch build-stamp
 debian/rules binary
touch build-stamp
dh_testroot
dh_testdir
# build kernel module source tarball
mkdir -p /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian
mkdir -p /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/nv
cp -r /usr/share/envy/nvidia-graphics-drivers/debian.binary/* /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian
for f in `ls /usr/share/envy/nvidia-graphics-drivers/debian.binary` ; do \
                perl -p \
                -e 's{#BASE_VERSION#}{}g;' \
                -e 's{#RELEASE#}{100.14.11}g;' \
                -e 's{#VERSION#}{100.14.11}g;' \
                -e 's{#UPSTREAMVERSION#}{100.14.11}g;' \
                -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg0.run}g' \
                < /usr/share/envy/nvidia-graphics-drivers/debian.binary/$f >            /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/$f ; \
                chmod 0644 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/$f ; \
            done
/bin/sh: cannot create /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patches: Is a directory
chmod 755 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patches          
cp /usr/share/envy/nvidia-graphics-drivers/NVIDIA-Linux-x86-100.14.11-pkg0/usr/src/nv/* /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/nv || true
chmod 755 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/rules
chown -R root:src /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules
tar -zcvf /usr/share/envy/nvidia-graphics-drivers/nvidia-kernel-source.tar.gz -C /usr/share/envy/nvidia-graphics-drivers/debian/temp modules
modules/
modules/nvidia-kernel/
modules/nvidia-kernel/debian/
modules/nvidia-kernel/debian/README.Debian
modules/nvidia-kernel/debian/changelog
modules/nvidia-kernel/debian/control.template
modules/nvidia-kernel/debian/copyright
modules/nvidia-kernel/debian/devfs.devices
modules/nvidia-kernel/debian/dirs.template
modules/nvidia-kernel/debian/override.template
modules/nvidia-kernel/debian/patches/
modules/nvidia-kernel/debian/patches/03_pci_get_class
modules/nvidia-kernel/debian/patches/02_pcialias
modules/nvidia-kernel/debian/patches/04_minion
modules/nvidia-kernel/debian/patches/00list
modules/nvidia-kernel/debian/patches/01_sysfs
modules/nvidia-kernel/debian/postinst
modules/nvidia-kernel/debian/postrm
modules/nvidia-kernel/debian/rules
modules/nvidia-kernel/nv/
modules/nvidia-kernel/nv/Makefile.kbuild
modules/nvidia-kernel/nv/Makefile.nvidia
modules/nvidia-kernel/nv/README
modules/nvidia-kernel/nv/conftest.sh
modules/nvidia-kernel/nv/cpuopsys.h
modules/nvidia-kernel/nv/gcc-version-check.c
modules/nvidia-kernel/nv/makefile
modules/nvidia-kernel/nv/nv-i2c.c
modules/nvidia-kernel/nv/nv-kernel.o
modules/nvidia-kernel/nv/nv-linux.h
modules/nvidia-kernel/nv/nv-memdbg.h
modules/nvidia-kernel/nv/nv-misc.h
modules/nvidia-kernel/nv/nv-vm.c
modules/nvidia-kernel/nv/nv-vm.h
modules/nvidia-kernel/nv/nv.c
modules/nvidia-kernel/nv/nv.h
modules/nvidia-kernel/nv/nvacpi.c
modules/nvidia-kernel/nv/nvreadme.h
modules/nvidia-kernel/nv/nvtypes.h
modules/nvidia-kernel/nv/os-agp.c
modules/nvidia-kernel/nv/os-agp.h
modules/nvidia-kernel/nv/os-interface.c
modules/nvidia-kernel/nv/os-interface.h
modules/nvidia-kernel/nv/os-registry.c
modules/nvidia-kernel/nv/pat.h
modules/nvidia-kernel/nv/rmretval.h
rm -rf debian/temp 
touch build-kernel-stamp
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
install -m 644 /usr/share/envy/nvidia-graphics-drivers/nvidia-kernel-source.tar.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-kernel-source/usr/src
install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/X11R6/lib/modules/drivers/nvidia_drv.so \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/drivers
install NVIDIA-Linux-x86-100.14.11-pkg0/usr/X11R6/lib/libXvMCNVIDIA.a /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/libXvMCNVIDIA.a;
install NVIDIA-Linux-x86-100.14.11-pkg0/usr/X11R6/lib/libXvMCNVIDIA.so.100.14.11 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/libXvMCNVIDIA.so.100.14.11;
install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/include/GL/gl.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/include/GL/glext.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/include/GL/glx.h \
/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/include/GL/glxext.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/libGL.so.100.14.11 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/libGLcore.so.100.14.11 \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
sed "s/__GENERATED_BY__/Debian nvidia-graphics-drivers/" NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib/" > /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/libGL.la
# install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/libGL.la /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/libGL.la
# TLS (nvidia-tls new for 6106)
install NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/libnvidia-tls.so.100.14.11 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/
install NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/tls/libnvidia-tls.so.100.14.11 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
#sed "s/__GENERATED_BY__/Debian nvidia-graphics-drivers/" NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/tls/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib\/tls/" > /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/nvidia/libGL.la
# install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/tls/libGL.la /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia/libGL.la
install -m 0644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib/libnvidia-cfg.so.100.14.11 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia/
install NVIDIA-Linux-x86-100.14.11-pkg0/usr/X11R6/lib/modules/extensions/libglx.so.100.14.11 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/extensions/
install NVIDIA-Linux-x86-100.14.11-pkg0/usr/X11R6/lib/modules/libnvidia-wfb.so.100.14.11 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/
install NVIDIA-Linux-x86-100.14.11-pkg0/usr/bin/tls_test /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
install NVIDIA-Linux-x86-100.14.11-pkg0/usr/bin/tls_test_dso.so /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
install -d /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/lintian/overrides
install -m 0644 debian/nvidia-glx.override \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/lintian/overrides/nvidia-glx
if [ "i386" == "amd64" ] ; then \
                install NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib32/libGLcore.so.100.14.11 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib32/libGL.so.100.14.11 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib32/libnvidia-tls.so.100.14.11 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-100.14.11-pkg0/usr/lib32/tls/libnvidia-tls.so.100.14.11 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib/tls ; \
        fi
[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86-100.14.11-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-100.14.11-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-100.14.11-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-100.14.11-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs
dh_installdocs -s
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_100.14.12_i386.deb'.
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_100.14.12_i386.deb'.
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_100.14.12_i386.deb'.
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-kernel-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
dpkg: regarding nvidia-kernel-source_100.14.12_i386.deb containing nvidia-kernel-source:
 nvidia-kernel-source conflicts with nvidia-new-kernel-source
  nvidia-new-kernel-source (version 1:100.14.11+2.6.20-16) is installed.
dpkg: error processing nvidia-kernel-source_100.14.12_i386.deb (--install):
 conflicting packages - not installing nvidia-kernel-source
Errors were encountered while processing:
 nvidia-kernel-source_100.14.12_i386.deb
Getting source for kernel version: 2.6.20-16-386
Kernel headers available in /lib/modules/2.6.20-16-386/build
apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

Done!
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;Updating cached package data&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
              &#9474; cipe-source                                                             &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;  &#9474;                               100%                                &#9474;  &#9474;  
              &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  
              &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Updated infos about 85 packages
The source tarball could not be found!
Package nvidia-kernel-source not installed?
Running "m-a -f get nvidia-kernel-source" may help.
find: /usr/src/modules/nvidia*: No such file or directory
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;Building nvidia-kernel-source, step 1, please wait...&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
              &#9474; Package nvidia-kernel-source not installed?                             &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;                                                                         &#9474;  
              &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;  &#9474;                                 0%                                &#9474;  &#9474;  
              &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  
              &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                















































                   &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;module-assistant, interactive mode&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                   &#9474; Build of the package nvidia-kernel-source failed! How do you  &#9474;  
                   &#9474; wish to proceed?                                              &#9474;  
                   &#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474;  
                   &#9474; &#9474;    VIEW      Examine the build log file                   &#9474; &#9474;  
                   &#9474; &#9474;    CONTINUE  Skip and continue with the next operation    &#9474; &#9474;  
                   &#9474; &#9474;    STOP      Stop processing the build commands           &#9474; &#9474;  
                   &#9474; &#9474;                                                           &#9474; &#9474;  
                   &#9474; &#9474;                                                           &#9474; &#9474;  
                   &#9474; &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; &#9474;  
                   &#9474;                                                               &#9474;  
                   &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;module-assistant, error message&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                   &#9474; Package nvidia-kernel-source was not built successfully, see  &#9474;  
                   &#9474; /var/cache/modass/nvidia-kernel-source*buildlog* for details! &#9474;  
                   &#9474;                                                               &#9474;  
                   &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;100%&#9472;&#9472;&#9472;&#9472;&#9508;
&#9474;                           < EXIT >                            &#9474;  
                   &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Selecting previously deselected package nvidia-glx.
(Reading database ... 152074 files and directories currently installed.)
Unpacking nvidia-glx (from nvidia-glx_100.14.12_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-glx:
 nvidia-glx depends on nvidia-kernel-100.14.11; however:
  Package nvidia-kernel-100.14.11 is not installed.
dpkg: error processing nvidia-glx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-glx
ENVY: Operation Completed
root@rickstone-desktop:/usr/share/envy#
```

---

### Post by Sockerdrickan on 2007-08-10
lol that's probably the largest message I ever saw

---

### Post by dartmusic on 2007-08-10
why thank you!

actually, I don't know how to make your message show up in the little scrolling box...any tips?

---

### Post by dannyboy79 on 2007-08-10
it can be helpful and save room on the forum to use pastebin.org, it's a place that you can paste large amounts of text or code for free and then you can simply copy the link, and put the link in the post here. many forums actual request that you do that but I am not sure about this forum. just a tip is all.

---

### Post by tseliot on 2007-08-10
> **dartmusic said:**
> why thank you!

actually, I don't know how to make your message show up in the little scrolling box...any tips?

you can put the text between a [ C O D E ]  and a [ / C O D E ] (without the spaces I put between one letter and the other and between the square brackets and letters.

As regards Envy:

type:
```
sudo apt-get --purge remove nvidia-*
```

```
sudo apt-get --purge remove envy
```

and should the system complain about it (it shouldn’t), just type:
```
sudo rm -R /usr/share/envy
```

Finally, get Envy's latest release from [my website]("http://www.albertomilone.com/nvidia_scripts1.html") , install it an launch it again.

Should the installation go wrong again you can post your /var/log/envy-installer.log again

---

### Post by dartmusic on 2007-08-10
Thanks for ALL of that info, Alberto.

I've done all the steps you listed (which I have already tried multiple times between every new "solution" I run across, with no success as of yet), except for re-installing Envy.  I am at work right now and VNC'ing in to my home machine, so if I re-install Envy and run it and it fails, I won't be able to get back in/on/etc. until I get home this evening.

My only other question, is this: have you updated Envy in the last week?  I installed it (and uninstalled, and reinstalled!) numerous times since last Sunday, always from your site.  

Thanks again.

---

### Post by dartmusic on 2007-08-10
Here's the output of the log.  I let Envy reconfig my xorg.conf file, but haven't yet rebooted.  Sorry to sound like I have little faith, but, I've done this 20 or so times with great success (manually and with Automatix) and have only recently had issues.  Check the log and let me know what you think.

And thanks again!

```
python pulse.py nvidia 
root@rickstone-desktop:/usr/share/envy# python pulse.py nvidia
Ubuntu Feisty 32bit
Your graphic card has been detected as a GeForce 6200
Your graphic card is supported by the latest driver
ENVY: The following packages are not installed:
linux-headers-`uname -r`

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-386 is already the newest version.
The following packages were automatically installed and are no longer required:
  librpcsecgss2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Checking the Dependencies for the New Method
OK: All the packages are installed
An installer has been detected
md5new: d41d8cd98f00b204e9800998ecf8427e
md5sumold: 3e76376b5f1a53e0c18694fa65691c75
ENVY ERROR: md5 Error! Trying to fetch the driver from the website
No installer detected
Download of the driver in progress, please wait
--12:59:04--  http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run
           => `NVIDIA-Linux-x86-100.14.11-pkg1.run'
Resolving us.download.nvidia.com... 61.213.147.6, 61.213.147.9
Connecting to us.download.nvidia.com|61.213.147.6|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15,311,226 (15M) [application/octet-stream]
100%[==========================================================>] 15,311,226    95.48K/s    ETA 00:00

13:01:21 (109.33 KB/s) - `NVIDIA-Linux-x86-100.14.11-pkg1.run' saved [15311226/15311226]
md5new: 3e76376b5f1a53e0c18694fa65691c75
md5sumold: 3e76376b5f1a53e0c18694fa65691c75
Checking the Dependencies for the New Method
OK: All the packages are installed
dpkg-buildpackage: source package is linux-restricted-modules-2.6.20
dpkg-buildpackage: source version is 2.6.20-16
dpkg-buildpackage: source changed by Colin Watson <cjwatson@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.6.20-16
debian/rules clean
echo '# THIS FILE IS AUTO-GENERATED FROM control.stub.in' > debian/control.stub
if [ "1.0.100.14.11" = "1.0.9639" ]; then \
                sed -e 's/@@NV_VERSION@@/1.0.9639/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                sed -e 's/@@NV_NEW_VERSION@@/1.0.100.14.11/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                sed -e 's/@@NV_LEGACY_VERSION@@/1.0.7185/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
echo '# THIS FILE IS AUTO-GENERATED FROM kernel-versions.in' > debian/d-i/kernel-versions;
sed -e 's/@@ABIVER@@/2.6.20/g' \
                debian/d-i/kernel-versions.in >> debian/d-i/kernel-versions
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware
cp -a debian/d-i/modules/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules/
cp: cannot stat `debian/d-i/modules/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/firmware/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware/
cp: cannot stat `debian/d-i/firmware/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/package-list debian/d-i/kernel-versions /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/
ln -s .. /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/debian
(cd /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386 && kernel-wedge gen-control) > debian/control
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
dh_testdir
dh_testroot
rm -f unpack-stamp build-stamp build-kernel-stamp \
                  modalias-patterns-stamp
rm -rf debian/build* debian/temp/
rm -f debian/vmware-*-kernel-modules-*.postinst
rm -f debian/vmware-*-kernel-modules-*.postrm
rm -f debian/linux-restricted-modules-[0-9]*.postinst
rm -f debian/linux-restricted-modules-*.postrm
rm -f debian/linux-restricted-modules-*.preinst
rm -f debian/linux-restricted-modules-*.prerm
rm -f debian/nic-restricted-modules-*.postinst
for i in -dev.dirs -dev.links -dev.postinst -dev.postrm \
                 -dev.preinst .dirs .docs .examples .links.amd64 \
                 .links .override .postinst .postrm .preinst \
                 .prerm .README.Debian .reportbug .shlibs; \
                do rm -f debian/nvidia-glx$i debian/nvidia-glx-legacy$i debian/nvidia-glx-new$i; \
        done
rm -rf nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1; \
        rm -f nvidia-kernel-source.tar.gz nvidia-legacy-kernel-source.tar.gz \
                nvidia-new-kernel-source.tar.gz
rm -f fglrx-kernel-source.tar.gz
dh_clean `find debian/d-i/modules debian/d-i/firmware -type l 2>/dev/null`
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
rm -rf avm-download build-avm-stamp unpack-avm-stamp
rm -rf debian/nic-restricted-modules-*-di \
                   debian/nic-restricted-firmware-*-di
rm -f correct-lib-path
cp -f debian/control.stub debian/control
debian/rules build
dh_testdir
if [ -e debian/build ]; then \
                mv debian/build debian/build.old; \
        fi
mkdir debian/build
mkdir -p debian/build/2.6.20-16-386
if [ "1.0.100.14.11" = "1.0.9639" ]; then       \
                cd nvidia && sh ./NVIDIA-Linux-x86-1.0-9639-pkg1.run --extract-only; \
                if [ -d /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches/ ]; then \
                  for i in /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches/*; do \
                        patch -p0 -d nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1 < $i; \
                  done; \
                fi; \
                cd ..; \
                cd nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1/usr/src/nv && ln -sf Makefile.kbuild Makefile; \
                cd /usr/share/envy/linux-restricted-modules-2.6.20 \
                cp -al nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1/usr/src/nv debian/build/2.6.20-16-386/nv; \
                for i in -dev.dirs -dev.links -dev.postinst -dev.postrm \
                         -dev.preinst .dirs .docs .examples .links.amd64 \
                         .links .override .postinst .postrm .preinst \
                         .prerm .README.Debian .reportbug .shlibs; \
                do sed -e "s/@@VERSION@@/1.0.9639/g" -e "s/@@NV_LEGACY@@//g" \
                        -e "s:@dirname@:nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1:"  -e "s/@@NV_ALT@@//g" \
                        < debian/nvidia-glx$i.in > debian/nvidia-glx$i; \
                done; \
        fi
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then  \
                cd nvidia && sh ./NVIDIA-Linux-x86-100.14.11-pkg1.run --extract-only; \
                if [ -d /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches-new/ ]; then \
                  for i in /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches-new/*; do \
                        patch -p0 -d nvidia/NVIDIA-Linux-x86-100.14.11-pkg1 < $i; \
                  done; \
                fi; \
                cd ..; \
                cd nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv && ln -sf Makefile.kbuild Makefile; \
                cd /usr/share/envy/linux-restricted-modules-2.6.20 \
                cp -al nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv debian/build/2.6.20-16-386/nv-new; \
                for i in -dev.dirs -dev.links -dev.postinst -dev.postrm \
                         -dev.preinst .dirs .docs .examples .links.amd64 \
                         .links .override .postinst .postrm .preinst \
                         .prerm .README.Debian .reportbug .shlibs; \
                do sed -e "s/@@VERSION@@/1.0.100.14.11/g" -e "s/@@NV_LEGACY@@/-new/g" \
                        -e "s:@dirname@:nvidia/NVIDIA-Linux-x86-100.14.11-pkg1:"  -e "s/@@NV_ALT@@/new/g" \
                        < debian/nvidia-glx$i.in > debian/nvidia-glx-new$i; \
                done; \
        fi
Creating directory NVIDIA-Linux-x86-100.14.11-pkg1
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 100.14.11..............................
......................................................................................................
......................................................................................................
............................................
if [ "1.0.100.14.11" = "1.0.7185" ]; then       \
                cd nvidia && sh ./NVIDIA-Linux-x86-1.0-7185-pkg1.run --extract-only; \
                if [ -d /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches-legacy/ ]; then \
                  for i in /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/patches-legacy/*; do \
                        patch -p0 -d nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1 < $i; \
                  done; \
                fi; \
                cd ..; \
                cd nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/src/nv && ln -sf Makefile.kbuild Makefile; \
                cd /usr/share/envy/linux-restricted-modules-2.6.20 \
                cp -al nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/src/nv debian/build/2.6.20-16-386/nv-legacy; \
                for i in -dev.dirs -dev.links -dev.postinst -dev.postrm \
                         -dev.preinst .dirs .docs .examples .links.amd64 \
                         .links .override .postinst .postrm .preinst \
                         .prerm .README.Debian .reportbug .shlibs; \
                do sed -e "s/@@VERSION@@/1.0.7185/g" -e "s/@@NV_LEGACY@@/-legacy/g" \
                        -e "s:@dirname@:nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1:"  -e "s/@@NV_ALT@@/legacy/g" \
                        < debian/nvidia-glx$i.in > debian/nvidia-glx-legacy$i; \
                done; \
        fi;
sed -e "s/@@KVERSION@@/$i/g;" debian/linux-restricted-modules.postinst \
                        > debian/linux-restricted-modules-2.6.20-16-386.postinst; \
                sed -e "s/@@KVERSION@@/$i/g;" debian/linux-restricted-modules.postrm \
                        > debian/linux-restricted-modules-2.6.20-16-386.postrm;
touch unpack-stamp
dh_testdir
touch build-stamp
touch unpack-avm-stamp
dh_testdir
touch build-avm-stamp
dh_testdir
#if [ "1.0.100.14.11" = "9639" ]; then \
                #sh -e nvidia/nvidia_supported \
                #debian/build/2.6.20-16-386/nv/nv-kernel.o nvidia \
                #> debian/build/2.6.20-16-386/nv/modules.alias.override; \
        #fi
#if [ "1.0.100.14.11" = "100.14.11" ]; then \
                #sh -e nvidia/nvidia_supported \
                #debian/build/2.6.20-16-386/nv-new/nv-kernel.o nvidia_new \
                #> debian/build/2.6.20-16-386/nv/modules.alias.override; \
#fi
#if [ "1.0.100.14.11" = "7185" ]; then \
                #sh -e nvidia/nvidia_supported \
                #debian/build/2.6.20-16-386/nv-legacy/nv-kernel.o nvidia_legacy \
                #> debian/build/2.6.20-16-386/nv/modules.alias.override; \
        #fi
touch modalias-patterns-stamp
echo '# THIS FILE IS AUTO-GENERATED FROM control.stub.in' > debian/control.stub
if [ "1.0.100.14.11" = "1.0.9639" ]; then \
                sed -e 's/@@NV_VERSION@@/1.0.9639/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                sed -e 's/@@NV_NEW_VERSION@@/1.0.100.14.11/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                sed -e 's/@@NV_LEGACY_VERSION@@/1.0.7185/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
echo '# THIS FILE IS AUTO-GENERATED FROM kernel-versions.in' > debian/d-i/kernel-versions;
sed -e 's/@@ABIVER@@/2.6.20/g' \
                debian/d-i/kernel-versions.in >> debian/d-i/kernel-versions
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware
cp -a debian/d-i/modules/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules/
cp: cannot stat `debian/d-i/modules/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/firmware/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware/
cp: cannot stat `debian/d-i/firmware/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/package-list debian/d-i/kernel-versions /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/
ln -s .. /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/debian
(cd /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386 && kernel-wedge gen-control) > debian/control
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
 debian/rules binary
dh_testdir
dh_installchangelogs -i
dh_installchangelogs: I have no package to build
dh_fixperms -i
dh_fixperms: I have no package to build
dh_compress -i
dh_compress: I have no package to build
dh_installdeb -i
dh_installdeb: I have no package to build
dh_gencontrol -i
dh_gencontrol: I have no package to build
dh_md5sums -i
dh_md5sums: I have no package to build
dh_builddeb -i
dh_builddeb: I have no package to build
echo '# THIS FILE IS AUTO-GENERATED FROM control.stub.in' > debian/control.stub
if [ "1.0.100.14.11" = "1.0.9639" ]; then \
                sed -e 's/@@NV_VERSION@@/1.0.9639/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                sed -e 's/@@NV_NEW_VERSION@@/1.0.100.14.11/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                sed -e 's/@@NV_LEGACY_VERSION@@/1.0.7185/g' \
                        -e 's/@@KVERSION@@/2.6.20/g' \
                        -e 's/@@ABIVER@@/2.6.20/g' \
                        debian/control.stub.in >> debian/control.stub; \
        fi;
echo '# THIS FILE IS AUTO-GENERATED FROM kernel-versions.in' > debian/d-i/kernel-versions;
sed -e 's/@@ABIVER@@/2.6.20/g' \
                debian/d-i/kernel-versions.in >> debian/d-i/kernel-versions
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware
cp -a debian/d-i/modules/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/modules/
cp: cannot stat `debian/d-i/modules/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/firmware/i386 /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/firmware/
cp: cannot stat `debian/d-i/firmware/i386': No such file or directory
make: [debian/control] Error 1 (ignored)
cp -a debian/d-i/package-list debian/d-i/kernel-versions /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/
ln -s .. /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386/debian
(cd /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386 && kernel-wedge gen-control) > debian/control
rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/d-i-i386
dh_testdir
dh_testroot
perl -p \
                        -e 's{#BASE_VERSION#}{1.0}g;' \
                        -e 's{#RELEASE#}{9639}g;' \
                        -e 's{#VERSION#}{1.0.9639}g;' \
                        -e 's{#UPSTREAMVERSION#}{1.0-9639}g;' \
                        -e 's{#URL#}{http://download.nvidia.com/XFree86/Linux-x86/1.0-9639/NVIDIA-Linux-x86-1.0-9639-pkg1.run}g' \
                        < /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/$f \
                        > /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/debian/$f ; \
                        chmod 0644 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/debian/$f ; \
                done    ; \
                cp -al nvidia/NVIDIA-Linux-x86-1.0-9639-pkg1/usr/src/nv /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel || true; \
                rm -f /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/nv/Makefile; \
                chmod 755 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/debian/rules; \
                chown -R root:src /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules; \
                rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-kernel/nv/precompiled; \
                tar -zcvf /usr/share/envy/linux-restricted-modules-2.6.20/nvidia-kernel-source.tar.gz -C /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp modules; \
                rm -rf debian/temp; \
        fi
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian; \
                mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/nv; \
                cp -r /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/* /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian; \
                set +e && for f in `ls /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary` ; do \
                        perl -p \
                        -e 's{#BASE_VERSION#}{1.0}g;' \
                        -e 's{#RELEASE#}{7185}g;' \
                        -e 's{#VERSION#}{1.0.7185}g;' \
                        -e 's{#UPSTREAMVERSION#}{1.0-7185}g;' \
                        -e 's{#URL#}{http://download.nvidia.com/XFree86/Linux-x86/1.0-7185/NVIDIA-Linux-x86-1.0-7185-pkg1.run}g' \
                        < /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/$f \
                        > /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian/$f ; \
                        chmod 0644 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian/$f ; \
                done; \
                cp -al nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/src/nv /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel || true; \
                rm -f /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/nv/Makefile; \
                chmod 755 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/debian/rules; \
                chown -R root:src /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules; \
                rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-legacy-kernel/nv/precompiled; \
                tar -zcvf /usr/share/envy/linux-restricted-modules-2.6.20/nvidia-legacy-kernel-source.tar.gz -C /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp modules; \
                rm -rf debian/temp; \
        fi
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian; \
                mkdir -p /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/nv; \
                cp -r /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/* /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian; \
                set +e && for f in `ls /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary` ; do \
                        perl -p \
                        -e 's{#BASE_VERSION#}{1.0}g;' \
                        -e 's{#RELEASE#}{100.14.11}g;' \
                        -e 's{#VERSION#}{1.0.100.14.11}g;' \
                        -e 's{#UPSTREAMVERSION#}{1.0-100.14.11}g;' \
                        -e 's{#URL#}{http://download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run}g' \
                        < /usr/share/envy/linux-restricted-modules-2.6.20/nvidia/debian.binary/$f \
                        > /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian/$f ; \
                        chmod 0644 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian/$f ; \
                done; \
                cp -al nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel || true; \
                rm -f /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/nv/Makefile; \
                chmod 755 /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/debian/rules; \
                chown -R root:src /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules; \
                rm -rf /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp/modules/nvidia-new-kernel/nv/precompiled; \
                tar -zcvf /usr/share/envy/linux-restricted-modules-2.6.20/nvidia-new-kernel-source.tar.gz -C /usr/share/envy/linux-restricted-modules-2.6.20/debian/temp modules; \
                rm -rf debian/temp; \
        fi
modules/
modules/nvidia-new-kernel/
modules/nvidia-new-kernel/debian/
modules/nvidia-new-kernel/debian/README.Debian
modules/nvidia-new-kernel/debian/changelog
modules/nvidia-new-kernel/debian/control.template
modules/nvidia-new-kernel/debian/copyright
modules/nvidia-new-kernel/debian/dirs.template
modules/nvidia-new-kernel/debian/override.template
modules/nvidia-new-kernel/debian/postinst
modules/nvidia-new-kernel/debian/postrm
modules/nvidia-new-kernel/debian/rules
modules/nvidia-new-kernel/nv/
modules/nvidia-new-kernel/nv/README
modules/nvidia-new-kernel/nv/nv.c
modules/nvidia-new-kernel/nv/nv-vm.c
modules/nvidia-new-kernel/nv/os-agp.c
modules/nvidia-new-kernel/nv/os-interface.c
modules/nvidia-new-kernel/nv/os-registry.c
modules/nvidia-new-kernel/nv/nv-i2c.c
modules/nvidia-new-kernel/nv/nvacpi.c
modules/nvidia-new-kernel/nv/os-agp.h
modules/nvidia-new-kernel/nv/os-interface.h
modules/nvidia-new-kernel/nv/nv-linux.h
modules/nvidia-new-kernel/nv/nv-misc.h
modules/nvidia-new-kernel/nv/nv-memdbg.h
modules/nvidia-new-kernel/nv/nv-vm.h
modules/nvidia-new-kernel/nv/nv.h
modules/nvidia-new-kernel/nv/rmretval.h
modules/nvidia-new-kernel/nv/cpuopsys.h
modules/nvidia-new-kernel/nv/nvtypes.h
modules/nvidia-new-kernel/nv/nvreadme.h
modules/nvidia-new-kernel/nv/pat.h
modules/nvidia-new-kernel/nv/gcc-version-check.c
modules/nvidia-new-kernel/nv/conftest.sh
modules/nvidia-new-kernel/nv/Makefile.nvidia
modules/nvidia-new-kernel/nv/Makefile.kbuild
modules/nvidia-new-kernel/nv/makefile
modules/nvidia-new-kernel/nv/nv-kernel.o
touch build-kernel-stamp
dh_testdir
dh_clean -k
dh_installdirs
if [ "i386" = "amd64" ]; then                                   \
                                install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32            \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/lib32;          \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libGL.so.100.14.11           \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32;              \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libGLcore.so.100.14.11               \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32;              \
                                if [ -e nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libnvidia-cfg.so.100.14.11 ]; then   \
                                        install -m 0644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libnvidia-cfg.so.100.14.11 \
                                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32;      \
                                fi;                                                                  \
                                sed "s/__GENERATED_BY__/Ubuntu nvidia--newgraphics-drivers/"    \
                                        nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libGL.la |  \
                                        sed "s/__LIBGL_PATH__/\/usr\/lib32/" >                       \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new-dev/usr/lib32/libGL.la; \
                        fi;                                                                          \
                        install nvidia/nvidia-glx-config                                             \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/sbin;                       \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/libnvidia-tls.so.100.14.11                             \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/;                       \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib/tls/libnvidia-tls.so.100.14.11                 \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/tls/;                   \
                        if [ "i386" = "amd64" ]; then                                   \
                                install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/libnvidia-tls.so.100.14.11           \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32/;             \
                                install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32/tls;       \
                                install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/lib32/tls/libnvidia-tls.so.100.14.11               \
                                         /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib32/tls/;                \
                        fi;                                                                          \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/X11R6/lib/modules/extensions/libglx.so.100.14.11   \
                                 /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/xorg/modules/;         \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.100.14.11       \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/xorg/modules/;  \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/tls_test              \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/nvidia;                 \
                        install nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/tls_test_dso.so       \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/lib/nvidia;                 \
                        install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/lintian/overrides; \
                        install -m 0644 debian/nvidia-glx-new.override                          \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/lintian/overrides/nvidia-glx-new; \
                        install -m 755 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/nvidia-bug-report.sh                            \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/bin/;                       \
                        if [ -e nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/share/man/man1/nvidia-settings.1.gz ]; then                \
                                install -m 755 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/nvidia-settings                 \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/bin/;               \
                                install -m 644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/share/man/man1/nvidia-settings.1.gz \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/man/man1/;    \
                        fi;                                                                          \
                        if [ -e nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/share/man/man1/nvidia-xconfig.1.gz ]; then         \
                                install -m 755 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/bin/nvidia-xconfig                  \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/bin/;               \
                                install -m 644 nvidia/NVIDIA-Linux-x86-100.14.11-pkg1/usr/share/man/man1/nvidia-xconfig.1.gz  \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/man/man1/;    \
                        fi;                                                                          \
                        install /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new.reportbug                       \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-new/usr/share/bug/nvidia-glx-new/script; \
                fi;
L_PATH__/\/usr\/lib/" >         \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy-dev/usr/lib/libGL.la;                \
                        if [ "i386" = "amd64" ]; then                                   \
                                install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32         \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy-dev/usr/lib32;               \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libGL.so.1.0.7185             \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32;           \
                                install -m 0644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libGLcore.so.1.0.7185         \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32;           \
                                if [ -e nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libnvidia-cfg.so.1.0.7185 ]; then     \
                                        install -m 0644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libnvidia-cfg.so.1.0.7185 \
                                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32;   \
                                fi;                                                                  \
                                sed "s/__GENERATED_BY__/Ubuntu nvidia--legacygraphics-drivers/" \
                                        nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libGL.la |   \
                                        sed "s/__LIBGL_PATH__/\/usr\/lib32/" >                       \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy-dev/usr/lib32/libGL.la;      \
                        fi;                                                                          \
                        install nvidia/nvidia-glx-config                                             \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/sbin;                    \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib/libnvidia-tls.so.1.0.7185                               \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/;                    \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib/tls/libnvidia-tls.so.1.0.7185                   \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/tls/;                        \
                        if [ "i386" = "amd64" ]; then                                   \
                                install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/libnvidia-tls.so.1.0.7185             \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32/;          \
                                install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32/tls;    \
                                install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/lib32/tls/libnvidia-tls.so.1.0.7185         \
                                         /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib32/tls/;             \
                        fi;                                                                          \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/X11R6/lib/modules/extensions/libglx.so.1.0.7185     \
                                 /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/xorg/modules/;              \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/tls_test               \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/nvidia;                      \
                        install nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/tls_test_dso.so        \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/lib/nvidia;                      \
                        install -d /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/lintian/overrides;      \
                        install -m 0644 debian/nvidia-glx-legacy.override                            \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/lintian/overrides/nvidia-glx-legacy; \
                        install -m 755 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/nvidia-bug-report.sh                             \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/bin/;                    \
                        if [ -e nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/share/man/man1/nvidia-settings.1.gz ]; then         \
                                install -m 755 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/nvidia-settings                  \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/bin/;            \
                                install -m 644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/share/man/man1/nvidia-settings.1.gz  \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/man/man1/; \
                        fi;                                                                          \
                        if [ -e nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/share/man/man1/nvidia-xconfig.1.gz ]; then          \
                                install -m 755 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/bin/nvidia-xconfig                   \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/bin/;            \
                                install -m 644 nvidia/NVIDIA-Linux-x86-1.0-7185-pkg1/usr/share/man/man1/nvidia-xconfig.1.gz   \
                                        /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/man/man1/; \
                        fi;                                                                          \
                        install /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy.reportbug                    \
                                /usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx-legacy/usr/share/bug/nvidia-glx-legacy/script; \
                fi;
#install
dh_testdir
dh_installchangelogs -s
dh_installdocs -s
dh_installexamples -s
dh_installman -s
dh_installinit -s
dh_link -s
# FIXME: Remove this when -legacy supports this library:
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                rm -f debian/nvidia-glx-legacy/usr/lib/libnvidia-cfg.so.1; \
                rm -f debian/nvidia-glx-legacy/usr/lib32/libnvidia-cfg.so.1; \
        fi;
dh_strip -s -X1.0.9639 -X1.0.7185 -Xtls_test
dh_compress -X.h -s
dh_fixperms -s
dh_installdeb -s
dh_shlibdeps -X'*tls*' -X'*lib32*' -X'*lib64*' -s \
                -l/usr/share/envy/linux-restricted-modules-2.6.20/debian/nvidia-glx/usr/lib:/usr/share/envy/linux-restricted-modules-2.6.20/debian/xorg-driver-fglrx/usr/lib
# this is a dirty hack, but we don't want -glx-legacy to depend on -glx
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
        sed -i -e 's/, nvidia-glx//' debian/nvidia-glx-legacy.substvars ;\
        fi;
dh_gencontrol -s
dpkg-gencontrol: warning: unknown substitution variable ${nvidia:NewVersion}
dpkg-gencontrol: warning: unknown substitution variable ${nvidia:NewVersion}
dpkg-gencontrol: warning: unknown substitution variable ${nvidia:NewVersion}
dpkg-gencontrol: warning: unknown substitution variable ${nvidia:NewVersion}
# fglrx, nVidia and ACM build with different version numbers
if [ "1.0.100.14.11" = "1.0.9639" ]; then \
                dh_gencontrol -v -pnvidia-glx -- -v1:1.0.9639+2.6.20-16 -Vnvidia:Version=1.0.9639; \
                dh_gencontrol -v -pnvidia-glx-dev -- -v1:1.0.9639+2.6.20-16 -Vnvidia:Version=1.0.9639; \
                dh_gencontrol -v -pnvidia-kernel-source -- -v1:1.0.9639+2.6.20-16 -Vnvidia:Version=1.0.9639; \
        fi;
if [ "1.0.100.14.11" = "1.0.100.14.11" ]; then \
                dh_gencontrol -v -pnvidia-glx-new -- -v1:100.14.11+2.6.20-16 -Vnvidia:NewVersion=100.14.11; \
                dh_gencontrol -v -pnvidia-glx-new-dev -- -v1:100.14.11+2.6.20-16 -Vnvidia:NewVersion=100.14.11; \
                dh_gencontrol -v -pnvidia-new-kernel-source -- -v1:100.14.11+2.6.20-16 -Vnvidia:NewVersion=100.14.11; \
        fi;
dpkg-gencontrol -pnvidia-glx-new -ldebian/changelog -isp -Tdebian/nvidia-glx-new.substvars -Pdebian/nvidia-glx-new -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
chmod 644 debian/nvidia-glx-new/DEBIAN/control
        chown 0:0 debian/nvidia-glx-new/DEBIAN/control
dpkg-gencontrol -pnvidia-glx-new-dev -ldebian/changelog -isp -Tdebian/nvidia-glx-new-dev.substvars -Pdebian/nvidia-glx-new-dev -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
chmod 644 debian/nvidia-glx-new-dev/DEBIAN/control
        chown 0:0 debian/nvidia-glx-new-dev/DEBIAN/control
dpkg-gencontrol -pnvidia-new-kernel-source -ldebian/changelog -isp -Tdebian/nvidia-new-kernel-source.substvars -Pdebian/nvidia-new-kernel-source -v1:100.14.11\+2.6.20-16 -Vnvidia:NewVersion=100.14.11
chmod 644 debian/nvidia-new-kernel-source/DEBIAN/control
        chown 0:0 debian/nvidia-new-kernel-source/DEBIAN/control
if [ "1.0.100.14.11" = "1.0.7185" ]; then \
                dh_gencontrol -v -pnvidia-glx-legacy -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
                dh_gencontrol -v -pnvidia-glx-legacy-dev -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
                dh_gencontrol -v -pnvidia-legacy-kernel-source -- -v1:1.0.7185+2.6.20-16 -Vnvidia:LegacyVersion=1.0.7185; \
        fi;
dh_md5sums -s
dh_builddeb -s
dpkg-deb: building package `nvidia-glx-new' in `../nvidia-glx-new_100.14.11+2.6.20-16_i386.deb'.
dpkg-deb: building package `nvidia-glx-new-dev' in `../nvidia-glx-new-dev_100.14.11+2.6.20-16_i386.deb'.
dpkg-deb: building package `nvidia-new-kernel-source' in `../nvidia-new-kernel-source_100.14.11+2.6.20-16_i386.deb'.
dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  librpcsecgss2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ENVY: The following packages are not installed:
nvidia-kernel-common

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  librpcsecgss2
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-kernel-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5176B of archives.
After unpacking 115kB of additional disk space will be used.
Selecting previously deselected package nvidia-kernel-common.
(Reading database ... 155280 files and directories currently installed.)
Unpacking nvidia-kernel-common (from .../nvidia-kernel-common_20051028+1ubuntu7_all.deb) ...
Setting up nvidia-kernel-common (20051028+1ubuntu7) ...

Selecting previously deselected package nvidia-new-kernel-source.
(Reading database ... 155291 files and directories currently installed.)
Unpacking nvidia-new-kernel-source (from nvidia-new-kernel-source_100.14.11+2.6.20-16_i386.deb) ...
Setting up nvidia-new-kernel-source (100.14.11+2.6.20-16) ...
modules/
modules/nvidia-new-kernel/
modules/nvidia-new-kernel/debian/
modules/nvidia-new-kernel/debian/README.Debian
modules/nvidia-new-kernel/debian/changelog
modules/nvidia-new-kernel/debian/control.template
modules/nvidia-new-kernel/debian/copyright
modules/nvidia-new-kernel/debian/dirs.template
modules/nvidia-new-kernel/debian/override.template
modules/nvidia-new-kernel/debian/postinst
modules/nvidia-new-kernel/debian/postrm
modules/nvidia-new-kernel/debian/rules
modules/nvidia-new-kernel/nv/
modules/nvidia-new-kernel/nv/README
modules/nvidia-new-kernel/nv/nv.c
modules/nvidia-new-kernel/nv/nv-vm.c
modules/nvidia-new-kernel/nv/os-agp.c
modules/nvidia-new-kernel/nv/os-interface.c
modules/nvidia-new-kernel/nv/os-registry.c
modules/nvidia-new-kernel/nv/nv-i2c.c
modules/nvidia-new-kernel/nv/nvacpi.c
modules/nvidia-new-kernel/nv/os-agp.h
modules/nvidia-new-kernel/nv/os-interface.h
modules/nvidia-new-kernel/nv/nv-linux.h
modules/nvidia-new-kernel/nv/nv-misc.h
modules/nvidia-new-kernel/nv/nv-memdbg.h
modules/nvidia-new-kernel/nv/nv-vm.h
modules/nvidia-new-kernel/nv/nv.h
modules/nvidia-new-kernel/nv/rmretval.h
modules/nvidia-new-kernel/nv/cpuopsys.h
modules/nvidia-new-kernel/nv/nvtypes.h
modules/nvidia-new-kernel/nv/nvreadme.h
modules/nvidia-new-kernel/nv/pat.h
modules/nvidia-new-kernel/nv/gcc-version-check.c
modules/nvidia-new-kernel/nv/conftest.sh
modules/nvidia-new-kernel/nv/Makefile.nvidia
modules/nvidia-new-kernel/nv/Makefile.kbuild
modules/nvidia-new-kernel/nv/makefile
modules/nvidia-new-kernel/nv/nv-kernel.o
Getting source for kernel version: 2.6.20-16-386
Kernel headers available in /lib/modules/2.6.20-16-386/build
apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  librpcsecgss2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;Updating cached package data&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
            &#9474; at76c503a-source                                                        &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;  &#9474;                               100%                                &#9474;  &#9474;  
            &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  
            &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
Updated infos about 85 packages
Extracting the package tarball, /usr/src/nvidia-new-kernel-source.tar.gz, please wait...
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;Building nvidia-new-kernel-source, step 1, please wait...&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
            &#9474; Build starting...                                                       &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;  &#9474;                               100%                                &#9474;  &#9474;  
            &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  
            &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;Building nvidia-new-kernel-source, step 2, please wait...&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
            &#9474; rm /usr/src/modules/nvidia-new-kernel/nv/cc-sanity-check                &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;                                                                         &#9474;  
            &#9474;  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  &#9474;
&#9474;  &#9474;                               100%                                &#9474;  &#9474;  
            &#9474;  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  &#9474;  
            &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
              





Done with /usr/src/nvidia-kernel-2.6.20-16-386_100.14.11-0ubuntu3+2.6.20-16.29_i386.deb .
Selecting previously deselected package nvidia-kernel-2.6.20-16-386.
(Reading database ... 155296 files and directories currently installed.)
Unpacking nvidia-kernel-2.6.20-16-386 (from .../nvidia-kernel-2.6.20-16-386_100.14.11-0ubuntu3+2.6.20-16.29_i386.deb) ...
Setting up nvidia-kernel-2.6.20-16-386 (100.14.11-0ubuntu3+2.6.20-16.29) ...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  librpcsecgss2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package nvidia-glx-new.
(Reading database ... 155303 files and directories currently installed.)
Unpacking nvidia-glx-new (from nvidia-glx-new_100.14.11+2.6.20-16_i386.deb) ...
Setting up nvidia-glx-new (100.14.11+2.6.20-16) ...

Selecting previously deselected package nvidia-glx-new-dev.
(Reading database ... 155353 files and directories currently installed.)
Unpacking nvidia-glx-new-dev (from nvidia-glx-new-dev_100.14.11+2.6.20-16_i386.deb) ...
Setting up nvidia-glx-new-dev (100.14.11+2.6.20-16) ...
Cleaning the build system:
NOTE: The following are only warnings
The build system is now clean
ENVY: Operation Completed
```

---

### Post by dartmusic on 2007-08-10
Just got home, rebooted...to a black screen.  :confused:

---

### Post by tjl30 on 2007-08-10
Hi, Thanks for the tutorial. I tried getting my graphics card working for about 3 days and after a lot of X windows crashes it finally is working... Well sort of. I still have an issue because I would like to run the Desktop Effects but when I go to [System][Preferences][Desktop Effects] I get the following "The Composite extension is not available" and when I type glxinfo | grep "GLX version" I get the following

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Anyways I have a e-GeForce 8800 GTS, and I would like the get desktop effects working. Any help would be fantastic. Thanks.

---

### Post by dannyboy79 on 2007-08-10
do you have the glx within your module section, like this?

Section "Module"
    Load           "i2c"
    Load           "bitmap" 
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

---

### Post by tseliot on 2007-08-11
> **dartmusic said:**
> Just got home, rebooted...to a black screen.  :confused:

The log says that all went well.

Boot in Recovery mode

then type:

```
nano /etc/X11/xorg.conf
```
Set the driver to "vesa" instead of "nvidia"
CTRL+O to save
CTRL+X to exit


then we can try to diagnose the error:

Boot as usual with either the "vesa" driver or the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" (or "vesa") instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by tseliot on 2007-08-11
> **tjl30 said:**
> Anyways I have a e-GeForce 8800 GTS, and I would like the get desktop effects working. Any help would be fantastic. Thanks.
How did you install the driver?

---

### Post by dartmusic on 2007-08-11
I did as you said, but there were no errors (that I can see), just a blank screen, so I rebooted into recovery mode and continued from there.  

This is the Xorg.0.log that was there when I booted into recovery mode.  The time looks right, so it must the the one you're looking for.  

Thanks!


```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux rickstone-desktop 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 11 10:23:54 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Nvidia GeForce 6200"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2578 card 1043,80f6 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2579 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1043,80a6 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1043,80a6 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 1043,80a6 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1043,80a6 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1043,80f3 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0221 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:03:0: chip 1106,3044 card 1043,808a rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:04:0: chip 105a,3373 card 1043,80f5 rev 02 class 01,04,00 hdr 00
(II) PCI: 02:05:0: chip 10b7,1700 card 1043,80eb rev 12 class 02,00,00 hdr 00
(II) PCI: 02:0d:0: chip 4444,0016 card 0070,b7f3 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf3d00000 - 0xf7dfffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc3c00000 - 0xe3bfffff (0x20000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf7e00000 - 0xf7efffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe3c00000 - 0xebbfffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV44A [GeForce 6200] rev 161, Mem @ 0xf6000000/24, 0xd0000000/28, 0xf5000000/24, BIOS @ 0xf7de0000/17
(--) PCI: (2:13:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xe4000000/26
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xec000000 from 0xefffffff to 0xebffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[1] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[2] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[3] -1	0	0xf7eff800 - 0xf7efffff (0x800) MX[B]
	[4] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[5] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[6] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[7] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[8] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[9] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[11] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d880 - 0x0000d8ff (0x80) IX[B]
	[16] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[19] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[22] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[23] -1	0	0x0000efa8 - 0x0000efab (0x4) IX[B]
	[24] -1	0	0x0000efa0 - 0x0000efa7 (0x8) IX[B]
	[25] -1	0	0x0000efac - 0x0000efaf (0x4) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efe7 (0x8) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[33] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[34] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[35] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[1] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[2] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[3] -1	0	0xf7eff800 - 0xf7efffff (0x800) MX[B]
	[4] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[5] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[6] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[7] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[8] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[9] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[11] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d880 - 0x0000d8ff (0x80) IX[B]
	[16] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[19] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[21] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[22] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[23] -1	0	0x0000efa8 - 0x0000efab (0x4) IX[B]
	[24] -1	0	0x0000efa0 - 0x0000efa7 (0x8) IX[B]
	[25] -1	0	0x0000efac - 0x0000efaf (0x4) IX[B]
	[26] -1	0	0x0000efe0 - 0x0000efe7 (0x8) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[33] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[34] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[35] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[5] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[6] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[7] -1	0	0xf7eff800 - 0xf7efffff (0x800) MX[B]
	[8] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[9] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[10] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[11] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[12] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[13] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[15] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000d880 - 0x0000d8ff (0x80) IX[B]
	[22] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[25] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[29] -1	0	0x0000efa8 - 0x0000efab (0x4) IX[B]
	[30] -1	0	0x0000efa0 - 0x0000efa7 (0x8) IX[B]
	[31] -1	0	0x0000efac - 0x0000efaf (0x4) IX[B]
	[32] -1	0	0x0000efe0 - 0x0000efe7 (0x8) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[39] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[40] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[41] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) NVIDIA(0): Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[5] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[6] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[7] -1	0	0xf7eff800 - 0xf7efffff (0x800) MX[B]
	[8] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[9] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[10] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[11] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[12] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[13] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[15] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000d880 - 0x0000d8ff (0x80) IX[B]
	[22] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[25] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[29] -1	0	0x0000efa8 - 0x0000efab (0x4) IX[B]
	[30] -1	0	0x0000efa0 - 0x0000efa7 (0x8) IX[B]
	[31] -1	0	0x0000efac - 0x0000efaf (0x4) IX[B]
	[32] -1	0	0x0000efe0 - 0x0000efe7 (0x8) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[39] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[40] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[41] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[5] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[6] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[7] -1	0	0xf7eff800 - 0xf7efffff (0x800) MX[B]
	[8] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[9] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[10] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[11] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[12] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[13] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[15] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[24] -1	0	0x0000d880 - 0x0000d8ff (0x80) IX[B]
	[25] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[26] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[28] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[30] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[31] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[32] -1	0	0x0000efa8 - 0x0000efab (0x4) IX[B]
	[33] -1	0	0x0000efa0 - 0x0000efa7 (0x8) IX[B]
	[34] -1	0	0x0000efac - 0x0000efaf (0x4) IX[B]
	[35] -1	0	0x0000efe0 - 0x0000efe7 (0x8) IX[B]
	[36] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[41] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[42] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[43] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[44] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6200 (NV44) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(II) NVIDIA(0): GPU Architecture: 0x40
(II) NVIDIA(0): GPU Implementation: 0x4a
(II) NVIDIA(0): GPU Revision: 0xa1
(II) NVIDIA(0): GPU RAM Type: DDR2
(--) NVIDIA(0): VideoBIOS: 05.44.a2.06.01
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, CRT-1, DFP-0, TV-0
(II) NVIDIA(0): Bus detected as AGP
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): VPES : 3
(II) NVIDIA(0): SPS  : 8
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing constraints for  : GeForce 6200
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0): 
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0): 
(--) NVIDIA(0): Connected display device(s) on GeForce 6200 at PCI:1:0:0:
(--) NVIDIA(0):     SYN 226-S11 (DFP-0)
(--) NVIDIA(0): SYN 226-S11 (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): SYN 226-S11 (DFP-0): Internal Single Link TMDS
(--) NVIDIA(0): SYN 226-S11 (DFP-0): Native FlatPanel Scaling is supported
(--) NVIDIA(0): SYN 226-S11 (DFP-0): DFP modes are not limited to 60 Hz
(--) NVIDIA(0):     refresh rate
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for SYN 226-S11 (DFP-0) ---
(--) NVIDIA(0): EDID Version                 : 1.3
(--) NVIDIA(0): Manufacturer                 : SYN
(--) NVIDIA(0): Monitor Name                 : SYN 226-S11
(--) NVIDIA(0): Product ID                   : 39
(--) NVIDIA(0): 32-bit Serial Number         : 585
(--) NVIDIA(0): Serial Number String         : 
(--) NVIDIA(0): Manufacture Date             : 2006, week 43
(--) NVIDIA(0): DPMS Capabilities            :
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : Yes
(--) NVIDIA(0): Maximum Image Size           : 570mm x 340mm
(--) NVIDIA(0): Valid HSync Range            : 15.0 kHz - 58.0 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 56 Hz - 75 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 80.0 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):   640  x 480  @ 75 Hz
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   800  x 600  @ 75 Hz
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0):   1024 x 768  @ 75 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   1280 x 768  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 68.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1328
(--) NVIDIA(0):     HSyncEnd, HTotal : 1360, 1440
(--) NVIDIA(0):     VRes, VSyncStart : 768, 775
(--) NVIDIA(0):     VSyncEnd, VTotal : 778, 790
(--) NVIDIA(0):     H/V Polarity     : +/-
(--) NVIDIA(0):   1920 x 1080 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(--) NVIDIA(0):     VRes, VSyncStart : 540, 542
(--) NVIDIA(0):     VSyncEnd, VTotal : 547, 563
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):   1280 x 720  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1390
(--) NVIDIA(0):     HSyncEnd, HTotal : 1430, 1650
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 736
(--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):   1440 x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1478
(--) NVIDIA(0):     HSyncEnd, HTotal : 1602, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 240, 244
(--) NVIDIA(0):     VSyncEnd, VTotal : 247, 262
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0): 
(--) NVIDIA(0): CEA-861B Timings:
(--) NVIDIA(0):   1920 x 1080 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.18 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(--) NVIDIA(0):     VRes, VSyncStart : 540, 542
(--) NVIDIA(0):     VSyncEnd, VTotal : 547, 562
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 5
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 736
(--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 2
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 736
(--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 3
(--) NVIDIA(0):   1280 x 720  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.18 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1390
(--) NVIDIA(0):     HSyncEnd, HTotal : 1430, 1650
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 4
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1478
(--) NVIDIA(0):     HSyncEnd, HTotal : 1602, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 240, 244
(--) NVIDIA(0):     VSyncEnd, VTotal : 247, 262
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 6
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1478
(--) NVIDIA(0):     HSyncEnd, HTotal : 1602, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 240, 244
(--) NVIDIA(0):     VSyncEnd, VTotal : 247, 262
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 7
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for SYN 226-S11 (DFP-0) ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Frequency information for SYN 226-S11 (DFP-0):
(II) NVIDIA(0):   HorizSync   : 15.000-58.000 kHz
(II) NVIDIA(0):   VertRefresh : 56.000-75.000 Hz
(II) NVIDIA(0):     (HorizSync from EDID)
(II) NVIDIA(0):     (VertRefresh from EDID)
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for SYN 226-S11 (DFP-0):
(II) NVIDIA(0):   1280 x 768 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 68.25 MHz
(II) NVIDIA(0):     HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):     HSyncEnd, HTotal : 1360, 1440
(II) NVIDIA(0):     VRes, VSyncStart :  768,  775
(II) NVIDIA(0):     VSyncEnd, VTotal :  778,  790
(II) NVIDIA(0):     H/V Polarity     : +/-
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for SYN 226-S11 (DFP-0) ---
(II) NVIDIA(0): "nvidia-auto-select" : 1280 x  768 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x768"           : 1280 x  768 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x768_60"        : 1280 x  768 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x720"           : 1280 x  720 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x720_60"        : 1280 x  720 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x720_60_0"      : 1280 x  720 @  59.9 Hz  (from: EDID)
(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "832x624"            :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "832x624_75"         :  832 x  624 @  74.5 Hz  (from: X Server)
(II) NVIDIA(0): "800x600"            :  800 x  600 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_75"         :  800 x  600 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "720x480"            :  720 x  480 @  59.9 Hz  (from: EDID)
(II) NVIDIA(0): "720x480_60"         :  720 x  480 @  59.9 Hz  (from: EDID)
(II) NVIDIA(0): "720x450"            :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450d60"         :  720 x  450 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  60.0 Hz  (from: VESA, EDID)
(II) NVIDIA(0): "640x400"            :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x400d60"         :  640 x  400 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384"            :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x384d60"         :  640 x  384 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for SYN 226-S11 (DFP-0): ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "1280x768"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "1280x768":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1280, 768]
(II) NVIDIA(0):     SYN 226-S11 (DFP-0): "1280x768"
(II) NVIDIA(0):         Size          : 1280 x 768
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1280 x 768
(II) NVIDIA(0):         Position      : [0, 0, 1280, 768]
(II) NVIDIA(0): MetaMode "1024x768":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1024, 768]
(II) NVIDIA(0):     SYN 226-S11 (DFP-0): "1024x768"
(II) NVIDIA(0):         Size          : 1024 x 768
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1024 x 768
(II) NVIDIA(0):         Position      : [0, 0, 1024, 768]
(II) NVIDIA(0): MetaMode "800x600":
(II) NVIDIA(0):     Bounding Box: [0, 0, 800, 600]
(II) NVIDIA(0):     SYN 226-S11 (DFP-0): "800x600"
(II) NVIDIA(0):         Size          : 800 x 600
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 800 x 600
(II) NVIDIA(0):         Position      : [0, 0, 800, 600]
(II) NVIDIA(0): MetaMode "640x480":
(II) NVIDIA(0):     Bounding Box: [0, 0, 640, 480]
(II) NVIDIA(0):     SYN 226-S11 (DFP-0): "640x480"
(II) NVIDIA(0):         Size          : 640 x 480
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 640 x 480
(II) NVIDIA(0):         Position      : [0, 0, 640, 480]
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 768
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "1280x720"      : 1280 x  720 @  60.0 Hz 
(II) NVIDIA(0): "1280x720_60_0" : 1280 x  720 @  59.9 Hz 
(II) NVIDIA(0): "1024x768_60"   : 1024 x  768 @  60.0 Hz 
(II) NVIDIA(0): "832x624"       :  832 x  624 @  74.5 Hz 
(II) NVIDIA(0): "800x600_72"    :  800 x  600 @  72.2 Hz 
(II) NVIDIA(0): "800x600_60"    :  800 x  600 @  60.3 Hz 
(II) NVIDIA(0): "800x600_56"    :  800 x  600 @  56.2 Hz 
(II) NVIDIA(0): "720x480"       :  720 x  480 @  59.9 Hz 
(II) NVIDIA(0): "720x450"       :  720 x  450 @  60.2 Hz DoubleScan 
(II) NVIDIA(0): "640x480_73"    :  640 x  480 @  72.8 Hz 
(II) NVIDIA(0): "640x480_60"    :  640 x  480 @  60.0 Hz 
(II) NVIDIA(0): "640x400"       :  640 x  400 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x384"       :  640 x  384 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384"       :  512 x  384 @  70.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384d60"    :  512 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "416x312"       :  416 x  312 @  74.7 Hz DoubleScan 
(II) NVIDIA(0): "400x300"       :  400 x  300 @  75.1 Hz DoubleScan 
(II) NVIDIA(0): "400x300d72"    :  400 x  300 @  72.2 Hz DoubleScan 
(II) NVIDIA(0): "400x300d60"    :  400 x  300 @  60.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d56"    :  400 x  300 @  56.3 Hz DoubleScan 
(II) NVIDIA(0): "320x240"       :  320 x  240 @  75.0 Hz DoubleScan 
(II) NVIDIA(0): "320x240d73"    :  320 x  240 @  72.8 Hz DoubleScan 
(II) NVIDIA(0): "320x240d60"    :  320 x  240 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): 
(II) NVIDIA(0): Computing DPI using physical size from SYN 226-S11 (DFP-0)'s
(II) NVIDIA(0):     EDID and first mode to be programmed on SYN 226-S11
(II) NVIDIA(0):     (DFP-0):
(II) NVIDIA(0):   width  : 1280 pixels  570  mm (DPI: 57)
(II) NVIDIA(0):   height : 768  pixels  340  mm (DPI: 57)
(--) NVIDIA(0): DPI set to (57, 57); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf7ef8000 - 0xf7efbfff (0x4000) MX[B]
	[8] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[9] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[10] -1	0	0xf7eff800 - 0xf7efffff (0x800) MX[B]
	[11] -1	0	0xf7fff400 - 0xf7fff4ff (0x100) MX[B]
	[12] -1	0	0xf7fff800 - 0xf7fff9ff (0x200) MX[B]
	[13] -1	0	0x50000000 - 0x500003ff (0x400) MX[B]
	[14] -1	0	0xf7fffc00 - 0xf7ffffff (0x400) MX[B]
	[15] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[16] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xf7de0000 - 0xf7dfffff (0x20000) MX[B](B)
	[18] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xf6000000 - 0xf6ffffff (0x1000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[27] -1	0	0x0000d880 - 0x0000d8ff (0x80) IX[B]
	[28] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[29] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[30] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[31] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[33] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[34] -1	0	0x0000ef60 - 0x0000ef6f (0x10) IX[B]
	[35] -1	0	0x0000efa8 - 0x0000efab (0x4) IX[B]
	[36] -1	0	0x0000efa0 - 0x0000efa7 (0x8) IX[B]
	[37] -1	0	0x0000efac - 0x0000efaf (0x4) IX[B]
	[38] -1	0	0x0000efe0 - 0x0000efe7 (0x8) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[43] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[44] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[45] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[46] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[47] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[48] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[49] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): Created ACPID client socket 14.
(II) NVIDIA(0): Interrupts enabled
(WW) NVIDIA(0): WAIT (0, 6, 0x8000, 0x00000500, 0x00000500)
(II) NVIDIA(0): Setting mode "1280x768"
(WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x00000500, 0x000005c4)
(WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x00000500, 0x000005c4)
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(WW) NVIDIA(0): WAIT (2, 11, 0x8000, 0x00000500, 0x00000b1c)
(WW) NVIDIA(0): WAIT (1, 11, 0x8000, 0x00000500, 0x00000b1c)

```

---

### Post by tseliot on 2007-08-11
> **dartmusic said:**
> I did as you said, but there were no errors (that I can see), just a blank screen, so I rebooted into recovery mode and continued from there.  

This is the Xorg.0.log that was there when I booted into recovery mode.  The time looks right, so it must the the one you're looking for.  

Thanks!
Try point 4 of the Problems Section of my guide (even though your problem doesn't match what's described in that part of the guide):
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION)

---

### Post by dartmusic on 2007-08-11
No dice, I'm afraid.  X crashes, complaining about "nvidia-auto-select," though I can't find any mention of that anywhere in my xorg.conf.

I can't understand why this has to be so difficult...though I really do appreciate your help.

---

### Post by Dubbayoo on 2007-08-11
I am unable to get the nvidia driver working with a Geforce FX 5500 on Feisty. Been using an ATI for 4 years now. The nv driver works fine but no 3D and text is a lil fuzzy, but that could be me.

I tried to install using Envy (automatic selection) and by just installing the pkgs then using Restricted Driver Manager. 

**Here is the X.log from a failed install. **

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug 11 14:21:05 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "PF790"
(**) |   |-->Device "nVidia Corporation NV34 [GeForce FX 5500]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2531 card 15d9,2980 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2532 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2533 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 15d9,2980 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 15d9,2980 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 15d9,2980 rev 04 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 15d9,2980 rev 04 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:1f:0: chip 8086,1360 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 03:00:0: chip 8086,1161 card 8086,1161 rev 01 class 08,00,20 hdr 80
(II) PCI: 04:01:0: chip 8086,1229 card 1014,305c rev 08 class 02,00,00 hdr 00
(II) PCI: 04:02:0: chip 1033,0035 card 1033,0035 rev 43 class 0c,03,10 hdr 80
(II) PCI: 04:02:1: chip 1033,0035 card 1033,0035 rev 43 class 0c,03,10 hdr 00
(II) PCI: 04:02:2: chip 1033,00e0 card 0e55,2928 rev 04 class 0c,03,20 hdr 00
(II) PCI: 04:03:0: chip 1000,000c card 1de1,3907 rev 01 class 01,00,00 hdr 00
(II) PCI: 04:04:0: chip 8086,1229 card 8086,100c rev 08 class 02,00,00 hdr 00
(II) PCI: 04:07:0: chip 1102,0004 card 1102,0053 rev 03 class 04,01,00 hdr 80
(II) PCI: 04:07:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 04:07:2: chip 1102,4001 card 1102,0010 rev 00 class 0c,00,10 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
	[4] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[5] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[6] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf6000000 - 0xf7ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x70000000 - 0x702fffff (0x300000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (2:31:0), (2,3,3), BCTRL: 0x8006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xf4000000/24, 0xe0000000/28
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf3ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[1] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[2] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[3] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[4] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[5] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[6] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[7] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[8] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[9] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[10] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[16] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[17] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[18] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[1] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[2] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[3] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[4] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[5] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[6] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[7] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[8] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[9] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[10] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[15] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[16] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[17] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[18] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[19] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[20] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[21] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[5] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[6] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[7] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[8] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[9] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[10] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[11] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[12] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[13] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[14] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[22] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[23] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[24] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[25] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[27] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[5] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[6] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[7] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[8] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[9] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[10] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[11] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[12] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[13] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[14] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[22] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[23] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[24] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[25] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[27] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf7200000 - 0xf7203fff (0x4000) MX[B]
	[5] -1	0	0xf720a000 - 0xf720a7ff (0x800) MX[B]
	[6] -1	0	0xf7100000 - 0xf71fffff (0x100000) MX[B]
	[7] -1	0	0xf7208000 - 0xf7208fff (0x1000) MX[B]
	[8] -1	0	0xf7207000 - 0xf7207fff (0x1000) MX[B]
	[9] -1	0	0xf7206000 - 0xf72060ff (0x100) MX[B]
	[10] -1	0	0xf7205000 - 0xf72050ff (0x100) MX[B]
	[11] -1	0	0xf7204000 - 0xf7204fff (0x1000) MX[B]
	[12] -1	0	0xf720b000 - 0xf720bfff (0x1000) MX[B]
	[13] -1	0	0xf7000000 - 0xf70fffff (0x100000) MX[B]
	[14] -1	0	0xf7209000 - 0xf7209fff (0x1000) MX[B]
	[15] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xf8000000 - 0xf8000fff (0x1000) MX[B]
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[25] -1	0	0x00009c00 - 0x00009c1f (0x20) IX[B]
	[26] -1	0	0x00009800 - 0x0000983f (0x40) IX[B]
	[27] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[28] -1	0	0x00009000 - 0x0000903f (0x40) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[30] -1	0	0x00000500 - 0x0000050f (0x10) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```


**Here is my xorg.conf file:**

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"PF790"
	Horizsync	30.0	-	97.0
	Vertrefresh	50.0	-	160.0
	Option		"DPMS"
EndSection

Section "Device"
	
			Option		"UseFBDev"		"true"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"PF790"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1400x1050"	"1280x960"	"1152x864"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1400x1050"	"1280x960"	"1152x864"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1400x1050"	"1280x960"	"1152x864"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1400x1050"	"1280x960"	"1152x864"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1400x1050"	"1280x960"	"1152x864"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1400x1050"	"1280x960"	"1152x864"	"1024x768"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

```


I don't have experience with nvidia so I don't know where to go here.

---

### Post by TennesseeAborigine on 2007-08-11
Totally new to Ubuntu, though we're becoming more acquainted since I've screwed it up and reinstalled about 5 times in the last week (i'm having fun, really :) ) . I've got a Nvidia 6200 and have been wrestling with getting the resolution right for my Samsung 205bw 20" widescreen LCD. I finally got it about 1/2 an hour ago and it was deceptively easy. First the info for the post...

Command: lspci -n | grep 0300
Result:         01:00.0 0300: 10de:0221 (rev a1)
Command: lspci | grep VGA
Result:         01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1

Now, What I Did...

First, it was a fresh install... i hadn't messed with it at all yet. 

i let Ubuntu Feisty Fawn update completely and then used the restricted driver manager to install the restricted drivers. 

at the command prompt i used $ sudo nvidia-settings (i can't remember which post i found that command on, i kinda just remembered it out of the blue)

this brought up a handy GUI showing my system information an a menu along the left side. from the menu i chose X server Display Configuration which gave me a tab with a resolution picklist. i simply picked my native monitor resolution from the list 1680 x 1050 

That was it.
So Far So Good...

Rock On Feisty Fawn!

:guitar:

---

### Post by TennesseeAborigine on 2007-08-11
[COLOR="Blue"][I]Now, What I Did...
First, it was a fresh install... i hadn't messed with it at all yet.
i let Ubuntu Feisty Fawn update completely and then used the restricted driver manager to install the restricted drivers.
at the command prompt i used $ sudo nvidia-settings (i can't remember which post i found that command on, i kinda just remembered it out of the blue)
this brought up a handy GUI showing my system information an a menu along the left side. from the menu i chose X server Display Configuration which gave me a tab with a resolution picklist. i simply picked my native monitor resolution from the list 1680 x 1050
That was it.
So Far So Good...[/I][/COLOR]

Update: Not so good, but close. my monitor kept that resolution until i switched users and then came back to my account to find a black screen with mouse control. A reboot and fresh login brought me back to the desktop with the 1024 x 768 resolution(just a little trick i picked up from a MS :evil: Windows OS). I read something about having to make it the default boot resolution. I'll keep looking and post a solution. Any suggestions would be welcomed.

thanks

---

### Post by TennesseeAborigine on 2007-08-12
Ok, we're good again

I remembered reading that you need to be in advanced mode when you used nvidia-settings. It worked. i previewed the settings and saved to xorg.conf via the GUI. 

All is well.. through 2 reboots and 3 user switches so far.

:guitar:

---

### Post by tseliot on 2007-08-12
> **Dubbayoo said:**
> I am unable to get the nvidia driver working with a Geforce FX 5500 on Feisty. Been using an ATI for 4 years now. The nv driver works fine but no 3D and text is a lil fuzzy, but that could be me.

I tried to install using Envy (automatic selection) and by just installing the pkgs then using Restricted Driver Manager. 
Mixing Envy with Restricted Driver Manager is not such a good idea.

Uninstall the driver through Envy and then install it with the Automatic installation.

Then reboot.

if this doesn't work, post the output of this command:
```
sudo modprobe nvidia
```

---

### Post by tseliot on 2007-08-12
> **tseliot said:**
> Mixing Envy with Restricted Driver Manager is not such a good idea.

Uninstall the driver through Envy and then install it with the Automatic installation.

Then reboot.

if this doesn't work, post the output of this command:
```
sudo modprobe nvidia
```

and post your /var/log/envy-installer.log

---

### Post by tseliot on 2007-08-12
> **dartmusic said:**
> No dice, I'm afraid.  X crashes, complaining about "nvidia-auto-select," though I can't find any mention of that anywhere in my xorg.conf.

I can't understand why this has to be so difficult...though I really do appreciate your help.

Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by Dubbayoo on 2007-08-12
> **tseliot said:**
> Mixing Envy with Restricted Driver Manager is not such a good idea.

Uninstall the driver through Envy and then install it with the Automatic installation.

Then reboot.

if this doesn't work, post the output of this command:
```
sudo modprobe nvidia
```

Completed with no change. 


```
steve@ubu:~$ sudo modprobe nvidia
steve@ubu:~$ 
```
I'm assuming that isn't good.

---

### Post by tseliot on 2007-08-12
> **Dubbayoo said:**
> Completed with no change. 


```
steve@ubu:~$ sudo modprobe nvidia
steve@ubu:~$ 
```
I'm assuming that isn't good.
It means that the module can be loaded...

Maybe you will be given the solution here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by masoodkamal on 2007-08-12
hi all

man there are so many ways mentioned in ubuntu forums to install nvidia drivers. :confused: soo confusing!!!!
Can anybody tell me which is the correct and working method to install. :) 
Help plz.. i am totaly new to linux.

---

### Post by autodidakt on 2007-08-13
Hi,

I'm a noob in Linux and Ubuntu so please excuse if i'm giving you not enough information or if i'm asking the wrong questions. :)

I Installed the latest Ubuntu Version on my Computer. After this i tried to install the Nvidia-drivers for my graphic card. I followed the Method one of the HOWTO. Everything worked fine until i pressed ALT+CTRL+BACKSPACE to restart the X-Server. After this i got this Output:

> (EE) Failed to load module "wfb" (module does not exist, 0)
(EE) NVIDIA(0): Need libwfb but wfbScreenInit not found

Fatal server errors:
AddScreen/ScreenInit failed for driver 0

I guess i have to install those packages but I don't know how without X-Server. Is there any tool like Yast in Suse wich helps me to install packages. If not please tell me how to do it from commandline.

Additional it says that i should restart GDM after fixing the problem. ...I don't know how to do that.

best regards,

Olli

---

### Post by tseliot on 2007-08-13
> **autodidakt said:**
> I Installed the latest Ubuntu Version on my Computer. After this i tried to install the Nvidia-drivers for my graphic card. I followed the Method one of the HOWTO. Everything worked fine until i pressed ALT+CTRL+BACKSPACE to restart the X-Server. After this i got this Output:
what's the model of your graphic card?

---

### Post by tseliot on 2007-08-13
> **masoodkamal said:**
> hi all

man there are so many ways mentioned in ubuntu forums to install nvidia drivers. :confused: soo confusing!!!!
Can anybody tell me which is the correct and working method to install. :) 
Help plz.. i am totaly new to linux.

Try either Restricted Drivers Manager (in the System menu) or Method 1 of my guide (i.e. the only officially supported methods).

---

### Post by autodidakt on 2007-08-13
8800GTS

Ah btw i installed the 64bit version of Unbuntu.

---

### Post by tseliot on 2007-08-13
> **autodidakt said:**
> 8800GTS

Ah btw i installed the 64bit version of Unbuntu.

It's a known bug in the official packages which affects geforce 8xxx.

Try Envy (**at your risk**):
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by autodidakt on 2007-08-13
the driver seemes to by installed properly by envy now.

thx a lot for the fast reply!

---

### Post by Theimon on 2007-08-15
I search the entire web and back but.....do you have a Feisty repository for the latest Envy?

---

### Post by tseliot on 2007-08-15
> **Theimon said:**
> I search the entire web and back but.....do you have a Feisty repository for the latest Envy?

No, you'll have to download it from my website. I might create one in the next future though

---

### Post by Theimon on 2007-08-15
> **tseliot said:**
> No, you'll have to download it from my website. I might create one in the next future though

Ah ok, thank you.

---

### Post by kneehighspy on 2007-08-19
great work, i finally switch to ubuntu (from msoft) and this works great, i've got a 8800GTS and it seems to work (so far) running dual widescreens (@ 1680x1050 each).  using separate X screen, not like windows.  tried twinview, but when i maximized any app, it showed up on both screens as one.

any way to set up the dualview as on win?

---

### Post by Garyu on 2007-08-19
Great guide tseliot. Now with the latest nvidia drivers and updated wine, LOTRO performance is like 10 times that of Windows (Vista). :)

---

### Post by media601 on 2007-08-19
Will Envy work for legacy nVidia Vanta 16 mb? Thanks.

---

### Post by lightyear87 on 2007-08-20
hi there,

I've a problem. i installed ubuntu 7.04. n then i installed graphics driver-"NVIDIA-linux-x86-100.14.11-pkg1.run"- for the on-board graphics card -"nvidia geforce 6100 nforce 430". During Installation it asked if i wanted to download precompiled kernel from nvidia site,but as i didn't have net access i opted for not to n it built a kernel n istalled it. After Installing, in Nvidia Controll Panal it said the graphics Controller is "nvidia geforce 6150SE nforce 430"(Don't know how!!!!). 
problem arose when i restarted (xserver). xserer got disabled. the reason it gave is something like this(in my own words).  " the version of kernel nvidia compiled didn't match with that of mine.It seems the version of kernel it built was 1.0.0 but i've 1.1.1(i don't have any idea what's it). please check in wiki your version of kernel."
 please tell me how to resolve this. i've another driver also(NVIDIA-Linux-x86-1.0-9755-pkg1.run.txt). i don't have net access(i use my cell(nokia 6020) as modem to access net in windows. i couldn't find a way to install the modem driver in ubuntu. please tell,if anybody knows,how to install that too. please.it'll be of great help).  well, could u tell me where do i get the right version of precompiled kernel to installing the graphics driver properly. n if thats possible how will the nvidia installer know where is the precompiled kernel(again,i don't know whats "precompiled-kernel")...  please help me out.

---

### Post by tseliot on 2007-08-20
> **lightyear87 said:**
> After Installing, in Nvidia Controll Panal it said the graphics Controller is "nvidia geforce 6150SE nforce 430"(Don't know how!!!!). 
problem arose when i restarted (xserver). xserer got disabled. the reason it gave is something like this(in my own words).  " the version of kernel nvidia compiled didn't match with that of mine.It seems the version of kernel it built was 1.0.0 but i've 1.1.1(i don't have any idea what's it). please check in wiki your version of kernel."

Have a look at this page (read where it says "Debian GNU/Linux or [K]Ubuntu with Xorg 7.x"):
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by lightyear87 on 2007-08-20
thanks a lot. 
but could u tell me how to figure out which version of xorg. is it same as the ubuntu version??
i'll try with the method told n get back to u. :).:guitar::guitar:

---

### Post by tseliot on 2007-08-20
> **lightyear87 said:**
> thanks a lot. 
but could u tell me how to figure out which version of xorg. is it same as the ubuntu version??

type:
```
Xorg -version
```

---

### Post by tseliot on 2007-08-20
> **media601 said:**
> Will Envy work for legacy nVidia Vanta 16 mb? Thanks.
Yes, you will have to install the legacy driver (71xx)

---

### Post by lightyear87 on 2007-08-21
everything went nice. i could install drivers. but i wouldn't get my favorite 1280x1024 resolution in it. 
n i installed compiz with some fusion plugins but it hangs after staying logged in for some time. n even though i opted for 1280x768 resolution n made it default in nvidia controll centre, once i enable gl desktop in compiz it would come back to 1024x768 res. i thought i would uninstall compiz,but after approaching u. its called gl desktop,after enabling which 'm facing the problem.
n which one is better , beryl or compiz???
thanks

---

### Post by tseliot on 2007-08-21
> **lightyear87 said:**
> everything went nice. i could install drivers. but i wouldn't get my favorite 1280x1024 resolution in it. 
n i installed compiz with some fusion plugins but it hangs after staying logged in for some time. n even though i opted for 1280x768 resolution n made it default in nvidia controll centre, once i enable gl desktop in compiz it would come back to 1024x768 res.
Type:
```
sudo nvidia-settings
```

set the resolution and save your settings.

[QUOTE=lightyear87;3226054]i thought i would uninstall compiz,but after approaching u. its called gl desktop,after enabling which 'm facing the problem.
n which one is better , beryl or compiz???
thanks
Compiz seems to be more stable (at least on my computer)

---

### Post by lightyear87 on 2007-08-21
n how bout my computer getting hanged??? whats the solution buddy

---

### Post by wwynn on 2007-08-21
Used Envy 0.9.7-0ubuntu8 to install the driver for an ASUS EN8500GT. After a system restart, I now have a choice in resolutions -- thank you. 

How do I get the refresh rate to be something other than 60 Hz?

BTW, when I enter "sudo nvidia-settings" in a terminal window, the response is "command not found". Dunno if that should be the case or not.

---

### Post by lightyear87 on 2007-08-22
> **tseliot said:**
> [QUOTE=lightyear87;3226054]everything went nice. i could install drivers. but i wouldn't get my favorite 1280x1024 resolution in it. 
n i installed compiz with some fusion plugins but it hangs after staying logged in for some time. n even though i opted for 1280x768 resolution n made it default in nvidia controll centre, once i enable gl desktop in compiz it would come back to 1024x768 res.
Type:
```
sudo nvidia-settings
```

set the resolution and save your settings.


Compiz seems to be more stable (at least on my computer)


well,Now everything's working fine. but 'm not getting 1280x1024 res in nvidia controll penal. so i edited xorg.conf n added 1280x1024 in the section screen under depth 24 of subsection.. but in nvidia ntrl panel 'm getting a new res 1280x960(don't know how).. :confused:please guide me. 
thanks

---

### Post by tseliot on 2007-08-22
> **lightyear87 said:**
> [QUOTE=tseliot;3226462]


well,Now everything's working fine. but 'm not getting 1280x1024 res in nvidia controll penal. so i edited xorg.conf n added 1280x1024 in the section screen under depth 24 of subsection.. but in nvidia ntrl panel 'm getting a new res 1280x960(don't know how).. :confused:please guide me. 
thanks

post the output of this command:
```
xrandr
```

---

### Post by tseliot on 2007-08-22
> **wwynn said:**
> Used Envy 0.9.7-0ubuntu8 to install the driver for an ASUS EN8500GT. After a system restart, I now have a choice in resolutions -- thank you. 

How do I get the refresh rate to be something other than 60 Hz?

BTW, when I enter "sudo nvidia-settings" in a terminal window, the response is "command not found". Dunno if that should be the case or not.
post the output of the following command:
```
sudo aptitude search nvidia
```

and post your /var/log/envy-installer.log

---

### Post by wwynn on 2007-08-22
sudo aptitude search nvidia:
p   nvidia-glx                                                     - NVIDIA binary XFree86 4.x/X.Org driver                                   
p   nvidia-glx-dev                                                 - NVIDIA binary XFree86 4.x/X.Org driver development files                 
p   nvidia-glx-legacy                                              - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver                          
p   nvidia-glx-legacy-dev                                          - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files        
p   nvidia-glx-new                                                 - NVIDIA binary XFree86 4.x/X.Org 'new' driver                             
p   nvidia-glx-new-dev                                             - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files        
v   nvidia-kernel-1.0.7184                                         -                                                                          
v   nvidia-kernel-1.0.8774                                         -                                                                          
v   nvidia-kernel-1.0.9631                                         -                                                                          
v   nvidia-kernel-1.0.9755                                         -                                                                          
p   nvidia-kernel-common                                           - NVIDIA binary kernel module common files                                 
p   nvidia-kernel-source                                           - NVIDIA binary kernel module source                                       
p   nvidia-legacy-kernel-source                                    - NVIDIA binary 'legacy' kernel module source                              
p   nvidia-new-kernel-source                                       - NVIDIA binary 'new' kernel module source                                 
p   nvidia-settings                                                - Tool of configuring the NVIDIA graphics driver                           
p   nvidia-xconfig                                                 - The NVIDIA X Configuration Tool                                    
--------------------------

no envy-<anything> in /var/log

---

### Post by tseliot on 2007-08-22
> **wwynn said:**
> sudo aptitude search nvidia:
p   nvidia-glx                                                     - NVIDIA binary XFree86 4.x/X.Org driver                                   
p   nvidia-glx-dev                                                 - NVIDIA binary XFree86 4.x/X.Org driver development files                 
p   nvidia-glx-legacy                                              - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver                          
p   nvidia-glx-legacy-dev                                          - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files        
p   nvidia-glx-new                                                 - NVIDIA binary XFree86 4.x/X.Org 'new' driver                             
p   nvidia-glx-new-dev                                             - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files        
v   nvidia-kernel-1.0.7184                                         -                                                                          
v   nvidia-kernel-1.0.8774                                         -                                                                          
v   nvidia-kernel-1.0.9631                                         -                                                                          
v   nvidia-kernel-1.0.9755                                         -                                                                          
p   nvidia-kernel-common                                           - NVIDIA binary kernel module common files                                 
p   nvidia-kernel-source                                           - NVIDIA binary kernel module source                                       
p   nvidia-legacy-kernel-source                                    - NVIDIA binary 'legacy' kernel module source                              
p   nvidia-new-kernel-source                                       - NVIDIA binary 'new' kernel module source                                 
p   nvidia-settings                                                - Tool of configuring the NVIDIA graphics driver                           
p   nvidia-xconfig                                                 - The NVIDIA X Configuration Tool                                    
--------------------------

no envy-<anything> in /var/log
It looks like nothing was installed...

type:
```
sudo envy -g
```

and install the driver.

then post your /var/log/envy-installer.log

---

### Post by wwynn on 2007-08-23
No can do, now. Envy went through the install process fully this time. After a restart things seemed normal, but the refresh rate was still 60 Hz. There was also a message and icon about (I think) restricted modules. So, I tried Add/Remove.

Add/Remove produced another error message, this one about broken packages or lists of packages. So, I executed the suggestions ("sudo apt-get update" and "sudo apt-get install -f"). There were some choices about duplicate packages, one expected and the other from a "maintainer". I went with the defaults because I thought that the duplicates were put there by Envy.

Next restart, I got a text screen with readable text surrounded by unusual characters. The messages were about X or gdm being broken. Now I have a command line interface only. Dunno how to capture text and post it. Nano and Lynx, maybe?

I could blow the server away and start over for the x-teenth time, but I would prefer to fix X / gdm. When it all gets fixed, I will probably rebuild it with steps that work, anyway, but right now the focus is on fixing this. Amazing to me that it is so difficult just to get a video card to run at more than 60 Hz.

---

### Post by Caffeine_Junky on 2007-08-23
To get your desired refresh-rate you just need **your **monitor spec's from a manual or the manufactures website
```

eg:
	Specifications
Model name 	Acer AC711
Size 	17" flat square tube
Phosphor pitch 	0.27mm diagonal
[COLOR="Red"]Scanning frequency 	H: 30 &#8211; 70kHz V: 50 &#8211; 160Hz[/COLOR]
Display area 	300x225 mm
Input signals 	RGB analogue
Maximum resolution 	1280x1024 @ 60Hz
Recommended resolution 	1024x768; flicker-free at [COLOR="Red"]85 Hz[/COLOR]
Video bandwidth 	108MHz
Power consumption 	75W
Dimensions (WxHxD) 	405x427x419 mm
Net weight 	14.9kg
```

..then edit your:   sudo gedit /etc/X11/xorg.conf  

to reflect the correct H & V

```
Section "Monitor"
    Identifier     "acer AC711"
    [COLOR="Red"]HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0[/COLOR]
    Option         "DPMS"
EndSection
```

and don't forget to save the changes...    then restart X  [Ctrl+Alt+Backspace]
login,  open terminal  type:  nvidia-settings (or look for it in your Applications menu) click:  X Server Display Configeration  > Resalution > Hertz & select your desired setting (85Hz' is mine)  and  Apply.  Done    ( I used Envy to install my nvidia driver).

---

### Post by lightyear87 on 2007-08-23
> **tseliot said:**
> [QUOTE=lightyear87;3232148]

post the output of this command:
```
xrandr
```


SZ:    Pixels          
Physical Refresh
 0   1024 x 768    ( 346mm x 260mm )  *50   53   54  
 1    800 x 600    ( 270mm x 203mm )   51   56   57   58  
 2    640 x 480    ( 216mm x 162mm )   52   60   61   62  
 3    832 x 624    ( 281mm x 211mm )   55  
 4    720 x 450    ( 243mm x 152mm )   59  
 5    640 x 400    ( 216mm x 135mm )   63  
 6    640 x 384    ( 216mm x 130mm )   64  
 7    576 x 384    ( 195mm x 130mm )   65  
 8    512 x 384    ( 173mm x 130mm )   66   67   68  
 9    416 x 312    ( 140mm x 105mm )   69  
 10   400 x 300    ( 135mm x 101mm )   70   71   72   73  
 11   320 x 240    ( 108mm x  81mm )   74   75   76  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

---

### Post by tseliot on 2007-08-23
> **lightyear87 said:**
> [QUOTE=tseliot;3232469]


SZ:    Pixels          
Physical Refresh
 0   1024 x 768    ( 346mm x 260mm )  *50   53   54  
 1    800 x 600    ( 270mm x 203mm )   51   56   57   58  
 2    640 x 480    ( 216mm x 162mm )   52   60   61   62  
 3    832 x 624    ( 281mm x 211mm )   55  
 4    720 x 450    ( 243mm x 152mm )   59  
 5    640 x 400    ( 216mm x 135mm )   63  
 6    640 x 384    ( 216mm x 130mm )   64  
 7    576 x 384    ( 195mm x 130mm )   65  
 8    512 x 384    ( 173mm x 130mm )   66   67   68  
 9    416 x 312    ( 140mm x 105mm )   69  
 10   400 x 300    ( 135mm x 101mm )   70   71   72   73  
 11   320 x 240    ( 108mm x  81mm )   74   75   76  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
Try point 10 of the Problems Section of this guide:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#PROBLEMS_SECTION)

Then if that didn't solve the problem try point 5 of the Problems Section of the same guide.


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[http://wiki.caoslinux.org/X_Server_Configuration](http://wiki.caoslinux.org/X_Server_Configuration)

---

### Post by lightyear87 on 2007-08-23
> **tseliot said:**
> 
OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[http://wiki.caoslinux.org/X_Server_Configuration](http://wiki.caoslinux.org/X_Server_Configuration)

btw i've crt monitor(viewsonic E70)
Thanks a lot

---

### Post by tseliot on 2007-08-23
> **lightyear87 said:**
> btw i've crt monitor(viewsonic E70)
Thanks a lot

It's the same.

---

### Post by lightyear87 on 2007-08-24
Everything worked. 
dude,i've been downloading stuffs offline from packages.ubuntu.com taking care of dependencies. i've compiz installed too. now 'm in need of compiz-fusion latest,which idon't get at the above mentioned site. so if u don't mind could u please tell me where 'll i get it offline pls
thanks for everything

---

### Post by Dark Star on 2007-08-24
Thanks a lot :) Both your tut and s/w envy is awesome :D

---

### Post by staticmovements on 2007-08-24
I am new to ubuntu. I run it in a macbook pro core2duo with a vmware virtual machine. I have the latest version of envy and my graphics card is NVIDIA GeForce 8600M GT .

When i tried to run it automatically the terminal showed this :

python pulse.py nvidia
root@myname-desktop:/usr/share/envy# python pulse.
ENVY ERROR: Nvidia card not found
root@myname-desktop:/usr/share/envy#


my architecture is 64 bit ?  because if it is, the drivers that are downloaded manually are only for 32 bit

what to do? download the IA64 driver from the nvidia site and them install it manually?
give me a clue. right now I dont know how to check if i have a driver installed in my system or not

thank you 

dionysis

---

### Post by tseliot on 2007-08-24
> **staticmovements said:**
> I am new to ubuntu. I run it in a macbook pro core2duo with a vmware virtual machine. I have the latest version of envy and my graphics card is NVIDIA GeForce 8600M GT .

When i tried to run it automatically the terminal showed this :

python pulse.py nvidia
root@myname-desktop:/usr/share/envy# python pulse.
ENVY ERROR: Nvidia card not found
root@myname-desktop:/usr/share/envy#


my architecture is 64 bit ?  because if it is, the drivers that are downloaded manually are only for 32 bit

what to do? download the IA64 driver from the nvidia site and them install it manually?
give me a clue. right now I dont know how to check if i have a driver installed in my system or not
If you run Ubuntu inside vmware your virtual machine will use a fake graphic card device which is not detected as an Nvidia card and that therefore won't work with the Nvidia driver.

It's a limitation of vmware

---

### Post by Schlicorice on 2007-08-25
I have an XFX Video Card.......which is a nVidia Geforce FX 5200 256MB AGP card and every method I've tried doesn't seem to work properly.  The horrible thing is that when I reboot, it won't even reboot into "X" (I think it's called), and I'm pretty new at this so the only solution to that is to re-install Ubuntu.

Does anyone have specific experience installing nVidia capabilities with this same graphics card?

Also, I'm sure this is a no-brainer for most too.....I can't change my settings in any of my text files (config type files).  The save button is greyed out, so, if I want to change a variable, I can't.

Any help would be greatly appreciated !!!

My first post....wow !!!

---

### Post by tseliot on 2007-08-25
> **Schlicorice said:**
> I have an XFX Video Card.......which is a nVidia Geforce FX 5200 256MB AGP card and every method I've tried doesn't seem to work properly.  The horrible thing is that when I reboot, it won't even reboot into "X" (I think it's called), and I'm pretty new at this so the only solution to that is to re-install Ubuntu.
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.


> **Schlicorice said:**
> Also, I'm sure this is a no-brainer for most too.....I can't change my settings in any of my text files (config type files).  The save button is greyed out, so, if I want to change a variable, I can't.
that's because you don't have the permission to edit those files.

try with:
```
gksudo gedit path_to_the_file
```

or simply:
```
sudo name_of_the_editor path_to_the_file
```

---

### Post by ozzyprv on 2007-08-26
> **tseliot said:**
> Hi, I've ported my guide about the Nvidia Drivers to Edgy Eft on the USDF.
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

OR try this mirror:

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)



Thanks a lot tseliot, your guide was of great help for me.

BTW, the first link is broken (at or least it was all say on Aug, 26th/07.

One only problem. I followed:
> 6) Create a link to the &#8220;Nvidia-Settings&#8221; Panel in your application menu:
file.pngCode:

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop


But I do not see any Nvidia menu/icon in the applications menu. Any help?

---

### Post by tseliot on 2007-08-26
> **ozzyprv said:**
> But I do not see any Nvidia menu/icon in the applications menu. Any help?
type:
```
gedit /usr/share/applications/NVIDIA-Settings.desktop
```

and post the content

---

### Post by ozzyprv on 2007-08-26
This is what I get from the gedit window
> 
[Desktop Entry] 
Name=NVIDIA Settings 
Comment=NVIDIA X Server Settings 
Exec=nvidia-settings 
Icon= 
StartupNotify=true 
Terminal=false 
Type=Application 
Categories=Application;System


---

### Post by tseliot on 2007-08-26
Get to the Applications/System tools menu

---

### Post by ozzyprv on 2007-08-26
> **tseliot said:**
> Get to the Applications/System tools menu

This is all I get (attachment).

---

### Post by SimonFitz on 2007-08-26
Hi ozzyprv

I'm in the same situation as you - followed tseliot's guide (thank you tseliot) but I do not have a Nvidia icon in the menu. However, in [*this post*]("http://ubuntuforums.org/showpost.php?p=2332483&postcount=4") in the "Unable to display 1680x1050 using nvidia driver" thread there was a suggestion by hardyn to enter the command: ```
gksudo nvidia-settings
``` in a terminal window. Up popped a config box allowing me to choose the resolution I wanted! Although I haven't rebooted since using this, it seems to work ... (famous last words of course). I've now added the command as a launcher in a panel.

Thought I'd post this just in case it was of any use to anyone.

Simon

---

### Post by ozzyprv on 2007-08-26
Thank you SimonFitz,

It works from the terminal indeed. But still puzzles me why the icon isn't there.

---

### Post by wwynn on 2007-08-31
> **Caffeine_Junky said:**
> To get your desired refresh-rate you just need **your **monitor spec's from a manual or the manufactures website
....


Thanks a bunch, Caffeine_Junky. Things did not quite work out that way, but now the driver is working and I have 1024x768_85. This post was a big help.

---

### Post by Kxpress on 2007-08-31
I followed the instruction: used Envy GUI to install the Nvidia driver for my Laptop's Quadros M140 grapghic card.

On the Envy terminal, I got the the point:

After unpacking 79.8 MB of additional disk soace will be used.
 Media change: please insert the disk label "Ubuntu 7.04_Fiesty -_Fawn release i386 "2007-0145"  in the drive '/cdrom/' and presss enter

I did but it did not proceed further ... I thought this is a completed script ,there is no need to interfere by the user ?

Am I doing something wrong here ? Please help

---

### Post by oo-boon-too on 2007-09-01
Hello, I used your Envy (Along with many other attempts) to get the nVidia driver for a 6600 GT to work. Your program did everything flawlessly, but their seems to be a single problem somewhere. After about a minute or so, my Mouse and Keyboard freeze. Any idea what i should do?

---

### Post by bricedebrignaisplage on 2007-09-02
This app is awesome, it did in 2 minutes what I had been trying to do for a whole day.
I found how to configure my 2 monitors, layout, resolution with the "Nvidia Settings" app in the system menu. I also found that the desktop background configuration dialog was modified to handle the new config.

However, I haven't found how to set the screensave correctly: my screen saver picture is split over the 2 screens, which means that I see only half of it...  **Is there a way to set the screen saver on the monitor only, or a (different) screen savers on each screen?**

One more question: the resolution of my monitor is now limited to 1024x768. Is there a way to increase that?

I am running Kubuntu 7.04 and I have a GeForce4 MX 440 with AGP8X (GPU 0).
Thanks.

---

### Post by Brinstar on 2007-09-12
i don't know if someone has already posted this (and i don't want to go through 31 pages to find out, thanks!), but it's possible and quite simple to install the official Nvidia drivers without Envy or any other 'helpers'

just sudo init 1, 'sh NVIDIA-***.run', reboot. you need the build-essential package installed but that should be on the CD.

edit: when you get asked if you want to connect to the net, just decline the offer.

edit 2: there is a problem doing this with the latest driver i.e. 100.*.11, some kind of kernel incompatibility to do with modules and/or sources. Stick with the 9631 version if you're going to try this. YMMV.

---

### Post by McSqueeb on 2007-09-12
And, you would be the man.  :)

---

### Post by justinin3d on 2007-09-12
Hi all I need help reinstalling my nvidia drivers,

currently when I log into Ubuntu I get a white screen, everything was running fine until when I decided to uninstall the drivers last night and then disabled the 3d accelerator without restarting, I had gotten the Xserver error before but I just did this following command in the 'offline' terminal, 

sudo dpkg-reconfigure xserver-xorg

I kept everything on default except for giving the monitor a name (though it runs on my second monitor now which isnt the one I put down)

so how do I install the nvidia drivers on the offline terminal?, I have an Nvidia 8800GTX videocard if that helps.

Thanks for all help!!! 

P.S has you might of notice, first time Ubuntu noobie :D.

---

### Post by zeddock on 2007-09-14
> **Brinstar said:**
> i don't know if someone has already posted this (and i don't want to go through 31 pages to find out, thanks!), but it's possible and quite simple to install the official Nvidia drivers without Envy or any other 'helpers'

just sudo init 1, 'sh NVIDIA-***.run', reboot. you need the build-essential package installed but that should be on the CD.

edit: when you get asked if you want to connect to the net, just decline the offer.

edit 2: there is a problem doing this with the latest driver i.e. 100.*.11, some kind of kernel incompatibility to do with modules and/or sources. Stick with the 9631 version if you're going to try this. YMMV.

I am still noobishly confused. Can you give a little more detail in the steps, please?

Thanx,

zeddock

---

### Post by man_bash on 2007-09-14
> **zeddock said:**
> I am still noobishly confused. Can you give a little more detail in the steps, please?

Thanx,

zeddock

navigate to where you have downloaded your nvidia drivers, ie cd /home/*username*/Desktop if desktp is where your downloaded driver is, then run 
sudo sh NVIDIA(press Tab to autocomplete)

---

### Post by clemrgooden on 2007-09-18
I just ran Envy for the first time in Ubuntu 7.04 on my Gateway MT3423 (GeForce Go 6100). After turning all the repositories on in Synaptic, I selected "Install the Nvidia Driver" and restarted. I experienced the same problem as when I tried to install the driver myself: a black screen after the Ubuntu loading bar (where the login screen should be). 
  So, I used the text-based Envy to uninstall the Nvidia driver, and restored my xorg.conf. I got into X again, but received the message: "Unable to initialize HAL!". I'm not sure what HAL is; I probably should.
  I am new to Ubuntu (and Linux in general) so hopefully someone can explain what I did wrong, if anything, and how to fix it. I am really looking forward to using Ubuntu, but I am becoming more and more frustrated with it everyday as I try to install drivers. Please help!
                Thank you everyone,
                     RG

---

### Post by suoko on 2007-09-19
I tried envy on a DELL notebook with nvidia 8600.
It works except for compiz which causes the following issues:
- window borders are missing. I had to add 'Option &#8220;AllowGLXWithComposite&#8221; &#8220;true&#8221;' to xorg.conf to have them back
- I can't move windows nor with &#8220;AllowGLXWithComposite&#8221; or without &#8220;AllowGLXWithComposite&#8221; . No solution to this yet. Do I miss another option?

All compiz effects work (except for wobbling because of "fixed" windows)

Another problem is the screen resolution. It is at its maximum. With the nvidia tool I can only choose the highest one. No other res. is shown although in the xorg.conf file I have many possibile resolutions

EDIT: I solved the wobbly problem by changing the wobbly option from the "GL desktop" application. I just disabled and then re-enable it. Nothing special.
I still have problems with resolution

---

### Post by lightyear87 on 2007-09-21
hi,

   could anybody please post the copy of xorg.conf file in ubuntu feisty fawn. I 've nvidia geforce 6100 nforce 430 on asus m2nmx mobo.. 

 and don't know whats wrong but i don't get 1280x1024 resolution in nvidia control panel. i followed tseliot's guide too. and any resolution i choose, after restr=arting it would come back to 1024x768. please help me

---

### Post by beholder_lt on 2007-09-21
hello everybody!
i've switched from windows to ubuntu two days ago.  the problem is that i can't get xorg.conf properly configured. at first the problem was the resolution - it was 1024x768 instead of 1440x900 (widescreen). i've solved this problem by removing the xorg.cfg and making it default. now the problem is that when i start my pc, i get an error which says that x server has failed to start because no screen has been found. then i delete the xorg.cfg, startx, nvidia-xconfig,  and now i need to configure the file because i get the same error when i reboot. configuring by the file by myself is a bit too tough for me, so i expect your help here. the video card is 8800gts and i am using ubuntu 7.04 feisty.
p.s. xorg-configure didn't help.
p.p.s. sorry for my english :)
the error itself:
Error: API MISMATCH
this nvidia driver component is version 100.14.19, but the nvidia kernel module version does not match. please make sure that the kernel module and all nvidia driver components have the same version
(EE) nvidia (0) failed to initialize the nvidia kernel module. Please ensure that there is a supported nvidia gpu in this system and that the nvidia device files have been created properly.
screen(s) have been found but none have a usable configuration.

---

### Post by aantetomaso on 2007-09-22
Hello,

I've tried Envy, after the native UBUNTU method (using restricted drivers manager), to install the latest NVIDIA drivers (Geforce GO 7400). It works very well and with the new driver I've better performances. However, two questions.

1) I have compiz fusion installed and sometimes I get the "black window", because I have to use 
    "compiz --replace -v" statement. The one I used with the old driver "compiz --replace --indirect-rendering decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &" seems not to work with the new NVIDIA driver : I have windows with no content inside...

2) I have a Sony VAIO VGN-FE31H with and external Philips 190s LCD screen. With this last screen I have no problems, but with VAIO LCD I cannot choose resolutions over 1280x800. I'd like the windows 1440x900 but I'va tried all methods...nothing. The X11 log says that the 1440x900 mode at 60 HZ is not valid and switches to the default mode.

3) when I switch to text mode "CTRL+ALT+F1" I get a strange and bad resolution..I don't know why.

I post my xorg.conf, please can someone help me ? This is the file I use with the VAIO screen. The one with philips is identical. Only the resolution in the "device" section changes, according to what "gtf" command says.

Thanks in advance.

---

### Post by fbiazi on 2007-09-22
Hello everybody,

**lightyear87**, may be Ubuntu is not detecting your monitor, normally this happens when you use desktop switching devices like ServSwitch from Blackbox to use only one set of monitor, keyboard and mouse on several CPU's.

well, The solution described here didn't solve the problem, so I cut it out (I don't want others working for nothing because of my post)...

The problem comes back every time I boot on Ubuntu.....

I have to install the nvidia kernel module every time it is turned on. I will try update or something else...

sorry for my english.

---

### Post by beholder_lt on 2007-09-22
so, i've done a system update today, i haven't done it before because i have slow internet and 2 hours for 200 mb is too much for me. today is saturday, so i have a lot of free time. i've done the automatic update and installed automatix. it has downloaded new nvidia drivers and has done something else, because the system starts properly.
but:
the problem is that it's the same as i had in the start.... no 1440x900...
[edit]
i have succesfuly fixed it by using envy and nvidia settings! :guitar:

---

### Post by jonaaathan on 2007-09-23
The Envy script installed the drivers easily for me and I was able to see the nVidia log o at the startup.  Everything seemed fine until i checked ```
lsmod | grep gart
``` it showed nvidia, and via_agp.  i also noticed when i checked ```
cat /proc/driver/nvidia/agp/status
``` it showed me 

Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Enabled
SBA:             Enabled

 How do I make the driver to load nVidia?  I have a GeForce 7300GT and I'm using Feisty Fawn 7.04.  I appreciate the help!

p.s.

I'm very new to Linux, so I would need step by step directions if you can help me. Attached is my xorg.conf file.

---

### Post by suoko on 2007-09-23
hi,

I'd like to solve the problem of resolution.
As I've already said resolution is too high (1720x1200) and I cannot choose a lower resolution through the nvidia-tool.
Moreover, the resolution setting (1720x1200)  is NOT present in the xorg.conf file!!
Here is the xorg file...

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007

Section "ServerLayout"
   Identifier     "Layout0"
   Screen      0  "Screen0" 0 0
   InputDevice    "Keyboard0" "CoreKeyboard"
   InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
   RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
   Load           "dbe"
   Load           "extmod"
   Load           "type1"
   Load           "freetype"
   Load           "glx"
EndSection

Section "ServerFlags"
   Option         "Xinerama" "0"
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
   ModelName      "LPL"
   HorizSync       30.0 - 75.0
   VertRefresh     59.0
   Option         "DPMS"
EndSection

Section "Device"
   Identifier     "Videocard0"
   Driver         "nvidia"
   VendorName     "NVIDIA Corporation"
   BoardName      "GeForce 8600M GT"
   Option "NoLogo" "True"
   Option "AllowGLXWithComposite" "true"
   Option "AddARGBGLXVisuals" "True"

EndSection

Section "Screen"
   Identifier     "Screen0"
   Device         "Videocard0"
   Monitor        "Monitor0"
   DefaultDepth    24
   Option         "TwinView" "0"
   Option         "metamodes" "nvidia-auto-select +0+0"
   SubSection     "Display"
       Depth       24
       Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
   EndSubSection
EndSection

---

### Post by Dimitriid on 2007-10-04
Hello, sorry if this was already posted but Im not finding anything so far.

I installed and used ENVY to get my nvidia driver working and autoconfigure my xorg.conf file fine. The problem for me seems to be uninstalling. I followed the guide at the F.A.Q. section C ( trying to get ready for Gutsy ) and it went ok but now without two problems, one which related to Envy and one that might not but im not sure.

1) My "restricted drivers" now only show Network and VMWare ( I have it installed ). No restricted nvidia anymore. I understand using the "nv" option is just the legacy driver right? ( I haven't been able to start compiz fusion so I am assuming it is ) Any way to get this back? I'd like to use the restricted drivers while I am waiting for Gutsy to be released, and also If they are not there now Im not sure they will be there on Gutsy. The "nv" driver right now by the way its working but badly: everything is shifted to the right and part of the display is even cut on the right ( cant see whatever it is there, i this case the clock i put on my custom panel ). No amount of monitor tweaking will get the image to display properly.

2) Metacity does not start with my session. I get no window borders, window list, etc. I have to open up a terminal and type in "metacity" manually, getting this error:
```
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded
``` As far as I know, before ENVY ( or if I reinstall it ) If i removed compiz fusion from my session menu it would load metacity fine, it would also load metacity fine if I killed compiz fusion. But now it does not seems to be the case, metacity just refuses to start with my session.

Thanks in advance.

---

### Post by JohnMcleod on 2007-10-05
Method 1 works really well on AMD64 fiesty - thanks tselliot!

---

### Post by bouncingmolar on 2007-10-07
>  Error API mismatch: this NVIDIA driver component has version 100.14.19, but the NVIDIA kernel module's version does not match. Please ensure that the kernel module and all NVIDIA driver components have the same version

I get the above xorg error when installing NVIDIA using ENVY. 

I uninstalled the envy nvidia driver again. 

Then I entered (from [http://ubuntuforums.org/showthread.php?t=391896](http://ubuntuforums.org/showthread.php?t=391896) ) 
```

sudo aptitude purge nvidia-glx nvidia-kernel-common
sudo aptitude install nvidia-glx

```
then it all seemed to work. so I thought i'd fixed something and i tried to install envy over the top... and it broke again, giving the intial error. 

Now when i enter the above again, instead the error is replaced with :

>  Fatal: error running install command for nvidia
(EE) Nvidia(0): Failed to load the NVIDIA kernel module!


Then: I tried installing Envy again... same error as first time. 

Then: I loaded envy -t in prompt (since x.org wasn't loading up) and uninstalled nvidia without restarting

Then: i typed 
```

apt-get uninstall nvidia*
yes

apt-get install nvidia-glx

startx

```

It then works correctly, I can even enable desktop effects, I can log out to prompt again. and type startx again.  and the effects will still work. 
HOWEVER:..... when i reboot....        D'oh. : Nvidia failed to lad the NVIdia Kernel Module.   :(
____________
ubuntu 32. and a nvidia geforce 7950 GT, AMD Dual 64 .... maybe i should install ubuntu 64?

---

### Post by bwallum on 2007-10-07
Hiya

I used Envy with Fiesty, it went well. Do you have anything for Gutsy AMD64? The Gutsy nVidia drivers are a little flaky so I'm asking the question rather than experiment.

Kind Regards
Bob

---

### Post by bouncingmolar on 2007-10-08
Following up my last post in this thread. I have now managed to get nvidia to work. 

I'm not sure if this made it work, but I went to /lib/modules/ and saw that there was a folder called: 2.6.20-15-generic ,  2.6.20-15-386 
so i moved them to my desktop in prompt (serverx wasn't working)

I rebooted using vesa 

I then used synaptic to install nvidia-glx and rebooted and it seems to be working now   ... ? i dunno if what i did fixed it but it seems to be working now.


Edit: 
D'OH i stuffed it again. When trying to load "restricted drivers manager" i was told i needed to install linux-restricted-modules-2.6.20-16-generic so I did . now i get:
>  Error: API mismatch: the nvidia kernel module has the version 1.0-7184 but this xmodule has the version 1.0-9631. Please make ssure the kernel module and all NVIDIA driver components have the same version 

I finally fixed it and my linux0restriced-modules-2.6.20-16-generic is no longer installed. why does it kill my nvidia glx anyway?

---

### Post by r691175002 on 2007-10-08
I can't get the nvidia drivers to work.  Running nvidia-settings outputs this:
```
ERROR: NV-CONTROL extension not found on this Display.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.
```

Changing the driver to nvidia in xorg.conf crashes the xserver no matter how I do it.

I have two 8600Gt's.

Any suggestions?

---

### Post by carlinuxlearner on 2007-11-01
Try this:

HOW TO: install your Nvidia driver in Ubuntu 7.10

(Please MAKE SURE with ANY commands (or path names) that you capitalized what I capitalize!!!! This is VERY important!)

I will start by giving you two options. Both options require that you have a internet connection of some kind. (preferably high-speed)

Option #1. Install your Nvidia driver with "Envy" 
(usually MUCH easier then installing the driver the manual way)

OR

Option #2. Install your Nvidia driver manually. (use this if Envy won't work)


If you choose Option #1 "Install your Nvidia driver with "Envy"" Then please proceed from here on.

1.1 
Go to your (System>>Administration>>Software Sources) make sure you have all your repositories enabled. (Check mark them all)

Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

1.2
Double click on the file you just downloaded and tell it to install

1.3
If all those steps went well then Envy should be installed and you should be able to find it in (Applications>>System tools), just run it and you should be able to install your driver all by your self very easily.


Option #2.

2.1
Open up a terminal window (Applications>>Accessories>>Terminal) type this in "sudo apt-get install build-essential"


2.2
In a terminal window type "lspci | grep VGA" find the part that has these around it "[ ]", write down what it says then go here 
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) 
If the name of your graphics card is in the list (such as "Geforce 6800") then download this driver to your Desktop
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run) 
(if that link is old go to this page to get driver) 
[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html) 
(if that link is old, go here and select the driver that starts with "100")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).


(EXAMPLE 

"carl@carlubuntu1:~$ lspci | grep VGA
01:0b.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
carl@carlubuntu1:~$"

The "GeForce4 MX 420" is the name you are looking for. So "GeForce4 MX 420" is what I would look for on the list here.
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

end of example)

2.3
IF YOUR GRAPHICS CARD NAME IS NOT ON THAT LIST look and see if it's on this one
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If it was in the "The 1.0-96xx driver supports the following set of GPU" section, then download this driver to your Desktop
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.01/NVIDIA-Linux-x86-96.43.01-pkg1.run)
(If that link is old then go here)
[http://www.nvidia.com/object/linux_display_x86_96.43.01.html](http://www.nvidia.com/object/linux_display_x86_96.43.01.html)
(If that link is old go here and select the driver that starts with "96")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

If you graphics card name was in the "The 1.0-71xx driver supports the following set of GPUs" section,
then download this driver to your Desktop.
[http://us.download.nvidia.com/XFree86/Linux-x86/71.86.01/NVIDIA-Linux-x86-71.86.01-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/71.86.01/NVIDIA-Linux-x86-71.86.01-pkg1.run)
(If that link is old go here)
[http://www.nvidia.com/object/linux_display_x86_71.86.01.html](http://www.nvidia.com/object/linux_display_x86_71.86.01.html)
(If that link is old go here and select the driver that starts with "71")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)


2.4
Print out this page!

2.5
Restart your computer! At the Grub boot menu (if it doesn't pop up click ESC before it's to late) and select the "recovery mode" kernel, and hit enter!

2.6
Once booted, type in "sh /home/yourusername/Desktop/NVIDIA" but DON'T HIT ENTER!!
(replace "yourusername" with your user name) 
click the TAB button on your key board twice, and it should fill out the rest of the name for you, 
THEN hit enter.

2.7
The installer will ask you some question (don't worry if it says your in "runlevel 1" it doesn't matter) just make sure you answer all the questions so that it will continue the installation process.

2.8
Once the installer is done restart your computer by pressing CTRL+ALT+DELETE, boot up normally. And your Nvidia driver should be installed!

TROUBLE SHOOTING

If you have problems installing "Envy" ether ask about it on the forums, or just do Option #2.

If (in Option #2) when you reboot you get a black screen don't worry it can be fixed!
Just press these keys ALT+F2 and then type this in at the command prompt "sudo nano -w /etc/X11/xorg.conf"
Find the part of the file that says "Device", find "Driver       "nvidia"" change "nvidia" to "nv".
Press ALT+X and save the file.
Restart your computer, try installing it again, or ask about it on the forums. (When asking on the forums, error messages are VERY helpfull please write down, or copy any you get)

C@RL

Any one is welcome to correct me on any thing!

---

### Post by 320blues on 2007-11-05
alberto--here's a kind of wierd problem.  i have an older nvidia geforce2 gts 32mb video card.  i just got it recently.  when i reloaded my system (xubuntu 7.04) and adjusted my settings i get a very wide variety of display settings (1024x768 is about all my 17" dell monitor works with) and i got all the refresh rates.  when i load either ENVY or the legacy glx driver in xubuntu, all i get is 800x600 as the best it will do.  i also don't get any actual configuation settings with envy.  i have used envy before with an nvidia mx4000 and got full configuration, etc.  
i just thought this was all rather strange.  i'm happy with my resolution, etc but thought you might be interested.  thanks for taking the time to read this.

---

### Post by carlinuxlearner on 2007-11-05
You should try editing your "/etc/X11/xorg.conf" file, I have installed that card before and got it to do much better resolutions than 800x600, but only by editing that file. If you don't know how to edit it just ask.

C@RL

---

### Post by infurnus on 2007-11-12
it took me a bit to play with the res it was wavy and off center at first but i was able to find the correct refresh rate + res that i wanted and its Awesome! vesa never looked this good.

---

### Post by GoJa on 2007-11-16
I have a new dell box with Ubuntu 7.04.  I have a Nvidia GeForce 8300GS (pci ID 0423).

**_Question 1:_**
I was reading the info at this URL:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

In step 3 there are references to loading different versions of the driver depending on your video card model, and links to a document to check if your card is supported.  I search by both model number (8300) and pci ID (0423).  I couldn't find either listed

What version of the driver do I use??


**_Question 2:_**
On this page:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)
they have alternate instructions to setup Nvidia cards.

Part of the instructions state

 > How to setup nVidia drivers in 7.04

System > Administration > Restricted Devices Manager
Enable Driver
Apply Changes

and later:

> With the nVidia Driver enabled in the restricted devices manager, we can safely go into the console ..........

When I attempt to go into the restricted devices manager, after I put in my password, a dialog box pops up which tells me:

> Your hardware does not need any restricted drivers.

It only has a close button, which when pressed closes the dialog box and nothing happens.

Any idea what is going on?  How do I enable the driver if I can't get into the restricted devices manager?  

NOTE:
In my "other" life as an ASIC designer I use UNIX/linux daily, so I'm adept at _using_ these operating systems but I'm a newbie when it comes to installing/maintaining/updating/etc.  I've been poking around with the package manager, some of the command line tools (dpkg) etc. and am starting to understand what is going on, but any info. or replies should take into account that I don't really know WTH I'm doing on the system maintence side.  I'm very comfortable using various shells, running scripts, using the command line so if I have to get down-n-dirty I can.  I just need to be pointed in the right direction.

Thanks for your help and patience!  I'm also new to the forum so please tell me if I'm doing something wrong.

---

### Post by devosion on 2007-11-24
When I run sudo apt-get install nvidia-glx-new im receiving this error:

> After unpacking 15.2MB of additional disk space will be used.
(Reading database ... 99944 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Also my video card isnt on the list. It's a GeForce 8500 GT, but im guessing since all the GT series are in the driver 9755 list that this is the driver I need to be downloading.

Gave Envy a shot and got nowhere. Retried installation of the software package and was given the same error again.

---

### Post by bwallum on 2007-11-25
xorg-driver-fglrx refers to an ATI Radeon card driver. It appears you may need to remove this first if you want to install a nvidia driver.

Use 
System>Administration>Synaptic Package Manager

Search for xorg-driver-fglrx and uninstall it. Then try to install the nvidia driver.

Regards
Bob

---

### Post by bwallum on 2007-11-25
xorg-driver-fglrx refers to an ATI Radeon card driver. It appears you may need to remove this first if you want to install a nvidia driver.

Use
System>Administration>Synaptic Package Manager

Search for xorg-driver-fglrx and uninstall it. Then try to install the nvidia driver.

Regards
Bob

---

### Post by corono on 2007-11-25
Thx alot m8! works like a charm :)

---

### Post by mazzi on 2007-11-28
Hi 
Do you have this guide for Ubuntu 7.10 ??

As you can see from my post counts I am a fresh newbie to this linux world. I have installed the 7.10 on my laptop and I tried to update everything. Then a pop up came up said nVidia  driver is restricted so I clicked on it and installed it, 

After restart this bloody white/black screen comes and I think it tries to optimize the video card but after couple of minutes it doesn't change. It seems that I can switch to terminal but I have no idea what  to do after I get there?!!

I fresh installed the Ubuntu for three times and installed the nvidia driver after each time! still no luck!

I am really enjoying ubuntu and I kinda expected these to happen, but this one I have no idea and online guides are too way advanced for me!

Thank you

---

### Post by drphibes52 on 2007-11-29
Hello,
I've been trying to install Nvidia driver support in Ubuntu 7.10 with no luck. My card is a BFG   -made Nvidia 7800 GS AGP card. I'm using a standard Intel motherboard with no overclocking anywhere. Ubuntu asks me if I want to use the restricted driver. I tell it to do so. Ubuntu says that everything is working. But when I run a 3D application it is extremely slow - I can watch things run frame by frame. Tried Envy - no luck there either - same result; slow. What can I do about this?

Thanks in advance for your help.

---

### Post by DJ_Peng on 2007-12-04
> **carlinuxlearner said:**
> Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

THANK YOU for this link! I decided it was time to ditch the dual boot with WinXP but rather than simply blow away the partition I'd do a full reboot, but the newer version of Envy gave e problems galore and I didn't have this older deb saved anymore. I ended up going back to Feisty (which I knew worked) and doing a distro upgrade and the older version of Envy is the only thing that would get my old GeForce 2 card to work right. I only wish I had seen this a day earlier. It would have saved me a ton of time and I don't know how many reinstalls trying to get the damned thing to work. I definitely owe you a beer.

---

### Post by runemaste644 on 2007-12-18
What commands would i run to get my nvidia kernel modules (nvidia.ko)back? Somehow they got lost and even after installing nvidia-glx-new again it still wont work.

---

### Post by sergiom99 on 2007-12-28
Hi.
I installed Kubuntu 32bit in an HP DV6646us laptop. 
When finished I only get to boot to the console, no graphics.

How can I enable the restricted drivers from command line, since I cannot use the restricted drivers manager???

Thanks for your help!

---

### Post by dimmubodom84 on 2008-01-13
**[SIZE="2"]HELP!!![/SIZE]**
Ive been trying to install the drivers for the NVIDIA GeForce Go 7150M but haven't had luck with it, would this website help me?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I have tried many times and i just keep getting an error saying:

*"Envy Error: Envy does not recognise your card as compatible with any version of the driver. this might happen because either your card is not supported by the driver or envy's hardwaredetection failed. you can try the manual installation at your risk."*
 
But when i do it manually I get a blue screen when rebooting can someone help me please :confused: 

_**Computer Specs:**_
**Product Number **GS726UA#ABA
**Microprocessor** 1.7 GHz AMD Athlon 64 X2 Dual-Core Mobile Technology TK-53
**Microprocessor Cache** 512KB L2 Cache
**Memory** 1024 MB (2 x 512 MB)
**Memory Max** Up to 4 GB
**Video Graphics** NVIDIA GeForce Go 7150M
**Video Memory** Up to 559 MB
**Hard Drive** 120 GB (5400 rpm)
**Multimedia Drive** SuperMulti 8X DVD±R/RW with Double Layer Support
**Display** 17.0" WXGA+ High-Definition BrightView Widescreen Display (1440 x 900)
**Fax/Modem** High speed 56K modem
**Network Card** Integrated 10/100BASE-T Ethernet LAN
**Wireless Connectivity** 802.11b/g WLAN
**Sound** Altec Lansing speakers
**Keyboard** 101-key compatible with scroll bar and integrated numeric keypad; 2 Quick Launch Buttons-HP Quick Play
**Pointing Device** Touch Pad with On/Off button and dedicated vertical and horizontal Scroll Up/Down pad
**PC Card Slots** One ExpressCard/54 slot (also supports ExpressCard/34) 
**External Ports** 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards 
• 4 Universal Serial Bus (USB) 2.0 
• 1 Headphone out w/SPDIF Digital Audio 
• 1 microphone-in 
• 1 VGA (15-pin) 
• 1 TV-Out (S-video) 
• 1 RJ-11 (modem) 
• 1 RJ -45 (LAN) 
• 1 notebook expansion port 3 
• 1 IEEE 1394 Firewire (4-pin) 
• 1 Consumer IR 


I Installed Ubuntu 7.04 on my laptop and everything seems stretched out, Im not sure if installing  NVIDIA drivers would help . someone please help. :(

---

### Post by sergiom99 on 2008-01-14
Hey there.
Check this post: [http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

Read the WHOLE thread, as this issue is discussed several times along the way.
I managed to install Nvidia drivers in my laptop (same card) but i use Kubuntu. Should not be very different since the post is about Ubuntu.
I installed it from the alternate CD and got no drivers, ran dpkg-reconfigure and selected VESA, got into Kubuntu and enabled restricted drivers.
In a previous install I managed to install envy following the link you posted, but it stopped working after several updates and need to do all that again everytime. So I made a clean install and found out the method I told you here, using restricted drivers.
Anyway, all you need to get your stuff working is on that post. I managed to do so and I am a noob!
Good luck dude.

---

### Post by CamaroSSMan on 2008-01-23
Hi Mr. Malone or anyone who can help,

I have tried to contact you via E-mail but have received no response. I have tried your program on my Ubuntu Linux box but it is not working. I have a NVIDIA 5200 PCI card in an old P3 that I am trying to use Linux on. I have tried setting the PCI as the primary display in the BIOS but when I boot off the latest Ubuntu DVD or boot off my HD with a fresh install & Updated version of Ubuntu I got nothing but a blank (not turned off) screen after the boot splash when the monitor is attached to the PCI card. I am trying to be able to use some 3d screen effects. I have been posting in this forum as well if you need more info. I have installed Envy but there is still no change. [http://ubuntuforums.org/showthread.php?t=673438](http://ubuntuforums.org/showthread.php?t=673438)

Thanks in advance if you or anyone can figure this out.  :confused:

---

### Post by atari130xe on 2008-01-27
I did a fresh install of Ubuntu Gutsy and Envy my box works ok but I can´t get to work 3D acceleration, what I should do? thanks!

---

### Post by atari130xe on 2008-01-27
I did a fresh install of Ubuntu Gutsy and Envy my box works ok but I can´t get to work 3D acceleration, what I should do? thanks! 

I have an GeForce 6200 128MB Ram Nvidia Chip and Envy did install the latest driver from Nvidia site 169.09

---

### Post by shwagpo on 2008-01-29
Okay, I have been digging for a few hours after having had tried to download from the restricted device manager, rather than envy.
I have a Geforce FX 5200(256 MB PCI), and all I get is blue screens unless I go recovery(gives me the error sreen and i cant read it.)

I have been trying to figure this out, and think I tried nearly everything so far up to here, perhaps I missed something.  I have purged and downloaded, downloaded ad purged, I had this question though(as VESA is not starting me up in the gui, it's all going error)

I changed my Xcon file driver to nv, and that is where it is now

Can i download the driver from the site direct like it says in this quote 
> 
2.2
In a terminal window type "lspci | grep VGA" find the part that has these around it "[ ]", write down what it says then go here 
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) 
If the name of your graphics card is in the list (such as "Geforce 6800") then download this driver to your Desktop
[http://us.download.nvidia.com/XFree8...14.19-pkg1.run](http://us.download.nvidia.com/XFree8...14.19-pkg1.run) 
(if that link is old go to this page to get driver) 
[http://www.nvidia.com/object/linux_d...100.14.19.html](http://www.nvidia.com/object/linux_d...100.14.19.html) 
(if that link is old, go here and select the driver that starts with "100")
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).



2.5
Restart your computer! At the Grub boot menu (if it doesn't pop up click ESC before it's to late) and select the "recovery mode" kernel, and hit enter!

2.6
Once booted, type in "sh /home/yourusername/Desktop/NVIDIA" but DON'T HIT ENTER!!
(replace "yourusername" with your user name) 
click the TAB button on your key board twice, and it should fill out the rest of the name for you, 
THEN hit enter.

and continue from there a la recovery mode.  My card is on the list in the first link.  And if so, what do I need to put into the terminal to get it to download and install, then (hopefully) get it working.  When I am not in recovery, I cant even see what i am typing.

---

### Post by rykel on 2008-02-02
Hi all,

Is there a similar ENVY thread for Gutsy?

Anyway, I have installed NVIDIA 169.07 successfully via ENVY, but now there is a new version 169.09 from the company.

How do I upgrade to the latest one using ENVY?

(Tried uninstalling and installing through the ENVY dialog, but it still installed only version 169.07)

---

### Post by dmacdonald111 on 2008-02-24
I followed the instructions using Envy, and everything installed perfectly. No errors, no warnings, all the effects worked (wobbly windows, desktop cube, etc.) and I was running with a minimum of 2,500 fps with glxgears.

That was yesterday. Today, I come to my computer, turn it on. No updates, no installation, nothing changed at all and it is running SO slow. I mean grindingly, painfully slow. glxgears announces a total of 17 fps!

I managed to (after 4 restarts) to turn off the desktop effects, but it is still unusable. Click, wait. Click, wait - that's what I expect from windoze. Not ubuntu.

My system: 3.06Ghz, 2.5Gb Ram, 1Gb Nvidia GeForce 8500GT, Feisty.

Also, the whole reason I bought an nvidia graphics card in the first place (only had it two days :D ) was that everyone kept saying how much better and easier it was to use in ubuntu as it "just works". Yeah, and if I can't get this working properly, then I'll go back to my 128Mb ATI card which had no problems installing and worked like a rocket compared with this one!

Any help or suggestions greatfully received.

Thanks!

---

### Post by superbiskit on 2008-05-30
> **dannyboy79 said:**
> .... Also, there is a bug possibly with the FX5900 and FX5700 so we could maybe try this out to see if it helps since your card is pretty similar to those 2.  do these commands:
```
gksudo gedit /boot/grub/menu.lst
```
look for this line, #defoptions=quite splash

I suppose I'm being a stinker, but he will probably have better luck if he spells it 'quiet'.
> **dannyboy79 said:**
> ....
if it start with "kernel" than make sure splash is gone. You won't have a pretty splash screen anymore but if you want nvidia driver and 3d acceleration than that's the price to pay.

Is this specific to a bug in those specific cards? If the cute splash screen is messing up nVidia in general, we need to be warned!  Blundering around, I saw someone post instructions for patching and flashing the firmware. Only for those with a strong constitution!

---

### Post by superbiskit on 2008-05-30
> **dannyboy79 said:**
> Yeap, that's exactly what had happened to me, ...
Man, I'm so relieved I'm not the only one!! Despite what my wife believes.
Would it not make sense to file this as a bug in APT? Or in the packaging.  If the kernel is upgraded to -16 and the restricted-modules (or one of the others like linux-ubuntu-modules) remains at -15, we would be better off if it broke the older package!

All it should take (I think) would be 
Conflicts: linux-generic < 2.6.22-15, linux-generic > 2.6.22-15

Just a thought. Anyway, a HUGE THANK YOU, especially to dannyboy79 and tseliot.  I may even be sane again by Tuesday.

---

### Post by drick55 on 2008-07-14
Followed the instructions to method 1 on my Mythbuntu 8.04 install. Worked great, got TV-out working now, was using an ATI card that just became a pain to get the TV-out working, so swapped to the NVidia, but needed the drivers.

Thanks very much tseliot.

---

