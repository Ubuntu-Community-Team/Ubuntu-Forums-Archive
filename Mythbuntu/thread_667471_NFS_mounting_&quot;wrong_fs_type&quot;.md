---
title: "NFS mounting &quot;wrong fs type&quot;"
date: 2008-01-14
forum: Mythbuntu
---

### Post by Scrier on 2008-01-14
Hello, 

I'm trying to share my backends media folder but I get an error when I try to mouut it on my backend machine.

Here is the /etc/fstab on the frontend:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2c9b898f-75fd-48ba-8830-dc8eeb3ba666 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=827460e7-0612-4913-bcd2-c4c8d8706464 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
Backend:/var/lib/media	/media-files	nfs	rsize=8192,wsize=8192,hard,intr,nfsvers=3,actimeo=0

And this is the error I get:
> mount: wrong fs type, bad option, bad superblock on Backend:/var/lib/media,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And this is what I get if I do dmesg | tail
> [   57.539376] input: Power Button (FF) as /class/input/input4
[   57.539390] ACPI: Power Button (FF) [PWRF]
[   57.539470] input: Power Button (CM) as /class/input/input5
[   57.539480] ACPI: Power Button (CM) [PWRB]
[   59.855981] r8169: eth0: link up
[   59.855989] r8169: eth0: link up
[   60.277789] NET: Registered protocol family 10
[   60.277858] lo: Disabled Privacy Extensions
[   68.211655] NET: Registered protocol family 17
[   95.489111] eth0: no IPv6 routers present

As for the Backend the folder is an lvm but not sure what information you need from that one for this to be solved.

---

### Post by superm1 on 2008-01-14
> **Scrier said:**
> Hello, 

I'm trying to share my backends media folder but I get an error when I try to mouut it on my backend machine.

Here is the /etc/fstab on the frontend:


And this is the error I get:


And this is what I get if I do dmesg | tail


As for the Backend the folder is an lvm but not sure what information you need from that one for this to be solved.
Have you properly exported the directory on your backend?

---

### Post by Scrier on 2008-01-14
> # /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/var/lib/media Backend/24(rw,no_root_squash,async)

that is the /etc/export file on the Backend.

---

### Post by chika.tambun on 2009-04-30
$ sudo apt-get install nfs-common
$ sudo mount 10.126.12.36:/data /mnt

it works

---

