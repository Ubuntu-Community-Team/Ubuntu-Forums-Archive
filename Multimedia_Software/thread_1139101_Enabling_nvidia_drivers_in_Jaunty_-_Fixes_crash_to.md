---
title: "Enabling nvidia drivers in Jaunty - Fixes crash to terminal"
date: 2009-04-26
forum: Multimedia Software
---

### Post by ed-koala on 2009-04-26
I've seen a number of people who had this problem, so here is a solution that worked for me, tho it is involved ...

My equipment:

Asus M3N72-D motherboard
AMD Phenom 9950 Quad-Core Processor
8 gb RAM
2 Samsung HD501LJ 500gb hard disks
Dual GeForce 9800 GTX+ video cards

First, open Synaptic and make sure the following packages are installed:

make
gcc
build-essential
dkms
linux-headers-2.6.28-11.42 (assumes you use the current kernel)
linux-headers-2.6.28-11.42-generic
linux-generic
linux-headers-generic
module-assistant

Next, make sure the following are NOT installed, and use the "Mark for complete removal" option if any need to be removed:

ALL nvidia pkgs (search for nvidia)
Any old kernel pkgs, ie linux-headers-2.6.27-X and earlier
(This might not be necessary, but I did it anyway)


Now, perform the following command in a terminal:

sudo lspci | grep VGA

The output will look something like this:

02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GTX (rev a2)

Write down the number begining each line (the 02:00:0 and 03:00:0 or whatever your output shows).

Go to System-Administration-Hardware Drivers and choose 180.44 and activate the driver - DO NOT REBOOT yet!!!

<If you have nothing to activate in hardware drivers, then go to Synaptic and install:>

nvidia-180-lidvdpau
nvidia-180-kernel source
nvidia-settings
nvidia-common


Open terminal and type:

sudo gedit /etc/X11/xorg.conf

Replace the graphics "Device" section with the following:

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:1:0:0"
Driver "nvidia"
EndSection

