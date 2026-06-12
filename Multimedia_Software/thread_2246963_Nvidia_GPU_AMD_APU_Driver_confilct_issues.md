---
title: "Nvidia GPU AMD APU Driver confilct issues?"
date: 2014-10-04
forum: Multimedia Software
---

### Post by cfultz on 2014-10-04
Hello Ubuntu Forums! I have searched high and low and seem to be like the only person in existence to run into this issue. 

I recently installed Ubuntu 14.04 on my custom built PC due to most of my games moving from strictly windows to SteamOS+Linux. Figured lets go ahead and cut the ball and chain. I have been running Linux on my work system as well as my laptop for well over two years and have become extremely comfortable with it, so the installation and transition isn't the huge thing, or so I thought. When I attempted to install 14.04 at first with my Nvidia 650 Ti (EVGA) still installed and powered on, I would get a garbled white, green, red, and blue screen, and that's it. Kept trying to load the installer instead of "Trying before I buy" to only result in the same thing.

Now, when I would disconnect the Nvidia GPU and hook into the on board AMD APU (AMD A10-5800K Trinity Quad-Core) everything boots up and installs just peachy. I tried after a successful installation and upgrade to hook the Nvidia card back up, this time it boots to a black screen and sits, however,  I am still able to access CTRL+ALT+F2. After browsing around and installing the latest Nvidia drivers from the PPA found on StackExchange ([http://askubuntu.com/questions/464354/update-nvidia-drivers-with-xorg-edgers-ppa](http://askubuntu.com/questions/464354/update-nvidia-drivers-with-xorg-edgers-ppa)) rebooting, removing, and all that fun stuff, there was no change. Spoke with a friend and he said to try and downgrade to 12.04 to see if the problem still exists. 

Well, it totally does but I am able to RDP in to it. I have tried to install the Nvidia drivers via RDP since I couldn't get it past the black screen of death to no avail. 


I'm at a loss Ubuntu Community. I've tried tons of stack exchange articles, guides on here, as well as other sites. I'm not sure what to do at this point other than order an ATI GPU and hope it works better... Any idea of what I need to do or where to proceed? I can provide logs if need be.

My Build:
Mobo: Asus F2 A85-M Pro
CPU: AMD A10-5800K Trinity QuadCore APU (AMD Radeon HD 7660D on board graphics)
GPU: Nvidia GTX 650 Ti
RAM: 2x G.Skill 8GB
HDD: Seagate 1TB

---

### Post by QIII on 2014-10-04
Hello!

Does you motherboard offer the option to disable the on-die ATi GPU on the APU and use the PCI-e GPU only?

---

### Post by cfultz on 2014-10-05
Hello!

Yes, it does have that option and it has been set to not activate with the PCI GPU installed. That's what's puzzling. Ubuntu still sees the ATI device even with the Nvidia GPU hooked in (or at least it is showing that through RDP).

---

### Post by khPWXxF on 2014-10-05
I had terrible problems with both an old pentium system with an 8400 board and with my mythbuntu amd system with onboard 8300.  Could not even support a terminal session. 

I concluded that the nvidia 311 drivers were incompatible. 
Fixed by

sudo apt-get update
sudo apt-get install nvidia-304

hth
Phil

---

### Post by cfultz on 2014-10-05
> **khPWXxF said:**
> 
sudo apt-get update
sudo apt-get install nvidia-304



I have attempted this now Phil. Won't believe it, same problem...


EDIT: 
Now, I reverted the change and tried to reinstall it (thinking I screwed something up) and received this:

> nvidia-304-updates : Conflicts: xorg-driver-binary


Double Edit:

When passing a 'nomodeset' in the grub, I am able to boot into the system using the PCI card but I still cannot set the desired drivers for the device...

[[IMG]http://i.imgur.com/6sRD2x8l.png[/IMG]](http://imgur.com/6sRD2x8)

Final Edit and solve: Went back and checked the BIOs yet again, there was a sneaky hidden setting three tree menus down that would disable all on board graphics... as soon as I set that, I'm able to boot just fine. Stuck at 1024x768 right now, but as far as the boot issues are concerned, they are fixed. 

Thanks for the help group!

---

