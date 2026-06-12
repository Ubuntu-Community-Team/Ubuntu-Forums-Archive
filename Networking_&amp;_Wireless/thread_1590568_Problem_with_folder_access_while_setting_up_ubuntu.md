---
title: "Problem with folder access while setting up ubuntu as file server"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by graeuk on 2010-10-08
Hi Everyone,

I am fairly new to Linux, dabbled with it over the years but am a experienced windows user so not a complete noob.  I am setting up Ubuntu 10.04 as a file server following a tutorial in Linux User and Developer mag which is great but having a bit of a problem getting it to work correctly.

I have two folders in the OPT directory and they can only be accessed by using the main username and password for the linux machine when logging on through my Win 7 machine, if I try and access the directory called 'alex' using the Alex username/password I can log into the folder but only have read only access.

I think (but am not sure) it has something to do with setting the ownership permissions of the folders .. 

part of the step after creating the directory was

# sudo chown -R root:users /opt/alex

and that didn't seem to work, it wouldn't allow me access as either user so I did

# sudo chown -R root:grae /opt/alex

grae is the main user and so that user has access but the user called alex doesn't ...

Can anyone advise?  I am sure you need more info so please let me know what would help you see what the problem is :)

Many Thanks,

Graham.

---

### Post by graeuk on 2010-10-11
Hi,
Is anyone able to help with this?
Thanks.
Graham.

---

### Post by graeuk on 2010-10-13
Or maybe there is a tutorial that someone could link me to that is recommended?  I am using 10.04LTS at the moment.

Thanks.

---

### Post by luvshines on 2010-10-13
> **graeuk said:**
> 

I have two folders in the OPT directory and they can only be accessed by using the main username and password for the linux machine when logging on through my Win 7 machine, if I try and access the directory called 'alex' using the Alex username/password I can log into the folder but only have read only access.

I think (but am not sure) it has something to do with setting the ownership permissions of the folders .. 

part of the step after creating the directory was

# sudo chown -R root:users /opt/alex

and that didn't seem to work, it wouldn't allow me access as either user so I did

# sudo chown -R root:grae /opt/alex

grae is the main user and so that user has access but the user called alex doesn't ...

Can anyone advise?  I am sure you need more info so please let me know what would help you see what the problem is :)

Many Thanks,

Graham.

If I get this correct, you have /opt shared through Linux machine which you are trying to access by Windows machine.
The alex directory is readable/writeable by grae but for alex it is only readable. Right ??

Did you setup Samba share on Linux machine or are you using Winscp from Win7 ?

---

### Post by graeuk on 2010-10-13
Hi.
I set up a Samba share on Linux.
thanks.
Graham.

---

### Post by luvshines on 2010-10-13
> **graeuk said:**
> Hi.
I set up a Samba share on Linux.
thanks.
Graham.

Samba setup was done by modifying smb.conf or using the Nautilus itself ??

If you followed modifying smb.conf then can you post the output of:
```
testparm -sp
```

Else, for nautilus configured shares:
```
net usershare info
```

---

### Post by graeuk on 2010-10-13
modifying it directly. The output is below, thanks.

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share1]"
Processing section "[alex]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = BS-OFFICE
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

[share1]
    comment = Ubuntu Share 1
    path = /opt/share1
    write list = grae, Graham, Martin
    create mask = 0755
    guest ok = Yes

[alex]
    comment = Ubuntu Share Alex
    path = /opt/alex
    write list = alex, Alex
    create mask = 0755

