---
title: "Any way to re-install/correct grub"
date: 2022-08-10
forum: MINT
---

### Post by Kris_M on 2022-08-10
Was using grub-customizer on Mint 20.3
Upgraded up Mint 21 which removed grub-customizer.
Now when I grub-upgrade the first boot grub menu item is wrong - has pointer to old kern.
advanced is fine.
/boot/grub/grub.cfg has 6 pointers to old proxies.
How fix
Or
How uninstall and re-install grub so it is correct?
Thanks

---

### Post by howefield on 2022-08-10
Thread moved to a more appropriate forum.

---

### Post by oldfred on 2022-08-10
If you can boot, just reinstall grub.
Or use Boot-Repair from live installer. Usually choose advanced mode for full reinstall, over any default that may just update menu.
Or chroot into system from live installer & reinstall grub.

I prefer to learn how to edit grub over using grub-customizer.
But you have to manually edit files.

---

### Post by Kris_M on 2022-08-10
> **oldfred said:**
> If you can boot, just reinstall grub.
Or use Boot-Repair from live installer. Usually choose advanced mode for full reinstall, over any default that may just update menu.
Or chroot into system from live installer & reinstall grub.

I prefer to learn how to edit grub over using grub-customizer.
But you have to manually edit files.

Thanks!
I corrected the first menu item by editing /boot/grub/grub.cfg though I think that will go wonky again if I run sudo update-grub
I can boot and am on it now - how would I "just reinstall grub"?
Thanks!

---

### Post by oldfred on 2022-08-10
Is it an UEFI install & is correct entry in fstab to mount ESP?
Grub will auto find ESP and use it, otherwise you have to add parameters. Or if you want grub in a different drive, or different name in UEFI menu
Defaults normally just work, if in your install. You can see all the parameters:
man grub-install

sudo grub-install
sudo update-grub

Should return with no errors.

If using live installer you then have to also mount partitions, chroot or use Boot-Repair to install grub to internal drive.

---

### Post by Kris_M on 2022-08-10
> **oldfred said:**
> Is it an UEFI install & is correct entry in fstab to mount ESP?
Grub will auto find ESP and use it, otherwise you have to add parameters. Or if you want grub in a different drive, or different name in UEFI menu
Defaults normally just work, if in your install. You can see all the parameters:
man grub-install

sudo grub-install
sudo update-grub

Should return with no errors.

If using live installer you then have to also mount partitions, chroot or use Boot-Repair to install grub to internal drive.

actually I just tried that but it still grabs the old stuff
```
sudo grub-install /dev/nvme0n1
sudo update-grub
```

yes, UEFI

there's a bunch of old proxies in grub.d that have old incorrect stuff, particularly 06,40,41,46

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290834&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=290834&stc=1[/IMG]

---

### Post by oldfred on 2022-08-10
Then try this:

sudo apt-get install --reinstall grub-efi-amd64

Not sure if reinstall will overwrite existing proxy files.
You may need this, to purge & create new empty /boot/grub folder:
sudo apt purge grub grub-efi-amd64 grub-common   #Once you run this system will not be bootable. So be sure to have a bootable live installer.
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub

---

### Post by Kris_M on 2022-08-10
> **oldfred said:**
> Then try this:

sudo apt-get install --reinstall grub-efi-amd64

Not sure if reinstall will overwrite existing proxy files.
You may need this, to purge & create new empty /boot/grub folder:
sudo apt purge grub grub-efi-amd64 grub-common   #Once you run this system will not be bootable. So be sure to have a bootable live installer.
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub

I don't think that will work because it doesn't get rid of the old proxies that are messing things up..
I think the only thing that would fix it is a complete new install.

What I did, was:
The script is 
/etc/grub.d.proxifiedScripts/custom

If I change the first entry in there (named ubuntu) to the latest kern, It boots to that and survives through boot. That's 3 lines where I just correct the kern number.

However, /boot/grub/grub.cfg looks terrible: says 46,46,46,43 etc. HOWEVER, when I boot, menu looks correct... 

So that fixes the first line in the grub boot menu.
I will probably have to manually change that with each new kern but that's not a prob as it takes about a minute and I would have had to do that if I still had grub-customizer.
Easy enough, so call this fixed. Thanks for your time!!!!!

---

### Post by oldfred on 2022-08-10
You can turn off execute bit on the proxy files, if you have the grub files.
The update-grub runs all the files in /etc/grub.d/that have execute and two numbers & underscore to start.

I turn off os-prober, although also a setting in /etc/default/grub. You can change almost all scripts as grub only need 3 or 4 to create a grub.cfg file.
sudo chmod a-x /etc/grub.d/30_os-prober

a-x means all (owner, group, other)  and remove x (execute)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Kris_M on 2022-08-11
Yes, I could turn off the execute bit. What I did at some point yesterday is move the 4 proxies to a sub folder and then ran update-grub - This gave me a menu with ONLY windows - NO linux .

