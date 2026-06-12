---
title: "Natty Alpha Install but Doesn't Boot to FakeRAID"
date: 2010-12-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ronparent on 2010-12-10
With some difficulty I was able to install Natty to a fakeraid partition but not boot to it. Boot ends on an initramfs prompt - disk by uiid does not exist. Verified that the raid drives are not activated (blkid list only non raid partitions). Also /dev/mapper is not populated. The system raid location exist long enough to run grub and begin loading of initramfs but apparently never is transferred to ramfs (my interpretation).

I may try again with Alpha 2.

---

### Post by alex.esmann on 2010-12-30
How did you manage to install Natty to a fakeraid partition? 

I am trying to do this myself. I have an intel raid controller setup using RAID10.

gparted detects the raid fine but the installer only detects the 2 subsets of the raid, it seems that parted_devices doesn't work properly?

Anyways if you could give me any pointers on how to get this to work, I'd appreciate it.

---

### Post by ronparent on 2010-12-31
If you enter 'dmraid -l' you will get an output indicating that intel raid10 is not supported. Sorry about that. Not all the levels supported by windows are supported by dmraid.

---

### Post by cristianfere on 2011-01-01
> **ronparent said:**
> With some difficulty I was able to install Natty to a fakeraid partition but not boot to it. Boot ends on an initramfs prompt - disk by uiid does not exist. Verified that the raid drives are not activated (blkid list only non raid partitions). Also /dev/mapper is not populated. The system raid location exist long enough to run grub and begin loading of initramfs but apparently never is transferred to ramfs (my interpretation).

I may try again with Alpha 2.

Assuming that your installation is correct.

After installation, you need create the file /boot/device.map with the following like content:

```

(hd0) /dev/mapper/isw_cicfjjcicd_Volume0

```

Replacing /dev/mapper/isw_cicfjjcicd_Volume0 by your respective fakeraid path device.

---

### Post by cristianfere on 2011-01-01
> **cristianfere said:**
> Assuming that your installation is correct.

After installation, you need create the file /boot/device.map with the following like content:

```

(hd0) /dev/mapper/isw_cicfjjcicd_Volume0

```

Replacing /dev/mapper/isw_cicfjjcicd_Volume0 by your respective fakeraid path device.

I forgot, create the file (/boot/device.map) using a live cd for access fakeraid partition where you instaled the system.

---

### Post by ronparent on 2011-01-01
cristianfere - That's interesting. I had given up on trying anything until the Alpha 2 came out. Will try your suggestion and report back. Thank you.

---

### Post by psusi on 2011-01-02
[QUOTE=cristianfere;10303570
After installation, you need create the file /boot/device.map with the following like content:
[/QUOTE]

device.map is not needed anymore with grub2.

---

### Post by cristianfere on 2011-01-03
> **psusi said:**
> device.map is not needed anymore with grub2.

I believe "not need" is different of "not useful"....

[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/420992/comments/11](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/420992/comments/11)

It's fixed my boot problem with my setup...

---

### Post by ronparent on 2011-01-13
Good news and ...

I installed testdrive and sync'ed the latest (as of Mon 10 Jan) natty 64 bit desktop into it on a usb key. Then I installed the natty image from the key to a partition on my raid. The installation was flawless including the grub-pc install to the raid partition and the boot loader also on the raid.

System also booted fine but without 3d (accompanied by messages that it would be started without unity). So far so good.

Then I mucked around with installing fglrx, uninstalling, reinstalling, etc. Bottom line, with no guidance of any kind I was unable to get unity up. With more mucking around I was able to initially boot to the classic desktop from the log-in screen. But no dice with getting any unity desktop from the standard desktop log in. All I get is a standard desktop with no controls at all (not even keyboard). I basically have to hit the reset to reboot since nothing I've tried has had any effect.

Also problematic, grub-install doesn't work. It faidls with the following message:
> ron@ron-GA-MA790GP-UD4H:~$ sudo grub-install --root-directory=/ /dev/mapper/nvidia_aebhdfib
[sudo] password for ron: 
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/disk/by-uuid/76744cea-fe3e-4414-b41e-a49137a3d058.  Check your device.map.
Auto-detection of a filesystem of /dev/disk/by-uuid/76744cea-fe3e-4414-b41e-a49137a3d058 failed.
Please report this together with the output of "/usr/sbin/grub-probe --device-map="/boot/grub/device.map" --target=fs -v /boot/grub" to <bug-grub@gnu.org>
Creating devoce.map in neither /boot nor /boot/grub helps. So off to report a bug or two.

---

