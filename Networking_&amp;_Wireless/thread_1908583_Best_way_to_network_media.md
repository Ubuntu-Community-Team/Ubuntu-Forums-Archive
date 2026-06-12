---
title: "Best way to network media"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by MidnightbluRose on 2012-01-13
Hello!

I'm building kind of like a media hub (running ubuntu) from spare computer parts I have around.  I'm thinking of having it run when I want, but having all my media stored on it.  Then having it stream to my laptop when I want to watch stuff.  Should save having to swap between harddrives and what not.

What's the best way to do this in Ubuntu?  I would like to be able to restrict which device on the home network can access it and what not.  Is there a good program that can do all of this?  

Thanks.

---

### Post by jsra on 2012-01-13
Hi,
it depends what you wanna share. I think Samba can fit your needs, you can use eg VLC media player on your notebook.

---

### Post by MidnightbluRose on 2012-01-13
> **jsra said:**
> Hi,
it depends what you wanna share. I think Samba can fit your needs, you can use eg VLC media player on your notebook.

I'll be watching this on my linux laptop.  Does Samba only do Linux to Windows?

---

### Post by jsra on 2012-01-13
If you need to share files just between Linux boxes you can go for NFS, [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). But if there will need to share files with Linux and also with Windows, I would go for Samba.

---

### Post by MidnightbluRose on 2012-01-14
> **jsra said:**
> If you need to share files just between Linux boxes you can go for NFS, [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). But if there will need to share files with Linux and also with Windows, I would go for Samba.

Thanks for the two options!

---

### Post by 2F4U on 2012-01-14
Samba allows you to share files and folder between Linux, Windows, Mac OSX and some more. It is not restricted to Windows. It is designed for heterogenous environments.

---

### Post by nothingspecial on 2012-01-14
I use sshfs. For example I have an alias like this

```
alias vids='sshfs -o idmap=user nothingspecial@192.168.1.16:/mnt/data/Videos ~/Videos'
```

When I want to watch a video on my laptop, I just type ```
vids
``` and they appear in my Videos folder.

---

### Post by MidnightbluRose on 2012-01-17
So I built the computer and got everything working.

Though, I did run into a few Samba issues.  Mainly, me getting an error when I tried to access one of the drives on my laptop.  I'm not exactly sure how I got it to work but I did.

I'll just post my story in case someone is trying to do something like this and stumbles on this topic.

I think I did some mixing of services to get it to work they way I wanted to.

Ultimately it came out like this:

On my laptop (running Ubuntu) I'm able to mount the three drives on the desktop (running Ubuntu).  Allowing me to access them on my ubuntu laptop and play/edit the video files.
If I go on a computer running Windows I can see the desktop, but when I try to access the files I get a login screen.  

I originally just wanted the desktop to show the stuff to linux only computer, but the above works fine.  

I was able to achieve this by:

- Adding the drives in Samba
- Going into the drives right clicking > Properties >  Share.  Clicking on the Share this folder, and Allow others to create and delete files in this folder.  Then going to permissions changing group to sambashare, and changing the others to no list, create/delete, no access.  My third drive doesn't have this option, but I guess it doesn't matter much. 

Thanks for the help!

---

