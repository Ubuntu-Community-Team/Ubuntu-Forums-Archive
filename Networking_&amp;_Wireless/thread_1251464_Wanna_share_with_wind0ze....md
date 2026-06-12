---
title: "Wanna share with wind0ze..."
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by shao on 2009-08-27
Hello,

Okay, so, recently my roomates, (who have windoze) have been sharing episodes of House M.D. on there windows network (you know where you share crap on there desktop).

So my question is; Is there any way I can access these files and also share some of mine from Ubuntu?

---

### Post by stlsaint on 2009-08-27
without going into all the sharing stuff...ie samba etc etc...i can tell you that if you all are on the same lAN as it sounds like you are than you will be able to see there hdd as ubuntu can view ntfs, fat, etc...now they wont be able to see you as windows cannot read ext 2/3/4!! someone with more experience in this area will be able to tell you how to set ftp within your LAN...

---

### Post by SoftwareExplorer on 2009-08-27
Yes. Right click on the folder you want to share. Click sharing options. It might prompt you to install a package if you have never shared folders with ubuntu. Once you are past that, check share this folder, and guest access. (Unless you want them to have to have a user on your computer or know your password). Click create share. ta-da!

---

### Post by SoftwareExplorer on 2009-08-27
> **stlsaint said:**
> without going into all the sharing stuff...ie samba etc etc...i can tell you that if you all are on the same lAN as it sounds like you are than you will be able to see there hdd as ubuntu can view ntfs, fat, etc...now they wont be able to see you as windows cannot read ext 2/3/4!! someone with more experience in this area will be able to tell you how to set ftp within your LAN...

On the Lan, filesystem doesn't matter. It all depends on protocol, and windows uses smb. Linux has a program to use smb protocol, so it can see windows shares and share with windows.

---

### Post by SoftwareExplorer on 2009-08-27
To access them, go to Places->Network.

---

### Post by jonathanmotes on 2009-08-27
> **SoftwareExplorer said:**
> To access them, go to Places->Network.

Samba network browsing in Ubuntu is mostly broken. You usually have to access windows shares directly. For example, you could put this in the detailed location bar in Nautilus (the file browser):
```
smb://computer-name-or-ip/username
```

Sometimes you have to use the ip address instead of the computer name (if there is not a WINS server on the network, for example.)

To access your share from a windows machine, use

```
\\computer-name-or-ip\username
```

---

### Post by stlsaint on 2009-08-27
> **SoftwareExplorer said:**
> On the Lan, filesystem doesn't matter. It all depends on protocol, and windows uses smb. Linux has a program to use smb protocol, so it can see windows shares and share with windows.


thanks for the help...

---

### Post by Iowan on 2009-08-27
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a Windows sharing How-To that may be helpful.

---

