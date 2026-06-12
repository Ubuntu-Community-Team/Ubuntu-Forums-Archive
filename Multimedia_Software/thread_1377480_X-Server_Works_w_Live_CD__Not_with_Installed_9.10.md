---
title: "X-Server Works w/ Live CD / Not with Installed 9.10"
date: 2010-01-10
forum: Multimedia Software
---

### Post by rsponza on 2010-01-10
Well,

After a Christmas morning scramble trying to get Sims3 working for the kids, I ended up pulling an Nvidia 6200 AGP card out of a perfectly good Ubuntu box and threw it into the kids' PC. I replaced it in the Ubuntu system with an old Nvidia Geforce 2 Ti AGP.

From the start I was unable to get any resolution higher than 800x600 with the GF2. Tried removing xserver-org, reinstalling, reconfiguring, etc. Installed the Nvidia legacy drivers, all no luck.

Tried booting with a 9.10 live CD and it works perfectly - various resolutions, refreshes, etc. So, the card is capable.

I've checked, rechecked, restored, modified xorg.conf to no success.

I'm at a text login now, startx returns (among other info) the following:

dlopen: /usr/lib/xorg/modules/drivers//nvidia_drv.so: undefined symbol: AllocateScreenPrivateIndex

(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available

Fatal server error:
no screens found

Now, I've checked, and nvidia_drv.so is where it's supposed to be (in the drivers directory). What concerns me is the "//" in the directory path string in the (EE) above preceding the driver name - shouldn't this be a "/"? Is the command not able to find the driver correctly?

Regardless, at this point my goal is simply to get the system to use whatever process the live cd is using which results in a working GUI. Don't need fancy 3d, etc, just want a working system. I've spent the last 3 days searching postings and I can't find a similar situation.

Help?

Bob

---

### Post by markbuntu on 2010-01-11
The problem is that the nvidia driver is set up for the wrong card so it fails.

Have you tried booting into the recovery kernel and using the fix x option?
If it works you will be using the generic VESA driver and be able to get to your desktop. Once there remove any nvidia driver, reboot and reinstall it.

If that does not work then you need to remove the nvidia driver from the terminal and reboot into recovery kernel before trying the fix x option.

sudo apt-get purge nvidia-*

---

### Post by DasEi on 2010-01-11
safemode is the way to go,

or use envyng-qt, as nvidia is fairly supported 
(first remove nvidiadriver (old card) the install for
the smaller one,

 nvidia-settings shall also work again, then

---

### Post by rsponza on 2010-01-12
Thanks for the replies - I was under the impression that removing, reinstalling and reconfiguring xserver would have "purged" all the nvidia drivers. I did try installing the correct nvidia legacy drivers when I was still able to access the desktop, but nothing I tried ever gave me back higher than 800x600 (in fact, I got a message each time I logged in that I was running in low-resolution mode).

I'll try the suggestions made by DasEi and markbuntu and see how they work.

Am I understanding correctly that the Live-CD simply loads the vesa driver? I'd be happy with that, since the Live-CD gives me all the resolutions and refresh rates I need.

Again, thanks for the help - I'll be sure to post results later this afternoon.

---

### Post by markbuntu on 2010-01-12
I am not sure about which driver the cd uses. It may be using the open source noveau driver or the VESA driver or even the proprietary nvidia driver. I don't use nvidia so I really can't say.

---

### Post by rsponza on 2010-01-12
Thanks for the suggestions.

Tried the fix x command after booting into the recovery console and it gave me a "No command 'fix' found" error.

I went ahead and purged the nvidia drivers, rebooted and tried again with same result.

Any ideas on how to copy the x server settings from the LiveCD to my hard drive to force them on boot?

Any other suggestions?

---

### Post by rsponza on 2010-01-12
Success!

It's working again. I went into recovery mode and chose to let the system fix broken packages (I think that was the wording). It did its thing and eventually requested a reboot.

Came right up with every resolution and refresh rate I was looking for.

Thanks DasEi and markbuntu for the help - this is exactly why I love this forum.

Thanks again!

Bob

---

