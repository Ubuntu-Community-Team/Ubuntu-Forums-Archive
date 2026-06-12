---
title: "nvidia twin head gutsy - can't get monitor working"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by tenjin on 2007-11-08
Hi,

Dell Dimension 9200
nVidia GeForce 7900GS
Dell 20" LCD running on DVI at 1600x1200
Benq 17" LCD running on VGA at 1280x1024
Intel Core 2 Duo
4Gb RAM
Gutsy Gibbon on a clean install
Dual boot with XP Pro

I have just done a clean install of Gutsy. I can't get my nVidia card working properly in single or twin head modes.

In a nutshell, I have installed the "restricted driver" nvidia driver and switched it on. When I do I'm forced to reboot, after which I get a crashed X server that will only run in "low resolution mode". Looking into it I see that it has switched to the bog standard VESA driver.

Switching back to NVIDIA from the low-res mode config window pull down gives me the "nv" driver rather than the "nvidia" driver. Manually editing the Xorg.conf file to use nvidia results in a working monitor on one side but I can't use nvidia-settings, I can't turn on the restricted driver, and I can't get the second monitor working.

Basically, the xorg.conf file is mashed by the Gutsy config utilities.

I've tried pasting in one from another posting here, but it didn't work. As soon as I get the nvidia driver working and then try to pull in the second monitor it reverts back to VESA.

Also, I need to make the DVI monitor the primary, but it keeps choosing the VGA monitor as primary. Help...

This is the worst graphic card problem I've had in over ten years. Fiesty seemed to work okay...

Any ideas? Someone suggested using "envy". Where would I get that from?

Cheers

D.

---

