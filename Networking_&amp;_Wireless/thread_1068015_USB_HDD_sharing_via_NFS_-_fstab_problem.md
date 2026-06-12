---
title: "USB HDD sharing via NFS - fstab problem?"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-02-12
I have an external USB HDD that I'm sharing between two laptops on a LAN via NFS. When the drive is plugged into a computer, it gets auto-mounted to /media/disk like it always has. The remote computer simply has to execute *sudo mount -a* from a terminal to get the drive to mount.

Now that the drive is being shared, though, unmounting **has to** be done in a terminal. Also, the unmounting has to be forced, since when trying to unmount, it says the 'device is busy' or something to that effect (since NFS is sharing it).

It's good that the drive can be shared while it's plugged into either computer, but what if I just want to unplug the thing and shut it off for a while? What if I'm away and the wife can't remember how to structure the command to forcibly unmount it?

How can I share this drive between two computers when it's mounted, and still be able to right-click on the desktop icon to unmount it like it used to be? I've been working for a week and a half trying to share this drive via Samba (since both laptops are dual-boot), but it's formatted FAT32 and I'm running into problems doing that.

Here's my fstab (the one on the wife's comp looks very similar, just the names are reversed)```
zero@zero-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0623c79f-b11d-4940-8f98-8f816ec68149 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b2970eb6-0267-4fc6-97c2-08f92837eed2 /home           ext3    relatime        0       2
# /dev/sda5
UUID=8887efa3-3b11-44e1-b24f-2f982a06bb72 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
princess-laptop:/home/princess/Public /home/zero/Sharepoints/Princess nfs rsize=8192,wsize=8192,timeo=14,intr
princess-laptop:/media/disk /home/zero/Sharepoints/USB nfs rsize=8192,wsize=8192,timeo=14,intr
```I can't think of any other info to provide. If anything else is needed, just let me know.

---

### Post by detroit/zero on 2009-02-14
Bump.

---

### Post by scratman on 2009-02-17
I think you are going to have problems with that one.  For a start, if you're using a sudo mount command to mount it, it will require a sudo umount command to unmount it.  Unless your wife has administrator access, this will not be possible for her.  However, if she does, you could probably just create a shell file with the commands, save it to her home folder, and just give instructions to explain how to run it.

---

### Post by detroit/zero on 2009-02-18
> **scratman said:**
> I think you are going to have problems with that one.  For a start, if you're using a sudo mount command to mount it, it will require a sudo umount command to unmount it.  Unless your wife has administrator access, this will not be possible for her.  However, if she does, you could probably just create a shell file with the commands, save it to her home folder, and just give instructions to explain how to run it.
Well, the thing is that the drive automounts to /media/disk on both computers when the USB cable is plugged in. The entries in fstab are for the second computer (i.e., the one the drive is not physically connected to) to mount the remote location to the created ~/Sharepoints/USB folder. The Public folder on both computers doesn't need any special treatment; it can be mounted/unmounted/shared/unshared (either as the folder it is on the computer it's actually in, or as a share on the remote comp) etc without any terminal commands at all. Since that's being mounted to the same ~/Sharepoints/NAME I figure it's a quirk with the handling of a FAT32 driv that's being shared. It could be anything, really, though.

I should have posted back, but I've been real short on time since I made this post. Since rebooting both computers, the external drive can be unmounted by a simple right-click on whichever computer it's plugged into, but I still get the message that says  the device is busy. I assume it's because NFS is sharing it, but I could be totally wrong.

---

