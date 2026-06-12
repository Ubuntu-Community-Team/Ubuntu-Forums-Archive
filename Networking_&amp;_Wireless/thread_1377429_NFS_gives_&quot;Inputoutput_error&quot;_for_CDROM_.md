---
title: "NFS gives &quot;Input/output error&quot; for CDROM on network"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by zcacogp on 2010-01-10
Chaps, 

I've been battling this one for a number of hours now, and am now out of solutions! 

I have a desktop machine, with a DVD drive in it, mounted at /media/cdrom0

I am trying to share this across a wireless network with two laptops, neither of them with CD drives in them. While I can see the cdrom drive across the network, whenever I try to open a file on it (typically something in VIDEO_TS), it doesn't allow me to access it. The error is "Error reading from file: Input/output error". 

If I try to open the DVD in the drive using movie player, I get the error "An error occurred. Could not read from resource."

A DVD in the drive on the server works fine - it plays in movie player and in VLC. 

Thus far I have tried various different settings in /etc/exports on the server and /etc/fstab on the laptops. I have tried the fixes mentioned in this thread: 

[http://ubuntuforums.org/showthread.php?t=817867&page=2](http://ubuntuforums.org/showthread.php?t=817867&page=2)

... namely, editing the 70-persistent-cd rules file (on the server and the client), and removing all links to block objects in /dev (on the server and the client), and even tried editing the /boot/grub/menu.lst on the server and the client, adding "all_generic_ide=1" in under # defoptions, and then running "sudo update-grub", as per the bug listed here: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/228624](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/228624)

The funny thing is that it doesn't always happen. It happens about 95% of the time, but occasionally, just occasionally, it works as it should and I can play a DVD across the network (which is what I am trying to do!) BUT I don't know what changes to make it work or fail - when it works I reboot to see if it will work reliably, and it then fails again. 

I would **really** appreciate any help anyone can offer in getting this one working. The machines are all on a private network, and all running 9.10 Karmic. The details of the individual machines are thus: 

**[COLOR="Red"]Server (desktop)[/COLOR]**: 9.10, kernel 2.6.31-17-generic, /etc/exports like this: 

```
# Allow the DVD Drive to be exported
 /media/cdrom0 192.168.10.1/24(rw,async,no_root_squash,no_subtree_check)


# Allow Helena to be exported
 /media/Helena 192.168.10.1/24(rw,no_root_squash,async,no_subtree_check)


# Allow Ianthe to be exported
 /media/Ianthe 192.168.10.1/24(rw,no_root_squash,async,no_subtree_check)
```

/boot/grub/menu.lst like this: 

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash all_generic_ide=1
```


**[COLOR="Red"]Laptop x61s:[/COLOR]** 9.10, kernel 2.6.31-17-generic, fstab like this: 

```
proc /proc proc defaults 0 0
# Entry for /dev/sda7 :
UUID=852bb28d-8c9b-4fc7-91ef-e632cd4297f4 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda8 :
UUID=671a8b44-04e7-4a9e-b9cb-2f9a6875f324 none swap sw 0 0
# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

/dev/sda6 /media/Ieuan ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda5 /media/Horatio ntfs-3g defaults,locale=en_GB.UTF-8 0 0


192.168.10.2:/media/cdrom0 /media/cdrom0 nfs rw,hard 0 0

192.168.10.2:/media/Helena /media/Helena nfs rw,hard 0 0

192.168.10.2:/media/Ianthe /media/Ianthe nfs rw,hard 0 0
```[B]

[COLOR="Red"]Laptop x31[/COLOR][/B]: 9.10, kernel 2.6.31-17-generic, fstab like this: 

```
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b0347238-90c3-4dfc-a370-1840d2f2ab35 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1acfa523-63bc-465f-82a5-5de88233f084 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

192.168.10.2:/media/cdrom0 /media/cdrom0 nfs rw,hard 0 0

192.168.10.2:/media/Helena /media/Helena nfs rw,hard 0 0

192.168.10.2:/media/Ianthe /media/Ianthe nfs rw,hard 0 0
```

The two other drives which are shared over NFS (Ianthe and Helena) both work fine. 

As a wildcard aside, I am also wondering whether it is related to a problem I have ejecting the DVD from the desktop (server) machine, which I have posted about here: 

[http://ubuntuforums.org/showthread.php?t=1376708](http://ubuntuforums.org/showthread.php?t=1376708)


Oli.

---

### Post by zcacogp on 2010-01-11
OK, update. I think this is semi-solved, so I'll mark it as solved. 

It appears that the success of viewing a DVD across the network depends upon the DVD. Some DVD's work every time. Some work very rarely. 

The ones that work every time work every time, as reliable as clockwork. 

The question is why some only work about one time in twenty. These ones will work every time when viewed on the machine which they are placed in, so it seems to be something to do with a combination of any one DVD and viewing it across an NFS network. Next step is to try it across a Samba network. (Which is a pain, and I have never had much success with Samba networks. Ho humm.) 


Oli.

---

