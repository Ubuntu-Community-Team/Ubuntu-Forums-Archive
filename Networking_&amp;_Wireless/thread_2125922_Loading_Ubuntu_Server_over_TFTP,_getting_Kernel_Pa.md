---
title: "Loading Ubuntu Server over TFTP, getting Kernel Panic on client."
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by MGertz on 2013-03-15
Hi guys.

I'm new here at this forum, so i have i have posted the right place.

I have a tried setting up a TFTP server, and that part actually works.

I have been following this guide.
[http://www.stevekelly.eu/cluster.shtml](http://www.stevekelly.eu/cluster.shtml)
But someplaces i have been editing a little bit.

my pxelinux.cfg/default file looks like this.
```
LABEL Ubuntu Server CloudNode
DEFAULT vmlinuz-3.5.0-23-generic
APPEND root=dev/nfs initrd=initrd.img nfsroot=10.0.0.200:/NFSROOT/ ip=dhcp rw

```

And the clients loads the vmlinuz-3.5.0-23-generic

But under the boot process they stalls with this error.

```

VFS: Cannot open root device "(null)" or unknown-block(2,0): error -6
Please append a correct "root=" boot option; here are the available partitions:
0b00      1048575  sr0   driver: sr
Kernel panic - not syncing: NFS: Unable to mount root fs on unknown-block(2,0)
Pid: 1, comm: swapper/0 Net tainted 3.5.0-23-generic #35~precise1-Ubuntu

```

I hope you guys can help me fix this issue.

---

### Post by matt_symes on 2013-03-15
Hi

> root=dev/nfs

Try this.

> root=**/**dev/nfs

Kind regards

---

### Post by MGertz on 2013-03-18
That didnt fix it.

---

### Post by matt_symes on 2013-03-19
Hi

I am setting up a pxe boot server today, something i have been meaning to to do for an age now, as i want the ability to boot a live CD for computers that are having trouble booting from USB or CD/DVD for various reasons. I'm currently downloading the alternate ISO and lubuntu 12.10 as a test environment.

I am following these guides.

[http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/](http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/)

and 

[http://www.serenux.com/2010/05/howto-get-an-ubuntu-live-cd-to-boot-off-a-pxe-server/](http://www.serenux.com/2010/05/howto-get-an-ubuntu-live-cd-to-boot-off-a-pxe-server/)

and the official pxeboot help from help.ubuntu.com.

I'll report back on how i get on. If i can get it working then hopefully that'll provide some insight into your problem.

Kind regards

---

