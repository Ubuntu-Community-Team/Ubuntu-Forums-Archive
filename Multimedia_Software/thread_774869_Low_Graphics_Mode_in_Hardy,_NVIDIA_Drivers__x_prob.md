---
title: "Low Graphics Mode in Hardy, NVIDIA Drivers / x problem"
date: 2008-04-29
forum: Multimedia Software
---

### Post by PenguinXtra on 2008-04-29
I cannot seem to get the NVIDIA Drivers working for my 8600M GT on a new install of Hardy Heron 8.04. On boot the display fails three times, then it defaults to Vesa Display drivers @ 800x600. Any attempt to mess with NVIDIA Settings prompts that I should run nvidia-xconfig under root. This does not seem to help. I found that messing with the /etc/X11/xorg.conf file allowed me to trick the display, but only after reinstalling the drivers. It seems like I am not the only one with this problem, and I was wondering if anyone could shed some light on the subject?

I have done many of the steps listed here:
[http://ubuntuforums.org/showthread.php?t=712479&page=4](http://ubuntuforums.org/showthread.php?t=712479&page=4)

It am able to install the Linux NVIDIA 173 x86_64 drivers on my machine
and after a... 

> 
sudo /etc/init.d/gdm stop
sh NVIDIA-Linux-x84_64-173.08-pk2.run       
sudo /etc/init.d/gdm start


On Gnome desktop start, the desktop will reboot with the new drivers and correct settings. From there I can go and configure the NVIDIA Settings and everything is gravy. On reboot however, the situation resets itself  and the process must be done again for proper video. Anyone have any ideas?

---

### Post by Zorael on 2008-04-29
Curious. Could you post the contents of your /etc/X11/xorg.conf file?


That said, everything you *should* need to do would be:
```
$ sudo su
# mv /etc/X11/xorg.conf /etc/X11/xorg.backup0804
# aptitude purge ~nnvidia
# dpkg-reconfigure xserver-xorg    # to regenerate one
# aptitude install nvidia-glx-new
# nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
Then reboot.


**If it doesn't work,**, do a safe boot and then post the contents of your /var/log/Xorg.0.log.old file. Better yet, choose to go back to the terminal in the bulletproof X menu (or by picking recovery mode at boot), enter this command, scroll down until you find a line that says 'Driver "**nvidia**"' and change it to 'Driver "**nv**"'.
```
$ sudo nano /etc/X11/xorg.conf
```
Ctrl+O to save, Ctrl+X to exit. Don't forget the log file if it doesn't work.

---

### Post by PenguinXtra on 2008-04-30
Yeah it was a no go on those instructions, I will post my old xorg.conf file in a sec.

---

### Post by PenguinXtra on 2008-04-30
For some reason those settings hosed my install, I can no longer ctrl+alt+f2 and I just tryed running a sudo gedit /etc/X11/xorg.conf and it wont open! WTF?!

---

### Post by PenguinXtra on 2008-04-30
Ok here is my old config, if anyone knows how to get my ctrl+alt+f2 console working please let me know.

---

### Post by Curlydave on 2008-05-01
I'm having a similar problem. I uninstalled my graphics driver package to troubleshoot why Quake Wars wasn't working, (probably unrelated in retrospect) then I had the same problem as PenguinXtra after a reboot. When I hit continue, it didn't go into low graphics mode, it froze on a black screen, after briefly showing a low-res X cursor.

I was able to get back into a GUI by selecting recovery mode from the boot menu, then the Fix X option. Gnome started up, without the nvidia drivers, or network support. I rebooted, and it errorred again. I repeated the recovery mode - fix X process, then removed the driver package. All was well in reboot-into-a-working-GUI land, but without nvidia drivers.

I then tried to install the driver from the nvidia website. I killed x, then ran the program using the black-screen console. It said that I should probably set runlevel to 3, and gave me the command. I exited the installer, and ran the command, causing the same error as before. I rebooted, then went into recovery mode, then root terminal. I installed the driver, ignoring the request to change the runlevel. It worked, and booted into a GUI.

The next time I rebooted, it gave me the low-graphics mode error again. I had to go into recovery mode and Fix X again. Here's where I'm at now: If I set up nvidia drivers and reboot, I can't get into a GUI. It doesn't matter if they're the nvidia ones, or the packaged ones. I don't know if the nvidia ones broke it, or if the packages did. I just want working nvidia drivers, like I had initially. It was so easy at first, just installing a package, but now it's broken when I install the same package. :(

How can I cleanly remove any traces of nvidia drivers on my computer, and set up X so it was on a fresh install?

---

### Post by rpkehoe on 2008-05-01
I was having a very similar issue with my geforce 5700.  I finally realized this morning that when I upgraded to Hardy, it did not update menu.lst.  So it ended up that I was loading the gusty kernel, and none of the graphics drivers other than vesa would work.  Once I updated menu.lst to the newest kernel in /boot, everything works.

Good luck

---

### Post by Zorael on 2008-05-01
The xorg.conf looks great. As the above poster mentioned, mind the kernel you're running.

Anyway, to troubleshoot we'll need your **/var/log/Xorg.0.log**, captured *when it's broken*. Alternatively, **/var/log/Xorg.0.log.old**, *the start of X after it was broken*. Else it could be a million things. :<

---

### Post by Curlydave on 2008-05-01
I've attached a copy of the old log file after it was broken. I appreciate any help. :)

---

### Post by Curlydave on 2008-05-01
I fixed it by reformatting. It took me all of half an hour to reformat, reinstall, and set up the basic packages like codecs, video drivers,(working this time) import my bookmarks, and set up btnx.

---

### Post by Akt on 2008-05-01
When I was upgrading from Gutsy to Hardy, it asked me what I wanted to do with menu.lst and I choose, keep the current one.  How do I update the menu.lst with the correct one for Hardy?

---

### Post by Knacker on 2008-05-02
> **Akt said:**
> When I was upgrading from Gutsy to Hardy, it asked me what I wanted to do with menu.lst and I choose, keep the current one.  How do I update the menu.lst with the correct one for Hardy?

This is my question too. How do I upgrade menu.lst to hardy version/kernel? I also (stupidly!) chose to keep most of the other files I was asked about...I'm not sure which ones they were either...they all sounded like configuration files, which I idiotically imagined would replace my desktop and etc. The thing that I'm also wondering about is whether, since menu.lst still works (sort of) with old kernel works, if old kernel (2.6.22-14) and any other old (gutsy) files are still taking up space on my machine...should old kernel and etc still be there? should I delete them?
Please help. My computer is pootched and I need it. Thanks!

---

### Post by rpkehoe on 2008-05-02
$ sudo gedit /boot/grub/menu.lst

Find the entry that looks like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f3394eec-ad89-4d43-9683-ec4fdbc79867 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


Make a copy of the whole section, paste it above the current entry (to make it default) and change it to match your new kernel:

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=f3394eec-ad89-4d43-9683-ec4fdbc79867 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

To double check your kernel version, you can do this:
$ ls -ltr /boot/initrd* | tail -1
-rw-r--r-- 1 root root 8111562 2008-04-27 20:46 /boot/initrd.img-2.6.24-16-generic

Make sure that the kernel and initrd match.

When you reboot it should then default to the new one.

Good luck

---

