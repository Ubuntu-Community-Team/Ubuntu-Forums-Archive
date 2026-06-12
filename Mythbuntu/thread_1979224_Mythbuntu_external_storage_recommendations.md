---
title: "Mythbuntu external storage recommendations"
date: 2012-05-13
forum: Mythbuntu
---

### Post by dulciepercy on 2012-05-13
Hi
I've upgraded Mythbuntu to 12.04 on an ASrock ion machine. I only have 30G SSD on board so all archived media is on an external USB drive. Thing is Mythbuntu never sees this drive (if I set it as a place where videos are stored) until after I go to the desktop and click on the drive to open it in Thunar.

So I look for alternatives. Would esata behave the same way? Has anyone tried one of the newish home NAS systems?

Alternatively, is there a startup command I can insert somewhere that "wakes up" the drive for me?

I've also tried storing stuff on Windows machines on the network, but unless everything is started in the right order, and Thor had a nice sandwich for lunch, the Myth machine won't find the network.

So any suggestions welcome, thanks.

---

### Post by Patrick27 on 2012-05-13
Have you tried tossing it in your /etc/fstab file to automatically mount on bootup?  If you need, you can find the UUID of your drive from a utility like gparted.

---

### Post by klc5555 on 2012-05-13
> **Patrick27 said:**
> Have you tried tossing it in your /etc/fstab file to automatically mount on bootup?  If you need, you can find the UUID of your drive from a utility like gparted.

Generally you can't put a USB drive in fstab because fstab loads before the USB drivers do. However you can put a mount line in your rc.local which loads up much later in the process. 

So that if sudo fdisk -l tells you that the USB drive partition is normally to be found at /dev/sdb1, the line added to the rc.local will be ```
mount /dev/sdb1  /var/lib/mythtv/recordings
``` or wherever you wish to mount the recording directory at. And it should mount at boot.

After it has so mounted, it should be checked to make sure it has not been mounted as owner "root", group "root". If it has, this can be changed with chown and the drive should be ready to go.

---

### Post by dulciepercy on 2012-05-17
Thanks for that information. I assume from this that clicking on the usbdisk icon on the desktop effectively mounts the disk because it hasn't been mounted at boot.

I will try this before purchasing any kit for esata.

---

### Post by klc5555 on 2012-05-18
> **dulciepercy said:**
> Thanks for that information. I assume from this that clicking on the usbdisk icon on the desktop effectively mounts the disk because it hasn't been mounted at boot.

I will try this before purchasing any kit for esata.

The rc.local technique works. I use one USB external 3T drive to house older TV recordings on one backend, which drive loads at boot to the mount point /var/lib/mythtv/oldrecordings (owner mythtv:mythtv). And I use two USB external 3T drives that load at boot on a second backend for video storage.

If you decide to use a drive that large, you'll need an external USB drive case whose circuitry handles drives larger than 2T (many don't; the ones that do cost just a few dollars more), and you'll likely want to use parted or gparted to set the drive up, since fdisk and its derivatives can't handle partitions larger than 2T

---

### Post by singedwings on 2012-05-18
I have previously mounted usb drives in fstab with no problems all you need to know is here [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

