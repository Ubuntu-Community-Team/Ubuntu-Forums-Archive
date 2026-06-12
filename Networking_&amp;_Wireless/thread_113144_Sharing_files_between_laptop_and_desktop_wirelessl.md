---
title: "Sharing files between laptop and desktop wirelessly"
date: 2006-01-05
forum: Networking &amp; Wireless
---

### Post by diggs on 2006-01-05
So how do I network the two computers? both are connected to the internet, and I have already downloaded samba. I would like to share and the files between the two; the majority of them are on my desktop on my partitioned drives. Thanks!:razz:

---

### Post by Zelut on 2006-01-05
Take a read here and see if it doesn't help...

[ubuntuguide - sharing dolders]("http://ubuntuguide.org/#sharefolderstheeasyway")

---

### Post by diggs on 2006-01-06
Thanks for the link. I am going to set it up so that upon booting I can read/write to the folders on my partitions.
we'll start with hda6.

sudo mkdir /media/hda6
sudo gedit /root/.smbcredentials

type in 
username:derek
password:666

sudo chmod 700 /root/.smbcredentials
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

//192.168.1.1/linux        /media/sharename  smbfs    credentials=/root/.smbcredentials       0       0

now the above IP adress is that of my router, in the guide it is saying that I should use 192.168.0.1. Is this correct?

---

