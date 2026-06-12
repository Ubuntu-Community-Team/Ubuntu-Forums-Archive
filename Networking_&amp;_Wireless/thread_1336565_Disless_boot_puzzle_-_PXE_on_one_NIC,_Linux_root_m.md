---
title: "Disless boot puzzle - PXE on one NIC, Linux root mount using the other"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by Cracauer on 2009-11-24
I have the following diskless boot puzzle. I use pxelinux for the Linux clients.  

I have a machine with two ethernet devices: [list] 
[*] one device does PXE but has no Linux driver 
[*] the other device has a Linux driver but no PXE 
[/list]  

So what I need to do is this: 
[list]
[*]Bring up the kernel via PXE
[*]Tell the kernel to NFS-mount the root filesystem on the other NIC
[/list]

I am not sure how to do this. Normally, the diskless boot process passes in the PXE NIC which already has an IP address and is all set.

Obviously this would involve either getting a second IP address for the NFS mount (or to shut down the PXE nic but I don't think that's the way to go).

Here's the pxeboot entry:
```

label libber2
        kernel vmlinuz-2.6.31.6-blah
        append root=/dev/nfs ip=dhcp \
 		nfsroot=172.18.30.2:/home/diskless/debian-amd64-root2 \
 		init=/sbin/init verbose=8

```

Note that I cannot do this anywhere in the root filesystem, obviously, since it doesn't come up.

So the only way that this can go down is via kernel commandline parameters, of which I would need these:
[list]
[*]The ability to tell the kernel to use a different Ethernet device.
[*]The ability to tell the kernel the new IP address/netmask/etc, because obviously it does not have the ability to do DHCP lookup without the userland.
[/list]

Any kernel commandline wizards around?

---

### Post by puppywhacker on 2009-11-24
after you load the kernel you need to load an initrd with a minimum system that can initialize your second interface (the non-pxe one) so you can configure an ip-address and then pivot the root from the initrd to the nfs-filesystem.

initrd overcomes the famous circular problems like "you need diskaccess to access the modules that can access your disk". Or the driver for the CDROM drive is delivered on a CD. Your problem falls in the same catagory

you can make an initrd with mkinitramfs and then with cpio and mounting the filespace make any changes. And then update the kernel to load the initrd

kernel vmlinuz-2.6.31.6-blah initrd=loadmefirst

Then again, if your goal is to make a diskless server you may also skip the whole nfs loading and load the image as initrd.
kernel vmlinuz-2.6.31.6-blah initrd=debian-amd64-root2

---

### Post by Cracauer on 2009-11-25
Right, the thing is a whole filesystem.

But what is the equivalent to /etc/rc in the initrd?

Do they have a regular startup shellscript in there? And where does it get mounted?

---

### Post by richard_wu0313 on 2011-04-13
i have similar requirement. But my PXE NIC was down after i selected PXE boot menu, so only one NIC could get IP and installation could go on

---

