---
title: "Trying to get nVidia drivers installed - I am almost in tears."
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by kingbuxton on 2007-05-13
First off I am running Ubuntu 7.04 in VMWare 6 under XP Pro. 

I already tried this [http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126) everything went well until it tried to reboot and I got the old X error - can't start - it isn't setup correctly. 

Redid Ubuntu - tried again - same exact error after everything seemed to work.

Then I tried this [http://browseatwork.com/nph-proxy.cgi/000000A/http/discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://browseatwork.com/nph-proxy.cgi/000000A/http/discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)

Seemed to work fine until the CTRL-ALT-F1 step - Nothing happened - just stays on the desktop.

Been on it all day - tried about three or four ways of installing them - all failed. In fact when I tried running Envy from a console to see what would happen - the menu comes up - I selected 1. Install nVidia drivers and it says it can't find an nVidia card?! I just laughed. I have an 8800Gts.

I really have tried with Linux, I don't play games all that often, I am bored with XP and I can't really be bothered with Vista (until Crysis appears anyway) so figured if I can get it working in VM first, get to grips with it, and then dual boot it. Tried many versions of Linux and always come unstuck on stuff that should be basics.

So here is my question. I go to nVidia.com. I get the latest driver NVIDIA-Linux-x86-1.0-9755-pkg1.run from [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html).

File is saved on desktop.

Can someone please give me a step by step on how to get that installed? Feel free to assume I know absolutely nothing, I wont take it personal. I figured getting VMWare up and running and Ubuntu installed would be the hard part, who knew?

NOTE: I basically know sod all about Linux, so this may be obvious to you guys. But why can't they make the driver a double click install reboot procedure like Windows? Don't shout, I am sure there is a good reason, but this seems a really complex way to do a simple procedure.

Off for some paracetamol - my head is hurting.

---

### Post by forestpixie on 2007-05-13
I'd be inclined to go to the Absolute Beginners Talk part of the forum - there's a good deal in there regarding nvidia - I've just today managed to get mine sorted - tekn a week off and on to get the last little bit done


this helped me at the beginning when I was confronted with 'odd' installation files!!!

[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

Didn't resort to tears but - shouting at the screen seemed to help at one point

Good luck

---

### Post by Aryra on 2007-05-13
Try visiting the restricted drivers panel in the admin section. It might be located there already. It always is for me whenever I install.

---

### Post by mlind on 2007-05-13
With feisty, It should be as easy as installing nvidia-glx package and changing 'nv' entries to 'nvidia' from /etc/X11/xorg.conf (in Device section). Then restart Xserver.

linux-restricted-modules package for your kernel should be already installed. This is how I got the proprietary nvidia drivers working.

---

### Post by thelinuxguy on 2007-05-13
You are using VMware. The virtual Ubuntu setup will not be seeing your real graphics card but one emulated by VMware. Goto System >> Administration >> Device Manager and I doubt you will see an nVidia there. On my virtual Ubuntu, it shows "[VMware SVGA II] PCI Display Adapter".

This may be your problem. Whatever Envy shows seems correct to me. Your virtual Ubuntu doesn't have an nVidia card after all.

I don't know how you can make your virtual Ubuntu see the real card. Someone more knowledgeable could be of help. If you want to try out the card you have got under Ubuntu, I suggest you try Wubi. I haven't tried it myself but from what I have read, it runs natively and makes a dual-boot system. Just that its on a big file on your Windows partition and disk intensive operations may be slightly slow due to this. Its just like installing / uninstalling another Windows app.

And if you are confident of the partitioning stuff and are not worried about accidentally wiping your data, go past Wubi and install Ubuntu to its own partitions. I am positive you will start liking it after the initial hiccups. 

Having said this, if you do manage to get your card recognised by the virtual machine and get the drivers working, I would be happy to know the answer.

> 
But why can't they make the driver a double click install reboot procedure like Windows?

Installing many drivers is a double click thing now. And you don't even need a system restart. Just restart X. Drivers are available in the repositories as mentioned above.

---

### Post by kingbuxton on 2007-05-13
OK, so the issue could be that I am in VMWare - that helps, at least there is a possibility that I am not totally dumb :) 

I am totally confident partitioning and dual booting - I have done it before. I need a bigger backup drive to get everything off C: - that is why I swiped (errrr borrowed) VMWare from work - I figured I could get it all working and then switch to a full install when I have a bigger drive. Looks like my best best bet is dump VMWare and dual boot.

I didn't know it was emulating the Gfx card - yes you are correct - in Device Manager there is no nVidia listed, that I can see.

Time to order a BIG drive - backup and try again. Thanks for the replies though.

I am determined to get it working this time (I saw Beryl vids on YouTube, are you kidding me?)

---

### Post by thelinuxguy on 2007-05-13
> **kingbuxton said:**
> Time to order a BIG drive - backup and try again. Thanks for the replies though.


Give Wubi a try before doing this. It seems to be very easy to install and uninstall. Take a look at the screenshots.

[http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

---

### Post by Wiebelhaus on 2007-05-13
> **kingbuxton said:**
> First off I am running Ubuntu 7.04 in VMWare 6 under XP Pro. 

I already tried this [http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126) everything went well until it tried to reboot and I got the old X error - can't start - it isn't setup correctly. 

Redid Ubuntu - tried again - same exact error after everything seemed to work.

Then I tried this [http://browseatwork.com/nph-proxy.cgi/000000A/http/discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://browseatwork.com/nph-proxy.cgi/000000A/http/discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)

Seemed to work fine until the CTRL-ALT-F1 step - Nothing happened - just stays on the desktop.

Been on it all day - tried about three or four ways of installing them - all failed. In fact when I tried running Envy from a console to see what would happen - the menu comes up - I selected 1. Install nVidia drivers and it says it can't find an nVidia card?! I just laughed. I have an 8800Gts.

I really have tried with Linux, I don't play games all that often, I am bored with XP and I can't really be bothered with Vista (until Crysis appears anyway) so figured if I can get it working in VM first, get to grips with it, and then dual boot it. Tried many versions of Linux and always come unstuck on stuff that should be basics.

So here is my question. I go to nVidia.com. I get the latest driver NVIDIA-Linux-x86-1.0-9755-pkg1.run from [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html).

File is saved on desktop.

Can someone please give me a step by step on how to get that installed? Feel free to assume I know absolutely nothing, I wont take it personal. I figured getting VMWare up and running and Ubuntu installed would be the hard part, who knew?

NOTE: I basically know sod all about Linux, so this may be obvious to you guys. But why can't they make the driver a double click install reboot procedure like Windows? Don't shout, I am sure there is a good reason, but this seems a really complex way to do a simple procedure.

Off for some paracetamol - my head is hurting.

your going to have a horrible time running ubuntu in VB with XP as host , swap the two and it runs flawlessly.

---

### Post by kingbuxton on 2007-05-16
thelinuxguy was bang on, I did an XP install in VMWare, and same thing, you can't install the Forceware drivers as there is no compatible hardware. It does seem to be emulating the Gfx. No wonder I couldn't get it working.

---

