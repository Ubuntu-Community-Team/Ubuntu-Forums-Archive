---
title: "Making changes to USB flash boot drive..."
date: 2010-06-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by clyderino on 2010-06-05
I am booting Meerkat from a USB flash drive. I would like to make changes (desktop appearance, add applications for example) which I would like to retain as permanent for future use. Is there a way to retain these new settings?  Thanks!

---

### Post by Longinus00 on 2010-06-05
I assume you have made a bootable usb drive from the iso. When you made the usb disk via "Startup Disk Creator" remember to enable extra space for it to save your settings, it's controlled via the slider at the bottom of the window.

---

### Post by garvinrick4 on 2010-06-06
> **clyderino said:**
> I am booting Meerkat from a USB flash drive. I would like to make changes (desktop appearance, add applications for example) which I would like to retain as permanent for future use. Is there a way to retain these new settings?  Thanks!I imagine you made your flash drive with unetbootin and it has no persistance (hold changes). As before me gentleman stated Startup Disk Creator in Administration will
hold up to 4 gig persistence. Compete install around 3.5 gig. So it is cool and it is a Live USB also as is unetbootin. If you make a 8 or 16 gig installed just like your HDD with a
/boot in sba1 a /in sba2 and swap in sba3 if needed. Will work but have to install mbr in sda in advanced tab on last page of install. Have to only in sba not sba1 not sba2 but always in sba. And not in sda but sba. 
 Ok make your partitions in gparted first. 100 meg for /boot and whatever for / and then if you have a macine that is short on ram give it a swap, got a couple gig of Ram forget swap.
Then on install you can go to drive sba and manual. And your partitions are already done just put them in as mentioned earlier your advanced tab sba. Install.
 If sda is using grub also. Boot into Linux the stick in flash drive. Do a couple of lines of Code.

sudo update-grub

sudo grub-mkconfig

Make sure in Bios that CD is first, USB second and HDD third in boot order.

Then reboot with USB inserted and should be in grub menu. Can actually do the same with an sdc. if want to have USB drives all over your machine.

Remember installs on USB's must be in grub and Startup disk creator does not mess with grub at all but limited to 4 gig.

---

### Post by C.S.Cameron on 2010-06-06
Here is another alternative with no limitation on persistence size:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by clyderino on 2010-06-07
> **Longinus00 said:**
> I assume you have made a bootable usb drive from the iso. When you made the usb disk via "Startup Disk Creator" remember to enable extra space for it to save your settings, it's controlled via the slider at the bottom of the window.

Thank you for the replies.
I reinstalled Meerkat with "Startup Disk Creator" on an 8 gig thumb drive and enabled extra space (I have about 3.4 g of room left.)

It upgrades nicely.

One odd thing, I have to hit a key as soon as Meerkat starts to get a menu which allows me to use my "Customized" version. Otherwise, the "default" boot gives me only the choice to try it (as if I never used it) or install it on the hard drive and takes a long time to boot.

---

