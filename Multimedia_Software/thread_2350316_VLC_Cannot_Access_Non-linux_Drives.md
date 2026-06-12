---
title: "VLC Cannot Access Non-linux Drives"
date: 2017-01-23
forum: Multimedia Software
---

### Post by Kerry Lange on 2017-01-23
I'm running VLC on a fresh install of Ubuntu 16.10. Ubuntu is run off an SSD and I have my audio files on an NTFS drive.

When I try to load a directory, the VLC dialogue boxes show me the root directory, my home directory and my directory, but I can't see hidden directories off the root. As a result, I can't access the media directory where I'm normally able to access my NTFS drives. When viewing the root folder and I right-click one or more folders, then click "Show hidden files", I still can't see any hidden files or directories (except within my own directory: i.e. /home/user/). As a result, I can't access my audio files. I know I can always copy the files over to the music folder in my home directory but the audio files are around 500 GB in size. I'd prefer to leave them where they are.

Has anyone else run into this? Does anyone have a suggestion how I might be able to access my NTFS drives?

BTW, I've asked this question on the VideoLAN forums and was told dialogue boxes are a Qt issue, which is controlled by Canonical/Ubuntu.

---

### Post by #&amp;thj^% on 2017-01-23
Is the NTFS Drive just a NTFS formatted partition...or dose it have windows on it also?

---

### Post by Kerry Lange on 2017-01-23
No, Windows is not installed on it. It's just a data drive.

I should also add I have no trouble accessing the drive otherwise. It shows up in Nautilus and I'm able to move files around or edit them as needed. It's just from within VLC I'm having the problem.

---

### Post by #&amp;thj^% on 2017-01-23
> No, Windows is not installed on it. It's just a data drive.
Dose Nautilus see those hidden files or folders...or is this just specific to VLC?

---

### Post by deadflowr on 2017-01-23
Sounds  like you installed the snap version of vlc.
Which has these bizarre behaviors in accessing various directories and locations.
(Since it has a default confinement configuration that normal packages do not have)

I believe installing the vlc snap package with the -devmode option lifts these restrictions.
(This would require a reinstall, though)
```
sudo snap install vlc --devmode
```
You can get a list of snap commands with 
```
snap help
```

Or ignore the snap package altogether and simply install the debian/apt version, which has none of these restrictions.
```
sudo apt install vlc
```

As snaps and traditional debian/apt packages are completely isolated from one another, so you can have both. ftr


For what it's worth, snap packages that are installed through the software center will be marked as non-free, since snap packages do not get the thorough review of code that a normal debian/apt package would.
(Or that is my limited armchair understanding of it)
and the vlc snap package in the software center is listed as daily.

I am really not even totally sure if this is accurate to your problem, only that it is very much like the behavior seen from that particular package.

Hope it helps
or makes sense

---

### Post by #&amp;thj^% on 2017-01-23
> **deadflowr said:**
> Sounds  like you installed the snap version of vlc.
Which has these bizarre behaviors in accessing various directories and locations.
(Since it has a default confinement configuration that normal packages do not have)

I believe installing the vlc snap package with the -devmode option lifts these restrictions.
(This would require a reinstall, though)
```
sudo snap install vlc --devmode
```
You can get a list of snap commands with 
```
snap help
```

Or ignore the snap package altogether and simply install the debian/apt version, which has none of these restrictions.
```
sudo apt install vlc
```

As snaps and traditional debian/apt packages are completely isolated from one another, so you can have both. ftr


For what it's worth, snap packages that are installed through the software center will be marked as non-free, since snap packages do not get the thorough review of code that a normal debian/apt package would.
(Or that is my limited armchair understanding of it)
and the vlc snap package in the software center is listed as daily.

I am really not even totally sure if this is accurate to your problem, only that it is very much like the behavior seen from that particular package.

Hope it helps
or makes sense
+1;) You read my mind here.

---

### Post by Kerry Lange on 2017-01-23
> **deadflowr said:**
> Sounds  like you installed the snap version of vlc.
Which has these bizarre behaviors in accessing various directories and locations.
(Since it has a default confinement configuration that normal packages do not have)

> Or ignore the snap package altogether and simply install the debian/apt version, which has none of these restrictions.
```
sudo apt install vlc
```

As snaps and traditional debian/apt packages are completely isolated from one another, so you can have both. ftr

Yes, it was a snap installation. As it stands, I can't uninstall the snap version, as it's asking me to verify through an Ubuntu One login. However, it won't accept my credentials, although I know they're correct. It's been identified as a bug and I've reported that it affects me.

So, it's a good thing I can have both installed side-by-side. VLC is up and running after I installed the debian/apt version.

Thank you!

---

### Post by #&amp;thj^% on 2017-01-23
When satisfied would you mark this solved as to help others.  
There is bound to be future visitors to this type of request.
Regards

---

### Post by Kerry Lange on 2017-01-23
1fallen, I've done exactly that.

---

### Post by ajgreeny on 2017-01-23
The command ```
sudo snap remove vlc
``` should remove it if you want to, which then needs your sudo password only.

---

### Post by deadflowr on 2017-01-23
> Yes, it was a snap installation. As it stands, I can't uninstall the snap version, as it's asking me to verify through an Ubuntu One login. However, it won't accept my credentials, although I know they're correct. It's been identified as a bug and I've reported that it affects me.
Still an issue I guess.

Though you can login through the command line
```
sudo snap login SSO-linked-email-address-here
```
it'll ask for your sudo password, then the password for your Ubuntu SSO account.
What this does is allow you to install snaps locally per user, without sudo.

---

### Post by Kerry Lange on 2017-01-23
> **ajgreeny said:**
> The command ```
sudo snap remove vlc
``` should remove it if you want to, which then needs your sudo password only.

That worked! Thank you!

---

