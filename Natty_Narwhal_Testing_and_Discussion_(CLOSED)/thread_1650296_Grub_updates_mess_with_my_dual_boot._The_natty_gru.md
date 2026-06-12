---
title: "Grub updates mess with my dual boot. The natty grub takes over."
date: 2010-12-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-12-21
Maverick is on sda and natty on sdb. Grub is installed to both MBR's.

When natty gets a grub update it takes over control. Have to install grub again to sda. I've customised sda grub but not natty.

Bit of a pain.

---

### Post by oldfred on 2010-12-21
I am in Lucid right now. We used to have to run dpkg for those with external drives to get grub to remember to reinstall to sdb. I see now in Lucid that it has changed to hard drive info - /dev/disk/by-id. But my Natty is in one of two identical drives, so I do not know what it will do then.

To see where dpkg sees grub:
sudo debconf-show grub-pc

One of the lines from above:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD6400AACS-00G8B1_WD-WCAUF1779071


To reset
sudo dpkg-reconfigure grub-pc

---

### Post by ratcheer on 2010-12-21
Same thing has happened with my system. I am just going ahead and using Natty grub all the time. It is working well.

Tim

---

### Post by dino99 on 2010-12-21
i'm really tired of this grub conf :(

having 3 grub2 (lucid/maverick/natty), so different releases installed on 2 different hdds

now the grub menu is missing memtest, ntfs (3d hdd), removed kernel cant be removed from menu (updated all the grubs)

with such config, users need to be able to choose which grub release to be set as default, or make the latest release take control over the others.

---

### Post by drs305 on 2010-12-21
I don't know if this is a change from the earliest versions of Grub2, but my tests indicate that G2 currently records the drive but always reverts to the partition from which the grub package update is run. 

Simply put, if the Grub2 package is udpating and you get to the screen in which you have to pick the drive and/or partition on which to install (and you pick the drive), your active OS at the time is going to have the controlling grub.cfg. (OK, maybe not so simply put, but read it twice and you will understand. ;-) )

If you run "sudo debconf-show grub-pc" it lists the location by *dev/disk/by-id* but it doesn't reflect anything about the partition - only the drive. Obviously the MBR records which partition to point to, but apparently it always points to the current partition during a package update.

Soooo, here's an example running your Ubuntu OS from sda5:

1, Grub package update including the drive/partition page, and you select only sda:  
Controlling grub.cfg  = sda5

2. "sudo grub-install /dev/sda" :  
Controlling grub.cfg  = sda5

3. "sudo grub-install --root-directory=/mnt/myotherlinux /dev/sda"
Controlling grub.cfg = myotherlinux grub.cfg

Of course, if you are in the 'non-controlling' OS, you can run 'update-grub' and it will rewrite it's grub.cfg. It just won't be displayed when you boot.

What can you do?
1. If you are testing Natty, you can probably expect several updates to Grub 1.99, which is going to take control of your grub menu. If you really need or want to keep another grub.cfg the controlling one, in Natty you can lock the current grub-pc version in Synaptic *and* with the following command:
```
echo grub-pc hold | sudo dpkg --set-selections
```
Of course locking the Natty Grub2 prevents further testing, which of course is the purpose of doing the testing in the first place.

2. Run 'sudo grub-install' with the '--root-directory' switch. There is a caveat with this however. The current version of G2 will be installed (ie Natty's Grub2 - 1.99 - would be installed in Maverick (1.98).

3. The next time you are in your production install, run 'sudo grub-install /dev/sda'.

4. Make a custom menu in your data partition and link it to the /etc/grub.d folder of each Ubuntu installation. Name it something other than any of the existing scripts so it won't be overwritten on a package update. If you name it 06_custom. In the menuentry, if you use /vmlinuz and /initrd.img instead of the actual kernel version it will be at the top of you menu and always boot the latest kernel in that partition.

I need to get a life. Happy Holidays.  :-)

---

### Post by Quackers on 2010-12-21
> **dino99 said:**
> i'm really tired of this grub conf :(

having 3 grub2 (lucid/maverick/natty), so different releases installed on 2 different hdds

now the grub menu is missing memtest, ntfs (3d hdd), removed kernel cant be removed from menu (updated all the grubs)

with such config, users need to be able to choose which grub release to be set as default, or make the latest release take control over the others.

Yes, to get old kernels out of the menu I've deleted them from synaptic then update grub in that system and in the system in which grub is in command.
I can't get rid of recovery menu entries at all.

---

### Post by drs305 on 2010-12-21
> **Quackers said:**
> I can't get rid of recovery menu entries at all.

If you are using the G2 in your current partition:
You know how to remove the recovery entries in your current partition via the setting in /etc/default/grub.

If you have recovery entries in the #30_os-prober section of grub.cfg, they are appearing because recovery menuentries exist in the 10_linux entry in the other partition's grub.cfg. If you want to stay in your current install, you can manually mount the other partition, edit the other  grub.cfg and remove the recovery menuentries from the 10_linux section. Then update-grub your current partition and the recovery entries will disappear. The next time you are in the other installation, disable the recovery mode option and update-grub in that partition (even though you aren't using it).

---

### Post by Quackers on 2010-12-21
Recovery entries must be coming from somewhere else because all 3 etc/default/grub's are edited by uncommenting the relevant line. That used to be enough in Maverick so not sure what's changed :-)

BTW drs305, nice Christmas hat :-)

---

### Post by philinux on 2010-12-22
Since we are testing Natty what I'm doing now is this. If I see a mention of a grub package in the updates from my chroot, I'll let it update but then run from Mav terminal sudo grub-install /dev/sda straight after.

---

### Post by Morbius1 on 2010-12-22
It is my sincere hope that this gets fixed at some point. I don't use grub to multiboot and my bootloader ( BootItNG ) occupies the MBR. It's worked fairly well now for almost a decade and the only Linux I've had a problem with was PCLinuxOS which insisted on overwritting the MBR every time there was a grub update in the repository.

---

### Post by dino99 on 2010-12-22
> **philinux said:**
> Since we are testing Natty what I'm doing now is this. If I see a mention of a grub package in the updates from my chroot, I'll let it update but then run from Mav terminal sudo grub-install /dev/sda straight after.

things are worst on that side, wonder if the actual grub team is able to design a simple but strong and stable bootloader (maybe distro independent)

---

