---
title: "black screen - 10.10 with Nvidia 260.19.xx drivers"
date: 2010-11-19
forum: Mythbuntu
---

### Post by davidstoll on 2010-11-19
I cannot seem to avoid a black screen bootup with a fresh install after activating the latest Nvidia drivers.  I've tried 10.04 and 10.10, but in both cases, activating nvidia-current (260.19.xx) seems to be the problem.

I have attached my xorg.conf and xorg.0.log files.

I am reading quite a bit about similar issues, but I can't seem to find a solution that works for me.  I have even followed instructions on change the grub boot line, but no luck.

I have even tried to remove nvidia-current and install the version 256.xx drivers from the Nvidia web site.  However, I get an error when I try to startx.  It says that there are conflicting drivers on the system 260 and 256.

I really hope someone can help me.
Thanks for your time.

---

### Post by klc5555 on 2010-11-19
Well, if you have no usable graphical shell at all because of the wonky NVidia driver, you should still be able to use the grub recovery to boot to a root prompt.

I imagine at that point you'd be able to do a dpkg-reconfigure xserver-xorg to set the driver back to the default open source nv, which would at least get you graphical support without NVidia. From there you should have little difficulty in setting up the 195. series drivers instead of the 260. series that are causing you trouble.

---

### Post by davidstoll on 2010-11-20
> **klc5555 said:**
> Well, if you have no usable graphical shell at all because of the wonky NVidia driver, you should still be able to use the grub recovery to boot to a root prompt.

I imagine at that point you'd be able to do a dpkg-reconfigure xserver-xorg to set the driver back to the default open source nv, which would at least get you graphical support without NVidia. From there you should have little difficulty in setting up the 195. series drivers instead of the 260. series that are causing you trouble.

Yes, I can boot to a command prompt, no problem.
I ran the dpkg-reconfigure xserver-xorg, rebooted, but still no luck.

---

### Post by LowSky on 2010-11-20
ok lets start with this, what video card do you have

second ubuntu has an error where the noveau (sp?) driver can onflit with the proprietary driver. try this tutorial

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by davidstoll on 2010-11-20
> **LowSky said:**
> ok lets start with this, what video card do you have

second ubuntu has an error where the noveau (sp?) driver can onflit with the proprietary driver. try this tutorial

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It's the ION video card from a NetTop (Asus Aspire One).
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103234R&cm_re=R3610-_-83-103-234R-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103234R&cm_re=R3610-_-83-103-234R-_-Product)

I was not aware of this procedure, so thank you for suggesting it.  However, I am still not having any luck.  I have the same black screen.

---

### Post by klc5555 on 2010-11-21
> **davidstoll said:**
> It's the ION video card from a NetTop (Asus Aspire One).
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883103234R&cm_re=R3610-_-83-103-234R-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103234R&cm_re=R3610-_-83-103-234R-_-Product)

I was not aware of this procedure, so thank you for suggesting it.  However, I am still not having any luck.  I have the same black screen.

Well, since you've already evidently purged your open-source nouveau driver and tried at least once to remove the 260. series nvidia drivers in some fashion from this install and compile the 255. series from the NVidia web site without success, it's not entirely clear what the status of your xorg.conf, your nvidia driver load, or your X install actually is at the moment. 

Likely they're somewhat of a mess. And if this is a brand new installation with nothing particular invested in it, your simplest procedure is likely be to reinstall, but stick with the open source driver until you have had the opportunity to install the 195. series drivers with synaptic. Then activate the earlier driver rather than the 260. series driver. That's what I'd do at this point, since while the current installation is probably salvageable, at about 45 minutes the reinstall is likely more time-effective than any other procedure.

---

### Post by davidstoll on 2010-11-21
> **klc5555 said:**
> Well, since you've already evidently purged your open-source nouveau driver and tried at least once to remove the 260. series nvidia drivers in some fashion from this install and compile the 255. series from the NVidia web site without success, it's not entirely clear what the status of your xorg.conf, your nvidia driver load, or your X install actually is at the moment. 

Likely they're somewhat of a mess. And if this is a brand new installation with nothing particular invested in it, your simplest procedure is likely be to reinstall, but stick with the open source driver until you have had the opportunity to install the 195. series drivers with synaptic. Then activate the earlier driver rather than the 260. series driver. That's what I'd do at this point, since while the current installation is probably salvageable, at about 45 minutes the reinstall is likely more time-effective than any other procedure.