Edit the BusID line to reflect the number you wrote down earlier (for me, that would be "PCI:2:0:0". ***MAKE SURE*** you use all colons as shown (the original line you copied had a period before the last zero), and add the PCI part as shown.

If you have sli, add the following line after the driver line:

Option "sli" "auto"

Save the file, reboot and you should have 3d graphics working.

***NOTE*** - for dual graphic card PCs, you may boot to a black screen but you'll hear the normal boot sounds. If that happens, use the other number you got from earlier OR plug your monitor into the other card.


This got Nvidia's restricted driver working for me after a number of other solutions failed.  After this, upgrading within Jaunty releases should go smoothly, but save this in case the next OS update screws you again.

---

### Post by hoodaman on 2009-04-26
You are such the man. I followed this to a T and got my SLi setup working like a champ. May all your days be filled with the same happiness your knowledge has given me.

Thanks a ton

---

### Post by ed-koala on 2009-04-26
I'm glad it helped. I'm not sure all that is absolutely necessary, but it does work, and your PC can see the restricted drivers, AND it should update fine in the future.

---

### Post by rmjohnson144 on 2009-04-27
Sweet, I got it to work just fine after only a dozen reinstalls and a whole day.  here's a couple things I did differently.

I used a shortcut I learned when having issues to uninstall all the nvidia programs from synapic package manager with this terminal command:```
sudo apt-get purge nvidia*
```

I downloaded and installed the latest nvidia drivers from nvidia's website (182.51), instead of installing the built in Hardware Drivers.

Thanks much
-=Mark=-

---

### Post by Ticketoride on 2009-04-27
> **rmjohnson144 said:**
> I downloaded and installed the latest nvidia drivers from nvidia's website (182.51
Where are you getting the 182.51 Driver from?

I can only find [v.180.51]("http://www.nvidia.com/object/linux_display_ia32_180.51.html")...

---

### Post by ea185028 on 2009-04-27
Hello All,

This is my first time posting here in Ubuntu forums and first time using Ubuntu..

Im not even sure if i should post my question here:

Anyway just installed 9.0.4 and everything works fine.. My question is how do i know that my SLI is already enabled?

I mean everything is fine like i can browse internet, watch movie but i dont know if Dual SLI is already enabled..

Is there a way to know this?

Thanks to All

---

### Post by ed-koala on 2009-04-27
> I downloaded and installed the latest nvidia drivers from nvidia's website (182.51), instead of installing the built in Hardware Drivers.

The reason I don't recommend using the Nvidia site's driver is if you do that install manually, when your kernel upgrades you have to reinstall it, it won't update automatically.  Using the repo solves this.

As for how to check sli, if you peek in your etc/X11/xorg.conf file, you may see a line like this:

```
Section "Device"
     Identifier      "Configured Video Device"
     BusID           "PCI:1:0:0"
     Driver          "nvidia"
     Option          "sli" "auto"      <<===========================II
EndSection
```

If it's not there, you can add it and reboot, then it'll be working if it's hardware enabled.  You can check it by going to Systen - Administration - NVIDIA X-Server Settings

---

### Post by rmjohnson144 on 2009-04-27
> **ed-koala said:**
> The reason I don't recommend using the Nvidia site's driver is if you do that install manually, when your kernel upgrades you have to reinstall it, it won't update automatically.  Using the repo solves this.

I didn't know this.  Maybe I'll use the repo next time.
although reinstall of driver is really painless if it doesn't screw up all these quirks that were fixed and it is nice having the latest drivers.  

> As for how to check sli, if you peek in your etc/X11/xorg.conf file, you may see a line like this:

```
Section "Device"
     Identifier      "Configured Video Device"
     BusID           "PCI:1:0:0"
     Driver          "nvidia"
     Option          "sli" "auto"      <<===========================II
EndSection
```

If it's not there, you can add it and reboot, then it'll be working if it's hardware enabled.  You can check it by going to Systen - Administration - NVIDIA X-Server Settings

Maybe that's why I needed to add the BusID line on my system.  I use my rig mainly for folding as it's my backup machine.  or maybe the release didn't put this feature in by mistake and is the main cause of issues?

anyway, thanks again
-=Mark=-

---

### Post by jonboy99 on 2009-04-29
Cracking post mate, sorted it for me.  I'll just add the following so searches will find this thread - many people I think like me didn't realise it's the SLI that is causing the problem, and get the following error when trying to boot:

Kinit: name_to_dev_t(/dev/disk/by-uuid/3c7a8f65-b709-494a-92f1-318a38220def)= sda5(8,5)
kinit: No resume image, doing normal boot...


And googling that doesn't suggest anything about the SLI fix, so hopefully this thread will bring the two problems together for SLI users.

---

### Post by rmjohnson144 on 2009-04-29
> **jonboy99 said:**
> Cracking post mate, sorted it for me.  I'll just add the following so searches will find this thread - many people I think like me didn't realise it's the SLI that is causing the problem, and get the following error when trying to boot:

Kinit: name_to_dev_t(/dev/disk/by-uuid/3c7a8f65-b709-494a-92f1-318a38220def)= sda5(8,5)
kinit: No resume image, doing normal boot...


And googling that doesn't suggest anything about the SLI fix, so hopefully this thread will bring the two problems together for SLI users.

I don't run SLI, but I have two video cards I do folding at home.  I left the sli part out.  so it seems with any dual card setup, this may be the solution.

---

### Post by ed-koala on 2009-04-30
I'm just happy I'm able to give back to the forums that have helped me so much.

I thought I'd take a moment to explain why the procedure is as long as it is ...

Removing the nvidia packages - Pretty self-explanatory, gives a fresh slate to work with.

The packages listed to install - These come from nvidia's instructions (or they did at the time I first did this).  They assure if you have a kernel change, packages needed to rebuild the drivers are available.

Xorg,conf - One of the biggest problems.  This file never seems to get automatically done correctly.  People with dual monitors (with or without SLI) absolutely need to edit this.  I found this info in another post here on the forums.

And, as mentioned previously, using the repositories and not doing a manual install allows Ubuntu to upgrade automatically if your kernel upgrades.

Here's hoping Linux spreads faster than the swine flu!!!

---

### Post by rmedved on 2009-05-07
Hey, I am pretty new to linux and I had a good system up and running on a computer I was borrowing. However after a fresh install of 8.04 on my old crappy emachines computer, I have been unable to install the nvidia driver. I have been trying to figure it out for almost a week now and have tried several how tos on the forums where other people seemed to be having success. I had the most success following the instructions of this thread: [http://ubuntuforums.org/archive/index.php/t-763236.html](http://ubuntuforums.org/archive/index.php/t-763236.html) I was able to install the driver provided on the nvidia website and had 3D graphics enabled, however once I rebooted I got nothing but a blank screen at login. 

I found this how to and got excited since it had instructions I hadn't seen on others, namely installing module assistant and identifying the busID. I thought for sure this was going to solve my problem but low and behold, once I rebooted I was once again greeted with the nasty blank screen that I have come to hate so much. I'm beginning to think that there is something very simple that I am overlooking or something I simply don't know that is causing my problem. 

Can any body out there please help me? I am about to throw my computer out the window (I would but I am too broke right now to buy a new one).

Cheers

---

### Post by rmedved on 2009-05-07
PS
I followed the instructions here once with no success. Then a second time after upgrading to Jaunty, still no success.

---

### Post by rmedved on 2009-05-07
here is my current xorg.conf:

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    BusID        "PCI:00:05:0"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by Unhban on 2009-05-07
Can I just confirm a couple of my thoughts? I'm running a Geforce4 MX460, quite an old card, but using the normal Nvidia driver X hangs at the login. So using this method sounds good and looking forward to trying it.

But.... the Hardware Driver says that 96.43.10 is my recommended driver for this graphics card, so I presume I let it go ahead with that?

I looked up the wiki for SLI :) and presume I don't need to put that line in for my card?

As you can perhaps tell I'm quite a newb, and this is the only thing that doesn't work on 9.04.... otherwise, loving Ubuntu!

Unh.

---

### Post by mosaic2s on 2009-05-07
am working with 
GeForce 6100 nForce 405.

The system reads the driver. Gives the correct display but unable to save to xorg.conf.

Am working on it.

btw, jaunty usb stick is cool.

---

### Post by Unhban on 2009-05-07
Well I went ahead with my presumptions, but... computer says no - X and the whole machine hung again at the login (actually the 9.04 backdrop login image starts to load then it all hangs, so I wonder if that is affecting it somehow!). So anyone with comments would be greatly appreciated!

BTW ed-koala, there's a small typo in your original post - the line should be:

**nvidia-180-libvdpau**  not  **nvidia-180-lidvdpau**

and I seem to have picked up the idea that with *gedit* you should use  **gksu** and not  **sudo**  because  **sudo**  uses user permissions and not root permissions which can screw things up when saving, apparently! :)

