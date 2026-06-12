---
title: "Permission, File Share, Partitions, etc"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by ultimatebuster on 2009-07-14
Hi!
I'm currently running a file server with Ubuntu 9.04 64 Bit Server Edition with GUI installed.

I partitioned the hard drive so I have a Data partition (ext4). I have a couple of questions.

I'm currently using SAMBA. The Windows client can see my Ubuntu Server from their network places.

[LIST=1]
[*]How come the used space is 8GB when I have absolutely nothing in that partition?
[*]How come that the "allow write" in Sharing Options always uncheck itself after I check it in root file browser? (gksudo nautilus)
[*]How do I set up an different account (possibly SAMBA account? IDK) for everyone on the Windows machines so they can write to the partition?
[*]How do **I** get to use the root account from a Windows client and manage all the files? (Read Write all files and their content?)
[/LIST]

I currently have an account named as "administrator". However, this account do not have root access unless I use "sudo" with everything.

Thanks a lot!

FYI: I'm a newbie to Ubuntu (< 2 month experience with Ubuntu 9.04 Desktop Edition)

---

### Post by martinbaselier on 2009-07-14
If you edit /etc/samba/smb.conf manually, you can choose more option, than by using the graphical interface.
If you type man smb.conf in a terminal, you'll get a complete list of all available options. 
You'd want to setup a share with user/password and make that user the owner of the specific share.
If you want a simpler and less secure approach you can allow anyone to read/write/delete files on the share. For that you need to change the rights of the directory on the linux server. 

How did you draw the conclusion, that there's 8GB used on an empty partition?

---

### Post by ultimatebuster on 2009-07-14
> **martinbaselier said:**
> If you edit /etc/samba/smb.conf manually, you can choose more option, than by using the graphical interface.
If you type man smb.conf in a terminal, you'll get a complete list of all available options. 

I'm currently using webmin to manage SAMBA. I can login using my 'administrator' credentials on a Windows machine. However, I want a separate account for storing data for another person. I'm not sure whether if you need a SAMBA account to login from Windows or just a regular user account at System -> Administration -> Users and Groups
> **martinbaselier said:**
> 
You'd want to setup a share with user/password and make that user the owner of the specific share.

Currently looking at some instructions for that.
> **martinbaselier said:**
> 
If you want a simpler and less secure approach you can allow anyone to read/write/delete files on the share. For that you need to change the rights of the directory on the linux server. 

No, that would be rather a bad idea. Open Wifi + that = massive amt of problems
> **martinbaselier said:**
> 
How did you draw the conclusion, that there's 8GB used on an empty partition?
Just look at these screenshots. Kind of confused about which one is right...

[IMG]http://i30.tinypic.com/2qwhqmo.png[/IMG]
[IMG]http://i26.tinypic.com/rw6qf8.png[/IMG]

---

### Post by ultimatebuster on 2009-07-17
bump!
Just to make myself clear, I wish to manage other "normal" user's file as well as my own without having to use the root account. Is that possible?

---

### Post by swerdna on 2009-07-18
Let's have a look at a couple of your questions:
> # How come the used space is 8GB when I have absolutely nothing in that partition?On the server, can you do these terminal commands and post the results here:
[LIST=1]
[*]df -Th
[*]ls -l /media/DATA
[/LIST]
And why do you think the screenshot shows the location as "on the desktop" for the directory being portrayed when it is in fact in /MEDIA? Are you clicking the properties of an icon portraying a hard drive instead?
> How come that the "allow write" in Sharing Options always uncheck itself after I check it in root file browser? (gksudo nautilus)If you're making shares with the Nautilus sharing tool, and the checkmark doesn't work, you might have "usershares" wrongly set up. Please post here the contents of the samba config file so I can look at your usershare setup parameters and see whether you've enabled therein the facility to share files outside the home directories.

You can create a normal Linux user e.g. "sambauser". Add sambauser to the Samba users database with this terminal command:```
sudo smbpasswd -a sambauser
```
Chown the directory "DATA" to owner "sambasuer" with this command:```
sudo chown -R sambauser:sambauser /media/DATA
```
Completely undo any usershare that you've made with the Nautilus sharing tool.
Chmod the directory to drwxr-x--- with ```
sudo chmod 750 /media/DATA
```and make any files already existing inside DATA to rw-r--r-- and directories to drwxr-xr-x

Add this code to the file smb.conf to share the directory:
```
[DATA]
path = /media/DATA
read only = no
force user = sambauser
```
FYI that share and a bunch of other options for shares are discussed in the following tutorial: 
[Samba Server and Ubuntu / Kubuntu: HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html")

We might deal with the other questions later, after these perhaps.

---

### Post by ultimatebuster on 2009-07-18
do I need to create "sambauser" with or without a password?

---

### Post by swerdna on 2009-07-18
> **ultimatebuster said:**
> do I need to create "sambauser" with or without a password?

I assume you are talking about this: sudo smbpasswd -a sambauser. Is that right? If that's what you're talking about, then yes, generate a password. You then supply the username and password to trusted external users. If you want access to everyone, guest access (which I think you said no to above) you add this line into the stanza for the share: ```
guest ok = yes
```

---

