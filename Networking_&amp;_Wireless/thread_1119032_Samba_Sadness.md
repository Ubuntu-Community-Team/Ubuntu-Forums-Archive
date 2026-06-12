---
title: "Samba Sadness"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by haqinai on 2009-04-07
OK I am not an Expert nor am I good a codes in terminal. 

Here is my need: 
I need to get samba working so that I can share files with windows clients. There is no servers, it is just workstation that are under a windows workgroup. I have done what I know to do but just can't get into the windows network from the Ubuntu workstation. nor can I see the shared files of the Ubuntu workstation from a windows workstation.  

I have ran $ "sudo aptitude install smbfs" and it did it's thing and then no go.....>>>?<<<

What am I doing wrong and what do I need to do?

---

### Post by Ubunt2u on 2009-04-07
Did you configure your shares?  I believe it's in /etc/samba/smb.conf

I setup a samba share for the first time a few months ago.  There may be more config options, let me check on my config so you can use it as an example.

---

### Post by Slim Odds on 2009-04-07
> **haqinai said:**
> I have ran $ "sudo aptitude install smbfs" and it did it's thing and then no go.....>>>?<<<

What am I doing wrong and what do I need to do?

smbfs is not the same as samba

smbfs is Samba file system utilities, not the samba daemon (smbd)

Try:
```
sudo apt-get install samba
```

---

### Post by Zimmer on 2009-04-07
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Samba_File_Sharing](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Samba_File_Sharing)

See here for adding SAMBA users.
I found it best to add your login username as a SAMBA user AND to add another with the same name and password as your WinXP login.

Allow folder sharing... as per the above link and  make sure the SAMBA config file has the correct Win workgroup set  (XP the default is MSHOME but in VISTA it is WORKGROUP - I think - but you may have already customized that name on your Win box....) Read the notes in the default samba config file, save a backup before you make changes...

see if you can acces the shares from the WIn box.

EDIT: some previous OLD links..
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
may be of some help.

---

