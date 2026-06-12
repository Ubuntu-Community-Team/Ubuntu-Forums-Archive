---
title: "install ubuntu on samba"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by DJJo on 2009-08-18
hi

I want to install ubuntu 9.04 on a samba share.
because i know that you alwas need sonting on your local harddisk.
so i thought of putting /boot on my local drive.
does someone know hou to do this?

---

### Post by fela on 2009-08-18
That would be terribly slow in 99% of cases. You can try it though.

This requires major hackwork/kludginess/guesswork! I think. You can try (don't follow this exactly - only do this if you know alot about Linux and know how to do what I tell you to do, plus only if you know exactly what each step does). This is only a rough guide and not even 50% guaranteed to work).

1) Boot up ubuntu LiveCD

2) Make sure that the samba server is up

3) Make sure you have enough network bandwidth to run Linux off the samba share. Do not do this if it's less than 100MB/s, is my philosophy. If you don't want an incredibly slow system.

4) On the livecd, install smbfs

5) On the livecd, add an entry to the fstab for the samba share, using smbfs as the fs type

6) run sudo mount -a on the livecd

7) Select install OS on the livecd, partitioning manually and creating a small (no smaller than 100MB I advise though) partition as ext3 for the boot partition (on a local drive) - and use the samba share for the root partition. Doubt it will work but you can try.

8) When the system installs successfully (doubt it lol) - stay on the livecd. Chroot onto the samba share, and run:

```
sudo apt-get install smbfs
```

9) still chrooted, run sudo update-initramfs -u

Now reboot and see if it doesn't work or not (I bet you 1,000,000,000 that it doesn't work).

Again, this is just speaking merely from my head without any experience using samba as a root partition. I don't even think it's possible unless you compile smbfs into the kernel and make it automatically detect the network when the kernel loads (I know how to do the latter). It would need to be built in and not a module. You could try compiling a patch for it I guess. Good luck, you'll need it! :(

EDIT: sorry for the typo if you saw it (I accidentally said sshfs instead of smbfs, lol)

---

### Post by DJJo on 2009-08-18
Thanks for your comment.

I do not need a fast system because i want to use it for XDMX.

it is a Distributed Multi-head X server. so i can use my computer as a video card.

u with you idea i can install it on the live cd

---

### Post by fela on 2009-08-18
> **DJJo said:**
> Thanks for your comment.

I do not need a fast system because i want to use it for XDMX.

it is a Distributed Multi-head X server. so i can use my computer as a video card.

u with you idea i can install it on the live cd

Did you actually try it then?

By the way, NFS (instead of SMBFS) is known to work in the way you want it. Only thing is, the server has to be Linux (unless there's a windows NFS server). I think you have to compile a custom kernel though, to make it bootup.

---

### Post by DJJo on 2009-08-18
I dont know. but it is woth a try.

i dit a test on 2 virtallboxes (installed)

---

### Post by DJJo on 2009-08-18
> **DJJo said:**
> I dont know. but it is woth a try.

i dit a test on 2 virtallboxes (installed)

i does not work because i can not reboot the system.
to open port 6000. 
[http://en.allexperts.com/e/x/xd/xdmx.htm](http://en.allexperts.com/e/x/xd/xdmx.htm)

---

### Post by fela on 2009-08-18
> **DJJo said:**
> i does not work because i can not reboot the system.
to open port 6000. 
[http://en.allexperts.com/e/x/xd/xdmx.htm](http://en.allexperts.com/e/x/xd/xdmx.htm)

Yes, I think you have to compile a custom kernel with smbfs and automatic DHCP configuration. It's much easier with NFS as there are plenty of howtos telling you how to run your root partition on a remote NFS share. You can even put your boot partition on a USB stick, floppy drive or CD if you want an entirely harddisk-less system (it's possible ;))

---

### Post by DJJo on 2009-08-19
Do you know to do that on the Alternate install cd?
and where i can find a totorial?

---

### Post by DJJo on 2009-08-19
> **DJJo said:**
> Do you know to do that on the Alternate install cd?
and where i can find a totorial?
no buddy??
install on samba does not work. i can not find my share dir

---

### Post by DJJo on 2009-08-20
after long searching dit i find a link.
[https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot](https://help.ubuntu.com/community/Installation/OnNFSDriveWithLocalBoot)
i am still testing it on my box.

> Edit BOOT=local to read BOOT=nfs

shute be

>  Edit "BOOT=local" to "BOOT=nfs" 

---

### Post by DJJo on 2009-08-22
I have him working no my laptop but.
I got to disable the networkmanager. and nou i want to conect my wifi.
so hou do i does theat with out my networkmanger.

---