The problem is that I do not have the original contents of grub.d (and a few other files or folders) and thus the original scripts. Yes I could build a new, dummy system and copy those contents over but I would never get all the files I need to make THIS build work as grub intended. Much work and no likely payoff.

The only thing I would gain is to have it automatically update the first grub boot menu line when new kern comes down the pike.

I can do that in less than a minute, manually.

---

### Post by oldfred on 2022-08-11
Ithought grub-customizer put the orginal grub files into a backup folder.
You showed a backup folder in grub which is not standard.

But a total reinstall of grub should reinstall all the grub files.

Years ago I saw you only needed standard 00_, 05_ and your own creation of a 06_custom.
The 06_ or a 40_custom which I use has what ever custom boot stanzas you want.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
Mega post of examples. May want to start at end & work backwards for latest examples.
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by Kris_M on 2022-08-11
I had not looked at the backup folder, so did so and restored everything and ran update-grub and got

```
kris@kris-ThinkPad-T570:~$ sudo update-grub
[sudo] password for kris:  
Sourcing file `/etc/default/grub.d/50_linuxmint.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
kris@kris-ThinkPad-T570:~$ 

```

So I have marked this solved as I have what I need and am done with it. I will put my time elsewhere.
Thank you for your time!
DONE!

---

### Post by oldfred on 2022-08-11
If you have this, then you have an error somewhere, either in a script or in /etc/default/grub.
> /boot/grub/grub.cfg.new

Your grub.cfg did not get updated. The .new is the file with an error.
I got that error once when I missed a closing } in 40_custom.
Problem was it said error was on last line when it was in middle of file.

---

### Post by Kris_M on 2022-08-11
yes I know what it says.
I did realize I made a stupid mistake so I just did it again, correctly following the instructions in the backup folder and got

```
kris@kris-ThinkPad-T570:~$ sudo update-grub
[sudo] password for kris:  
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50_linuxmint.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
kris@kris-ThinkPad-T570:~$ 
```

instructions:
```
How to restore this backup
--------------------------
 * make sure you have root permissions (`gksu nautilus` or `sudo -s` on command line) otherwise you won't be able to copy the files
 * to fix an unbootable configuration, just copy:
     * '/etc/grub.d/backup/boot_grub' to '/boot/grub'
 * to reset the whole configuration (if it cannot be fixed by using grub customizer), also copy these files:
     * '/etc/grub.d/backup/etc_grub_d' to '/etc/grub.d'
     * '/etc/grub.d/backup/default_grub' to '/etc/default/grub'
