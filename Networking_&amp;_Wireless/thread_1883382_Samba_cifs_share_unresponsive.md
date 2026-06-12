---
title: "Samba cifs share unresponsive"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by blind0wl on 2011-11-19
Hi,

I have a strange problem with my cifs share.  I have mounted the drive using
```
sudo mount -t cifs //192.168.0.3/Movies /mnt/mce/Movies -o username=blindy,password=*******
```

I was using the /etc/fstab way but have the same issue.  Basically when I try to cd to the directory the console does not respond, so I type:
```
cd /mnt/mce/M
```
and then tab to finish and the console becomes unresponsive.  I can however access the console using Alt F2 etc and the system has not locked up.  I've tried typing the whole address out or:
```
ls -ahl /mnt/mce/Movies
``` and I get the same behaviour.

If I try in gnome the file browser just sits there with the Loading status forever.

If I reboot and remount it works fine...and to be honest, sometimes it comes good after a few hours without rebooting.

It was a fresh install of Oneric a few days ago.

My Windows machines have no problem getting to the shares either.

Any help is appreciated

Blindy

---

### Post by davetv on 2011-11-19
Hi Blindy, what OS is the movies share machine running? Seems a problem with network discovery in any case.

---

### Post by blind0wl on 2011-11-19
Windows 7 Ultimate are the other machines.

---

### Post by davetv on 2011-11-19
I'd try opening a samba share on your Linux box, and mapping a persistent drive on the movies share box to that share. Other than that, maybe smbfs rather than cifs.

---

### Post by blind0wl on 2011-11-20
Hmm...if I try to use smbfs to mount the drive...I get this:

```
sudo mount -t smbfs //192.168.0.3/Movies /mnt/mce/Movies -o username=blindy,password=*******
[sudo] password for blindy:
mount error(12): Cannot allocate memory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

---

