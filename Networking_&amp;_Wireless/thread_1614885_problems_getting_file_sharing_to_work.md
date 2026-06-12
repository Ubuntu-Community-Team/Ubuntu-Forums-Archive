---
title: "problems getting file sharing to work"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by yogi1983 on 2010-11-06
hello  folks,
im having problems getting file sharing to work. here is what i have, upstairs a desktop with 10.04 on it. using ethernet for its connection to a wireless router. downstairs i have a laptop also running 10.04, it is connected wireless. i found out that i have to install apache2.2-bin and libapache2-mod-dnssd to enable file sharing.
after installing it on both machines. i can see the desktop from the laptop but when i try to open it i get an error message. "unable to mount location" and DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)   I'm stumped i spent alot of time looking around but cant find the answers. some people suggest installing samba, but i do not think that i need it. any help would be great
:P

---

### Post by yogi1983 on 2010-11-06
well i wound up installing samba on both machines. i got as far as being able to access my laptop from the desktop. but still no luck getting into the desktop. still says it cant mount the drive. i don't know where im going wrong. i'm pretty sure i have all the permissions set correctly. i rebooted both machines. just lost know

---

### Post by Morbius1 on 2010-11-06
> DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)The only time I've encountered that error was when the user tried to access a shared samba folder with authentication. There is a bug that concerns saving the username and password in the client. When you set up your "Personal File Sharing" share did you select something other than "Require Password: Never". Try setting it to never and see if it resolves the issue.

As for the samba issue we need to know what method of samba sharing you're using - there are two. The output of the following commands will give us that information:
```
net usershare info --long
``````
testparm -s
```

---

### Post by yogi1983 on 2010-11-06
yogi@yogi-laptop:~$ net usershare info --long
info_fn: file /var/lib/samba/usershares/public is not a well formed usershare file.
info_fn: Error was Path is not a directory.
yogi@yogi-laptop:~$ testparm -s
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
yogi@yogi-laptop:~$ 






this is at the laptop i will go do it on the big box too.
thanks for the help. i found a way to get to it using nautilus but its a pain

---

### Post by yogi1983 on 2010-11-06
yogi@yogi-desktop:~$ net usershare info --long
[public]
path=/home/yogi/Public
comment=
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/predators_2010_dvdrip_h264_aac-dobbs_(kingdom-release) is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[music]
path=/home/yogi/Public/music
comment=
usershare_acl=Everyone:F,
guest_ok=n

[my book]
path=/media/My Book
comment=
usershare_acl=Everyone:F,
guest_ok=n

[movies]
path=/home/yogi/Public/movies
comment=
usershare_acl=Everyone:F,
guest_ok=n

yogi@yogi-desktop:~$ testparm -s
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
yogi@yogi-desktop:~$ 



this is from the desktop. i also made sure i had never checked in the personal file sharing preferences 
thank you for your help:P
yogi

---

### Post by Morbius1 on 2010-11-06
Let's get something straight here.

Personal File Sharing sets up a baby apache server which announces it's share to the network using avahi. It can only share one folder /home/username/Public.

On the desktop you created a Samba share of the very same directory:
> [public]
path=/home/yogi/Public
comment=
usershare_acl=Everyone:F,
guest_ok=nTo be honest I have no idea what would happen if you try to share the same directory using Samba and "Personal File Sharing" at the same time. I would disable "Personal File Sharing".

You have "guest_ok=n" which is fine but that means you will have to create users with samba passwords. Is there a reason you do not want to  allow guest access? In the beginning you might want to allow guest access just to make sure everything works.

Your music and movies shares are all subdirectories of the public share and are configured similarly. There's really no point in doing that since everyone will be able to go through the public share.

On the laptop you have no samba shares. It looks like you tried to create one:
> info_fn: file /var/lib/samba/usershares/public is not a well formed usershare file.
info_fn: Error was Path is not a directory.But then you deleted the directory which would also disable "Personal File Sharing".

---

