---
title: "Feisty upgrade: Failed to load module wfb"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by Huffalump on 2007-04-20
I have searched the forums, asked on irc, and googled around without success.

I did find a bug report which I believe to be relevant at [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)

How are people fixing this problem?   I would really like to have X back, so I can resume computing.

While it should not matter:
- GeForce FX 5600 (AGP)
- It worked just fine under Edgy, when I used ENVY to install
- Yep, had Beryl working and everything
- Upgraded to Feisty and it exploded.

Help?


Post-Mortem Edit:
It appears no one has the brains to solve this, but I wanted to leave some breadcrumbs for others since I know the IRC channel has been flooded with other people having problems with Feisty upgrade knocking their previously working video over the head.  So, kids, it's a bit ugly, but I did find this to be a temporary workaround.

When in recovery mode (at the grub boot prompt), you are automagically logged in as root.  You can issue the following command: 
```

nano /etc/X11/xorg.conf  

```

Don't be scared by the weirdness of how it looks, what you've done is basically open this X configuration document into a text editor.  Use your arrow keys to scroll down to the section that has information on your video card.  It will most likely be a two-line entry looking something like
```

Section "Device"
   Identifier "NVIDIA Corporation NV?? [GeForce ?? ????]
   Driver "nvidia"
EndSection

```

That portion is telling X to use the nvidia driver (which is the best available and the one you probably desire to use, as do I).  But X is broken in Feisty.  So, you're forced to revert to a lower quality driver instead, just to get into your GUI.  To do that, change "nvidia" to be "nv" and then save the document (CTRL+O for "WriteOut"/save).  Exit (CTRL+X).  At the command prompt, type reboot.  When your system comes back, just select your normal grub entry (not recovery mode).

From there, you're back into the gui until you can find a genius to help get the correct drivers working.  It's not the best solution, but it will get you back to work on crutches.

IF anyone has the REAL solution on how to fix this Feisty upgrade problem, please let us know!

---

### Post by arthur_kalm on 2007-04-20
I'm having the exact same problem. I have an 8800 GTS here. I've found some information regarding this problem but nothing that resolves it. Any help would be much appreciated.

**Edit**: This is rather frustrating because I can't use my second monitor or use Ubuntu at regular resolution (only at 800x600)

---

### Post by Lykourgos on 2007-04-20
Have you installed nvidia-glx-new?

---

### Post by Huffalump on 2007-04-20
Yes, I started out with nvidia-glx-new which did not work.

Recently, I've been trying nvidia-glx (normal) on another thread, if you're interested
[http://ubuntuforums.org/showthread.php?t=414434](http://ubuntuforums.org/showthread.php?t=414434)

---

### Post by arthur_kalm on 2007-04-20
Well I've gotten past the wfb error. Check out the forth post [here]("https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641"). However, now X fails with the error that it can't find: ```
/lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko
```

I do have nvidia-glx-new installed....

---

### Post by arthur_kalm on 2007-04-20
OK I've fixed that as well, essentailly what I had to do was create a symbolic link to nvidiafb.ko (since that was the only thing on my system with the name nvidia and ko). I did the following:

```

cd /lib/modules/2.6.20-15-generic/kernel/drivers/video
sudo ln -s nvidia/nvidiafb.ko nvidia.ko

```

Viola, it works perfectly. I just tried and compiz is working as well. Hope that helps someone :)

---

### Post by Huffalump on 2007-04-21
You had me hopeful for a moment! :]

But it still fails to work for me.  Here I am on Day 3 of wrestling with this ridiculous problem.  I am becoming quite exasperated and really hope someone can help.  Alright, here's what I did this particular time.

1. Download the nVidia drivers from here: [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)
2. Extract sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -x
3. cp NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 ~/local-configs/
4. sudo ln /home/myusername/local-configs/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules/libwfb.so
5. Changed permission to match other items (i.e., remove execute as program via GUI)
6. chown root:root libnvidia-wfb.so.1.0.9755 
7. cd /lib/modules/2.6.20-15-generic/kernel/drivers/video  AND  sudo ln -s nvidia/nvidiafb.ko nvidia.ko