Unh.

---

### Post by rmjohnson144 on 2009-05-07
> **rmedved said:**
> here is my current xorg.conf:

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    **BusID        "PCI:00:05:0"**
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

You might double check that pci line.  you can use nano to edit the xorg.conf file if you have no gui.

```
sudo nano /etc/X11/xorg.conf
```

good luck
-=Mark=-

---

### Post by Unhban on 2009-05-07
Thanks for the good wishes Mark, I need em! :)

My xorg.conf is:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:1:0:0"
Driver "nvidia"
EndSection
----------------------

The BusID line concurs with what I got when running the command  **sudo lspci | grep VGA** to find out about the MX460.... I got:

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 460] (rev a3)

I just wonder about:

Option	"AddARGBGLXVisuals"	"True"

Unh.

---

### Post by rmjohnson144 on 2009-05-07
Did you try removing that line?  also, with that old of a card you may not need the BusID line if you want to give that a try.

Not sure what else to suggest to try.  I'm still a linux newb and wouldn't have gotten my card working without this thread.

-=Mark=-

---

### Post by Unhban on 2009-05-08
Grrr... just tried what you suggested about removing that line, then just removing the BUSID line, then removing both and on each occasion computer says no i.e. hangs at the login screen.

I wouldn't be so fussed but I need the 3D acceleration to run Wine properly... :sad:

I just wonder if there's some command line command that will look at the card and the NVidia driver and say 'Ah yes, this is what you really need in xorg.conf and also these other files too!'.

Unh.

---

### Post by rmedved on 2009-05-08
So I decided that after a week of trying to fix this I would have to concede that Jaunty had officially beat me and I downgraded to 8.04. I am sad to not be running 9.04 but I have 3D graphics again. It's bittersweet. I don't like losing.

---

### Post by futuroimperfetto on 2009-05-09
I have a Dell XPS m1330 with an nVidia 8400 GS and just upgraded to Jaunty. I couldn't use the latest 180.44 driver, because the screen would start flashing at the login screen and then throw me to low-res mode. 

For some reason, I could use the 173 driver (called "basic driver") without a hitch.

I followed ed-koala's instructions from his first post and fixed it! It worked like charm for me.

Thanks ed-koala!

---

### Post by o0pie on 2009-05-09
I wanted to thank the OP for posting this article, I upgraded to 9.04 today and spent the whole day trying various fixes. A few caveats for me. Since I was stuck at the console I could not use the tool synaptic you referred to, further more im a newbie and didnt know what it was, but needless to say it and gedit would not work for me. 

The difference for me was using:

sudo envyng-t

to install the Nvidia 180 drivers and nano to edit the xorg.conf.

Heh, I did get the black screen of death on the the first reboot because I used 2:0:0 instead of 3:0:0.

But I'm seeing at my fist glimpse of the 9.04 login screen on my other machine as I type this post.

Thanks man, now to see if WoW on Wine is all they say it is!

---

### Post by mosaic2s on 2009-05-10
Sorry, it did not work for me. neither have other options for nvidia in jaunty. have filed bug report.

---

### Post by Unhban on 2009-05-10
> **mosaic2s said:**
> have filed bug report.
Any chance of pointing us to the URL please?

Unh.

---

