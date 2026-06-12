---
title: "&quot;Permission Denied&quot; While Accessing Ubuntu Share from OS X"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by Hobbesie on 2010-07-22
Hey all,

I've got some folders shared on our Ubuntu machine so that everybody can access them. However, some of our users are having problems with that. The two users who are on Macbooks can barely access anything without getting a "Permission Denied" message. I've hit the directories with chmod 777 just to obliterate any lingering issues, but yet the issue persists. 

Any help? We're getting a little exasperated over here and I'm beginning to see people sharpening swords.

---

### Post by JackNocturne on 2010-07-22
I had quite a **similar** situation myself, though i had changed the permissions it still denied access. 

I got it to work by typing my **user name & password**(when accessing the $shares) in the computer which wants to access my shared folders then it worked from there on.

---

### Post by Hobbesie on 2010-07-22
> **JackNocturne said:**
> I had quite a **similar** situation myself, though i had changed the permissions it still denied access. 

I got it to work by typing my **user name & password**(when accessing the $shares) in the computer which wants to access my shared folders then it worked from there on.

Thanks for the quick reply!

I tried logging in, but upon trying to save a file the software claims that the file is read-only. Help?

---

### Post by JackNocturne on 2010-07-22
> **Hobbesie said:**
> Thanks for the quick reply!

I tried logging in, but upon trying to save a file the software claims that the file is read-only. Help?

So it did **log-in** but now it doesnt want to **save/write** file to the disk?

---

### Post by JackNocturne on 2010-07-22
[IMG]http://i1021.photobucket.com/albums/af334/JackNocturne/Screenshot-1.png[/IMG]

---

### Post by Hobbesie on 2010-07-22
I just took a look at that screenshot, and my Share folder is set up exactly like that. 

However, I just logged into the share on another computer and it worked, for some reason. It's fine and dandy that way, but this user really needs to be able to access files from the original computer.

I checked the properties of the file in question, and it says that the owner is nobody, with a group of nogroup. Perhaps this is adding to the problem?

---

### Post by JackNocturne on 2010-07-22
> **Hobbesie said:**
> 
I checked the properties of the file in question, and it says that the owner is nobody, with a group of nogroup. Perhaps this is adding to the problem?


I have never heard of a file/folder having no owner, try changing the owner to be **you**

---

### Post by Penguin Guy on 2010-07-22
In your case, I believe you'll want to use [FONT="Courier New"]chmod[/FONT] with the [FONT="Courier New"]--recursive[/FONT] parameter:
```
chmod **-R** 777
```

---

### Post by Hobbesie on 2010-07-22
> **Penguin Guy said:**
> In your case, I believe you'll want to use [FONT="Courier New"]chmod[/FONT] with the [FONT="Courier New"]--recursive[/FONT] parameter:
```
chmod **-R** 777
```

Ran the recursive command, and the Mac user is still getting a Read-Only error. *sigh*

---

### Post by Penguin Guy on 2010-07-22
I assume you're using Samba?

---

### Post by JackNocturne on 2010-07-22
> **Hobbesie said:**
> Ran the recursive command, and the Mac user is still getting a Read-Only error. *sigh*

I dont know if you did, but all these (the command above given by Penguin Guy) and my suggestion in enabling **write** permission from the picture i attached have to be done using **root user permission**

---

### Post by Morbius1 on 2010-07-22
Do you as the local login user of the box with the share have read write access to the folder and it's files that is shared. If so then do this:

Open smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your local login user name.*[/COLOR]

Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```The "force user" will act as a mask and convert the remote user to you for those shares. As an added benefit all newly added files and folders saved by remote users will have you as owner eliminating the nobody:nogroup problem.

---

### Post by Hobbesie on 2010-07-22
> **Penguin Guy said:**
> I assume you're using Samba?

I imagine so. I set up the share by right-clicking on the folder and selecting "share".

---

### Post by Morbius1 on 2010-07-22
> **Hobbesie said:**
> I imagine so. I set up the share by right-clicking on the folder and selecting "share".
Yes you're using Samba. Samba calls it usershare. It uses the package Nautilus-share.

Did my suggestion not work?

---

### Post by Hobbesie on 2010-07-22
> **Morbius1 said:**
> Do you as the local login user of the box with the share have read write access to the folder and it's files that is shared. If so then do this:

Open smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your local login user name.*[/COLOR]

Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```The "force user" will act as a mask and convert the remote user to you for those shares. As an added benefit all newly added files and folders saved by remote users will have you as owner eliminating the nobody:nogroup problem.

