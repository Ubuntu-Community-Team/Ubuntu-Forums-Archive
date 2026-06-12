---
title: "Samba shares for guests"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by Ellhound on 2009-10-17
Let me just start off by saying I'm new to Ubuntu.
I'm trying to set up my server on Ubuntu 9.04, and I've run into a problem with Samba. 
What I'm trying to do is create several shares, which can be accessed RO by anyone, and one RW for anyone. So without any type of security.
I read some howto's on editing smb.conf, and I added the one I'm currently using below.
Currently when I try to access the shares from my main computer using the same login details as the ones I use on the server everything works fine. But when I try to access them from another computer, I get a security popup asking for a username and password. 

I cant seem to figure out what I did wrong, and its probably something stupid. I hope one of you will be able to help me out:P

```

[global]
    ; General server settings
    netbios name = server
    server string =
    workgroup = ABC
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
;   security = user
    null passwords = true
;   username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes


[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/


[blackhole]
path= /mnt/blackhole
browseable = yes
read only = no
guest ok = yes

[downloads]
path= /mnt/downloads
browseable = yes
read only = yes
guest ok = yes

[films 1]
path= /mnt/films1
browseable = yes
read only = yes
guest ok = yes

[films 2]
path= /mnt/films2
browseable = yes
read only = yes
guest ok = yes

[films 3]
path= /mnt/films3
browseable = yes
read only = yes
guest ok = yes

[films 4]
path= /mnt/films4
browseable = yes
read only = yes
guest ok = yes

[series]
path= /mnt/series
browseable = yes
read only = yes
guest ok = yes

```

---

### Post by dmizer on 2009-10-18
Try removing this stanza:
```
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/
```
Restart your samba server, and see if it works then.

---

### Post by Ellhound on 2009-10-18
I tried it, no luck.
Also, I probably should have said this on the first post but I do want access to /home aswell

---

### Post by dmizer on 2009-10-18
> **Ellhound said:**
> I tried it, no luck.
Also, I probably should have said this on the first post but I do want access to /home aswell

Yes, but accessing "home" is a secondary problem. Let's sort the main part of your problem and then add the nicer things.

Try this:
```

#======================= Global Settings =======================

[global]
   workgroup = ABC
   netbios name = server
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   name resolve order = lmhosts host wins bcast

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

   security = share
   encrypt passwords = true  
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Printing ##########

   printing = cups
   printcap name = cups

############ Misc ############

   usershare allow guests = yes

#======================= Share Definitions =======================

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[blackhole]
path= /mnt/blackhole
browseable = yes
read only = no
guest ok = yes

[downloads]
path= /mnt/downloads
browseable = yes
read only = yes
guest ok = yes

[films 1]
path= /mnt/films1
browseable = yes
read only = yes
guest ok = yes

[films 2]
path= /mnt/films2
browseable = yes
read only = yes
guest ok = yes

[films 3]
path= /mnt/films3
browseable = yes
read only = yes
guest ok = yes

[films 4]
path= /mnt/films4
browseable = yes
read only = yes
guest ok = yes

[series]
path= /mnt/series
browseable = yes
read only = yes
guest ok = yes
```

---

### Post by Ellhound on 2009-10-18
Thanks for the help.

I can now access the shares, but they are all read-only.

edit: the read only problem was caused by forgetting to chmod the dir :x fixed.

---

### Post by dmizer on 2009-10-18
> **Ellhound said:**
> Thanks for the help.

I can now access the shares, but they are all read-only.

edit: the read only problem was caused by forgetting to chmod the dir :x fixed.

Good.

Now, instead of sharing your entire home directory (which is dangerous and extremely inadvisable), just share a single folder from within your home directory. Your current smb.conf file makes this extremely easy. All you have to do is right click on a folder you'd like to share, select "sharing options", make sure at least the first two check boxes are marked. Only mark the third checkbox if you want everyone to be able to access the folder.

Now, you should be able to see the share inside your home directory as well.

---