```

---

### Post by luvshines on 2010-10-13
From your smb.conf
1. [share1] looks world browseable since it has 'guest ok = yes'. As you said in comment #1 they are accessible only with passwords, I think you should consider commenting that out, for security (if you wish)

2. For [alex], in comment #1 you mentioned chown -R root:grae /opt/alex. Then I don't think alex will able to write to it if it doesn't have permissions for write, since it is owned by root user and grae group

What is the output for following:
```
ls -ld /opt/alex
```

---

### Post by graeuk on 2010-10-13
> **luvshines said:**
> From your smb.conf
1. [share1] looks world browseable since it has 'guest ok = yes'. As you said in comment #1 they are accessible only with passwords, I think you should consider commenting that out, for security (if you wish)

2. For [alex], in comment #1 you mentioned chown -R root:grae /opt/alex. Then I don't think alex will able to write to it if it doesn't have permissions for write, since it is owned by root user and grae group

What is the output for following:
```
ls -ld /opt/alex
```
Thanks, yes I was just testing the guest browsable thing, it will go :)

output as requested

```
drwxrwxr-x 2 grae users 4096 2010-10-06 17:21 /opt/alex
```

---

### Post by luvshines on 2010-10-13
Is alex a part of users group ??

```
groups alex
```

---

### Post by graeuk on 2010-10-13
> **luvshines said:**
> Is alex a part of users group ??

```
groups alex
```
Ah, it appears not!

```
alex : alex adm dialout fax cdrom floppy tape dip video plugdev fuse
```

how do I add him to that then??  This is all really helpful, slowly learning my way around linux again, haven't used it for ages and even then didn't do much!

thanks!

---

### Post by luvshines on 2010-10-13
> **graeuk said:**
> Ah, it appears not!

```
alex : alex adm dialout fax cdrom floppy tape dip video plugdev fuse
```

how do I add him to that then??

thanks!

```
sudo usermod -a -G users alex
```

---

### Post by graeuk on 2010-10-13
> **luvshines said:**
> ```
sudo usermod -a -G users alex
```
the user alex can now edit the filename and open it but not edit/save it ...

---

### Post by luvshines on 2010-10-13
> **graeuk said:**
> the user alex can now edit the filename and open it but not edit/save it ...

I was expecting something would be still be wrong ;)

What if we add the group users to write-list for [share]:
```
write list = alex, Alex, @users
```

Change the line in smb.conf, restart the service and give it a try.
**PS: My fingers are crossed**

---

### Post by graeuk on 2010-10-13
> **luvshines said:**
> I was expecting something would be still be wrong ;)

What if we add the group users to write-list for [share]:
```
write list = alex, Alex, @users
```

Change the line in smb.conf, restart the service and give it a try.
**PS: My fingers are crossed**
nope :(

---

### Post by Morbius1 on 2010-10-13
We meet again, luvshines. :) How about this as an idea:

Your permissions on the target directory will allow anyone in the group "users" to add to or delete from that directory but has no affect on it's content:
> drwxrwxr-x 2 grae users 4096 2010-10-06 17:21 /opt/alexThis:
> sudo chown -R root:users /opt/alexWould have changed the group ownership to all the files to "users" but it's likely that all of the permissions are still set at 755. So you need to change permissions an all the content to 775:
```
sudo chmod -R 0775 /opt/alex
```Now to prevent this becoming an infinite loop of permissions changes you will need to modify your share definition to make all new files have 775 permissions and ownership group = "users"

> [alex]
comment = Ubuntu Share Alex
path = /opt/alex
write list = alex, Alex
[COLOR=Blue]create mask = 0775
force group = users[/COLOR][COLOR=Blue]
[/COLOR]

---

### Post by luvshines on 2010-10-13
@Morbius1

I am pleased that you stepped in, I am always lost with file permissions. And then I claim to be working on linux for past 2 yrs, :lolflag:, I am ashamed of my ignorance. But, what the heck, it helps me learn :D

I was just wondering that 'force group' will mask the user's actual primary group and the new files will be owned by force group, right.. But as by default 'writeable' is no, don't we need @users in 'write list' ?

Who will be the owner of the newly created files ?

---

### Post by graeuk on 2010-10-13
Hey,
It didn't help .... however ... I thought I should try creating a new file and then editing that and that worked fine .. still can't edit the old file though but that isn't a huge problem.

what I need to know really is where I went wrong ... are there steps I should be following ... maybe I got some wrong ... as I said I used linux user and developer mag tutorial which seemed ok ... 

thanks,

Graham :)

---

### Post by luvshines on 2010-10-13
What are the permissions for the file you are trying to modify ?

---

### Post by graeuk on 2010-10-13
> **luvshines said:**
> What are the permissions for the file you are trying to modify ?
here is the output 
```
grae@grae-ubuntu:~$ ls -ld /opt/alex/ooos.txt
-rwxrwxr-x 1 grae grae 12 2010-10-06 17:21 /opt/alex/ooos.txt
grae@grae-ubuntu:~$ ls -ld /opt/alex/hi.txt
-rwxrw-r-- 1 alex users 17 2010-10-13 19:33 /opt/alex/hi.txt
```

---

### Post by luvshines on 2010-10-13
> **graeuk said:**
> here is the output 
```
grae@grae-ubuntu:~$ ls -ld /opt/alex/ooos.txt
-rwxrwxr-x 1 grae grae 12 2010-10-06 17:21 /opt/alex/ooos.txt
grae@grae-ubuntu:~$ ls -ld /opt/alex/hi.txt
-rwxrw-r-- 1 alex users 17 2010-10-13 19:33 /opt/alex/hi.txt
```

I don't think you'll be able to write to ooos.txt since it is owned by grae:grae

For hi.txt, is this the new file you created ? Wonder why isn't it 775

In comment#16, Morbius1 asked to do 'sudo chmod -R 755 /opt/alex', did you do that ?

---

### Post by graeuk on 2010-10-13
> **luvshines said:**
> I don't think you'll be able to write to ooos.txt since it is owned by grae:grae

For hi.txt, is this the new file you created ? Wonder why isn't it 775

In comment#16, Morbius1 asked to do 'sudo chmod -R 755 /opt/alex', did you do that ?
I did: 'sudo chmod -R 775 /opt/alex'

---

### Post by luvshines on 2010-10-13
> **graeuk said:**
> I did: 'sudo chmod -R 775 /opt/alex'

Gud :) But hi.txt is 764 :confused:

From ooos.txt and hi.txt, which one are you trying to modify ??

oops will not work i guess, for hi.txt change it to 755 explicitly and then try again

---

### Post by graeuk on 2010-10-13
> **luvshines said:**
> Gud :) But hi.txt is 764 :confused:

From ooos.txt and hi.txt, which one are you trying to modify ??

oops will not work i guess, for hi.txt change it to 755 explicitly and then try again
hi.txt is fine it is the other one but I am guessing that is due to the fact the ownership is grae and not alex...I am not too worried about making it work as it was only a test file.

I just need to figure out how I set this up in the future :)

---

### Post by graeuk on 2010-10-13
Done it. I chown'd it to the users group both the main directory and the file and it works :) lovey jubly! I am going to try and set it up with a new account and a new folder to make sure I understand how it really works :)

thanks to you both for your help with this today! :)

Graham.

---

### Post by Morbius1 on 2010-10-13
>                                  Gud :smile: But hi.txt is 764 :confused:That's my fault.

"create mask" is for files - "directory mask" is for folders. I applied a directory mask value to the create mask parameter  - rookie mistake :oops:

The way this should be done is with a combination of "create mask" for files and directory mask for folders:
> [alex]
comment = Ubuntu Share Alex
path = /opt/alex
write list = alex, Alex
[COLOR=Blue]create mask = 664
directory mask = 775
force group = users[/COLOR]

---

