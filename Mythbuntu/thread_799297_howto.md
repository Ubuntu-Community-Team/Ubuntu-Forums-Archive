---
title: "howto"
date: 2008-05-18
forum: Mythbuntu
---

### Post by ghostwalker50 on 2008-05-18
How do i set the location for my Movie/Video to a file server on my network. 


thanks
Fernando

---

### Post by uMuppet on 2008-05-19
Mount the network location to a local folder and change the Mythvideo location to this folder.

Create the mount folder
```
sudo mkdir /media/Movies
```

Then edit your fstab file,
```
sudo gedit /etc/fstab
```

and add this some code like this

# movies shared folder on mythtv
//192.168.1.10/Movies /media/Movies smb defaults 0 0
# Video Server location - Mount Folder on Mythbuntu  

Then change the location of your videos folder to /media/Movies in frontend setup.

Then either reboot or enter,
sudo mount -a




Note:
When using NFS or Samba and Mythvideo on multiple frontends, it helps to have
both video locations mounted at the same absolute path. (IE, all your
videos should either reside in or be symlinked to the same dir on all
machines (ie /var/lib/mythtv/videos))

---

### Post by ghostwalker50 on 2008-05-19
thank you i will try i ttonight when i get home....

---

