---
title: "How To Permanently Mount an XP's shares in Ubuntu 9.04"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by wdavro on 2009-08-22
I'm just depressed.  I was a net admin through nt4 and Novell 4.  I have "some" knowledge.  Or at least I thought I did.

I've been trying to get up to speed on Linux for years but just keep finding it too cryptic and difficult.  Recently I had a local company build a Ubuntu 9.04 box for me.   Currently, I'm trying to permanently mount my Windows XP shares on my other desktop computer in my home folder on my Ubuntu box.  I originally posted a question back on 7/25 which solved one question but I've been trying to get it to work using fstab ever since and haven't succeeded.  I've read countless threads, man pages and wiki how-to's and while they all have good information, I still haven't figured it out yet.

I am the only user (david) on 9.04 (besides root) but I want to mount the shares only for me to see and use in case I create other users in Ubuntu.  I can successfully see the XP shares using Places > Network.  I have also successfully shared some Ubuntu directories to my XP desktop.

I have tried mounting them in folders in /mnt as root but no good.  I have created the folders for the mount points in my home directory.  I have tried both owned as Root and owned by david.  I have a credential file in /etc/samba with perms at 200 with the XP share login ID and password.  The various fstab entries I have tried are:

# //desktop/cdrive   /home/david   ntfs-3g   credentials=/etc/samba/credentials,uid=1000,gid=1000,rw,suid,dev,exec,auto,async,_netdev   0   0
# //desktop/cdrive   /home/david/cdrive-desktop   ntfs-3g   defaults,umask=0   0   0
# smb://desktop/cdrive   /media/WinShares   ntfs-3g   defaults,umask=0   0   0
#//hp6230/cdrive   /home/david/HP6230-C-Drive   smbfs   iocharset=utf8,credentials=/etc/samba/credentials.lt,uid=1000,gid=1000   0   0
#/mnt/xp.cdrive
//hp6230/cdrive   /mnt/xp.cdrive   smbfs   iocharset=utf8,credentials=/etc/samba/credentials.lt,uid=0,gid=0   0   0

With the above, the sudo mount -a comand gives me:
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

Could I beg someone to craft the correct fstab line for me using the following line as a template?

//hp6230/cdrive   /home/david/HP6230-C-Drive   smbfs   iocharset=utf8,credentials=/etc/samba/credentials.lt,uid=1000,gid=1000   0   0

My very humble thanks in advance.

---

### Post by swerdna on 2009-08-22
I believe smbfs is finally removed in kernels 2.6.27+ so use cifs now.

Try this command line version first because it will give you error messages that you can see and they will guide you to the correct solution (maybe :)):```
mount -t cifs -o username=server_user,password=server_pwd,uid=1000,gid=1000 //hp6230/cdrive /home/david/HP6230-C-Drive
```

Then, when it's working just manipulate it a bit for the fstab version, like this:```
//hp6230/cdrive /home/david/HP6230-C-Drive cifs username=server_user,password=server_pwd,uid=1000,gid=1000 0 0
```

Reference: [Samba: HowTo Mount a CIFS Network Share [AKA Mapped Network Drive] in openSUSE]("http://opensuse.swerdna.org/susesambacifs.html")

---

### Post by wdavro on 2009-08-22
Thank you for your response.  

I tried your Mount command in terminal to no avail.  I replaced server_user with the share user name, and server_pwd with the password.  Otherwise I left the line exactly as you wrote it.

without sudo it tells me only root can do that.  With sudo it simply gives me a detailed usage response.

---

### Post by swerdna on 2009-08-22
Sure -- you have to use sudo -- forgot to mention that. I also forgot the options lead-in parameter (-o), so I's really like this for the first one:```
mount -t cifs -o username=server_user,password=server_pwd,uid=1000,gid=1000 //hp6230/cdrive /home/david/HP6230-C-Drive
```Note I put "-o" in front of the options, that's what I forgot.

---

### Post by wdavro on 2009-08-22
My heart is aflutter!  Tantalizingly close!

I entered the modified command in terminal and it worked perfectly.
I then took your originalcode for the fstab, added the -o, saved and ran sudo mount -a and it told me:

[mntent]: line 15 in /etc/fstab is bad

(The line in question is in fact line 15)
Here's what I put in fstab:

//hp6230/cdrive /home/david/HP6230-C-Drive cifs -o username=xxxx,password=xxxx,uid=1000,gid=1000 0 0

what did I do wrong?

---

### Post by swerdna on 2009-08-22
Take out the "-o", have a tranquilizer, wait 10 minutes and then when you're calm -- run sudo mount -a

(I know, I know -- I forgot to tell you that "-o" is just for the command line version).

---

### Post by wdavro on 2009-08-23
Ah, I feel so much better....

The command works and fstab loads .

Now, I have another challenge though.  I'm trying to take the userid and password out of the fstab file using the credentials option.  The trick is that I want the mount points to be in the /home/david folder but I suspect the mounting in fstab is taking place as root.  

I tried the cred files in /etc/samba but got permission errors with mount -a.  So I put the credential files in /root but still get the perm errors.  Perhaps the permission problem is about root trying to mount in /home/david.

Is my goal possible?  Do I need to make myself a member of the Root group?

---

### Post by dmizer on 2009-08-23
> **wdavro said:**
> Ah, I feel so much better....

The command works and fstab loads .

Now, I have another challenge though.  I'm trying to take the userid and password out of the fstab file using the credentials option.  The trick is that I want the mount points to be in the /home/david folder but I suspect the mounting in fstab is taking place as root.  

I tried the cred files in /etc/samba but got permission errors with mount -a.  So I put the credential files in /root but still get the perm errors.  Perhaps the permission problem is about root trying to mount in /home/david.

Is my goal possible?  Do I need to make myself a member of the Root group?

Please see the 2nd link in my sig. It will explain how to make a credentials file and how to mount everything so that you can see it as your regular user.

---

### Post by tedtester on 2009-08-23
It's so well explained, and as you know u're still using DEBIAN as Base
so take a look at this page please:

[http://www.debian-administration.org/articles/165]("http://www.debian-administration.org/articles/165")

---

### Post by dmizer on 2009-08-23
> **tedtester said:**
> It's so well explained, and as you know u're still using DEBIAN as Base
so take a look at this page please:

[http://www.debian-administration.org/articles/165]("http://www.debian-administration.org/articles/165")

As you know, Ubuntu is not exactly the same as Debian. And as a result, smbfs is not available in the repositories. The information you linked to does not apply unless you compile smbfs support into the Ubuntu kernel manually. This is why I linked to my CIFS tutorial rather than a smbfs tutorial.

---

### Post by tedtester on 2009-08-23
1. .... just sudo apt-get install smbfs
2. do the steps decribed in the debian article
- replace cifs within fstab instead of smbfs

that's it

---

### Post by dmizer on 2009-08-23
> **tedtester said:**
> 1. .... just sudo apt-get install smbfs
2. do the steps decribed in the debian article
- replace cifs within fstab instead of smbfs

that's it

It doesn't quite work that way, as smbfs options != cifs options.

---

### Post by wdavro on 2009-08-23
I've spent the last few hours reading through the link you sent to the point that my head was spinning.  I decided to try a few things and finally solved it.

Of course, it was a user error (doh!).  When I built the cred files, I the first line I put in began: user= instead of username=.  That generated the following message:

mount error(13): Permission denied

Once I fixed that, all was well.

Your link also supplied the fix for the "cifs  server not responding" error on reboot.

Thank you for all your help, and the phenomenal amount of information you have provided to me, and to all the others.

---