I still get the following error about n API mismatch for the nVidia kernel version 1.0-9755 but X has 1.0-9631.  Please note that I have previously (more than once) flushed out all my nvidia-glx and linux-restricted modules as seen here: [http://ubuntuforums.org/showthread.php?t=414434&page=2](http://ubuntuforums.org/showthread.php?t=414434&page=2)

Can anyone help further?  I am bordering on insane.

---

### Post by arthur_kalm on 2007-04-21
Huffalump, I'm getting the same error about the API mispatch. I'll update again as soon as I figure it out. Don't go insane :(, just use the nv driver for now...

**Edit:** Hehe, one Google search later and I found [this]("http://www.linuxquestions.org/questions/showthread.php?t=545010"). Basically edit /etc/default/linux-restricted-modules-common and add nv to DISABLED_MODULES like so: DISABLED_MODULES="nv". Reboot (to remove the module from the kernel), and viola :)

---

### Post by jagolis on 2007-04-22
I also am having issues with the related nvidia modules. So far the only combination that I can get to work is the 2.6.20-15-386 kernel and nvidia-glx-new, but that 386 doesn't have SMP. 

I tried what Huffalump wrote, and what arthur_kalm wrote, and I continually get “Error running install command for nvidia.” I think I still have a 6.06 kernel cached, I'm going to try that with the drivers provided by nvidia and see what happens.

---

### Post by jagolis on 2007-04-22
> **jagolis said:**
> I also am having issues with the related nvidia modules. So far the only combination that I can get to work is the 2.6.20-15-386 kernel and nvidia-glx-new, but that 386 doesn't have SMP. 

I tried what Huffalump wrote, and what arthur_kalm wrote, and I continually get “Error running install command for nvidia.” I think I still have a 6.06 kernel cached, I'm going to try that with the drivers provided by nvidia and see what happens.

Well, I thought it had worked at one time... But no longer. I'll have to stick with 1 core until they get this resolved.

---

### Post by arthur_kalm on 2007-04-24
> **jagolis said:**
> Well, I thought it had worked at one time... But no longer. I'll have to stick with 1 core until they get this resolved.

Huh? I'm using the 2.6.20-15-generic kernel. It comes with support for dual cores out of the box...

---

### Post by jagolis on 2007-04-26
Agreed, the generic does, but the 386 specific one refuses to detect my second core.

My list of installed images:
2.6.17-11-generic
2.6.20-15-386
2.6.20-15-generic
2.6.20.15-lowlatency

The nvidia drivers don't work with any one but the 386, either from the package manager or the binary installer.

---

### Post by x1a4 on 2007-04-27
Hi,

Purge **nvidia-glx**: 

sudo aptitude purge nvidia-glx

and install **nvidia-glx-new**: 

sudo aptitude install nvidia-glx-new

---

### Post by et voilà on 2007-05-01
Tx Arthur, my nvidia.ko not found was fixed by:

cd /lib/modules/2.6.20-15-generic/kernel/drivers/video
sudo ln -s nvidia/nvidiafb.ko nvidia.ko

I had an API mismatch also before and I believe I fixed it by verifying that only nvidia-kernel-source was installed (nvidia-glx with a geforce4 mx) and not nvidia-new-kernel-source or nvidia-legacy-kernel-source. They are not uninstalled when you use nvidia-glx it seems (bug?)

Ciao

---

### Post by jagolis on 2007-05-02
To everyone having issues:

