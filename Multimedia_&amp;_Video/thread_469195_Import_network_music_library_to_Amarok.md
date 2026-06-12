---
title: "Import network music library to Amarok"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by wie6Ein0 on 2007-06-09
Is there a way to import my music collection that's shared on a Windows XP desktop computer into Amarok's music library without physically copying the files to the computer? The directory with the music collection can be accessed on my laptop with Ubuntu 7.04 Feisty Fawn using Samba.

I can play the audio files over the network using Amarok, but I'd like to have them shown in Amarok's music library. The preferences and options appear to only let me select local directories.

---

### Post by lawr_rawr on 2007-06-09
If you mount your smb share via command line (instead of "Connect to Server..."), you can mount it into the directory of your choice. 

As root, make a new directory under /media:
```
sudo mkdir /media/<foldername>
```

Then mount the smb share:
```
sudo mount -t smbfs //windows/share /media/folder -o rw,username=<name>,password=<pass>
```

After that, you should be able to select /media/foldername in Amarok. Rescan your collection and it should pick up the new stuff.

Now, there's one problem with this -- since you mount the share as root, only root has write permissions! I'm trying to figure out how to fix this now... anyone else have ideas?

---

### Post by patrickfromspain on 2007-06-09
sudo chmod 777 /media/folder could be a solution?

---

### Post by lawr_rawr on 2007-06-09
chmod 777 /media/folder didn't work for me -- the parent folder had rw permissions, but once the smb share was mounted into it, it only had read.

Here's how I fixed it:
```
sudo mount -t smbfs //windows/share /media/<name> -o username=<user>,password=<password>,fmask=777
```

Since I'm using Ubuntu on my laptop and only want the smb share mounted at home, I don't want to mount the share every time I logon. If you're permanently connected to the network with the smb share, you might want to set it up in fstab.

---

### Post by wie6Ein0 on 2007-06-09
> **lawr_rawr said:**
> chmod 777 /media/folder didn't work for me -- the parent folder had rw permissions, but once the smb share was mounted into it, it only had read.

Here's how I fixed it:
```
sudo mount -t smbfs //windows/share /media/<name> -o username=<user>,password=<password>,fmask=777
```Since I'm using Ubuntu on my laptop and only want the smb share mounted at home, I don't want to mount the share every time I logon. If you're permanently connected to the network with the smb share, you might want to set it up in fstab.

I am getting an error when doing what you have instructed:

```
mount: wrong fs type, bad option, bad superblock on //192.168.2.3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Here's what I entered into the terminal:

```
sudo mount -t smbfs //192.168.2.3 /media/music
```

I left it at that since there is no username or password to be entered.

---

### Post by lawr_rawr on 2007-06-09
Oh, okay. You probably need to install smbfs.
```
sudo apt-get install smbfs
```

I set up the first smb share a couple weeks ago and hadn't tried another until today -- guess I forgot I'd added that package. You might also need smbclient (but I think that one is installed by default).

---

### Post by lawr_rawr on 2007-06-09
Also, this thread lists a bunch of different ways to mount smb shares:
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

