---
title: "An error occurred while mounting remote folder"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by woodyg on 2012-02-15
I want to auto-mount a remote folder on startup. I have placed 
 
```
//192.168.1.100/m-backup        /media/remotefolder     username=m-xubuntu,password=xyz smbfs    auto    0    0 
```in etc/fstab, but all I get is the error message 

**"an error occurred while mounting media/remotefolder"**

Can someone see what the problem is, or suggest how I can debug it (or is there an easier way to do this)?

---

### Post by sudodus on 2012-02-15
If you use 'vanilla' Ubuntu, your file browser should be Nautilus. Then you can select

***File -- Connect to server***
and select service: ***Windows*** (which is using samba)

When your remote drive is mounted, you can drag and drop its icon to the left panel of Nautilus.

And the next time you log in, you can mount it by clicking the icon on the left panel of Nautilus :-)
--
It works in the same way if you use ***sftp*** which is called SSH in the submenu of Nautiles.

---

### Post by woodyg on 2012-02-15
Thanks, but **I need it to be done on startup (automatically)**, as I will have LuckyBackup to perform automatic backups of my main hd which will be copied into that remote folder.

---

### Post by woodyg on 2012-02-16
Previously (on a Xubuntu rather than my current Ubuntu) I used this

```
//192.168.1.100/m-backup        /media/remotefolder  smbfs   credentials=/root/.smbcredentials,noperm,file_mode=0777,dir_mode=0777   0       0
```with my login details in root/.smbcredentials (idea from [this site]("http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_113.html"))

That worked fine, but it doesn't work now on Ubuntu (not even an error message). I don't mind using either approach, as long as it works. What am I doing wrong? :(

---

### Post by Morbius1 on 2012-02-16
> That worked fine, but it doesn't work now on Ubuntu (not even an error message).If you run the following command it has no  error messages?
```
sudo mount -a
```BTW1: You did create /media/remotefolder first, right?

BTW2: smbfs is no longer used. You might want to change that to cifs.

---

### Post by woodyg on 2012-02-16
sudo mount -a was useful. I realised that the syntax wasn't 100% correct. the following worked:

//192.168.1.100/m-backup    /media/remotefolder    cifs    username=m-xubuntu,password=xyz,noperm,file_mode=0777,dir_mode=0777,auto    0    0

Useful syntax info was found in this [introduction to fstab]("https://help.ubuntu.com/community/Fstab")

---