```


This is probably because the old grub.cfg points to stuff that doesn't exist now.

When I tried it with the current grub.cfg I got same thing.

---

### Post by oldfred on 2022-08-11
This is my grub.d, looks like your scripts are not running?

```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l /etc/grub.d [/COLOR]
total 136 
-rwxr-xr-x 1 root root 10627 Apr 15 16:50 [COLOR=#54ff54]**00_header**[/COLOR][COLOR=#000000] [/COLOR]
-rwxr-xr-x 1 root root  6260 Apr 15 16:50 [COLOR=#54ff54]**05_debian_theme**[/COLOR][COLOR=#000000] [/COLOR]
-rwxr-xr-x 1 root root 18683 Apr 15 16:50 [COLOR=#54ff54]**10_linux**[/COLOR][COLOR=#000000] [/COLOR]
-rwxr-xr-x 1 root root 43031 Apr 15 16:50 [COLOR=#54ff54]**10_linux_zfs**[/COLOR][COLOR=#000000] [/COLOR]
-rwxr-xr-x 1 root root 14180 Apr 15 16:50 [COLOR=#54ff54]**20_linux_xen**[/COLOR][COLOR=#000000] [/COLOR]
-rwxr-xr-x 1 root root  2924 Feb  6  2022 [COLOR=#54ff54]**20_memtest86+**[/COLOR][COLOR=#000000] [/COLOR]
-rwxr-xr-x 1 root root 13369 Apr 15 16:50 [COLOR=#54ff54]**30_os-prober**[/COLOR][COLOR=#000000] [/COLOR]
-rwxr-xr-x 1 root root  1372 Apr 15 16:50 [COLOR=#54ff54]**30_uefi-firmware**[/COLOR][COLOR=#000000] [/COLOR]
-rwxrwxrwx 1 fred fred  1732 Jul 24 11:00 [COLOR=#54ff54]**40_custom**[/COLOR][COLOR=#000000] [/COLOR]
-rwxr-xr-x 1 root root   215 Apr 15 16:50 [COLOR=#54ff54]**41_custom**[/COLOR][COLOR=#000000] [/COLOR]
-rw-r--r-- 1 root root   483 Apr 15 16:50 README


[/FONT]
```

---

### Post by Kris_M on 2022-08-11
> **oldfred said:**
> This is my grub.d, looks like your scripts are not running?

```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ ls -l /etc/grub.d [/COLOR]
total 136 
-rwxr-xr-x 1 root root 10627 Apr 15 16:50 [COLOR=#54ff54]**00_header**[/COLOR]
-rwxr-xr-x 1 root root  6260 Apr 15 16:50 [COLOR=#54ff54]**05_debian_theme**[/COLOR]
-rwxr-xr-x 1 root root 18683 Apr 15 16:50 [COLOR=#54ff54]**10_linux**[/COLOR]
-rwxr-xr-x 1 root root 43031 Apr 15 16:50 [COLOR=#54ff54]**10_linux_zfs**[/COLOR]
-rwxr-xr-x 1 root root 14180 Apr 15 16:50 [COLOR=#54ff54]**20_linux_xen**[/COLOR]
-rwxr-xr-x 1 root root  2924 Feb  6  2022 [COLOR=#54ff54]**20_memtest86+**[/COLOR]
-rwxr-xr-x 1 root root 13369 Apr 15 16:50 [COLOR=#54ff54]**30_os-prober**[/COLOR]
-rwxr-xr-x 1 root root  1372 Apr 15 16:50 [COLOR=#54ff54]**30_uefi-firmware**[/COLOR]
-rwxrwxrwx 1 fred fred  1732 Jul 24 11:00 [COLOR=#54ff54]**40_custom**[/COLOR]
-rwxr-xr-x 1 root root   215 Apr 15 16:50 [COLOR=#54ff54]**41_custom**[/COLOR]
-rw-r--r-- 1 root root   483 Apr 15 16:50 README


[/FONT]
```

that is (obviously ) because you have never run grub-customizer.
The saved grub.d is:
```
kris@kris-ThinkPad-T570:~$ ls -l /etc/grub.d/backup/etc_grub_d
total 128
-rw-r--r-- 1 root root 10627 Aug 30  2021 00_header
-rw-r--r-- 1 root root  6258 Aug 30  2021 05_debian_theme
-rw-r--r-- 1 root root 18151 Aug 30  2021 10_linux
-rw-r--r-- 1 root root 42359 Aug 30  2021 10_linux_zfs
-rw-r--r-- 1 root root 12894 Aug 30  2021 20_linux_xen
-rw-r--r-- 1 root root 12059 Aug 30  2021 30_os-prober
-rw-r--r-- 1 root root  1424 Aug 30  2021 30_uefi-firmware
-rw-r--r-- 1 root root   214 Aug 30  2021 40_custom
-rw-r--r-- 1 root root   216 Aug 30  2021 41_custom
-rw-r--r-- 1 root root   483 Aug 30  2021 README
kris@kris-ThinkPad-T570:~$ 

```

though they are dated aug 30 2021 they are probably from much earlier - that was just copied by one of the upgrades.

present grub.d:
```
kris@kris-ThinkPad-T570:~$ ls -l /etc/grub.d
total 240
-rwxr-xr-x 1 root root 10627 Nov 12  2020 00_header
-rwxr-xr-x 1 root root  6260 Apr 15 17:50 05_debian_theme
-rwxr-xr-x 1 root root   920 Aug  3 14:44 06_linux_proxy
-rwxr-xr-x 1 root root 18683 Apr 15 17:50 10_linux.dpkg-dist
-rwxr-xr-x 1 root root 43031 Apr 15 17:50 10_linux_zfs.dpkg-dist
-rwxr-xr-x 1 root root 14180 Apr 15 17:50 20_linux_xen.dpkg-dist
-rwxr-xr-x 1 root root 13369 Apr 15 17:50 30_os-prober.dpkg-dist
-rwxr-xr-x 1 root root  1372 Apr 15 17:50 30_uefi-firmware.dpkg-dist
-rwxr-xr-x 1 root root   700 Feb 20 22:06 35_fwupd
-rwxr-xr-x 1 root root   604 Aug  3 14:44 40_custom_proxy
-rwxr-xr-x 1 root root   215 Apr 15 17:50 41_custom.dpkg-dist
-rwxr-xr-x 1 root root  1903 Aug  3 14:44 41_linux_proxy
-rwxr-xr-x 1 root root 42359 Nov 12  2020 42_linux_zfs
-rwxr-xr-x 1 root root 12894 Nov 12  2020 43_linux_xen
-rwxr-xr-x 1 root root 12059 Nov 12  2020 44_os-prober
-rwxr-xr-x 1 root root  1424 Nov 12  2020 45_uefi-firmware
-rwxr-xr-x 1 root root   604 Aug  3 14:44 46_custom_proxy
-rwxr-xr-x 1 root root   216 Nov 12  2020 47_custom
drwxr-xr-x 4 root root  4096 Aug 30  2021 backup
drwxr-xr-x 2 root root  4096 Sep  8  2021 bin
drwxr-xr-x 2 root root  4096 Aug 10 19:43 proxifiedScripts
-rw-r--r-- 1 root root   483 Nov 12  2020 README
kris@kris-ThinkPad-T570:~$ 
```

We keep wasting more time with this. There is no solution to be found here. i really would like to move on to other things.

---

