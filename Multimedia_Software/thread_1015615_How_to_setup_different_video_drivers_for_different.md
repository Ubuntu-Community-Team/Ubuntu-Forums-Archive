---
title: "How to setup different video drivers for different kernels"
date: 2008-12-19
forum: Multimedia Software
---

### Post by binger on 2008-12-19
Hey all,
I am running Ubuntu Studio and have the generic kernel as well as the RT kernel installed.  I also am a dreadful owner of a ATI card on this system.  I don't want to ruin my RT audio system with the FGLRX but I want to use FGLRX for gaming.  Is there a way to setup FGLRX for my generic kernel and the open source ATI/Radeon drier for my RT kernel?

Thanks,
Brian

---

### Post by Ng Oon-Ee on 2008-12-21
Ah, since no1 has taken a shot at this, I'll contribute my 1 cents worth...

I do not think it possible to do what you want to do without some pretty in-depth knowledge of the Linux file-system (specifically you'd have to know whether there are kernel-specific startup conf files). Unfortunately I do not know of such files.

Concerning the video driver, it is set up in xorg.conf. I have not heard of the possibility of 'branching' within xorg.conf itself, so perhaps the solution is to have two different xorg.conf files and a script which links the correct file to the expected /etc/X11/xorg.conf location.

Long-term solution, however, will be to fix whatever issues you're having with FGLRX and the RT system. What's the issues, actually? I use NVidia, always have in Linux, so I'm not aware of what's current in terms of bugs and regressions.

---

### Post by markbuntu on 2008-12-29
I have no problems with fglrx and UbuntuStudio except that after a rt kernel update I sometimes need to run the installer again to load the kernel modules. Nvidia users also seem to have this problem when using the nvidia proprietary drivers.

Nevertheless, I have had some problems in the past with fglrx and UbuntuStudio on intitial install and I found the best way to deal with that is to remove fglrx and reinstall it after installing UbuntuStudio and then everything is fine.

A lot of proprietary driver users have problems with kernel updates because they fail to remove the old driver and its kernel modules when installing a new driver. This results in more than one kernel module of the same name that confuses the kernel builder so it does not load any of those modules and leaves it up to you to do so manually. This is not unreasonable behavior on the part of the kernel.

---

