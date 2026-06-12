---
title: "Using a Guarddog firewall with Ubuntu"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by GlenDobbs on 2008-12-26
One of the problems I ran into trying to use the Guarddog firewall with Ubuntu was Ubuntu uses mawk vs gawk which was expected. I originally configured and saved the firewall script using a Mepis 6.5 live CD distro, but when I tried to run the script under Ubuntu the problem surfaced. Since it is a very good firewall I finally developed the following workaround so I can use it with Ubuntu:

I setup my disk with two partitions, one for Ubuntu 8.04 and one for Slackware 12.1. Once both have been installed and initialized with the firewall script loaded in Slackware under /etc/rc.d/rc.local, I then boot into Ubuntu normally and in a terminal mount the Slackware partition:

> sudo mount -t ext3 /dev/sda1 /mnt
> sudo mount -t proc proc /mnt/proc
> sudo chroot /mnt
# /etc/rc.d/rc.local
issue ctrl D to go back to Ubuntu
> sudo umount /mnt/proc
> sudo umount /mnt
> exit - and go back to using Ubuntu with guarddog firewall protection!

In my case I don't install a boot loader for Slackware and just access it with the install DVD, but if you install Slackware first Ubuntu will find it and make it bootable when grub is installed.

Anyone who would like a copy of the firewall script can email me and I'll send it to them.  email glen.dobbs at googlemail.com or gmail.com

Ciao

---