To answer your question, yes and no. Some files/folders have local read and write access, while others do no. (I just opened a file, made a change, and it wouldn't save.)

---

### Post by Morbius1 on 2010-07-22
The change I suggested will only convert new remotely added folders. The chmod's that everyone has suggested should have fixed the current ones.

Is this a share of an NTFS or FAT32 formatted partition by any chance?

Why not post the output of the following command so we can get an idea of the ownership and permissions of the content of the shared folder:

```
ls -al /path-to-shared-folder
```

---

### Post by Hobbesie on 2010-07-22
> **Morbius1 said:**
> The change I suggested will only convert new remotely added folders. The chmod's that everyone has suggested should have fixed the current ones.

Is this a share of an NTFS or FAT32 formatted partition by any chance?

Why not post the output of the following command so we can get an idea of the ownership and permissions of the content of the shared folder:

```
ls -al /path-to-shared-folder
```

Sure. This is one of two shared folders...but I imagine it'll give you an idea of what is going on. Here you go:

total 716
drwxrwxrwx 14 paul   paul      4096 2010-07-22 10:34 .
drwxrwxrwx  5 paul   paul      4096 2010-07-12 11:27 ..
drwxrwxrwx  3 nobody nogroup   4096 2010-07-22 10:17 Acorn.app
-rwxrwxrwx  1 nobody nogroup   4848 2010-06-23 13:42 Aaa.ctb
drwxrwxrwx  6 paul   paul      4096 2010-06-26 17:00 Photos_MISC
-rwxrwxrwx  1 paul   paul    243652 2010-06-28 13:58 autodesk.pdf
drwxrwxrwx  2 paul   paul      4096 2010-06-30 14:30 Some Documents
drwxrwxrwx  4 paul   paul      4096 2010-07-22 14:16 Ling
drwxrwxrwx  2 paul   paul      4096 2010-07-15 12:03 Memo
-rwxrwxrwx  1 paul   paul     51600 2010-06-16 10:38 Elements.ods
-rwxrwxrwx  1 paul   paul     51679 2010-06-16 11:52 Elements - rev.ods
-rwxrwxrwx  1 paul   paul     61205 2010-06-15 18:03 Elements.xlsx
drwxrwxrwx  4 paul   paul      4096 2010-07-15 15:59 Documents
drwxrwxrwx  2 nobody nogroup   4096 2010-07-16 16:15 boxMove
-rwxrwxrwx  1 nobody nogroup  15364 2010-07-22 10:15 .DS_Store
drwxrwxrwx  2 paul   paul      4096 2010-07-22 14:43  Reports
-rwxrwxrwx  1 paul   paul     76927 2010-06-09 14:50 mod list(5).pdf
drwxrwxrwx  2 paul   paul      4096 2010-06-21 15:17 Moving
drwxrwxrwx  3 paul   paul      4096 2010-07-21 17:20 Software
drwxrwxrwx  3 nobody nogroup   4096 2010-07-09 15:07 .TemporaryItems
-rwxrwxrwx  1 nobody nogroup   4096 2010-07-09 15:07 ._.TemporaryItems
drwxrwxrwx  2 paul   paul      4096 2010-07-22 13:43 sheets
-rwxrwxrwx  1 paul   paul     71538 2010-06-09 14:37 agreement(4).pdf
-rwxrwxrwx  1 paul   paul     81118 2010-06-09 14:48 CR.pdf

---

### Post by Morbius1 on 2010-07-22
OK, I'm stumped.

I can't imagine under what conditions samba would differentiate by the OS of the client but post the output of the following commands to see if there's anything strange or conflicting in how your shares are set up:

```
net usershare info
``````
testparm -s
```

---

### Post by Hobbesie on 2010-07-29
> **Morbius1 said:**
> OK, I'm stumped.

I can't imagine under what conditions samba would differentiate by the OS of the client but post the output of the following commands to see if there's anything strange or conflicting in how your shares are set up:

```
net usershare info
``````
testparm -s
```

Sorry for getting back to you so late...I was out of town for a few days.

testparm -s gives this:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


net usershare info gives this:

[admin]
path=/home/paul/Documents/Admin
comment=
usershare_acl=Everyone:F,
guest_ok=y

[projects]
path=/home/paul/Documents/Projects
comment=
usershare_acl=Everyone:F,
guest_ok=y

[1001]
path=/home/paul/Documents/Projects/1001
comment=
usershare_acl=Everyone:F,
guest_ok=y

[software]
path=/home/paul/Documents/Admin/Software
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by Morbius1 on 2010-07-29
There's nothing wrong with your samba shares. The only thing that's missing in your smb.conf is:
```
force user = paul
```But for all your existing files the:
```
sudo chmod -R 0777 /home/paul/Documents
```that Penguin Guy suggested should have taken care of things.

I'm still stumped.

---

