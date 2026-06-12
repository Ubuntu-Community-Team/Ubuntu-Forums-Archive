---
title: "Unable to classic share with Samba between two Lucid machines"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by Vic79 on 2012-03-04
I am aware tons of threads have been written about this topic. I have read lots of them, but still stuck in the same point. No sharing at all between laptop and desktop; and inside laptop, I am even unable to mount laptop's shared directories. 

Using Nautilus, go to Places -> Network -> Windows Shares on.. -> Workgroup (Plats in my case). When I see workgroup, sometimes both machines are shown, sometimes just one... and not always the machine I am using, which keeps me surprised. Anyway, when I try to access something shown in the machine that appears as shared, then user and password are required; I type them and then a dialog is displayed that says: Cannot mount Windows Share. It doesn't matter what I choose regarding what to do with the password (remember or not). 

Info I guess can be interesting:

-Updated-to-day Lucid in all machines
-Static IP addressing. DNS resolver is far of my knowledge, so I left it as is stated in smb.conf by default: commented (;), with this order -> lmhosts host wins bcast
-I have chosen to use Classic share method instead of Nautilus Share or Personal File Sharing with apache. Got samba from repositories, and edited smb.conf by hand. I used smbpasswd to add my username. User exists already in both machines, with the same password. I really want security = user and not share; a bit maniac here.
-Both machines in the same Workgroup (Plats). Netbios name used in smb.conf just in case it was necessary, but it isn't shown with testparm -s. In fact, there's some uncommented info in smb.conf that testparm -s doesn't show.

-smb.conf looks like this:
```

root@LaFoss:/media/PENYA/LAN Share Area# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[LAN Share Area]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    workgroup = PLATS
    server string = laptop
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
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

[LAN Share Area]
    comment = LAN Share Area
    path = /media/PENYA/LAN\ Share\ Area/
    valid users = vic
    read only = No
    create mask = 0755
    guest ok = No

```-Smbtree command shows:
```

#smbtree
PLATS
    \\LAFOSS                laptop
        \\LAFOSS\print$             Printer Drivers
        \\LAFOSS\LAN Share Area     LAN Share Area
        \\LAFOSS\IPC$               IPC Service (laptop)

```-With usershare command:
```

#net usershare info --long
#

```I guess this confirms I am not sharing anything through nautilus-share, which is what I want as I read is not a good idea to use several ways of sharing at the same time with the same directories..

-Both machines have the same user, vic, and this user belongs to samba group. I don't know if here uppercase or lowercase matters, so I've used always lowercase. Same with workgroup and netbios name.

-This user has been entered to samba through
```

sudo smbpasswd -L -a vic
******

```-smbusers file exists, and has the following:
```

#cat /etc/samba/smbusers
vic = Vic, vic

```This is for a third machine running WinXP that my parents own... but still never tried if this function at all. 

-Permissions on shared directory looks like this:
```

drwxrwxrwx 1 root root    0 2011-06-19 13:06 LAN Share Area

```-Directory is owned by root; trying
```

root@LaFoss:/media/PENYA/LAN Share Area# chown vicent /media/PENYA/LAN\ Share\ Area

```has no effect. Anyway, I don't know if this matters at all, I've read owning shared directory helps...

-I have not tried to mount directory using fstab o something like that... first I should be able to manually mount my own shared directories, shouldn't I?

If more information is required, please tell me. Any help will be appreciated, I don't know what to do now.

Thanks in advance

---

### Post by Morbius1 on 2012-03-04
**Fix the path to your share from this:**
> [LAN Share Area]
    comment = LAN Share Area
[COLOR=Blue]    path = /media/PENYA/LAN\ Share\ Area/[/COLOR]
    valid users = vic
    read only = No
    create mask = 0755
    guest ok = NoTo this:
> [LAN Share Area]
    comment = LAN Share Area
[COLOR=Blue]    path = /media/PENYA/LAN Share Area[/COLOR]
    valid users = vic
    read only = No
    create mask = 0755
    guest ok = NoSmb.conf is probably the only place in all of Linux where you don't use any special escapes for spaces. I swear Samba does this sort of thing to drive us nuts.

*** Side note:***
> Netbios name used in smb.conf just in case it was necessary, but it  isn't shown with testparm -s. In fact, there's some uncommented info in  smb.conf that testparm -s doesn't show.
smb.conf is not the only thing in charge of samba on your system. smb.conf is used to add to and/or modify the default parameters of samba.

If you want to see the default settings that have not been modified by smb.conf run the following command:
```
testparm -sv /dev/null
```There you will see that your netbios name and things like "security = user" have already been set for you. You will also notice for example that "map to guest" is set to Never.

When you run "testparm -s" you simulate what samba itself does when it runs. It takes smb.conf and compares it to the defaults. It keeps the things that are different ( like your shares or "map to guest = Bad User" ), removes the things that are the same ( security = user & "netbios name = lafoss" ), and shows you how smb.conf itself is affecting how samba runs. Since the netbios name was already set to lafoss in the defaults, adding it to smb.conf had no affect.

[COLOR=Blue]**EDIT**[/COLOR]: If you have static ip addresses on all your machines you no longer need to browse to the shares. Just run:
```
 nautilus smb://192.168.0.100
```
[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the server*[/COLOR]
And then when the nautilus open up to that address bookmark it: Bookmarks > Add Bookmark. It will show up on the left panel of Nautilus sort of like a mapped drive does in Windows.

---

### Post by Vic79 on 2012-03-05
Thanks a lot for you fast response and help! I've read lots of posts from you here regarding Samba configuration and helping people have success with it.
Never imagined the way Samba dealed with white spaces.
Last night I gave up and went to bed; now at work, but this afternoon I will try what you suggest and post what happen, hope will be helpful for more people.

---

### Post by Vic79 on 2012-03-05
It works like a charm!!! Thanks, thanks a lot Morbius1. I was a bit  hopeless. Now I find myself a bit stupid asking such things, but never  imagined escapes, which I use a lot on terminal, would be here the cause  of the problem.

Definitely, these things are what makes great this world, people helping  others build their systems. This was my very first post, and it has  been a pleasure. It's a bit kind of addiction. 

Just to sum up in case someone finds and reads this thread trying to  network 2 or n computers with Ubuntu (and I guess any GNU/Linux machine... not only Lucid): 
- The smb.conf shown in the first  post works flawlessy just correcting what Morbius1 detected. This conf  gives you the samba classic sharing option, not relying in neither  Nautilus usershare nor apache's pfs. 
- It's not even necessary to use a GUI, just gedit, nano.. your smb.conf similar to mine, changing obviously folder path.
- Security is user and not guest, I guess it's a better option in terms of security. 
- Remember having an account of the user who is gonna share in every  machine (useradd), this user must be member of samba group, and you  shoud use smbpwd to enter its password for samba. In every machine.
- I employed static addressing, but I believe DHCP doesn't change anything... I am not sure here. There's *name resolve order = lmhosts host wins bcast*, but I left it commented.

Thanks again!!

---

