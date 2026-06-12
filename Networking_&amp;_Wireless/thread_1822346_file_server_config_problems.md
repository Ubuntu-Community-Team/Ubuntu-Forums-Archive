---
title: "file server config problems"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by rinorho on 2011-08-10
i to All.
 
I'm newbie :) and just installed SAMBA, OpenSSH and LAMP On ubuntu SERVER (x64 10.04 LTS ). My home file server is based on :
 
-AMD XII 240e 
- 2x2Gb DDR3 @1333Mhz
- ASROCK N68C-S UCC
- TP-LInk GIGABIT PCI LAN ADAPTER 
- MAXTOR EIDE 7200rpm 80Gb (System)
- 4x 2TB WD20EARS (storage)
 
Following some guides on the web... I encountered some problems.:(:(
 
1) I can't mount automatically the 4 x 2TB HDD (WD20EARS), already ext4 formatted
 
I create one folder named ARCHIVIO and used it as mounting point (see below my fstab config file)
 
[COLOR=red]# /etc/fstab: static file system information.[/COLOR]
[COLOR=red]#[/COLOR]
[COLOR=red]# Use 'blkid -o value -s UUID' to print the universally unique identifier[/COLOR]
[COLOR=red]# for a device; this may be used with UUID= as a more robust way to name[/COLOR]
[COLOR=red]# devices that works even if disks are added and removed. See fstab(5).[/COLOR]
[COLOR=red]#[/COLOR]
[COLOR=red]# <file system> <mount point> <type> <options> <dump> <pass>[/COLOR]
[COLOR=red]proc /proc proc nodev,noexec,nosuid 0 0[/COLOR]
[COLOR=red]/dev/mapper/fileserverubunturino-root / ext4 errors=remount-ro 0 1[/COLOR]
[COLOR=red]# /boot was on /dev/sda1 during installation[/COLOR]
[COLOR=red]UUID=8b05e3e7-61a7-46c6-bb7c-0b0d21997e17 /boot ext2 defaults 0 2[/COLOR]
[COLOR=red]/dev/mapper/fileserverubunturino-swap_1 none swap sw 0 0[/COLOR]
 
 
[COLOR=red]UUID=cee2ab03-cc79-49c8-b86b-466b5143a488 /media/ARCHIVIO ext4 defaults 0 0[/COLOR]
 
[COLOR=red]UUID=48a42a55-db8d-4927-9607-714e56cdf288 /media/ARCHIVIO ext4 defaults 0 0[/COLOR]
 
[COLOR=red]UUID=be5d84ee-087f-4f53-864d-c9cd8e4b8e0b /media/ARCHIVIO ext4 defaults 0 0[/COLOR]
 
[COLOR=red]UUID=16f39004-8729-46aa-b1a5-c974afbd88a1 /media/ARCHIVIO ext4 defaults 0 0[/COLOR]
 
2)My W7 x64 client don't sees the ubuntu server, but I can access to the server from Windows 7 inserting the ip address in address bar ([\\192.168.X.Y]("file://192.168.x.y/"))
The transfer rate is fast 90Mbyte\second (Gigabit connection)
 
 
Attached my samba config file:
 
 
 
[SIZE=3][COLOR=black]**Where I'm wrong?**[/COLOR][/SIZE]
 
Please help me!
 
 
Thanks at lot
bye

---

### Post by rinorho on 2011-08-11
ANY IDEA?
 
thanks
 
bye

---

### Post by drdos2006 on 2011-08-11
Yes,
Create separate /media/hdd_folders for each harddrive.
e.g.
From a terminal on your server, 
sudo mkdir  /media/ARCHIVIO_01
sudo mkdir  /media/ARCHIVIO_02
sudo mkdir  /media/ARCHIVIO_03
sudo mkdir  /media/ARCHIVIO_04

Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings. You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
###  	web site is here: http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by rinorho on 2011-08-11
> **drdos2006 said:**
> Yes,
Create separate /media/hdd_folders for each harddrive.
e.g.
From a terminal on your server, 
sudo mkdir /media/ARCHIVIO_01
sudo mkdir /media/ARCHIVIO_02
sudo mkdir /media/ARCHIVIO_03
sudo mkdir /media/ARCHIVIO_04
 
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings. You could also install the Desktop and run the server as a virtual machine using Virtualbox.
 
 
 
And on your server..........
 
```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
###      web site is here: http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb
 
Add extra libraries with :
sudo apt-get -f install

```
 
regards
 
Thanks a lot,
 I'll try it this evening
 
bye

---

