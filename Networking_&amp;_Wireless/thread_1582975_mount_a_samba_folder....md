---
title: "mount a samba folder..."
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by neorf on 2010-09-27
I've tried to mount a samba folder locate in //192.168.0.103/picture to /media/PHOTOS_STORAGE
with:
[PHP]
sudo mount -t smbfs //192.168.0.103/pictures/ /media/PHOTOS_STORAGE -o username=Guest,password=
[/PHP]
but i get this error:
[PHP]
mount: wrong fs type, bad option, bad superblock on //192.168.0.103/pictures/,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/PHP]

what can i do?

thanks

neorf

---

### Post by donc786 on 2010-09-27
I don't know if this will be much help, as I have lots of problems similar to yours. One thing I have found useful is to mount the location through my places menu by selecting Connect to server just below network. I select server type windows share, the IP of the location of the files for server, the share name I want to mount, my username for the network, finally the password when prompted. I also add the location as a bookmark to make things quicker. I tried using the terminal with little success. My results are identical to yours. I have been messing with this for a long time and this seems to be the quickest way for me to connect. I have also had limited success using nautilus to connect by pressing ctr+L then entering smb:///serverIP/share that worked well for me, then it not so well. I don't know what changed. I will include some screen shots to assist with identifying what the steps look like. The systems are running 10.04 desktop, 10.04 Studio, 10.04 Xubuntu, and XP. The Xubuntu notebook has been my biggest challenge.

---

### Post by cj.surrusco on 2010-09-27
> **neorf said:**
> I've tried to mount a samba folder locate in //192.168.0.103/picture to /media/PHOTOS_STORAGE
with:
[PHP]
sudo mount -t smbfs //192.168.0.103/pictures/ /media/PHOTOS_STORAGE -o username=Guest,password=
[/PHP]
but i get this error:
[PHP]
mount: wrong fs type, bad option, bad superblock on //192.168.0.103/pictures/,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/PHP]

what can i do?

thanks

neorf

Do you have smbfs installed? 

You can see by running:
```
sudo apt-get install smbfs
```

---

### Post by donc786 on 2010-09-27
> **cj.surrusco said:**
> Do you have smbfs installed? 

You can see by running:
```
sudo apt-get install smbfs
```

I have the same problem, I tried installing smbfs. I have the newest version already installed. Any other suggestions? I seem to recall some changes to fstab, or something like that in months past when I did all this. Is that relevant to this issue?

---

