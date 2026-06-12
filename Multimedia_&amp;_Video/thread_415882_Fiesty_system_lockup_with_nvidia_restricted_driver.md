---
title: "Fiesty system lockup with nvidia restricted drivers"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by randomphrase on 2007-04-20
I am having a problem with the "nvidia" restricted drivers. They were working fine on Edgy, but not after upgrading to Fiesty. Also system works fine with the "nv" drivers.

The symptoms are:
- Black screen on startup. Note the monitor does *not* go out of sync. This is not a sync problem, it's just displaying a completely black screen FWICT
- System does not respond to pings
- Existing SSH sessions are frozen

AFAICT this is a complete system lockup.

Same symptoms when starting the recovery console, then using startx. Also, the nvidia modules can be loaded into the kernel using insmod without problem.

Tried both nvidia-glx, and nvidia-glx-new drivers, with same result.

Hardware: Athlon XP 3200+ (running Fiesty amd64), nVidia GeForce 6600GT, Dell 2407WFP.

[Note there seem to be others with similar symptoms in a [separate thread]("http://ubuntuforums.org/showthread.php?t=414187"), but also many others with completely different problems, hence I'm starting a new thread.]

---

### Post by randomphrase on 2007-04-22
OK I have a fix. It's not ideal, but it does at least allow the restricted drivers to load.

Use a kernel argument iommu=noaperture.
 
This was inspired by the [thread here]("http://www.nvnews.net/vbulletin/showthread.php?t=83419"), even though I don't understand the entirety of the situation.

Also it seems that this results in an AGP aperture size of 32MB which is (AFAICT) suboptimal.

No desktop effects yet but will keep working on it.

Hope this helps someone

---

### Post by Cariboo1938 on 2007-10-21
> **randomphrase said:**
> OK I have a fix. It's not ideal, but it does at least allow the restricted drivers to load.
Use a kernel argument iommu=noaperture. ....
Hope this helps someoneI am also having a problem with the "nvidia" restricted drivers. They were working fine on Edgy, but not after upgrading to Fiesty. Also system works fine with the "nv" drivers. The symptoms are, that after using "Restricted Drivers Manager" to enable/install newer nvidia driver and rebooting the system, the GUI doesn't start and I get the message : Failed to start xserver : and a command line prompt to login, I have to change /etc/X11/xorg.conf DEVICE section and replace "nvidia" with "nv" to get GUI back running. I found this message in the "nvidia-bug-report.log"
Quote:
26.150026] AGP bridge at 00:00:00
[ 26.150030] Aperture from AGP @ f0000000 size 4096 MB (APSIZE 0)
[ 26.150032] Aperture too small (0 MB)
[ 26.150033] Your BIOS doesn't leave a aperture memory hole
[ 26.150035] Please enable the IOMMU option in the BIOS setup
[ 26.150037] This costs you 64 MB of RAM

Do you have an idea if your fix would work for me too? 
What would be the step by step procedure to do this:"Use a kernel argument iommu=noaperture"??.

Edit:
I had to edit /boot/grub/menu.lst:

1) Find this section and add "iommu=noaperture":
Quote:
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e4af70f0-d555-49ab-8dd0-687cc3e7f81c ro iommu=noaperture

2) Save the file and type:
Code: "sudo update-grub"

and then 
3) restart  my computer!

BTW:
There must be a conflict between my BIOS (Phoenix Award Ga -K8NS Ultra-939 F5) and the kernel so that AGP aperture is not reported correctly.

---

