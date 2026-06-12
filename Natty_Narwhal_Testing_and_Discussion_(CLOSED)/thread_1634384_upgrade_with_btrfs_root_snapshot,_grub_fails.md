---
title: "upgrade with btrfs root snapshot, grub fails"
date: 2010-11-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by benjo316 on 2010-11-30
(back-story) So, I created a volume snapshot (called it unstable) and tried to remount it; that didn't work, so I rebooted with rootflags=subvolid=257 appended to the kernel line. That seemed to work, more or less.

So, with a sigh of relief, I ran "update-manager -c -d", clicked upgrade, and waited. An hour or so later, I see that grub (along with some dependent packages) failed to install properly. Here's the output of "apt-get -f install":

```
ben@ben-ubuntu:~$ sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-2.6.37-7-generic (2.6.37-7.18) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-7-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-7-generic /boot/vmlinuz-2.6.37-7-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-7-generic /boot/vmlinuz-2.6.37-7-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-7-generic /boot/vmlinuz-2.6.37-7-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-7-generic /boot/vmlinuz-2.6.37-7-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-7-generic /boot/vmlinuz-2.6.37-7-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-7-generic /boot/vmlinuz-2.6.37-7-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-7-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-7-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up memtest86+ (4.10-1.1ubuntu1) ...
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
dpkg: error processing memtest86+ (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on memtest86+; however:
  Package memtest86+ is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.99~20101126-1ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          grub-probe: error: cannot find a device for / (is /dev mounted?).
Installation finished. No error reported.
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.37-7-generic; however:
  Package linux-image-2.6.37-7-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.37.7.9); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.37-7-generic
 memtest86+
 ubuntu-standard
 grub-pc
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Here's what's mounted:

```
/dev/sda5 on / type btrfs (rw,compress,subvolid=257)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda6 on /home type ext3 (rw,commit=0)
/dev/sda7 on /media/safe type ext3 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda2 on /boot type ext2 (rw)
gvfs-fuse-daemon on /home/ben/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ben)
```

Given / and /boot are both mounted, and /boot is an ext2 fs, I don't see what's going wrong. I've attached the kern.log, but it's not very useful.

(unrelated problem: mouse and keyboard appear to be frozen when I reach the log-in screen; either nouveau is locking up, or something is preventing the drivers from loading quickly)

Edit: actually, looks like the first thing to fail is the kernel, but it's caused by something grub is doing.

[ATTACH]177010[/ATTACH]

---

### Post by cariboo on 2010-11-30
I had the same problem several weeks ago, it turns out in my case that grub wasn't pointing to the /boot partition and instead trying to boot from / where it couldn't find a kernel.

---

### Post by benjo316 on 2010-11-30
Did you fix it, do you remember how?

It's booting fine; Grub comes up and I can enter the new kernel and initrd.img manually, but one of the update scripts aren't finding one of either /boot or /.

---

### Post by cariboo on 2010-11-30
I did fix the problem by manually editing /boot/grub/grub.cfg entering the correct UUID. I eventually reinstalled Natty, as btrfs was so glacially slow, that is virtually unusable.

---

### Post by benjo316 on 2010-11-30
Definitely something wrong with grub; just booted into the maverick subvolume and upgraded the kernel, and it finished okay.

Edit:
grub bug here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/450260](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/450260)
Mouse/Keyboard bug here: [https://bugs.launchpad.net/ubuntu/+bug/684597](https://bugs.launchpad.net/ubuntu/+bug/684597)

---

### Post by Slug71 on 2010-12-04
I really hope the licensing issue is sorted out soon.

---

