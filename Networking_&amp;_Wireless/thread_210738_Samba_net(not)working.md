---
title: "Samba net(not)working"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by Sandsound on 2006-07-07
Having some troubles mounting a Samba share.

I have made a folder on my local pc (sudo mkdir /mnt/musik) and have shared a folder on the server (actualy its a whole disk i have shared). I can see and read files from the server when i navigate my way through "netvork servers" useing Nautilus, but when I try to do :
sudo mount -t smbfs //server/musik /mnt/musik

I get :
mount: wrong fs type, bad option, bad superblock on //server/musik,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

I have tryed other variations, even those sugested elsewhere in the forum, but it I get the same mount error.

If I do :
smbtree

I get a list that clearly says I have a \\server\musik

Am I missing something here ?

---

### Post by BuffaloX on 2006-07-07
Just mount like this:

mount 192.168.0.1:/home/sharedfolder /media/loacalfolder

---

### Post by Sandsound on 2006-07-07
> **BuffaloX said:**
> Just mount like this:

mount 192.168.0.1:/home/sharedfolder /media/loacalfolder

Thought I just could use the samba-share name ?

---

### Post by nashjc on 2006-07-07
I've also had lots of trouble, but seem to be "almost" there.

I've been trying to share a vfat partition across a local network. This proved REALLY easy in Xandros 3.02 (right click drive directory (actually given the name "D:" for the non-linux types), and select sharing etc. No such luck with Ubuntu, but there's some other nice stuff I'd like to use. 

If I set up smb.conf to show the drive, (/media/hda5) I can see it over the net, but not log in "Permission denied". 

Problem seems to be that /media/hda5 is given ownership root:plugdev by fstab, and 770 mode (others no rights) due, as far as I can understand, to "umask=007" in fstab. Since I'm not a permissions specialist, I'm guessing a bit here.

Anyway, creating a new directory /media/ddd and unmounting the drive and remounting it on ddd allows access OK. ddd has 777 permissions which may not be ultimately the best or safest choice, but at least points the way. 

Does anyone know how I should go about making regular mountpoint work?

JN

---

### Post by nashjc on 2006-07-07
To answer my own question, though I don't understand all the details:

Change the fstab line for the appropriate drive to have 
umask=000, gid=users   (default umask=007, gid=46) The 46 corresponds to user "plugdev". 

Unmount/mount, restart samba. Voila.

JN

---

