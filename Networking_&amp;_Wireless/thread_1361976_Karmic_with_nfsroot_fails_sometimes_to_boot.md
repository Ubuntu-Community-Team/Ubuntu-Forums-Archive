---
title: "Karmic with nfsroot fails sometimes to boot"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by der-brumm-baer on 2009-12-22
Hello,

I have a Karmic FileServer with nfs shares and TFTP server on it.
The DHCP and forwarding does my IPFire Firewall.
Both are running in KVM Virtual Machines.

Now I try to boot via nfsroot from a Zotac ION Board as a MediaCenter.

I installed a Karmic 9.10 Live CD to an USB Harddisk and then copied the root to the fileserver.
I changed the initrd to boot from a nfs-share and removed the Network-Manager.

After some other Steps I boot the System from the nfs-share an it comes up completely to the Desktop. 
But after some reboots it stops some times, with the message that it couldn't mount the root filesystem.
There ist also the message that rpc.statd didn't start.
Also when I add another nfs-share to the fstab it won't come up.
When I try to mount the share in the fstab, when the system is up, it works, so it couldn't be the line in the fstab.

I hope you can help me to solve this Problem

Greetings
Sven

---

