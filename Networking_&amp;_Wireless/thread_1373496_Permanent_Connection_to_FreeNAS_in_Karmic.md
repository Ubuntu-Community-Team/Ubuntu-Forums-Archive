---
title: "Permanent Connection to FreeNAS in Karmic?"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by rbscairns on 2010-01-05
After many years of M$, I am tying Ubuntu on one of my office computers. All the other office computers are still on M$ XP (hopefully not for long). So far Ubuntu Karmic is great and I am hoping to stick with it now and into the future. My Ubuntu computer system is-
[INDENT]Make = ASUS eee B202
CPU = Intel Atom 270 @ 1.6GHz
RAM = 2MB of DDR2-533 SO-DIMM
HDD = 160GB SATA @ 5,400 RPM
Wireless = 802.11 b/g/n
OS = Ubuntu 9.10 (stock)[/INDENT]This is connected via WLAN to a router to my office system. The wireless router is-
[INDENT]Netgear RangeMax WPN824v3[/INDENT]This is connect via a wired LAN to my office network attached storage (NAS). My NAS system is-
[INDENT]Make = ASUS eee B202
CPU = Intel Atom 270 @ 1.6GHz
RAM = 1 GB of DDR2-533 SO-DIMM
HDD = 360GB SATA @ 5,400 RPM
Software = FreeNAS 0.7RC2
Services = CIFS/SMB enabled
OS = FreeBSD 7.2[/INDENT]
Things are going well. I can connect to my NAS using Places>Network and double-clicking on the NAS icon. I currently have to do this each time I log in.

What I would like to do is make this connection "permanent", meaning that it will automatically mount my NAS when I log in to Ubuntu and display an icon for the NAS on my desktop.

I have searched but found nothing to guide me in this quest. I would appreciate it if someone here could point me in the right direction.

---

### Post by Loosewheel on 2010-01-06
Hi rbscairns,
I mount NFS files with an entry in '/etc/fstab'.
'man fstab' in a console gives usage. Here's a nfs share in my fstab file.
'server2:/home/usrname/dir /home/usrname/dir nfs rsize=8192,wsize=8192,nosuid,soft	0	0' 
(all on one line).
And here is a excerpt from 'http://en.wikipedia.org/wiki/SMBFS',
"The Linux kernel includes two SMB client implementations that use the Linux VFS, providing access to files on an SMB server through the standard file system API: smbfs and cifs. Also it is possible to mount the whole hierarchy of workgroups/servers/shares ("neighborhood") through fuse kernel module and its userspace counterpart fusesmb."

Right direction?

---

### Post by rbscairns on 2010-01-07
Thanks Loosewheel. That gives me something more to study (good). I'll come back if I get (probably) stuck.

---

