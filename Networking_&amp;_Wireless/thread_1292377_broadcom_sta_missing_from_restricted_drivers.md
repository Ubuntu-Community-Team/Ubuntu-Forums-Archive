---
title: "broadcom sta missing from restricted drivers"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by elj4176 on 2009-10-15
I have had the broadcom sta driver in use for awhile now but when I rebooted the other day my wireless (4312) light stayed orange. I checked in the restricted driver manager to see if I had to re-enable it but it is not in there anymore.
lshw -C network shows:

*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

I'm using a usb wireless adapter at the moment but I'd rather get my 4312 working again. Any idea why the driver is missing and how to get it back?

---

### Post by swoody on 2009-10-15
Is the b43 driver still showing up in 'Hardware Drivers'? 

Make sure your 'Restricted' repository is still enabled. If it's not, enable it, then refresh your package lists. Also check to make sure both 'bcmwl-modaliases' and 'bcmwl-kernel-source' are installed. If everything looks good so far, you should be able to do:
```
sudo modprobe wl
```
to activate the driver again.

If this doesn't work to get your wireless back up, can you give us the output of 'lspci' and 'ifconfig'

---

### Post by Ayuthia on 2009-10-15
You might check and see if the file is still there:
```
ls /lib/modules/$(uname -r)/volatile
```
If nothing shows up, then the restricted modules portion is not running.  You can restart it by:
```
sudo /etc/init.d/linux-restricted-modules-common start
```Then you can do the following:
```
sudo depmod -a
sudo modprobe wl
sudo iwlist scan
```These commands will rebuild the modules list and then try to load the wl module.

Hopefully it will show up and work after that.

---

### Post by elj4176 on 2009-10-15
I still have restricted drivers in use (nvidia and ricoh webcam). The b43 driver isn't listed and I don't know that it ever was in there.

The problem appears to be when I boot into Ubuntu 9.04, kernel 2.6.28-15-generic because I stepped back in the grub menu and selected 2.6.28-14-generic and the sta driver shows up again and my 4312 wireless works fine.

Seems odd but I guess I can just keep booting into the previous kernel.

edit:

I rebooted back into 2.6.28-15 and the sta didn't show and wireless didn't work. I ran:

Code:

sudo depmod -a
sudo modprobe wl
sudo iwlist scan


and the blue light came on and the sta was listed in the restricted drivers now and wireless works. How do I make this stick so I do not have to run these commands every time I reboot?

thanks for the help!

---

### Post by swoody on 2009-10-15
I'm not sure how to take care of this issue, but I have noticed a lot of bugs being reported about wireless issues with the 2.6.28-15 kernel. I'll have to look into it a bit more, but hopefully someone can post a fix here for you :)

---

### Post by elj4176 on 2009-10-15
I appreciate the quick responses! I didn't even think to depmod -a before the modprobe wl but I will remember it next time.

I could always move to 9.10 and see what happens ;)

---

### Post by Ayuthia on 2009-10-15
Does the wl module still disappear after you restart?  Usually the depmod -a will make it stick because the system knows that it exists now.  The only time that it would not work is when the wl module disappears completely.

As for bumping up to 9.10, I would not do that yet.  I just installed the beta and no options came up for me at all for my laptop.  I have a Broadcom 4328 card (which uses the Broadcom STA driver) and an ATI graphics card.  I am currently using an ethernet cable and updating to see if it will show up afterwards.  They usually have these issues resolved before the release.  EDIT: The current updates bring the kernel to 2.6.31-14 and the Broadcom STA driver is there, but a patch still needs to be downloaded to make it work.  Hopefully that is resolved before the final.

The only concern that I have right now is that the linux-restricted-module-common no longer exists so there is no easy way to bring up the restricted modules.  I should take a look at the code to see where it is grabbed.

---

### Post by elj4176 on 2009-10-16
The wl module loaded just fine in the .15 kernel this morning so it seems to be fixed.
Thanks!

---

### Post by gdp77 on 2009-10-31
while using the live-cd I could use the broadcom restricted driver and my laptop's modem restricted driver from system---> administration ---> hardware drivers.

Now I have installed ubuntu in my HD (kernel 2.6.31-14) and there are no restricted drivers options in the system --> administration --> hardware drivers.

From update manager I cant's see any .15 kernel update.

---

### Post by swoody on 2009-11-01
> **gdp77 said:**
> while using the live-cd I could use the broadcom restricted driver and my laptop's modem restricted driver from system---> administration ---> hardware drivers.

Now I have installed ubuntu in my HD (kernel 2.6.31-14) and there are no restricted drivers options in the system --> administration --> hardware drivers.

From update manager I cant's see any .15 kernel update.

gdp77 - Did you just do a fresh install of Karmic? I noticed this issue as well. Try connecting your computer via ethernet cable, and running 'sudo apt-get update' and the drivers should show up in Hardware Drivers after that.

---

### Post by howcanireachthesekids on 2009-11-02
> **swoody said:**
> gdp77 - Did you just do a fresh install of Karmic? I noticed this issue as well. Try connecting your computer via ethernet cable, and running 'sudo apt-get update' and the drivers should show up in Hardware Drivers after that.
What is another way to get Broadcom 4312 driver to show in Hardware Drivers without having access to ethernet cable internet :(

---

### Post by swoody on 2009-11-02
Well, since the driver *should* be on the liveCD, you should be able to insert your Ubuntu liveCD, and then enable it to be used as a repo in System>Administration>Software Sources, and see if you can install the bcmwl-kernel-source package (STA driver package). If you're able to get this installed, then you just need to reboot, and you're good to go :)

If you are having troubles with the Live CD, try downloading the package with a computer that has working internet, from [HERE.]("http://packages.ubuntu.com/karmic/bcmwl-kernel-source") Then transfer it to your other computer, and install it. Again, reboot and you should be up and running :)

---

