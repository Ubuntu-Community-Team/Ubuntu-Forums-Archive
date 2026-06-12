---
title: "install fails at partitioning discs."
date: 2010-09-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bj0 on 2010-09-15
I'm trying to install 10.10 on an old laptop (asus s5n), and when the installer pops up, after asking the usual keyboard questions, pops up the following error:

```

This partitioner doesn't have information about the default type of partition tables on your architecture.  Please send an e-mail message to debian-boot@lists.debian.org with information.

Please note that if the type of the partition tables is unsupported by libparted, then this partitioner will not work properly.

```
This error doesn't really say anything helpful or even what information to send...

The laptop has 10.04 installed on it already, but I want to wipe it out with a fresh install of 10.10.  It gives me the option to continue anyway, so I do and select the partition method: "Guided -- use entire disk".

It then pops up and asks me to:
```

Select the type of partition table to use.

```

with several options: aix,amiga,bsd,dvh,gpt,mac,msdos,pc98,sun,loop.

I tried msdos, pc98, and gpt, not sure what I am supposed to pick, but it fails on the step "install the base system" after that.

I'm installing over pxe, using the netboot/ directory from the archive.ubuntu.com server.

Is this a known issue? Any information that would help figure out what is going on?

---

### Post by dino99 on 2010-09-15
better to prepare your partitions before installing, boot on partedmagic then prepare / , swap, /home (if not existing yet). when done, instead of automatic installation, use manual installation and select partitions made by partedmagic

[http://partedmagic.com/](http://partedmagic.com/)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by ranch hand on 2010-09-15
Die you check the md5sum on the ISO?

---

### Post by bj0 on 2010-09-15
There was no iso, as I said I was using the netboot/ files from the server.  I think this was the problem, though, I downloaded the .iso and booted into the LiveCD install and it's installing fine from that.

---

### Post by srs5694 on 2010-09-15
Please post the output of "sudo fdisk -l" on the computer. Also, if you've got any external storage devices, like USB flash drives, plugged into the computer, unplug them.

---

### Post by xebian on 2010-09-15
> **bj0 said:**
> There was no iso, as I said I was using the netboot/ files from the server.  I think this was the problem, though, I downloaded the .iso and booted into the LiveCD install and it's installing fine from that.

I had the same problem with the netboot(09/13/2010) a while ago.  I got the same warning and can only recognize the usb stick installer.  Could not detect the HD.  Had to abort.

---

### Post by bj0 on 2010-09-16
Yea, i just tried with the latest 'linux' and 'initrd.gz' from the server.

This time I did it in Virtualbox just for testing (with bridged adapter), and I am having the same issue.

To test my pxe setup I tried the same with 10.04 and it detected the disk drive fine.

---

### Post by bsmith1051 on 2010-09-16
> **dino99 said:**
> better to prepare your partitions before installing, 
That's not very helpful, you know.  The goal isn't simply to get it working but to figure-out if there's something wrong with the install routine.

---

### Post by bj0 on 2010-09-16
> **bsmith1051 said:**
> That's not very helpful, you know.  The goal isn't simply to get it working but to figure-out if there's something wrong with the install routine.


Also, it still fails to install even if you prepare your partitions beforehand

---

### Post by xebian on 2010-09-16
There's a brand new boot.img today (9/16/2010) but haven't checked it yet.  I doubt it's the installer as it gets the partitioner from the repo.

---

