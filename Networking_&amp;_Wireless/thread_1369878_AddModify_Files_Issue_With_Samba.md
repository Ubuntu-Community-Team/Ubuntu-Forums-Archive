---
title: "Add/Modify Files Issue With Samba"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by IAmNotAUser on 2010-01-01
I hope this is in the right place - it is a networking issue I think. 

I have a Ubuntu Server set up as a file store for my home network, backups and the like. 

I have one user, sysamin, set up on the server, and Samba set up to share my /mnt folder with the network.

When I log onto my Windows 7 machine, I give my sysamin password and can access the /mnt folder and the folders and files beneath it, but I cannot modify them in any way, or drag-and-drop files into the file structure.

Sysamin is set up to be the owner and has read/write permissions, so why can I not modify the files or add new ones?

Can anyone please suggest some config to look at in order to try to fix this? 

Thanks

---

### Post by Morbius1 on 2010-01-01
File sharing has two steps to permissions. Samba states what MAY be done to a folder but linux itself states what CAN be done to the folder.

We need to find the linux permissions on the shared folder and it's contents:

Open **Terminal **
Type **ls -dl /mnt/shared_folder**
Type [B]ls -l /mnt/shared_folder

[/B]Substitute the real name for shared_folder

---

### Post by IAmNotAUser on 2010-01-01
```
ls -dl /mnt
drwxr-xr-x 6 root root 4096 2009-12-22 16:45 /mnt
```

```
ls -l /mnt
total 364
drwxr-xrwx 19 sysamin sysamin   4096 2010-01-02 00:07 Files
drwxr-xr-x  5 sysamin sysamin  36864 2010-01-02 00:27 Uni
drwxrwxrwx  1 root    root    327680 2010-01-02 00:30 UniBackup
drwxr-xrwx 62 sysamin sysamin   4096 2009-12-23 15:38 Videos

```

I'm trying to save files inside /mnt/Files if that's any help.

---

### Post by Morbius1 on 2010-01-02
I'm getting sloppy. I never asked you how you set up your shares: "Classic Samba" or Nautilus-share ( right click > sharing options).

You could post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

This will tell us the share definitions on both sharing methods. 

In the mean time, you could do this:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Now depending on which method of sharing you're using you need to add the following line to your smb.conf:

```
force user = sysamin
```If you're using Nautilus share add it to the [COLOR=Blue][global][/COLOR] section.
If your using "Classic Samba" add it to the share defintition itself. For Example:

> [folder]
comment = 
path = /mnt/Folder
public = no
writable = yes
[COLOR=Blue]force user = sysamin[/COLOR]If you can read and write to those files as sysamin while logged onto that box so should the remote user.

---

### Post by IAmNotAUser on 2010-01-02
> **Morbius1 said:**
> I'm getting sloppy. I never asked you how you set up your shares: "Classic Samba" or Nautilus-share ( right click > sharing options).

You could post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

This will tell us the share definitions on both sharing methods. 


I could have sworn that I did the right-click method, but when I right click inside the folder now, I don't get the option for 'sharing options' at all, so now I'm not so sure. I may have just set this up when I reinstalled to Ubuntu (I used to be running Kubuntu).

This is the output I got from those commands:

```
sysamin@H-SERVER:~$ net usershare info
sysamin@H-SERVER:~$ testparm -=s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Mount]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    wins support = Yes
    default service = global
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    winbind trusted domains only = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Mount]
    path = /mnt

```

> 
In the mean time, you could do this:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Now depending on which method of sharing you're using you need to add the following line to your smb.conf:

```
force user = sysamin
```If you're using Nautilus share add it to the [COLOR=Blue][global][/COLOR] section.
If your using "Classic Samba" add it to the share defintition itself. For Example:

If you can read and write to those files as sysamin while logged onto that box so should the remote user.

I added force user = sysamin to the [Mount] section...do I need to restart a process? And should I add the writeable = yes that you have in your quote too as I still cannot write to the folder.

Also, I'd rather not have to force a user, I was hoping that within the next month I would add a second user, so to restrict what other people can see on the server, whilst still allowing me full access to the files.

---

### Post by Morbius1 on 2010-01-02
OK, now I'm really confused:

