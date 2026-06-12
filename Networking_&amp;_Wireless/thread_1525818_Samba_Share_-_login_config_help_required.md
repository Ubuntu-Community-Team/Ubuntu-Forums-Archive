---
title: "Samba Share - login config help required"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by Stusy on 2010-07-07
I've never used a Samba share before, but it seem the easiest solution on my home network to replace my MaxtorNAS as I have a server sitting there always on.

Any way quick overview, I have a few Xbox's (running XBMC) linked around the house and depending on the location the have access to certain shares.

see below:-

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Share]"
Processing section "[Kids]"
Processing section "[Adults]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        server string = Lorax
        interfaces = eth0
        bind interfaces only = Yes
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

[Share]
        comment = Basic Share
        path = /mnt/share
        read only = No
        guest ok = Yes

[Kids]
        comment = Kids Share
        path = /mnt/kids
        read only = No
        guest ok = Yes

[Adults]
        comment = Adults Share
        path = /mnt/adults
        valid users = adults
        read only = No


{tried a few combinations, but the above is the latest inclination}

-----------------------------------------

[Share] is a normal share with pics and music etc
[Kids] is for all our kiddy films
[Adult] is for all the Adult material (and no its not full of porn - well not completely)

As you can see I just want to set a username/password for the [Adult] share. I've set a Linux user adults with a password and the login box comes up, but it never authenticates.

I can see that the system should be using the standard passwd file, but how does Samba use this?

Any pointers gladly appreciated.

Many thanks

---

### Post by Iowan on 2010-07-07
Did you create a Samba user/password "adults" as well as the Linux user (**smbpasswd)**?

You might be able to build a group named "adults", assign members, and make the group the valid user.

---

### Post by Stusy on 2010-07-08
> **Iowan said:**
> Did you create a Samba user/password "adults" as well as the Linux user (**smbpasswd)**?

You might be able to build a group named "adults", assign members, and make the group the valid user.

Yes done that....

I'm thinking it may be an issue with the permissions of the mount.

I have 4 drives mounting on boot up in fstab. I've mounted them within the /mnt folder with permissions of the relevant user.

I'm just thinking I should remount them within their own home folder.

Its off for now, I'll output the configurations and permissions when I get home.

---

### Post by Stusy on 2010-07-08
OK. I've been going round in circles for a while now.

So this is how far I've got:-

I've got 4 drives mounting in fstab so they mount on boot.

/dev/sda1 /mnt/share ntfs rw,user,auto,uid=share,gid=share  0 0
/dev/sdc1 /mnt/temp ntfs rw,user,auto,uid=share,gid=share  0 0
/dev/sdd1 /mnt/adults ntfs rw,user,auto,uid=adults,gid=adults  0 0
/dev/sde1 /mnt/kids ntfs rw,user,auto,uid=kids,gid=kids 0 0

As you can see above I've set the ownerships as they mount.

Just to check (mount -l)

/dev/sda1 on /mnt/share type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Share]
/dev/sdc1 on /mnt/temp type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Temp]
/dev/sdd1 on /mnt/adults type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Adult]
/dev/sde1 on /mnt/kids type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Kids]

and ls -l (on /mnt)

drwxrwxrwx 1 adults adults  4096 2010-07-07 08:56 adults
drwxrwxrwx 1 kids   kids    4096 2010-07-07 21:43 kids
drwxrwxrwx 1 share  share   4096 2010-07-08 11:13 share
drwxrwxrwx 1 share  share  12288 2010-07-07 16:13 temp

Have the following users:-

U:share
P:******
U:kids
P:******
U:adults
P:******

smbpasswd all of the users and used the same password.

Now I want to share these so that the following:-

Share - Adult - requires login to access
Share - Share & Temp requires login to access
Share - Kids - No login Required

Can I get some pointers as to where I may be going.

Kids Share is pretty easy.

[Kids]
   comment = Kids Share
   path = /mnt/kids
   browseable = yes
   writable = yes
   guest ok = yes
   available = yes

That pretty much opens it up to everybody and the Xbox's on the network can see if and stream.

**NOTE = Would you believe it. Its now working**. I will post this up along with my testparm

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Share]"
Processing section "[Adults]"
Processing section "[Kids]"
Processing section "[Temp]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        server string = Swaytech
        interfaces = eth0
        bind interfaces only = Yes
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

[Share]
        comment = Basic Share
        path = /mnt/share

[Adults]
        comment = Adults Share
        path = /mnt/adults

[Kids]
        comment = Kids Share
        path = /mnt/kids
        read only = No
        guest ok = Yes

[Temp]
        comment = Temp Share
        path = /mnt/temp
        read only = No
        guest ok = Yes

Temp is currently set so I don't require a login


Next thing is to get the shares to work with my Xbox 360.

---

