---
title: "mount no longer does what it did"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by leemajors on 2009-05-06
hey,

after a fresh 9.04 install, my mount command doesn't do what it used to on 8.10.

i have a NAS and i used to type:

sudo mount -t nfs 192.168.2.243:/mnt/vader /media/vader

which would mount a folder on the NAS to a local folder.

now, when I type that I get:

mount: wrong fs type, bad option, bad superblock on 192.168.2.243:/mnt/vader,
missing codepage or helper program, or other error
(for several filesystems (e.g. nfs, cifs) you might
need a /sbin/mount.<type> helper program)
In some cases useful info is found in syslog - try
dmesg | tail or so


any thoughts?

---

### Post by Old *ix Geek on 2009-05-06
I can't help, but just wanted to say that I'm having similar issues. As for you, it worked fine in 8.10 and broke after installing 9.04.

---

### Post by Washdogg on 2009-05-06
Have you tried smbfs? (obviously only works if the NAS is shared with samba... and you'll need the package).

To mount the shares on my server I type:

sudo smbmount //<ip>/path/ /path/to/mountpoint

Hope this helps.

Washdogg

---

### Post by leemajors on 2009-05-08
not a bad idea, but not really solving the problem more like skirting around it... shouldn't mount still work?

---

### Post by leemajors on 2009-06-03
can anyone help with this? i'm still perplexed as to why mount would suddenly stop working after an upgrade. i currently can't mount to any of my drives on the NAS.

---

### Post by dmizer on 2009-06-03
According to the error, it just looks like you might not have the proper tools installed for mounting nfs (they may have gotten removed in your upgrade).

Try this:
```
sudo apt-get install portmap nfs-common
```

If that doesn't do anything, please post the the output of the following command:
```
sudo iptables -L
```

---

### Post by leemajors on 2009-06-12
omg, thank you! installing those extra packages worked a treat.

i wish i could have read that error and known what packages were missing too!

thanks, that's great. :)

---

### Post by orangep on 2009-10-03
I'm still stuck back at stage 1. I have been using NFS mounts for
years with no problems, so I know how to configure and use NFS.
Last spring I updated Ubuntu, and NFS has not worked since.
My scripts to mount partitions from other Linux machines stopped
working. Other systems, still running Debian Linux, and not updated,
still have nfs working correctly.

The updated machines all give the same error message:

root@carmen:~# mount rebecca:/opt /opt-rebecca
mount: wrong fs type, bad option, bad superblock on rebecca:/opt,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg doesn't have anything informative to say.

the suggested apt-get install command above just says that all of
those packages are already the latest versions -- that is,
portmap and nfs-common are already the latest versions. Everything
is up to date.

So what changed last spring?

By the way, I'm having this problem with both 32-bit and 64-bit
versions of Debian/Ubuntu.

TIA.

---

### Post by dmizer on 2009-10-04
> **orangep said:**
> 
mount: wrong fs type, bad option, bad superblock on rebecca:/opt,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This probably means that you don't have all the necessary packages installed. That or you've written the fstab line incorrectly. Make sure you've installed all the packages according to the 4th link in my sig, or just see my post above.

If you still get the error message, please post your current /etc/fstab line.

---

### Post by orangep on 2009-10-08
Bingo! Even though I was sure that all was installed, it wasn't.
It turns out that the new CD distribution does not install everything
that you need for nfs, not any more. Linux used to...

So the new laptop NFS wasn't working because portmap and other things
were missing.

But what is really strange is that the main monster, a 64-bit dual-core
Athlon, is also fixed. Both NFS and Samba have started working again.
All that I can guess is that an upgrade sometime between Spring and now
fixed it, and I had not retested the NFS or Samba.

Well anyway, thanks.

---

### Post by orangep on 2013-02-28
Note to later readers: rpcbind has replaced portmap.

If you type: sudo apt-get install portmap

It says: Note, selecting 'rpcbind' instead of 'portmap'

---

### Post by QIII on 2013-02-28
This is a very old thread

Thread closed.

---

