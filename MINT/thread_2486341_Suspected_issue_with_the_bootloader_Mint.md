---
title: "Suspected issue with the bootloader Mint"
date: 2023-04-26
forum: MINT
---

### Post by nedpfeiffer on 2023-04-26
Hello all,

A couple of hours ago I tried installing Linux Mint on an external SSD using my laptop. I think somewhere in the process Linux Mint changed GRUB, I'm not certain. But now I can't boot into Ubuntu, which is installed on the laptop's internal NVME drive. I tried running boot-repair and it didn't automatically detect any issues. Here are the logs for those who are curious: [https://pastebin.ubuntu.com/p/4mXYywn642/](https://pastebin.ubuntu.com/p/4mXYywn642/) 

I'm certain I didn't overwrite my Ubuntu installation with Linux Mint, I was very careful not to do so. I have backups of all my file fortunately, but they are dated by a couple of weeks. I'd really appreciate any help, thank you!

---

### Post by oldfred on 2023-04-26
Moved to Mint sub-forum.

Do not know Mint, but I believe it is based on Ubuntu. And uses the same installer with this bug. New Ubuntu, but not flavors now have new installer that may fix issue.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

With external connected can you boot into internal install?
If so reinstall grub from within internal install making it default install.
sudo grub-install

To fix external drive, you need to add an ESP - efi system partition as FAT32 with boot,esp flags.
And change fstab to use that ESP, not internal drive's ESP.
And then reinstall grub which will then use UUID of fstab entry on external drive for grub's files.
External drive will not have Ubuntu entry in UEFI, but will boot just like live installer from UEFI:XXX where XXX is name or label of external drive.

You also can fix boot by editing the  grub in ESP with correct UUID for internal install.

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /boot/efi/EFI/ubuntu/grub.cfg [/COLOR]
search.fs_uuid [COLOR=#ff0000]9da6b198-e2ca-4e27-8a18-6daf4ecfc324[/COLOR] root  
set prefix=($root)'/boot/grub' 
configfile $prefix/grub.cfg
[/FONT]
```

And see UUID with  & showing just my / partition's UUID as I have many partitions.
lsblk -f

[FONT=monospace][COLOR=#000000]nvme0n1p4 ext4   1.0   jammy     [/COLOR][COLOR=#ff0000]9da6b198-e2ca-4e27-8a18-6daf4ecfc324[/COLOR][COLOR=#000000]   11.4G    55% /[/COLOR]



[/FONT]

---

