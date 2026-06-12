---
title: "Cannot share between 2 ubuntu machines"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by Rufus_T_Firefly on 2011-06-21
I've tried to find a thread regarding sharing between Ubuntu machines, but I only see threads on how to share with a windows network. My windows machines I have no problem with, it is between the ubuntu machines that I cannot figure out how to do it.

I run Ubuntu 11.04 64-bit. Samba is installed, Apache is installed so I can check the box in Personal File Sharing under System Settings. My windows machine can access the shares and Ubuntu can access their shares. My 3 ubuntu machines will not browse each others shares.

It says "Failed to mount". I can see the folders, but not get into them. What is the problem?

I'm quite new to this (I've run Windows since 1.0).

Gent

---

### Post by Morbius1 on 2011-06-21
> My windows machine can access the shares and Ubuntu can access their  shares. My 3 ubuntu machines will not browse each others shares.I do not understand those 2 statements together. Ubuntu can access the shares - ubuntu cannot browse each others shares ?

Anyway, a "failed to mount" doesn't sound like a Samba issue it sounds like a Linux permissions issue so we need to see how things are set up:

Please post from one of the Ubuntu machines with shares the following commands:
```
smbtree
``````
net usershare info --long
``````
testparm -s
```

---

### Post by Rufus_T_Firefly on 2011-06-21
The first statement means that Ubuntu cannot browse another Ubuntu, but the same shares are accessible from a Windows machine. Between the Ubuntus it's impossible.

```

Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED

```

```

[public]
path=/home/bass/Public
comment=Shared folder
usershare_acl=Everyone:F,
guest_ok=y

[tv]
path=/media/EntertainMe/TV
comment=
usershare_acl=Everyone:F,
guest_ok=y

[storage]
path=/media/Storage/storage
comment=
usershare_acl=Everyone:F,
guest_ok=y

[movies]
path=/media/EntertainMe/Movies
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Public]"
NOTE: Service Public is flagged unavailable.
Processing section "[TV]"
NOTE: Service TV is flagged unavailable.
Processing section "[Movies]"
NOTE: Service Movies is flagged unavailable.
Processing section "[storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
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

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Public]
    comment = Public share
    path = /home/bass/Public
    read only = No
    guest ok = Yes
    available = No

[TV]
    path = /media/EntertainMe/TV
    read only = No
    guest ok = Yes
    available = No

[Movies]
    path = /media/EntertainMe/Movies
    read only = No
    guest ok = Yes
    available = No

[storage]
    path = /media/Storage/storage
    read only = No
    guest ok = Yes

```

Any clues?

---

### Post by Morbius1 on 2011-06-21
[1] Change your security mode to user:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Find the following line:
> security = shareChange it to this:
> security = [COLOR=Blue]**user**[/COLOR]Then add the following line to the [global] section:
```
force user = bass
```[COLOR=Blue]*I'm guessing here that "bass" is your login user name on that box. If not change to the correct name*[/COLOR]

[2] There are two completely different ways to create samba shares and you are using both at the same time on the same target folders. This is not a good idea. In addition the shares you have defined in smb.conf itself are tagged as "unavailable" so they will in fact be ... well ... unavailable.

Since all your shares are guest accessible I would recommend you remove the classic shares in smb.conf and stick with creating shares only in Nautilus. Just use whatever utility you used to create the classic shares and remove them. This will leave only the shares you created in Nautilus. 

[3] The last problem is all these references to shares in /media/... I have a feeling these are pointing to an ntfs partition ( although I have no reason to think that ). In step [1] above I had you add a "force user" to smb.conf which should get rid of the "failed to mount" error.

When you are all done making changes restart samba:
```
sudo service smbd restart
```

---

### Post by Rufus_T_Firefly on 2011-06-21
I think I've done all that you said I should do.

I edited the config file as you suggested.

Since I am a beginner I do not know what you mean with sharing in 2 ways, but I removed all shares from samba, removed them from Nautilus (which I guess is just right clicking on a folder in my Home folder and choose "sharing options") and also removed them from System Settings / Internet and Network / Shared Folders.

Then I restarted samba and also the PC altogether to be on the safe side.

I right clicked on my PUBLIC folder, chose to share and again restarted.

If this would be done right, I should be able to click on NETWORK and see my computer and then click it to browse. I can see: "bass's public files on bass-Dell-DXP051" but when I click it I get: "Unable to mount location - DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)".

Here's a new dump:

```
bass@bass-Dell-DXP051:~$ smbtree
Enter bass's password: 
bass@bass-Dell-DXP051:~$ 

```

```
[public]
path=/home/bass/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

```

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    force user = bass

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```

---

### Post by Morbius1 on 2011-06-21
Let's clear something up: **Personal File Sharing** is not Samba. It has nothing to do with Samba.

When you browse the network it shows up as something like this:
> "bass's public files on bass-Dell-DXP051"I can't really help you with this since I really don't think it works very well. More than likely you haven't got avahi-daemon running but that's just a guess. I'm trying to help you with the Samba part of this problem.
> If this would be done right, I should be able to click on NETWORK and see my computer and then click it to browse.Almost right. The path is NETWORK > Windows Network > ...
"bass's public files on bass-Dell-DXP051" is showing up under network instead of "Windows Network" because it's not Samba.

You do have one problem - your host name is too long.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section:
```
 netbios name = bass-DXP051
```[COLOR=Blue]*It doesn't have to be that exact name but it does have to be **15** characters or less in length.*[/COLOR]

Save smb.conf, exit gedit, and then restart both of these services:
```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by Rufus_T_Firefly on 2011-06-21
I cannot seem to get a fix on this, so I'll just reinstall the whole thing. I might have messed it up too much, since I don't really know what I'm doing. Now I can't even get Windows to access the shares like before.

I've tried everything.

But this time I won't mess with any other sharing but Samba.

It's quite confusing for a guy who's only had Windows crapping up his life before. But I'll get the hang of it.

---

### Post by Morbius1 on 2011-06-21
After you made the change to the netbios name did you run smbtree and did it show you your own shares?

---

### Post by Gahhruuba on 2011-06-21
I am currently having the same problem sharing files between 2 Ubuntu 10.04 Computers. If someone could please PM me and try to fix this problem that would be fantastic.

Found a solution... A simple easy solution..
Filezilla

---

