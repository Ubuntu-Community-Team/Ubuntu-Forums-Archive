---
title: "Network shares mount problems"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2012-07-19
Not sure if this is the right place, but here goes;

I have a Netgear ReadyNAS nv+. The main shared folder as either cifs or nfs is //readynas01/media

The address of the NAS is 192.168.1.16

When I "Browse Networks" from nautilus on a Ubuntu based (12.04) PC, I can connect to the readynas just fine on 

smb://readynas01.local/media/  
or
smb://192.168.1.16/media/
or
smb://readynas01/media/
all work.

However, I have had no luck trying to mount the readynas from fstab as in 

//readynas01/media/ /mymountpoint cifs 0 0

findsmb gives me
```
192.168.1.16    READYNAS01    +[MSHOME] [Unix] [Samba 3.5.15]

```


dmesg | tail gives me

```
[   30.921006] CIFS VFS: cifs_mount failed w/return code = -113
[   30.921011] CIFS VFS: cifs_mount failed w/return code = -113
[   43.201413] CIFS VFS: Error connecting to socket. Aborting operation
[   43.201489] CIFS VFS: Error connecting to socket. Aborting operation
[   43.249404] CIFS VFS: cifs_mount failed w/return code = -113
[   43.249409] CIFS VFS: cifs_mount failed w/return code = -113
```

I have the same problem trying to mount from my other linux pcs. 

Macbook and my Windows 7 PC connect OK, of course. 

Any ideas anyone?

Thanks

---

### Post by StariBrko on 2012-07-19
Hi,
It seems you have quite similar problem as I had.
Check my topic: "attempting to mount NAS on Ubuntu server"
Maybe you can find it usable.

I was desperately trying to mount nfs shares, and than I finally succeeded but with **_cifs _**type of share ...

The command that solved the problem was:
```
sudo mount -t *NAS_IP_address*:/*MyNetworkShare* /*MyMountPoint* -o username=*MyUsername*,password:*MyPassword*
```

---

### Post by Morbius1 on 2012-07-19
I'm a little confused:
> When I "Browse Networks" from nautilus on a Ubuntu based (12.04) PC, I can connect to the readynas just fine on 

smb://readynas01.local/media/  
or
smb://192.168.1.16/media/
or
smb://readynas01/media/
all work.

However, I have had no luck trying to mount the readynas from fstab as in If you are using "smb://..." it's already mounted at [B]/home/your-user-name/.gvfs

[/B]If you have no problems with the mountpoint and just want the share to be mounted at login use Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by rukiaEnix on 2012-07-19
I have a shared mounted at boot time like this (fstab line):

```

//10.143.1.34/share /media/share smbfs credentials=/root/.acc 0 0

```Where /root/.acc is where I have my username and password so I can access this share.

Do you need credentials to access this NAS?

---

### Post by GuiGuy on 2012-07-19
> **Morbius1 said:**
> I'm a little confused:
If you are using "smb://..." it's already mounted at [B]/home/your-user-name/.gvfs

[/B]If you have no problems with the mountpoint and just want the share to be mounted at login use Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Thanks for those tips. I didn't know about /home/your-user-name/.gvfs

---

### Post by GuiGuy on 2012-07-19
> Do you need credentials to access this NAS?

Not as far as I know. I have lodged a support ticket with Netgear to see if that is the case. However, I wouldn't think credentials are needed because cifs mounts out of the box on my daughter's netbook.

---

### Post by GuiGuy on 2012-07-19
> **StariBrko said:**
> 
```
sudo mount -t *NAS_IP_address*:/*MyNetworkShare* /*MyMountPoint* -o username=*MyUsername*,password:*MyPassword*
```

Thanks. I'd tried all that. without luck so far.

---

### Post by GuiGuy on 2012-07-19
Thanks for the replies; I'll work my way through them and will post back...

---

### Post by M!K3_$ on 2012-07-19
> **GuiGuy said:**
> Thanks. I'd tried all that. without luck so far.

Because it is samba, you will have to do something different.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")
[http://luhman.org/blog/2010/04/30/how-mount-windows-smb-shares-ubuntu-linux]("http://luhman.org/blog/2010/04/30/how-mount-windows-smb-shares-ubuntu-linux")

---

### Post by GuiGuy on 2012-07-20
```

sudo apt-get install cifs-utils

```

I thought I had it installed. Alas....

Anyway, all good.

---

