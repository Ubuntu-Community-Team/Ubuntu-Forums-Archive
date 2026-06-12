---
title: "Access denied in Win7 to Samba server"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by koopman on 2013-05-28
I always hate to ask for help, but I've been at this for days and am at my witts end.  Running 12.04 LTS and Win7 pro.  I can browse to the Ubuntu box in Win, but when I try to access any files in the folders I get an access denied error.  Here is my testparm.  

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %K Samba Server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snwe\s*\spassword:* %n\n *retype\snew\spassword:* %n\n *password\supdated\ssuccesfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1024
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb
    guest ok = Yes

[public]
    path = /server
    force user = nobody
    force group = nogroup
    read only = No
    create mask = 0755


```

Permissions for the folder:

```
ls -al /server
total 44
drwxrwxrwx   9 nobody  nogroup  4096 May 11 15:29 .
drwxr-xr-x  26 root    root     4096 May 28 09:41 ..
drwxrwxr-x   6 koopman koopman  4096 May 28 07:40 Backups
drwxrwxr-x   2 koopman koopman  4096 May 11 14:05 Documents
drwxrwxr-x   2 koopman koopman  4096 May 11 14:16 Movies
drwxrwxr-x 242 koopman koopman 12288 May 11 15:27 Music
drwxrwxr-x  28 koopman koopman  4096 May 11 14:15 Pictures
drwxrwxr-x   2 koopman koopman  4096 May 11 14:04 Recorded TV
drwx------   5 koopman koopman  4096 May 11 14:02 .Trash-1000


```

It is a secure local network and I'm not conserened about user access, so I'd like everyone to sign in as guest with full access.  I've also tried setting up user accounts and samba users with no luck.  I have the desried folder shared with full permission in nautalis.  Any suggestions would be very very appreciated.  

Koop

---

### Post by ahallubuntu on 2013-05-28
~

---

### Post by prodigy_ on 2013-05-28
For compatibility with Win 7 you need to add to your smb.conf (in [global] section) something like:
```

ntlm auth = no
lanman auth = no
client ntlmv2 auth = yes
```

---

### Post by Morbius1 on 2013-05-28
Well, all of the subfolders in the directory you are sharing are read / write to koopman. 

Yet you are forcing all your samba clients to take on the identity of "nobody":
> [public]
    path = /server
**[COLOR=#0000cd]    force user = nobody[/COLOR]**
    force group = nogroup
    read only = No
    create mask = 0755


Try changing "force user" to koopman. Then restart samba:
```
sudo service smbd restart
```

---

### Post by koopman on 2013-05-28
> **prodigy_ said:**
> For compatibility with Win 7 you need to add to your smb.conf (in [global] section) something like:
```

ntlm auth = no
lanman auth = no
client ntlmv2 auth = yes
```

You're awesome.  What a life saver.  Works like a charm!

---

### Post by Morbius1 on 2013-05-29
> **koopman said:**
> You're awesome.  What a life saver.  Works like a charm!
I hope you don't mind but I have an unhealthy obsession about these things.

Two of the three additions are already in the defaults so adding them to smb.conf should have done nothing:
> morbius1@morbius:~$ testparm -sv /dev/null | grep auth
Load smb config files from /dev/null
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Loaded services file OK.
Server role: ROLE_STANDALONE
    auth methods = 
    **[COLOR=#0000cd]lanman auth = No[/COLOR]**
    ntlm auth = Yes
    **[COLOR=#0000cd]client NTLMv2 auth = Yes[/COLOR]**
    client lanman auth = No
    client plaintext auth = No
That leaves "ntlm auth = Yes". 

From the documentation:
> If this option, and lanman auth are both disabled, then only NTLMv2 logins will be            permited. Not all clients support NTLMv2, and most will require special configuration            to use it.
OK, that makes sense and changing it's value to No is the right thing to do. 

So my assignment for the foreseeable future is to find out why my 3 Samba servers all of which have ntlm auth set to Yes have no problems being accessed by Win7 clients. Unless someone has some insight into why it's required for one and not for the other.

---