You have no nautilus-shares and you're trying to share /mnt which only root owns. No one not even sysamin has access to /mnt. 

Try this:

Open **Terminal**
Type **shares-admin**
Then "Shared Folders" > Add > Path = /mnt/Files > uncheck "read only" > Share

You should get something in your smb.conf that looks like this:
> [Files]
path =  /mnt/Files
available = yes
browsable = yes
public = yes
writable = yes

See if that works first. We can always change the authentication and add the force user later if we have to.

---

### Post by IAmNotAUser on 2010-01-02
Root owns /mnt, but it is set up so that other users have read but not write permissions when I do ls -dl /mnt.

When I try the shares-admin, the box pops up, but add is greyed out. There is a Mount already in there, and when I select it and click properties, then the boxes inside that window are greyed out too.

This is the same whether I run shares-admin or sudo shares-admin.

---

### Post by SteveHillier on 2010-01-02
IAmNotAUser,
forgive me if I am confused.

Your original post says 
> can access the /mnt folder and the folders and files beneath it, but I cannot modify them in any way

and your last post says
> but it is set up so that other users have read but not write permissions

Aren't there exclusive options?  Surely unless you allow write permissions you will not be able to add or modify files.

---

### Post by IAmNotAUser on 2010-01-02
/mnt is set up in that way, with root as the owner and with others with only read permissions.

However, sysamin is set up as the owner of /mnt/Files, and has read and write permissions enabled, indeed when I am at the machine, I have no problems modifying files. It's only when I go to my Windows machine I have issues.

---

### Post by Morbius1 on 2010-01-02
First we need to create a viable share. Right now you don't have one.

You need to click on the "unlock" button once the gui opens up. But let's just edit what you have directly in smb.conf.

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Change this:
> [Mount]
    path = /mntTo this:
> [[COLOR=Blue]Files[/COLOR]]
[COLOR=Blue]path =  /mnt/Files
available = yes
browsable = yes
public = no
writable = yes[/COLOR]Save the file, exit gedit, and back in the terminal type: [B]sudo service samba restart

[/B]Now tell us what happens when you try to access the share.[B]

[COLOR=Blue]*This is a whole lot easier with nautilus-share BTW. *[/COLOR]
[/B]

---

### Post by IAmNotAUser on 2010-01-02
Thanks for your help Morbius1. I can now delete and modify files inside /mnt/Files. I assume I just redo the other 3 and then I'm set, yes? :)

I use a mobile dongle to connect to the internet, and so my server does not have internet access. Would the greyed out boxes be activated if I downloaded and installed nautilus-share?

---

### Post by Morbius1 on 2010-01-02
> I assume I just redo the other 3 and then I'm set, yes?I think so, but just post back if there's a problem.

> Would the greyed out boxes be activated if I downloaded and installed nautilus-share?     First, It should have been installed by default so I'm concerned about it's absence.

Second, You have a workable system using "Classic" samba. It was the way all sharing was once done and is still the only option for complex sharing situations in a mixed windows / linux environment. I'd just keep what you have. I was simply expressing a little frustration, Sorry.

---

### Post by IAmNotAUser on 2010-01-02
> **Morbius1 said:**
> First, It should have been installed by default so I'm concerned about it's absence. 

Is that true on the server distro too? I have a feeling that I simply clicked the x in the samba share part of the install, and left it at that when I originally did it. Although, I may have broken something since, it's quite possible.

> **Morbius1 said:**
> Second, You have a workable system using "Classic" samba. It was the way all sharing was once done and is still the only option for complex sharing situations in a mixed windows / linux environment. I'd just keep what you have. I was simply expressing a little frustration, Sorry.

Not an issue at all. I do plan on plugging it in at some time, so would you advise getting that package when I do?

---

### Post by Morbius1 on 2010-01-02
You really don't need to as you've got experience now using the traditional method. And like I said there is infinitely more fine tuning that you can do on a per-share basis using smb.conf then you could ever do with nautilus-share. 

Nautilus-share is more for the vast majority of desktop users that simply want to share folders to peers on the network.  With nautilus-share and CUPS server to handle printing, the average desktop user never needs to touch smb.conf. Unless there's a problem :)

---