I found this on [http://www.nvnews.net/vbulletin/showthread.php?p=1237079](http://www.nvnews.net/vbulletin/showthread.php?p=1237079)

if you have EVER installed nvidia-glx-new at any point in time, it leaves behind a crucial file: /lib/linux-restricted-modules/.nvidia_new_installed

Remove it and then install with the binary drivers.

I have spent hours upon hours fiddling and reinstalling, and that single file was the only thing keeping it from working. I hope this will help other people.

---

### Post by Huffalump on 2007-05-25
> **arthur_kalm said:**
> Huffalump, I'm getting the same error about the API mispatch. I'll update again as soon as I figure it out. Don't go insane :(, just use the nv driver for now...

**Edit:** Hehe, one Google search later and I found [this]("http://www.linuxquestions.org/questions/showthread.php?t=545010"). Basically edit /etc/default/linux-restricted-modules-common and add nv to DISABLED_MODULES like so: DISABLED_MODULES="nv". Reboot (to remove the module from the kernel), and viola :)

Arthur, I wanted to leave some belated thanks for your help.  However, I was never able to get Feisty to work properly.    A few minutes ago, I tried the following on a fresh install:

1. Download the nVidia drivers from here: [http://www.nvidia.com/object/linux_d..._1.0-9755.html](http://www.nvidia.com/object/linux_d..._1.0-9755.html)
2. Extract sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -x
3. cp NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 ~/local-configs/
4. sudo ln /home/myusername/local-configs/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules/libwfb.so
5. Changed permission to match other items (i.e., remove execute as program via GUI)
6. chown root:root libnvidia-wfb.so.1.0.9755
7. cd /lib/modules/2.6.20-15-generic/kernel/drivers/video AND sudo ln -s nvidia/nvidiafb.ko nvidia.ko
8. sudo gedit /etc/default/linux-restricted-modules-common ...and then set DISABLED_MODULES="nv"

The result was no substantive change.  nv still loads in X rather than nvidia, which means Beryl, games, and other thing do not work.  The only difference I saw was that nVidia no longer appears  in the System > Administration > Restricted Drivers Manager which is interesting but does not allow me to use my hardware.

---

### Post by xenobytes on 2007-05-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I experienced similar problems. I found this bug: [98641 ]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641")

In it, there were a couple of posts that were helpful to me: 


> linux-restricted-modules-2.6.20 (Ubuntu) - contain 2 kernel modules : nvidia.ko and nvidia_new.ko

when you install nvidia-glx-new, nvidia_new.ko will be loaded..

kernel module successfully loaded when system is loading, but when X trying to start ... nvidia-glx Xorg driver can't find libwfb driver.

nvidia drivers have 2 part: one for Kernel and one for Xorg Server.

workaround: get file [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html), extract wfb lib.

....

change description of this bug .. linux-restricted-modules-2.6.20 is not affected.
nvidia-glx-new (1.0.9755+2.6.20.5-14.19) - affected

take a look -> [http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=nvidia-glx-new&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=nvidia-glx-new&version=feisty&arch=i386)
this package must contain

usr/lib/xorg/modules/libwfb.so --> sm link to libnvidia-wfb.so.1.0.9755
usr/lib/xorg/modules/libnvidia-wfb.so.1.0.9755 

--- Both from xoco

Basically, (assuming that you have nvidia-glx-new drivers installed and linux-restricted-modules-2.6.20-15 and have set up your xorg.conf correctly) all you need to do to get around X failing to detect your wfb module is:

```
# sh NVIDIA-<version information>pkg1.run -x
```

Then copy out the libnvidiawfb.so.<version> to your /usr/lib/xorg/modules directory and create a symlink to libwfb.so. Make sure that the permissions are the same as everything else in the directory. 

```
# cp NVIDIA-<version info>pkg1/usr/X11R6/lib/modules /usr/lib/xorg/modules/
# ln -s libnvidia-wfb.so.<version> libwfb.so
# chmod 644 libnvidia-wfb.so.<version>
# rmmod nvidia
# modeprobe nvidia
# /etc/init.d/gdm restart

```
And you should be on your way to a splash screen.

Cheers, 

-Gavin

---

