---
title: "Ubuntu to Ubuntu file sharing over LAN"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by cwrann on 2011-12-02
I am trying to share the files on my desktop that runs Ubuntu 10.04 with my laptop that runs Ubuntu 11.10 and vice versa. I basically want to use my Desktop as a server type of computer. The computers are on the same LAN. 

I have set the sharing options to share on all the folders that I want my laptop to have access to but I can't seem to figure out how to access those folders from my laptop. 

For some reason I am having  hard time finding information on sharing Ubuntu to Ubuntu, most of what I see is concerned with sharing Ubuntu to Windows.

---

### Post by oldfred on 2011-12-03
I used Samba to copy files to my laptop that was XP. But I only did it occasionally and Windows, firewall, or virus checker would update and change things or I update my Ubuntu install and have all sorts of issues. So I changed my laptop to Ubuntu and use NFS. I can script the changes if I do a new install and have not had any issues since.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

I had to install server on both laptop & desktop depending on which way I copy data. And adjust IP address as needed.

#Part of new install scripts to add apps & configurations:
#NFS setup
fname_exp=/etc/exports
nfs1="/mnt/data 192.168.1.0/24(rw,no_root_squash,async)"
nfs2="/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)"
echo $nfs1 >> $fname_exp
echo $nfs2 >> $fname_exp

# For NFS /etc/exports already edited
apt-get install nfs-kernel-server nfs-common portmap
#
dpkg-reconfigure portmap
exportfs -a
service portmap restart

Two versions one for DT (Desktop) & one for LT (laptop), I run these when I want to sync DT & LT, but each pulls data from the other, both have same mount of /mnt/data so I add DT or LT to know it is the other computer:
#!/bin/bash

sudo mkdir /mnt/data_DT
sudo mkdir /mnt/shared_DT
sudo mount 192.168.1.20:/mnt/data /mnt/data_DT
sudo mount 192.168.1.20:/mnt/shared /mnt/shared_DT

#!/bin/bash
# run Mount_NFS.sh first
rsync -aruvP /mnt/data_DT/Documents /mnt/data
rsync -aruvP /mnt/data_DT/Projects /mnt/data
rsync -aruvP /mnt/data_DT/PDF /mnt/data
rsync -aruvP /mnt/data_DT/kmymoney /mnt/data
#
rsync -aruvP /mnt/shared_DT/OfficeFiles /mnt/shared
rsync -aruvP /mnt/shared_DT/mozilla /mnt/shared
rsync -aruvP /mnt/shared_DT/Photos/All2011 /mnt/shared/Photos

---

### Post by cwrann on 2011-12-03
Thank you very much, looks like I have some work ahead of me.

---

