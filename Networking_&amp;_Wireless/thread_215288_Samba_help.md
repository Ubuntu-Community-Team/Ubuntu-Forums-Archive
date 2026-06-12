---
title: "Samba help"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by IciCle on 2006-07-13
I have mounted 3 samba shares through nautilus and they are now on my desktop but I cannot make links to folders on the shares so I am wondering how I can do this. I am looking to make links from folders on the shares so I can share files from them to a file server I am running

---

### Post by IciCle on 2006-07-15
Please help me :-\

---

### Post by MrHorus on 2006-07-15
I am not quite sure what you mean by making links and sharing on a file server.

Why not just mount the volumes on your fileserver?

---

### Post by rmjb on 2006-07-15
Could you clarify the last part of your request, it's a little confusing.

Also, how are you making these links? Are they the ones on the side of the filemanager (Natutilus) or are they in some other folder like your Desktop?

- rmjb

---

### Post by IciCle on 2006-07-15
ok I went to the Places menu on my desktop and chose connect to server and I chose windows file share and mounted all my shares that way and they just appear on my desktop but when I navigate through them and try to make a shortcut to a folder on a share it just says unsupported opperation

---

### Post by slider on 2006-07-15
Search is your friend

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by IciCle on 2006-07-15
thats for that but now I am running into another problem.  I have the info put into fstab but it gives me an error hen I try to do mount -a

mount: wrong fs type, bad option, bad superblock on //192.168.0.10/Frylock,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb2       /home           ext3    defaults        0       2
/dev/sdb1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.0.10/Frylock  /media/Frylock  smbfs  credentials=~/.smbcredentials,dmask=777,fmask=777  0  0

---

### Post by IciCle on 2006-07-16
can anyone help with this?

---

### Post by dinub1 on 2006-07-17
> **IciCle said:**
> can anyone help with this?

I do not know why you are complicating yourself. In my opinion it has nothing to do with definitions in fstab. All you have to do is go into settings/shared folders and define which folders you want shareable. You will need to type the system administrator's password and then define the folder you want shareable, with Samba or with NFS (or both) and the type of share, i.e read only, writable etc. Press OK and your folders are shared. If you have another computer connected to that network then you are able to see those shared folders. Hope this answers your question.

---

### Post by bforbes on 2006-07-17
Have you installed smbfs?
```

sudo apt-get install smbfs

```

---

### Post by IciCle on 2006-07-17
neither one of you are getting what I am saying.  I am trying o mount a share from a windows box on my linux box my previous post contains the error I got while trying and also contains my fstab info because I am trying to permantly mount it

---

### Post by rmjb on 2006-07-17
Try mounting it as a cifs share instead of a smbfs share. It format of the line in fstab varies slightly but I see people on this forum get better success that way than with smbfs.

- rmjb

---

### Post by bforbes on 2006-07-17
> **IciCle said:**
> neither one of you are getting what I am saying.  I am trying o mount a share from a windows box on my linux box my previous post contains the error I got while trying and also contains my fstab info because I am trying to permantly mount it

You would need to install smbfs to do what you are doing, unless you want to use cifs, but I don't know anything about that. Try what I suggested:
```

sudo apt-get install smbfs
sudo /etc/init.d/samba restart
sudo mount -a

```

---

### Post by IciCle on 2006-07-17
I already have smbfs installed and I tried to switch it to cifs and I get the same error

---

### Post by bforbes on 2006-07-18
```

//192.168.0.10/Frylock /media/Frylock smbfs credentials=~/.smbcredentials,dmask=777,fmask=777 0 0

```
Are you absolutely sure that the IP address and share name are correct? You could also try using the old school username=,password= options instead of credentials.

---