Interestingly, I don't see 195 in synaptic.  The highest I see is 185.

---

### Post by davidstoll on 2010-11-21
One other thing, now I only have a max resolution available of 640x480.  I did try to reset the xorg.conf file using nvidia-xconfig.

:(

---

### Post by klc5555 on 2010-11-21
> **davidstoll said:**
> One other thing, now I only have a max resolution available of 640x480.  I did try to reset the xorg.conf file using nvidia-xconfig.

:(

The 195.36.24 drivers were the "current" set for Ubuntu 10.04, which I'm still running. They may not have been included as an option with 10.10. Nvidia lists 185.18.36 as supporting the ION GPUs, so if that's what you have easily available in 10.10, they should work fine.

From  your posts I don't have any clear sense at all of what you're running at the moment. Is this still the original install or a reinstall? Are you running the 185. series NVidia drivers, the nouveau driver, the nv driver, or something else? If the nvidia and you're stuck at 640x480 (already an improvement over what you had), do you get an error at boot saying only "low resolution" mode is available. If you get such a message, what tuner(s) does the setup have? Does dmesg output indicate a vmalloc error at boot? NVidia used with some tuners, notably the Hauppauge 1600, require that you set the vmalloc parameter to 256m or 512m in the kernel line in grub for both the nvidia driver and the tuner driver to load correctly.

---

### Post by davidstoll on 2010-11-21
> **klc5555 said:**
> The 195.36.24 drivers were the "current" set for Ubuntu 10.04, which I'm still running. They may not have been included as an option with 10.10. Nvidia lists 185.18.36 as supporting the ION GPUs, so if that's what you have easily available in 10.10, they should work fine.

From  your posts I don't have any clear sense at all of what you're running at the moment. Is this still the original install or a reinstall? Are you running the 185. series NVidia drivers, the nouveau driver, the nv driver, or something else? If the nvidia and you're stuck at 640x480 (already an improvement over what you had), do you get an error at boot saying only "low resolution" mode is available. If you get such a message, what tuner(s) does the setup have? Does dmesg output indicate a vmalloc error at boot? NVidia used with some tuners, notably the Hauppauge 1600, require that you set the vmalloc parameter to 256m or 512m in the kernel line in grub for both the nvidia driver and the tuner driver to load correctly.

Ok, so right now I have a fresh install of 10.10 64 bit.  I have not activated any drivers or even installed anything.

I'm as fresh as possible with GUI access.  However, I do need VDPAU so I can utilize the video acceleration which is the whole reason I got this unit.

Next, this is a frontend, so no recording devices are attached to it.

Lastly, 185 are listed, but the "version" in synaptic package manager says it is 260.x

Ok, so if I go down to 180 drivers, they say they are version 185.  If I mark one of the nvidie-180 drivers to be installed, it requires one of the 185 dependencies which are version 260.

I know this sounds strange, but trust me that's what it says...

Package____________Version
nvidia-glx-185________260.xx
nvidia-185-vppau_____260.xx
nvidia-glx-180________185.xx
nvidia-180-vdpau_____185.xx

If I opt to install one of the 180 files (version 185), it requires me to install one of the 185 (version 250) dependencies.

As soon as I activate one of the drivers, I'm going to get the black screen again.  I had tried to reinstall the OS (10.10, 10.04, 32 bit, 64 bit, etc) numerous times.

---

### Post by klc5555 on 2010-11-22
Well, front-end only shoots my conflicting driver theory. But there do seem to be odd issues with ion boards, and nvidia with or without nouveau drivers 

I note from the mythtv lists that there was a thread a year or so ago re. ion boards and NVidia. Namely that the posters were setting up their ion boards for DVI/HDMI, which worked fine until they set up NVidia drivers, which defaulted to the VGA output and would use nothing else. Blank screen until they hooked up a VGA cable. Then full resolution.

They never could get the DVI/HDMI to work, but got full resolution through the VGA. [http://www.mythtv.org/pipermail/mythtv-users/2009-June/257383.html](http://www.mythtv.org/pipermail/mythtv-users/2009-June/257383.html)

If you're using the digital output from your ion board, you might want to try it with a VGA cable.

Since we're essentially guessing at this point, there are also some postings and how-tos devoted to bypassing the Ubuntu "nouveau driver bug" yielding a blank screen with NVidia graphics starting with Ubuntu 10.04. One such workaround consists in booting with the option "nouveau.modeset=0" [no quotes] in the kernel commandline in grub. Testing it and (if it works) permanently implementing it are (very briefly) described here: [http://www.*****************/driver/articles/fix-dell-latitude-e6410-black-screen-during-ubuntu-10-04-installation.html](http://www.*****************/driver/articles/fix-dell-latitude-e6410-black-screen-during-ubuntu-10-04-installation.html)

I notice this nouveau bug workaround isn't included in the community binary driver document referenced earlier in the thread.

This particular how-to describes the replacement from the recovery root-prompt of the 260 drivers by the 255 ones from NVidia's site, which technique did not appear to work on your machine. But it also mentions the grub kernel-line edit as an alternative workaround. [http://www.*****************/driver/articles/fix-black-screen-with-ubuntu-10-10-installation.html](http://www.*****************/driver/articles/fix-black-screen-with-ubuntu-10-10-installation.html)   

If these don't appear to surround the problem, then I guess we'll keep looking.
---------------------
Final note: I don't know why the forum's software is censoring the addresses of the last two howtos, but I suppose typing in manually d*o*w*n*l*o*a*d*a*t*o*z*.com without the asterisks will get you where the expurgated portion of the hyperlink would have. The complete recommendations of the earlier one are as follows:

   1. Hit ESC at the grub prompt and F6
   2. Installed 10.04 with alternate media and no x
   3. Use nouveau.modeset=0 on the GRUB boot command (if you have nvidia card graphics)
   4. Upon booting into textmode install the working nvidia drivers (System -> Administration -> Hardware Drivers)
   5. Modify /boot/grub/grub.conf to include nouveau.modeset=0 in the kernel commandline

---

### Post by davidstoll on 2010-11-22
> **klc5555 said:**
> Well, front-end only shoots my conflicting driver theory. But there do seem to be odd issues with ion boards, and nvidia with or without nouveau drivers 

I note from the mythtv lists that there was a thread a year or so ago re. ion boards and NVidia. Namely that the posters were setting up their ion boards for DVI/HDMI, which worked fine until they set up NVidia drivers, which defaulted to the VGA output and would use nothing else. Blank screen until they hooked up a VGA cable. Then full resolution.

They never could get the DVI/HDMI to work, but got full resolution through the VGA. [http://www.mythtv.org/pipermail/mythtv-users/2009-June/257383.html](http://www.mythtv.org/pipermail/mythtv-users/2009-June/257383.html)

If you're using the digital output from your ion board, you might want to try it with a VGA cable.

Since we're essentially guessing at this point, there are also some postings and how-tos devoted to bypassing the Ubuntu "nouveau driver bug" yielding a blank screen with NVidia graphics starting with Ubuntu 10.04. One such workaround consists in booting with the option "nouveau.modeset=0" [no quotes] in the kernel commandline in grub. Testing it and (if it works) permanently implementing it are (very briefly) described here: [http://www.*****************/driver/articles/fix-dell-latitude-e6410-black-screen-during-ubuntu-10-04-installation.html](http://www.*****************/driver/articles/fix-dell-latitude-e6410-black-screen-during-ubuntu-10-04-installation.html)

I notice this nouveau bug workaround isn't included in the community binary driver document referenced earlier in the thread.

This particular how-to describes the replacement from the recovery root-prompt of the 260 drivers by the 255 ones from NVidia's site, which technique did not appear to work on your machine. But it also mentions the grub kernel-line edit as an alternative workaround. [http://www.*****************/driver/articles/fix-black-screen-with-ubuntu-10-10-installation.html](http://www.*****************/driver/articles/fix-black-screen-with-ubuntu-10-10-installation.html)   

If these don't appear to surround the problem, then I guess we'll keep looking.
---------------------
Final note: I don't know why the forum's software is censoring the addresses of the last two howtos, but I suppose typing in manually d*o*w*n*l*o*a*d*a*t*o*z*.com without the asterisks will get you where the expurgated portion of the hyperlink would have. The complete recommendations of the earlier one are as follows:

   1. Hit ESC at the grub prompt and F6
   2. Installed 10.04 with alternate media and no x
   3. Use nouveau.modeset=0 on the GRUB boot command (if you have nvidia card graphics)
   4. Upon booting into textmode install the working nvidia drivers (System -> Administration -> Hardware Drivers)
   5. Modify /boot/grub/grub.conf to include nouveau.modeset=0 in the kernel commandline


Interestingly, I am using VGA...haven't even tried the HDMI.  Might open a whole new can of worms.

The reason this whole thing got started was because a boot disk (from Micro$oft) destroyed my linux partition even though I told it to "do nothing" and reboot.  So, the drivers were behaving very well.  I had, however installed 9.04 and have been upgrading since then.

One other thing the thread suggesting the nouveau.modeset=0 didn't work for me and neither did the installation using the 256 driver script from Nvidia.

Those threads seem like the same issue, but maybe they aren't...?

Right now I've got a completely fresh install of 10.10 64bit and no nvidia drivers installed.  Not sure how to tell what the resolution is, but it appears to be high.  However, video playback doesn't work because it is relying on the CPU (ion) and jacks the usage to 100% because it is HD content.

What would you suggest at this point (assuming a fresh install)?  I just know that as soon as I activate Nvidia drivers, it's going to crap out on me again.  I'll be able to get it back using the dpkg command from a previous post, but then I'll be back to 640x480 max res where I was before.

---

### Post by klc5555 on 2010-11-22
Well, the one real differences between 9.04 and 10.x in this area is the [bleeping] nouveaux driver, and the level of xorg. There are things that Ubuntu does almost as well as other distros do them, but there are also things that other distros handle practically without thought that Ubuntu turns into a complete nightmare. nvidia drivers belong to the latter category.

At this point, you have a fresh install; the nouveau drivers are installed and running, but the nvidia driver packages are not installed/activated.

I'd probably follow the binary driver how-to that Low Sky linked to earlier and purge the nouveau driver completely from a prompt (after installing/activating the nvidia drivers) with sudo apt-get --purge remove xserver-xorg-video-nouveau  I don't know whether you had previously tried purging the nouveau driver completely, but I would check to be sure the nv driver package was installed and ready to go first: xserver-xorg-video-nv, since that particular open-source nvidia driver is not known to conflict with anything, not even on Ubuntu. Then, if for some reason the nvidia driver doesn't want to activate, at least you'll have something else ready to work with.

Finally, as the how-to suggests, you might still need to run sudo nvidia-xconfig from a prompt to finish activating the nvidia driver.

Bet you wish you were still running 9.04 by this point.

---

### Post by iscraigh on 2010-11-22
Had the same problem with my aspire revo

I downgraded the drivers using this script  (look @ post #18 )

I assume you have blacklisted the nouveau drivers.

[http://www.wildfiregames.com/forum/index.php?showtopic=13668#]("http://www.wildfiregames.com/forum/index.php?showtopic=13668#")

That solved that problem, and it also worked on a pc with an nvidia 8400gs based card.

Let me know if this solves your problem.

Craig

---

### Post by davidstoll on 2010-11-22
Interesting update:
I had previously tried to downgrade the drivers, but I wasn't 100% sure if I was undoing everything correctly.

So, I allowed all updates to occur for my system (whatever upgrades synaptic wanted to install), but did not ever activate my nvidia driver.

Well, I rebooted and I have a black screen.

I looked and I don't have any nvidia drivers installed because the only nvidia program on my system is nvidia-detector, which was the only thing on the fresh install when it was working.

What do I need to look at to determine what's going on at this point?  i.e. what log file or...?

---

### Post by davidstoll on 2010-11-23
Ok, so there are actually two completely separate things causing the same black screen issue.  This is why I didn't think downgrading the drivers to v256 worked.

1) Downgrading the drivers did work.

2) my second issue involves lirc

Since the second issue is not related to the topic, I am going to start a separate thread.

Thanks for everyone's help.  Follow me here if you can help with lirc...
[http://ubuntuforums.org/showthread.php?p=10152787](http://ubuntuforums.org/showthread.php?p=10152787)

---

