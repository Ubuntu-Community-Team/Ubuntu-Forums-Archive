---
title: "Unable to mount drive thru NFS after 10.04 install"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by couzin2000 on 2010-06-12
Hi,
I had originally setup my 8.10-equipped desktop and laptop so that I could read movies stored on the desktop through my wireless router onto my laptop. All this was working well.

Then I upgraded my desktop to 9.04, 9.10, and finally 10.04. after some re-editing of the config files on the desktop, I was still able to read off the desktop using the same command:
```
sudo mount 192.168.0.102:/media/Downloads /home/sebastien/sebastien-desktop-downloads
```
Now, I just updated my laptop to 10.04 (from disk, like the desktop), and the abovementioned command now gives me this message:
```
sebastien@sebastien-laptop:~$ sudo mount 192.168.0.102:/media/Downloads /home/sebastien/sebastien-desktop-downloads
mount: wrong fs type, bad option, bad superblock on 192.168.0.102:/media/Downloads,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

sebastien@sebastien-laptop:~$ 

```
I have NO idea what that means. I'm unsure at this point what the cause of this might be, so I turn to you. Please help!

---

### Post by couzin2000 on 2010-06-12
OK, never mind -- here's what fixed it:
```
sudo apt-get install nfs-common
```
:oops:

---

