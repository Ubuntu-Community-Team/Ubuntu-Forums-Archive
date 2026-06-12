---
title: "Lack of security with SAMBA and WD Live"
date: 2011-10-03
forum: Multimedia Software
---

### Post by hollywoodpete on 2011-10-03
I am a novice user and have a bizarre problem. I have 3 hard drives mounted on a file server Ubuntu 11.04. I want to share 2 out of the 3 with everyone on my home network. The third hard drive has movies that I wound prefer not having my children view so I set it up with a username and password in samba. Unfortunately the WD Live is still able to access these movies without a password. Is there a better way to set this security?

---

### Post by Morbius1 on 2011-10-03
> The third hard drive has movies that I wound prefer not having my  children view so I set it up with a username and password in samba. We would have to know how you set these shares up so please post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```> Unfortunately the WD Live is still able to access these movies without a  password.
Remote client by any chance using Windows? It may only appear to be able to access the shares without a password depending on how you set up the passwords for those remote clients.

---

### Post by hollywoodpete on 2011-10-03
```
nighthawk@PowerEdge:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Movies plus]"
Processing section "[TV Shows and Music]"
Processing section "[Adult]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    guest account = nighthawk
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
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Movies plus]
    path = /media/Movies plus
    read only = No

[TV Shows and Music]
    path = /media/TV Shows and Music
    read only = No

[Adult]
    path = /media/Adult
    valid users = nighthawk
    read only = No
nighthawk@PowerEdge:~$
```

---

### Post by hollywoodpete on 2011-10-03
```
nighthawk@PowerEdge:~$ net usershare info --long
[movies plus]
path=/media/Movies plus
comment=
usershare_acl=Everyone:F,
guest_ok=y

[adult]
path=/media/Adult
comment=
usershare_acl=Everyone:R,S-1-5-21-4038646543-1807607175-3156384897-3000:F,
guest_ok=n

nighthawk@PowerEdge:~$
```

---

### Post by hollywoodpete on 2011-10-03
All Ubuntu computers but not sure if the WD Live is considered windows

---

### Post by Morbius1 on 2011-10-03
There's a couple of housekeeping issues that should be taken care of first:
>      security = SHAREUnless you did that because of some unique networking issue you are having I would set that back to the default:
```
security = user
```Then restart samba:
```
sudo service smbd restart
```You are also using 2 completely different methods of creating samba shares on the same folders and in one case they don't agree.

I would go back into Nautilus and remove the shares for:
> /media/Movies plus
/media/AdultSee how far that gets you while I try to figure out what a "WD Live" is ;)

---

### Post by hollywoodpete on 2011-10-03
Thanks for the help. Any changes from the default settings were probably something I did with a GUI. I struggle with command line editing. I will make the changes and repost. I had to go back to work so I am away from the computer now.

Sorry about the WD Live comment. It is a Western Digital network media player. I have 2 of them for my wife and kids to watch movies from the network. It makes it much easier for them. They don't have to go digging through our Massive DVD collection.

Thanks for you quick reply

---

### Post by hollywoodpete on 2011-10-03
I did use a program called Serviio to stream media. I think it may have made some of theses changes?

---

### Post by Morbius1 on 2011-10-03
Now there's 2 things I've never used before. I'm beginning to wonder if I'm the best man for the job. :)

---

### Post by hollywoodpete on 2011-10-03
> **Morbius1 said:**
> There's a couple of housekeeping issues that should be taken care of first:
Unless you did that because of some unique networking issue you are having I would set that back to the default:
```
security = user
```Then restart samba:
```
sudo service smbd restart
```You are also using 2 completely different methods of creating samba shares on the same folders and in one case they don't agree.

I would go back into Nautilus and remove the shares for:
See how far that gets you while I try to figure out what a "WD Live" is ;)

I need a little more basic help to make this change. I went to /ect/samba/smb.conf and tried to change the line without success
/etc/samba/smb.conf

---

### Post by Morbius1 on 2011-10-04
> I went to /ect/samba/smb.conf and tried to change the line without success
/etc/samba/smb.conf
Did you edit the file as root:
```
gksu gedit /etc/samba/smb.conf
```

The thing that's not clear to me though is your use of Serviio. You have 2 file servers in use and it's not clear to me which one is being accessed from your client.

---

### Post by hollywoodpete on 2011-10-04
> **Morbius1 said:**
> Did you edit the file as root:
```
gksu gedit /etc/samba/smb.conf
```The thing that's not clear to me though is your use of Serviio. You have 2 file servers in use and it's not clear to me which one is being accessed from your client.

I am not using Serviilo now. I was using it before when I thought that a UPnP server would be a better way to stream media so it could be accessed by a PS3 on the network. It worked well except for the inability to regulate which movies could be viewed.

I was hoping I could restrict access to some of the movies to adult viewers.

Currently there is only one file server in use

---

### Post by Morbius1 on 2011-10-04
And If Samba is the only file server in use then the share definition you already have ( assuming you made the corrections to the rest of the system I suggested) will do exactly what you want:
> [Adult]
    path = /media/Adult
    valid users = nighthawk
    read only = NoIt will restrict access to only nighthawk.

If this "WD Live" thing is allowing everyone to access the share then it's passing the "nighthawk" user name and samba password automatically.

It's easy enough to verify I guess. While you are logged into the server itself access the "Adult" share though Network in Nautilus. You should be prompted for credentials to access.

---

### Post by hollywoodpete on 2011-10-04
> **Morbius1 said:**
> And If Samba is the only file server in use then the share definition you already have ( assuming you made the corrections to the rest of the system I suggested) will do exactly what you want:
It will restrict access to only nighthawk.

If this "WD Live" thing is allowing everyone to access the share then it's passing the "nighthawk" user name and samba password automatically.

It's easy enough to verify I guess. While you are logged into the server itself access the "Adult" share though Network in Nautilus. You should be prompted for credentials to access.

Thanks. I am away from the terminal again but will try as soon as I get home. Thanks for your patience

---

