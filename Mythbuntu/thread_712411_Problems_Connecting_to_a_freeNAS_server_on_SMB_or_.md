---
title: "Problems Connecting to a freeNAS server on SMB or NFS"
date: 2008-03-01
forum: Mythbuntu
---

### Post by SteveOSupremo on 2008-03-01
Hey guys my system is a FreeNAS Server running several IDE Drives each of which is shared over SMB (for windows) and NFS (for *nix) This is where I have my 2 TB of Videos, Music, Photos, etc. stored all the drives are formated NTFS because I cam from a windows background.

My Mythbuntu Computer is a Athalon 64 with a smaller hdd (120 gig) and DVD drive. No tuner yet.  

These are both hardwired to a router where they all have static IP addresses.  

Now for my question.  

How do I mount the Server from my Mythbuntu PC?

I'v followed guides all over the net and I generally recieve a 

mount: wrong fs type, bad option, bad superblock on //server/share/folder,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Here is the most helpful guide [http://ubuntuforums.org/showthread.php?t=667580]("http://ubuntuforums.org/showthread.php?t=667580")

any ideas?

SteveO

---

### Post by mrsteveman1 on 2008-03-01
If you are mounting as SMB, are you mounting by ip address or by netbios name?

---

### Post by Athelstan101 on 2008-03-01
Sounds like you might need to install the samba libraries:
$ sudo apt-get update
$ sudo apt-get install smbfs

Search for the available samba shares:
$ smbtree

Mount the samba share:
$ sudo mkdir /mnt/my_samba
$ sudo mount -t smbfs \\\\Server\\Folder  /mnt/my_samba -o username=<name>,password=<password>

---

### Post by SteveOSupremo on 2008-03-02
Hey thanks for all the helps something still isn't right. 

I am trying to mount by NetBios Name and by IP.  
Athelstan101 
I tried the last line of code there and all I got was an error.  I just turned off my other PC without typing the error mesage out *dough* so whe I get back home I will rerun and get the error.

SteveO

---

### Post by SteveOSupremo on 2008-03-06
HA HA I'm an idiot!!!

anyway I must have missed the $smbtree part before because that would have told me that I had the wrong directory!!!

anyway it works now!!!
yea
yea
yea

---

