---
title: "file sharing desktop to laptop"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by hashi856 on 2009-05-07
Where should I go for information on networking my desktop(windows) to my laptop(ubuntu).

I've never networked anything in my life, I just want to be able to share files between computer.

---

### Post by coutts99 on 2009-05-07
Samba

[https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html")

---

### Post by hashi856 on 2009-05-07
dsf

---

### Post by Iowan on 2009-05-07
I don't understand "dsf", but [here]("https://help.ubuntu.com/community/SettingUpSamba") is another Samba help page - and a [third]("http://samba.netfirms.com/") for good measure. Eventually, you'll want to mount some of these shares, then [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To will be handy.

---

### Post by mattgyver83 on 2009-05-08
While you should still read up on networking heres a short post on how you can do this quickly and easily through nautilus. 

> 1.  Find out the 'Workgroup' your windows computer(s) are on
[INDENT]a. Right click computer on start menu (vista) or my computer (xp) and select properties[/INDENT]
[INDENT]b. Workgroup is listed in section 'Computer name, domain, and workgroup settings'[/INDENT]
2.  Install samba on ubuntu, sudo apt-get install samba
3.  Edit smb.conf to reflect your proper workgroup name found on windows machine, restart samba
[INDENT]a.  gksudo gedit /etc/samba/smb.conf[/INDENT]
[INDENT]b.  sudo /etc/init.d/samba restart[/INDENT]
4.  Create a samba user and password
[INDENT]a.  sudo smbpasswd -a <YOUR_USERNAME>[/INDENT]
[INDENT]b.  this will prompt you to create a pasword for the user[/INDENT]


Your computer should be recognized on the network now, use your windows login credentials to access windows shares, and your smbpasswd login info you created for windows-to-linux connections. 

In nautilus (file browser) you can easily right click the folder and select 'Sharing options' granted you have the correct file permissions for the folder you wish to share.  Anything under the home directory should be easily shared.  When you create your first shared file it may prompt to install packages required for sharing, make sure you follow through.

Hope this helps you get started!

---

### Post by hashi856 on 2009-05-08
Wow Thanks

---

### Post by Steven_S on 2009-05-08
Thanks for these links! Will come in handy in a few days ;)

---

