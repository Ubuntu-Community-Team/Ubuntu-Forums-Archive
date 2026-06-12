---
title: "Slow Transfer Speeds in with Samba and Ghost"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by cdusseau on 2010-08-11
Basic setup:

Server: Ubuntu 10.04 with DHCP, TFTP, SAMBA and NFS running
Clients: Many different types of Dell laptops and desktops
Connection Method: netbootdisk that connects to Samba share and loads ghost

Basically we hook up a bunch of random computers to the network at once, load up ghost via netbootdisk and download the images from the server via ghost. I realize there may be a bottleneck coming from our use of outdated switches, but I am confused by the fact that back when we were using windows server instead, we got better transfer speeds under load (10+ machines going at once). I always figured Linux would be faster, but such is not the case so far. I am hoping there is a simple configuration fix for this =)

My smb.conf file:
```
#======================= Global Settings =======================

[global]
workgroup = discount.local
netbios name = image-server
server string = %h server (Samba, Ubuntu)
lanman auth = yes
client lanman auth = yes
security = user
encrypt passwords = yes
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
socket options = TCP_NODELAY SO_RCVBUF=65535 SO_SNDBUF=65535

[share]
	comment = DE Image Server
	valid users = samba,@samba
	writeable = yes
	browsable = yes
	path = /media/Images
```

My fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda6 during installation
UUID=60f646cc-ac8d-4710-ad28-630e15d1495b /               ext4    errors=remount-ro 0       1

# /home was on /dev/sda7 during installation
UUID=6a36c893-68ce-468e-bbdf-8f0c8265b343 /home           ext4    defaults        0       2

# swap was on /dev/sda5 during installation
UUID=4d1595fc-3812-4645-9ad9-eaab75c88a1f none            swap    sw              0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Shared devices for Image Server
/dev/sda2 /media/Images ntfs-3g umask=0,user,auto,exec,rw 0 0
#/dev/sda4  /media/clonezilla  ext4  defaults  0  0
/dev/sda4  /media/clonezilla  ext4  rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock 0 0
```

If you see anything in my smb.conf file you dont think I need or that I am missing, let me know. I would like to clean it up but I dont know what every option does yet.

Also, if you didnt catch it, I'm just looking for a way to speed up transfers under load.

---

