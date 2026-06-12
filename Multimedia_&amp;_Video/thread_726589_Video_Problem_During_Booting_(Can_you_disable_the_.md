---
title: "Video Problem During Booting (Can you disable the boot GUI?)"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by Pseudonomous on 2008-03-16
Hello,

This is not a crucial problem, since my system remains operational, but it is annoying to me.  When I boot an Ubuntu/Kubuntu/Xubuntu live CD on another computer, it loads a little graphic while it's booting the kernal.  My laptop displays a nice little graphic plus a list of what the system is doing as the kernal boots, but after my desktop get's past the grub loader stage of booting, it just goes to a blank screen.  I also swear it takes longer to boot than my old Pentium II does (running a server install of Ubuntu plus fvwm as a window manager)  After the system starts GDM (or KDM) it works fine.  I believe my computer has difficulty displaying the boot/shutdown images and that's why the screen goes blank for 3 or 4 minutes while booting. 

I'm not actually that interested in fixing the computer so it loads the little graphic while booting, I'm more interested in mucking around with the system so it doesn't display it, just the the terminal, until it finishes booting and starts KDM (or GDM)  Can anybody tell me how to do this?

THANKS!

PS

I have a pentium IV running Ubuntu 7.10 w/ both the Ubuntu and Kubuntu packages installed (it did the same thing with edgy eft ) with an intel 8284 G / GL graphics controller, for anyone curious about the apparent hardware problem.

---

### Post by Existentialist on 2008-03-16
To eliminate the splash screen edit:

/boot/grub/menu.lst

Near the bottom you should see the kernels, remove the parts in bold:

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8e8ae-d388-41d8-bdfb-3119113b0f96 ro **quiet splash**
initrd /boot/initrd.img-2.6.22-14-generic
**quiet**

So it will look something like:

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8e8ae-d388-41d8-bdfb-3119113b0f96 ro
initrd /boot/initrd.img-2.6.22-14-generic

Save this, and then on shutdown and startup you will not see the splash screen.

---

### Post by Pseudonomous on 2008-03-17
Thank you very much, I will try this as soon as I get home

---

### Post by Pseudonomous on 2008-03-19
Worked like a charm and it has improved my boot-time noticeably.

---

### Post by Existentialist on 2008-03-19
Glad it worked for you.  Just as a note, any time a new kernel is released, you will need to go back and edit the file again to remove the splash screen from the new kernel when booting.

---

### Post by mcduck on 2008-03-19
> **Existentialist said:**
> Glad it worked for you.  Just as a note, any time a new kernel is released, you will need to go back and edit the file again to remove the splash screen from the new kernel when booting.
No, you don't. You just need to edit the default settings in the menu.lst file as well as the active kernel line. In this case the important line is the one with "# defoptions=quiet splash".

When the menu.lst file is recreated during kernel updates the settings under default options are used.

Anyway, the actual problem here is probably just that usplash is trying to use wrong resolution, can't find splash screen images for it and therefore only displays black screen and slows the boot down. While disabling the splash completely of course fixes the boot speed, you could just as well fix the actual problem by editing the usplash configuration file (/etc/usplash.conf)to use correct resolution, and then run "sudo update-usplash-theme usplash-theme-ubuntu".

---

### Post by RazielSedai on 2008-03-25
> **mcduck said:**
> Anyway, the actual problem here is probably just that usplash is trying to use wrong resolution, can't find splash screen images for it and therefore only displays black screen and slows the boot down. While disabling the splash completely of course fixes the boot speed, you could just as well fix the actual problem by editing the usplash configuration file (/etc/usplash.conf)to use correct resolution, and then run "sudo update-usplash-theme usplash-theme-ubuntu".

I've been having this exact same problem ever since I got a widescreen monitor.  Is there a specific resolution that's best to be used, or should it be the maximum for the monitor?  I've tried a bunch of different resolutions and none of them seem to work.

---

### Post by Pgi947 on 2008-03-25
The reason it is taking forever and a day to boot from splash is due to the splash resolution, you just need to edit the splash file properties and set it to a lower resolution, something like 1200x800... had the same issue on my laptop.

Try the following...

sudo gedit /etc/usplash.conf

Then edit settings as follows:

yres=1280
xres=800

---

### Post by stanz on 2008-03-25
Thanks for that!
I just did a fresh install to 7.10 and noticed the lack of splash.
This happened on my GW Notebook and GW box @ home -- with both
KDE & Gnome 7.10.

Again - thanks for the fix!!


:guitar:

---

