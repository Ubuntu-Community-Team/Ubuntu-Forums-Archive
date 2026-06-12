---
title: "samba share not mounting at boot"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by kamelie1706 on 2011-08-12
Hi,

I have been searching around but could not find an answer that suits my problem.

Here is the line I have in my /etc/fstab
//192.168.1.188/openshare       /mnt/lacie_nas/openshare        cifs    errors=remount-ro,iocharset=utf8,file_mode=0777,dir_mode=0777   0       0

The remote directory is a LACIE NAS.

At boot the directory is not mounted but if I execute the command "mount -a" it works perfectly.

Any idea where I should look after?

Thanks!

---

### Post by kamelie1706 on 2011-08-12
I have added "mount -a" to /etc/rc.local .... did not solve the problem

is there a way to mount without typing a password (as with sudo)? my nas directory does not require one

---

### Post by kamelie1706 on 2011-08-12
Maybe I am trying the wrong solution. I  want to have a script running a cron job that mount the directory and copy files. 

Would it be then as simple as making this running under root crontab?
mount -a
rsync my_sync_command

is it the best/more secure approach?

I understood that playing with the sdoers permissions with NOPASSWD is not recommended for security reason.

---

### Post by kamelie1706 on 2011-08-15
even we root access it seems that "mount -a" require password.

I have done:
sudo -i 
mount -a

then it requires password ... will it do the same if I use "mount -a" in a script run as root crontab?

---

### Post by kamelie1706 on 2011-08-15
Hi,

at the end it worked very nicely in  a script run in root crontab.

I have now happy backup running every hour when my computer is on :guitar:

---

