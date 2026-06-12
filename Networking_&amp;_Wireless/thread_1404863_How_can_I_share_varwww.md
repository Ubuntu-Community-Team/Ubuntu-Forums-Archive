---
title: "How can I share /var/www?"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by ForumCat on 2010-02-11
I need to share my /var/www folder on a Ubuntu Server 9.1 machine, but I have been unsuccessful.  I can see the share from my Vista machine, and I can read/copy files from the share, but I can't write to it.  That is, I can't paste files into the share, rename files, delete files, etc.

Here is what I've done so far.

1.  Set up Linux user named family and added the family user to the root group.

2.  smbpasswd -a family  (...and set password to same password as Linux user by the same name)

3.  The owner and group of the /var/www folder and its contents are root and root, respectively.

4.  The permissions for /var/www and contents are drwxrwxr-x

5.  Configured my /etc/samba/smb.conf file as follows...

[global]

workgroup = MYGROUP
netbios name = WWW
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
usershare allow guests = yes

[www]
path = /var/www
read only = No
writable = Yes
create mask = 0775
directory mask = 0777

NOTE:  If I change the permissions for /var/www to drwxrwxrwx (777) then I can write to the share, but I don't want all users to have write access, because this is going to be a public web server.  I only want the family user to be able to write files to the share.

Can someone please help me?

Thanks,
ForumCat

---

### Post by suseendran.rengabashyam on 2010-02-12
Hi,

There seems to be similar problems with SAMBA share and Windows Vista. Have you tried accessing the SAMBA share from a Windows XP machine ?? Do you get a similar error ??

Try to upgrade SAMBA and see whether it helps.

Here is a link to a similar thread i.e sharing /var/www
[http://ubuntuforums.org/showthread.php?t=290653](http://ubuntuforums.org/showthread.php?t=290653)

---

### Post by ForumCat on 2010-02-12
I have not tried XP, but I have tried Windows 7 Enterprise, and that can't write either.  Read only.  Next I'm going to try updating Ubuntu/Samba like you suggested.  I'll let you know how that goes.  Thanks!!!

---

### Post by DGortze380 on 2010-02-12
You're probably better off using FTP or SFTP.

---

### Post by ForumCat on 2010-02-12
SOLVED!!!  I used Aptitude to install all available updates and upgrades.  In the process, since Samba was upgraded, I was prompted whether I wanted to overwrite my /etc/samba/smb.conf file.  I figured, "What the heck?"  After finishing with Aptitude, I followed the instructions in this thread...

[http://ubuntuforums.org/showthread.php?t=290653](http://ubuntuforums.org/showthread.php?t=290653)

...to configure the fresh and new /etc/samba/smb.conf file.  Then I restarted Samba.  After that, my share worked just fine!  Not sure which solved the problem--the updates/upgrades or the fresh smb.conf file--but I would recommend doing both in the future.

Thanks for the help!

---

