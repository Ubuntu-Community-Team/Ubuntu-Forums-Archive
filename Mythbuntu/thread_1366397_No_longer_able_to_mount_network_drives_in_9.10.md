---
title: "No longer able to mount network drives in 9.10"
date: 2009-12-28
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-12-28
I've just upgraded my Mythbuntu 8.10 box to 9.10 via a clean install. Most things worked very smoothly. However, I am no longer about to mount my external hard drives.

Previously, I had the following line in my fstab file:

```
//172.16.100.250/HTPC /media/linkstation	cifs	auto,_netdev	0	0
```

Strangely, that didn't automatically mount the external drive at startup, but would mount it if I manually typed

```
sudo mount -a
```

I could also mount the drive manually simply by typing

```
sudo mount //172.16.100.250/HTPC /media/linkstation
```

None of these things works after the upgrade. And yes, I did remember to recreate the mount point.

I get the following error message when I try (either by mounting via fstab or manually):

>  wrong fs type, bad option, bad superblock on //172.16.100.250/HTPC,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any ideas what might have changed and what I can do to get my external hard drives back?

Thanks
NM

---

### Post by joho500 on 2009-12-29
Hi NM,

I think I've had the same problem. What helped me was the installation of the package smbfs.

Joost

---

### Post by rickyble on 2009-12-29
yea I have been having problems with Samba also since I upgraded.  Samba works just fine and then after a few days it just drops and I have to do a samba restart.  Then it will work for a few more days.  At first I couldnt get it to work at all and did a reinstall of the samba package.  Something really weird

---

### Post by NautiusMaximus on 2010-01-01
Many thanks, joho500. I installed smbfs (and the samba client as well for good measure), and then everything just worked.

Another problem solved, just a couple of thousand to go...

---

### Post by joho500 on 2010-01-02
You're welcome. Glad to be of help and good to hear that I remebered it right! :D

Joost

---

