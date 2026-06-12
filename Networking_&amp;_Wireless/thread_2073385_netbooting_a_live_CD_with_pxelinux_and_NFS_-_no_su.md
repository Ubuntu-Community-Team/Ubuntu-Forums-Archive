---
title: "netbooting a live CD with pxelinux and NFS - no success"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by deruberhanyok on 2012-10-19
Hello all,

I've been trying to netboot a live CD and keep running into errors. I've followed a bunch of tutorials and tried every configuration setting I can think of to no avail.

We're using Windows Server 2008 for DHCP, TFTP, NFS. Eventually we want to do a custom spin of Ubuntu to netboot on our network, but for now I'm just trying to get the regular Live CD to work.

So I've decided to go back and start from scratch following the instructions laid out [here]("https://wiki.ubuntu.com/LiveCDNetboot") as closely as I can given that I have a Windows server.

Switching to a linux server is not an option.

I have:

-configured tftp at "tftpboot\"
-configured nfs at "nfssrv\"
-taken the ISO files for 9.10 and 12.04 and extracted their entire contents to "nfssrv\ubuntu910x64" and "ubuntu1204x64"
-copied the "casper\initrd.lz" and "casper\vmlinuz" files from both to their respective directories of "tftpboot\ubuntu910\" and "tftpboot\ubuntu1204\"
-set up a boot menu with these two entries plus one for clonezilla:

```

menu label Ubuntu 9.10
kernel=ubuntu910/vmlinuz
append boot=casper netboot=nfs nfsroot=x.x.x.x:/nfssrv/ubuntu910x64 initrd=ubuntu910/initrd.lz --

menu label Ubuntu 12.04
kernel=ubuntu1204/vmlinuz
append boot=casper netboot=nfs nfsroot=x.x.x.x:/nfssrv/ubuntu1204x64 initrd=ubuntu1204/initrd.lz --

```

-allowed anonymous access via NFS permissions
-set the "all machines" to have read/write permissions
-allowed root access for NFS

So far:

pxeboot works just fine, as does TFTP and my menu setup. I can verify the connection to the server works as I can boot and run clonezilla (although that is fetching the filesystem.squashfs via tftp and executing it locally, so it doesn't help with troubleshooting NFS).

When selecting an Ubuntu option from my menu - I'm testing with both 12.04 and 9.10, since 9.10 was the latest version listed in the above linked tutorial - vmlinuz and initrd load properly. I then get the various scrolling texts and I get to a splash screen, only to get dumped back to busybox shortly thereafter.

The problem always comes back to the same thing: the errors in casper.log show that it can't find any files. For whatever reason, it is prefixing "/root" to everything. Rather than look for "/dev/" it's looking for "/root/dev", for example. I don't know if this is normal behavior, but it's where the log stops so I assume it isn't.

If I change "boot=casper" to "boot=nfs" in the entries, the system seems to get farther, but then I get:

```

Begin: running /scripts/nfs-premount ...
Done.
mount: device or resource busy

```

In an endless loop.

If, instead, I leave "boot=casper" and add "root=/dev/nfs" I get the "/root" prefix problem again:

```

Begin: Preconfiguring /etc/modules... ...
Done.
Begin: Preconfiguring networking... ...
/scripts/casper-bottom/23networking: line 31: can't create /root/etc/network/interfaces: nonexistent directory
cp: cannot create '/root/var/log': Is a directory
Done.
Begin: Running /scripts/init-bottom ...
mount: mounting /dev on /root/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing the init= bootarg.

```

If I add "root=/dev/nfs" and change "boot=casper" to "boot=nfs" I get the endless loop of nfs-premount again.

casper.log is full of "no such file or directory" errors.

I'm not sure what else I can try. I've been searching the net on and off for days trying to figure out what options I might be missing, and I'm coming up with nothing.

So, network gurus: what am I missing?

---

### Post by deruberhanyok on 2012-10-22
Anyone?

---

### Post by deruberhanyok on 2012-11-12
Should this maybe have been posted in a different forum?

---

