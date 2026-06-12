---
title: "Sharing CD drives over ethernet"
date: 2010-06-08
forum: Multimedia Software
---

### Post by akester on 2010-06-08
Kinda a random question...
I was wondering if you can emulate a cd drive over the network.  Something like NFS, where it is mounted like a local drive.

I am creating a CD duplicator but cannot seem to find a large enough case lying around.  What I was thinking was to have one system be the main dekstop (with keyboard, monitor, etc) and another be a slave that holds 3 or 4 cd drives that the main desktop can write to.

I know this is vauge, and kinda weird... I'm sure not many people run into this.

Thanks for any help!

---

### Post by pytheas22 on 2010-06-08
I don't think it's exactly what you want, but you can turn your CDs into ISO images, and then share them remotely via NFS.  On the remote machines, you can mount the ISO images as loopback devices with a command like:
```

mount /nfs/share/image.iso -o loop -t iso9660 /some/mountpoint
```

Or even easier, if you have a graphical environment on the remote computers, you can simply right-click on the ISO image and select "Open with Archive Mounter."  This produces the same effect as putting the CD in your drive.

If you need to write data to the CDs, however, this method won't really work, since ISO images can only be mounted read-only.  In principle you could get around this limitation by unpacking the images, writing to them and then packing them back up, but that gets very complicated.

---

### Post by akester on 2010-06-08
yea, I would need to write data.  It would be something where the remote cd drives show up as local cd drives on the main system.
I'll try to explain it better:
CD DRIVE >>> UBUNTU (/dev/cdrom)
CD DRIVE >>> NETWORK >>> UBUNTU (/dev/cdrom1)

---

### Post by pytheas22 on 2010-06-08
I have no idea whether it would work or address your needs, but you might be able to use NFS to share the /media directory of the remote computer.  Since that's where Ubuntu creates mountpoints when it auto-mounts CDs, you should be able to read and write to the CD from remote machines by accessing its mountpoint.

Otherwise, I don't know of a good way to do this.  I feel like it is possible to do, because our remote console for our blade server rack at work allows us to pass local media from a workstation to the blade server, and I'm pretty sure that's all Linux-based.  Unfortunately, I have no idea how exactly that magic is achieved, and I can't find instructions anywhere.

---

### Post by akester on 2010-06-08
I'll try that.  Thanks for the help!

---

