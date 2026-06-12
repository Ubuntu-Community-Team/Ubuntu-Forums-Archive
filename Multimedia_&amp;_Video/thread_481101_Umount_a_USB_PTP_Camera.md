---
title: "Umount a USB PTP Camera"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by ianhaycox on 2007-06-22
I'm using the supplied USB cable with my Fuji F31 camera to transfer photos to KUbuntu but can't find any way to umount/safely remove the device once the transfer is complete.

I get a camera icon on the desktop but right-clicking does not give me a 'safely remove' option. If I plug in a USB Key then I do get the option.

The device is reported as a camera://USB PTP Class Camera@[usb:004,002] when I plug it in. Data transfer is really slow, but I can live with that. There are some posts on the same slow transfer rates but they didn't help me.

I'm using KDE if that makes a difference. I'd really like to be sure not to corrupt my data by unplugging incorrectly, so any help appreciated.


The output from mount

```
/dev/sdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sdb3 on /mnt/data type ext3 (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
/dev/sdb1 on /media/sdb1 type ntfs (rw,nls=utf8,umask=007,uid=0,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdc on /media/cdrom0 type iso9660 (ro,user=ian)
```

and the tail of dmesg shows 

```
[  223.067099] usb 4-8: new high speed USB device using ehci_hcd and address 2
[  223.200554] usb 4-8: configuration #1 chosen from 1 choice

```

output lsusb 

```
Bus 004 Device 002: ID 04cb:01c1 Fuji Photo Film Co., Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

---

### Post by zzztownsend on 2007-07-09
Hi Ian

I have the same camera, but I use Ubuntu (gnome). When I plug the camera in it is recognised as a USB PTP class camera, and the gThumb utiltiy autostarts allowing pictures to be transferred. The connection speed is fast and reliable and disconnects safely.

gnome does not mount the camera as a usb mass storage device using mount and I can't see anything in my (or your!) mount output which would correspond. 

You could try installing gThumb or reading up on how to get PTP transfers going in KDE

This works for me with one exception - where I have a video file on the camera this causes gThumb to crash and won't transfer it to the computer. Please post if you find a solution to this!

I am going to have a lie down now as I have exhausted my knowledge

Cheers

Matt

---

