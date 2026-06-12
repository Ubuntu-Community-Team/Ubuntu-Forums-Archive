---
title: "Cannot automount Samba share"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by qajaq on 2009-06-15
I have a machine running Kubuntu 9.04 set up as a file server, running Samba. Another machine dual-boots Windows XP professional and openSuSE 11.1, and it has no trouble connecting to the Samba share. On the openSuSE OS, the share is automatically connected via a line in the /etc/fstab file.

However, I am unable to get my laptop (also running Kubuntu 9.04) to mount the same Samba share, even with the Ethernet cable plugged in, making a wired connection.

I can make the connection using the command```
smbclient //Kodiak/mnet
```
But when I issue the command```
mount -t cifs //Kodiak/mnet /datanet
```
I get the error message
> mount: wrong fs type, bad option, bad superblock on //Kodiak/mnet,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Similarly, if I put the following line in my /etc/fstab file:```
//Kodiak/mnet  /datanet  cifs  auto,username=xxx,password=xxx  0  0
```
I get the same error message. This is the same as the line in the /etc/fstab file on the openSuSE machine, which works flawlessly.

When I run ```
dmesg | tail
``` I get > CIFS VFS: cifs_mount failed w/ return code = -22

Any ideas what I need to do differently to make Kubuntu mount the Samba share?

---

### Post by Wicca on 2009-06-15
Did you install smbfs?

```
sudo apt-get install smbfs
```

---

### Post by qajaq on 2009-06-15
That did it! I obviously neglected to include that in the notes I made while setting up the network connection on my openSuSE machine, and so overlooked it on the Ubuntu installation.

Thanks, Wicca!

---

