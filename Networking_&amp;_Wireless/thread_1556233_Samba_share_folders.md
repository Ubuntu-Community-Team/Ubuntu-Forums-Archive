---
title: "Samba share folders"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by Project_Pat on 2010-08-19
how do i have a public share folder for ANYONE to add files to? and how do i have a folder onlny one user can edit?  share settings: [Share]    comment = UbuntuServer's Share    browsable = yes    path = /srv/samba/share    guest ok = yes    read olny = no    create mask = 0775  the editable one [websiteEDIT]    comment = UbuntuServer's Website editable    browsable = yes    path = /var/www    guest ok = no    read olny = no    create mask = 0775

---

### Post by gordintoronto on 2010-08-19
I created a share by right-clicking on a folder name in Nautilus. I selected "share this folder" and "guest access" and I have used it (read, write, delete) from other computers, both Windows and Ubuntu, on the network.

All the computers have the same username and password, I don't know if that is relevant.

I don't know how to set up a single-user share.

---

### Post by Morbius1 on 2010-08-19
Let me clean up your post so that normal humans can read what you've already done:

> [Share]
comment = UbuntuServer's Share 
browsable = yes 
path = /srv/samba/share 
guest ok = yes 
[COLOR=Blue]read olny = no [/COLOR]
create mask = 0775

[websiteEDIT] 
comment = UbuntuServer's Website editable 
browsable = yes 
path = /var/www 
guest ok = no 
[COLOR=Blue] read olny = no [/COLOR]
create mask = 0775You need to fix the spelling of [COLOR=Blue]olny[/COLOR] - it's only.

Without knowing how the rest of your smb.conf looks it does appear that [Share] will allow guest access. If it doesn't it's likely that you don't have linux permissions set correctly. You would have had to do something like this to make linux permissions match samba authentication:
```
sudo chmod 0777 /srv/samba/share 
```As for [websiteEDIT] it's not going to do what you want:

first there's an error, this:
> [COLOR=Blue]read **olny** = no [/COLOR]Should be this:
> read only = yesThen you need to add a line allowing only one user to write to that share:
```
write list = morbius
```[COLOR=Blue][I]Changing morbius to whoever you want to grant write access to that share

[/I][COLOR=black]"write list" takes precedence over "read only = yes"[/COLOR][/COLOR]

---

### Post by Project_Pat on 2010-08-19
ok i fixed all the only >.< sorry lol and heres my new code and it still doesnt work... should i post my entire conf?

```
[websiteEDIT]
   comment = UbuntuServer's Website editable
   browsable = yes
   path = /var/www
   guest ok = no
   read only = no
   create mask = 0775
   write list = patrick

```

---

### Post by Morbius1 on 2010-08-19
> should i post my entire conf?You can, but the best way to do that is with this command. It will also report any error messages that might give you a hint to your problem:
```
testparm -s
```But before you do that let's look at that share. Did you create a user named "patrick" on the server and then give him a samba password:
```
sudo smbpasswd -a patrick
```
And when you say it doesn't work what exactly do you mean? Patrick can't get access or is there a specific error message you're getting.

---

### Post by Project_Pat on 2010-08-19
heres my testparm -s

```
login as: patrick
patrick@UbuntuServer's password:
Linux UbuntuServer 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose

  System information as of Thu Aug 19 13:54:21 PDT 2010

  System load:  0.0                Processes:           90
  Usage of /:   1.2% of 146.01GB   Users logged in:     0
  Memory usage: 27%                IP address for lo:   127.0.0.1
  Swap usage:   0%                 IP address for eth0: 192.168.5.151

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Thu Aug 19 11:44:05 2010 from hp-barnes.home
patrick@UbuntuServer:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[cdrom]"
Processing section "[Share]"
Processing section "[websiteEDIT]"
Processing section "[website]"
Processing section "[etc]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = BARNES
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

[cdrom]
        comment = Samba server's CD-ROM
        path = /cdrom
        guest ok = Yes
        locking = No

[Share]
        comment = UbuntuServer's Share
        path = /srv/samba/share
        read only = No
        create mask = 0775
        guest ok = Yes

[websiteEDIT]
        comment = UbuntuServer's Website editable
        path = /var/www
        write list = patrick
        read only = No
        create mask = 0775

[website]
        comment = UbuntuServer's Website
        path = /var/www
        create mask = 0755
        guest ok = Yes

[etc]
        comment = UbuntuServer's etc
        path = /etc
        admin users = patrick
        read only = No
        create mask = 0775


```

mmm like from windows i try to get it and it says "log in" so i put in patrick and password. i can get in, read but cant write. when i dont log in, the folders with the "guest ok" thing work properly

also if it means anything which i believe does ```
security = user
```

---

### Post by Morbius1 on 2010-08-19
It doesn't sound like a samba problem it sounds like a linux permissions problem. Samba's not denying you access, linux is.

"patrick" has to have permissions to write to /var/www

What are the permission on /var/www
```
ls -al /var/www
```

---

### Post by Project_Pat on 2010-08-19
```
patrick@UbuntuServer:~$ ls -al /var/www
total 12
drwxr-xr-x  2 root root 4096 2010-07-21 10:41 .
drwxr-xr-x 15 root root 4096 2010-07-21 10:39 ..
-rw-r--r--  1 root root  177 2010-07-21 10:41 index.html

```

do i have to do something with chsomething? i never find a spot that explains that stuff

---

### Post by Project_Pat on 2010-08-19
```

patrick@UbuntuServer:/var/www$ ls -al
total 12
drwxr-xr-x  2 patrick root 4096 2010-07-21 10:41 .
drwxr-xr-x 15 root    root 4096 2010-07-21 10:39 ..
-rw-r--r--  1 patrick root  177 2010-07-21 10:41 index.html
```

ok i can now move files... so yea it was a problem with linux but how do i do it for a group of people can edit instead of just ME ?

---

### Post by Project_Pat on 2010-08-20
alright i got it, just had to open permissions on the files and directories useing stuff liek chown, chgrp, chmod... thanks ^^

---

