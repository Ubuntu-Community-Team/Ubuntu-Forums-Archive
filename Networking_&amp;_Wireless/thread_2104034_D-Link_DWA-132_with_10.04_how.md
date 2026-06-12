---
title: "D-Link DWA-132 with 10.04 how ??"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by keevill on 2013-01-11
I have several users running 10.04 and the wireless lan card I have bought them is the D-Link DWA-132.
I cannot get it to work in 10.04 even though lsusb sees the device. Users running 12.04 it works out of the box.
Anyway to get it to work without  upgrading ?
Upgrading takes a long time and existing settings are not kept despite the upgrade process saying that they will . Hence my reluctance to upgrade just for the wifi adaptor.
-keevill-

---

### Post by ahallubuntu on 2013-01-11
Ubuntu 10.04 LTS is supported only until April 30, 2013.  You'll have to upgrade anyway soon after that, if you still want updates and bug fixes (and to be able to install new software).  Why not upgrade now instead of wasting time trying to make this card work?

I just upgraded (clean install, actually) from 10.04 LTS to 12.04 LTS and am happy I finally did.  A number of little things seem fixed or better than they used to.  I'm using Gnome Classic, so the look and feel are not much different from 10.04.

You could always do one clean install of 12.04, do all the software installs you like and updates, then clone that install for every new user instead of doing the same thing over and over again.  Linux is quite flexible in moving to new hardware.  I did my laptop install on a desktop and ported it to my laptop without changing a thing.

---

### Post by keevill on 2013-01-11
> **ahallubuntu said:**
> Ubuntu 10.04 LTS is supported only until April 30, 2013.  You'll have to upgrade anyway soon after that, if you still want updates and bug fixes (and to be able to install new software).  Why not upgrade now instead of wasting time trying to make this card work?

I just upgraded (clean install, actually) from 10.04 LTS to 12.04 LTS and am happy I finally did.  A number of little things seem fixed or better than they used to.  I'm using Gnome Classic, so the look and feel are not much different from 10.04.

You could always do one clean install of 12.04, do all the software installs you like and updates, then clone that install for every new user instead of doing the same thing over and over again.  Linux is quite flexible in moving to new hardware.  I did my laptop install on a desktop and ported it to my laptop without changing a thing.

Interesting idea - clone a new vanilla install ... reminds me of the days of Norton Ghost which worked only sometimes......which prog do you suggest I use to clone ? 
The reason I wanted to get the wireless card(s) to work is because of the numbers of users on 10.04 - about 12 and the time taken to do it. Each user takes a few hours by the time the update is finished I've re-set up the printers, emails etc etc.
-keevill-

---

### Post by ahallubuntu on 2013-01-11
OK, I did a little googling, and it appears this model uses a Realtek 8192CU chipset.  You can verify this by simply downloading the driver from Realtek and building it (see below) and see if it works.  You can also get its hardware ID from an lsusb listing.  (Or if you connect it in 12.04 when it's working, see what driver is being used; do "sudo lshw -C network" and see what driver is listed in the "Configuration:" line for the wireless card.)

I have a few dongles with this same chipset - I am pretty sure I built the driver in 10.04 (in 11.04 for sure and it worked fine).  Fortunately, building the driver is easy.

You'll have to build the driver in 12.04 anyway.  Although the wireless appears to work automatically, it really doesn't: it's unreliable, connections are unstable, etc.  Same problem in 12.10.  But, you can still just build the driver.  The only problem with building the driver (requires a few commands in a terminal window) is that each time the kernel is updated, you have to re-build the driver.  But it's very quick.  You can even make a little script to do it each time and tell the users how to do it; just put an icon on their desktop to re-build it, should they do an update that includes a new kernel.

Here's a description I wrote up a few months ago on how to build the driver.  Should work in 10.04 LTS.  Try it:

[http://ubuntuforums.org/showthread.php?t=2076315](http://ubuntuforums.org/showthread.php?t=2076315)

---

### Post by ahallubuntu on 2013-01-11
As for cloning: there are lots of ways. You could use a Clonezilla CD to clone.  Personally, I find Clonezilla kind of user-unfriendly and dislike it, despite its rich set of features.  The user interface gives me a headache.  I usually use a copy of Acronis True Image (like Ghost) I bought, because it works reliably with Linux ext4 partitions and is easy to use.

Gparted actually supports partition copying (right-click on a partition and "copy" and then right-click on the destination partition and "paste.").  Not automatic but still pretty simple; if the golden image is simple (one partition for /, one swap), it might be pretty simple.  It might even copy the Grub boot sector, not sure.  Gparted has an excellent user interface.

A crude clone method is simply using the dd command.  It copies everything (even unused sectors) so it's horribly inefficient, but it works.  As long as the destination disk is of equal or larger size from the source disk, the destination doesn't have to be the same size.  I can't remember having actually put my swap partition FIRST (sda1) but if you do that and put the "/" partition last (sda2), you could easily just grow it to take advantage of a larger destination disk (use Gparted).  Just make the source image as small as possible.  20GB is actually very adequate for a very basic installation of Ubuntu 12.04.

After the clone and after adjusting partition size for a larger partition, just:
- delete the /etc/udev/rules.d/70-persistent-net.rules file so eth0 and wlan0 are re-created on new network cards at next reboot, instead of being eth1/wlan1 .
- change /etc/hostname (and /etc/hosts) if you don't want them all to have the same hostname.

---

### Post by keevill on 2013-01-15
> **ahallubuntu said:**
> As for cloning: there are lots of ways. You could use a Clonezilla CD to clone.  Personally, I find Clonezilla kind of user-unfriendly and dislike it, despite its rich set of features.  The user interface gives me a headache.  I usually use a copy of Acronis True Image (like Ghost) I bought, because it works reliably with Linux ext4 partitions and is easy to use.

Gparted actually supports partition copying (right-click on a partition and "copy" and then right-click on the destination partition and "paste.").  Not automatic but still pretty simple; if the golden image is simple (one partition for /, one swap), it might be pretty simple.  It might even copy the Grub boot sector, not sure.  Gparted has an excellent user interface.

A crude clone method is simply using the dd command.  It copies everything (even unused sectors) so it's horribly inefficient, but it works.  As long as the destination disk is of equal or larger size from the source disk, the destination doesn't have to be the same size.  I can't remember having actually put my swap partition FIRST (sda1) but if you do that and put the "/" partition last (sda2), you could easily just grow it to take advantage of a larger destination disk (use Gparted).  Just make the source image as small as possible.  20GB is actually very adequate for a very basic installation of Ubuntu 12.04.

After the clone and after adjusting partition size for a larger partition, just:
- delete the /etc/udev/rules.d/70-persistent-net.rules file so eth0 and wlan0 are re-created on new network cards at next reboot, instead of being eth1/wlan1 .
- change /etc/hostname (and /etc/hosts) if you don't want them all to have the same hostname.

I went ahead and made a Clonezilla live cd. I wanted to clone the image onto an external 120 hard disk which I connected via a usb housing. The process was taking hours and hours, so I abandoned it.
I really would like to clone an image onto a 64 Flash drive and use that to clone onto other machines but the size of the source hard disk has to be the same as the destination hard disk and that's a problem.

-keevill-

---

