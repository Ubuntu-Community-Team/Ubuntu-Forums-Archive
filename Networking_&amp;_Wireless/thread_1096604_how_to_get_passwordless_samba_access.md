---
title: "how to get passwordless samba access ?"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2009-03-15
Hi all.

I'd like to be able to share files on a home network.

At the moment, when clients try to access my ubuntu 8.10 fileserver, a password is requested.
I'd like disable the password requirement.

This is my existing smb.conf:

```

[global]
    ; General server settings
    netbios name = faustina
    server string = 
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[shared_folder]
    path = /media/shared/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = USER
    force group = WORKGROUP
    available = yes

```

I also suspect that samba is not honouring this file.
In nautilus, when I right click on the folder decribed in the conf file, the option to share to guests is greyed out.
In the conf, guests are explicitly allowed.

Will I have to uninstall and reinstall samba?
How can I remove the password requirement ?
Is there an alternative to samba that is easier to configure and use ?

---

### Post by loell on 2009-03-19
i think there should be something like a

```
guest account = nobody
```

somewhere there.

[http://www.chipnick.com/2008/05/03/setting-up-samba/]("http://www.chipnick.com/2008/05/03/setting-up-samba/")

---

### Post by bobdobbs on 2009-03-19
> **loell said:**
> i think there should be something like a

```
guest account = nobody
```

somewhere there.

[http://www.chipnick.com/2008/05/03/setting-up-samba/]("http://www.chipnick.com/2008/05/03/setting-up-samba/")

Simply adding that line doesn't work.

I'm considering the possibility that on ubuntu the smb.conf is ignored.
I know it sounds odd, but I keep getting the same results: the share can be seen but no accessed, no matter what changes I make.

---

### Post by Demented ZA on 2009-07-20
I'm having this exact same problem.

Feels like smb.conf is not making any effect on the system. And I did restart both pc's. 

I'm trying to share a 500GB drive formatted in NTFS so that two windows pc's can do backups to it over the network. 

Both pc's can see the shares fine, but once I try to open it, asks me for username and password. I type in the username and password, but it keeps saying invalid access. 

The system was installed as Ubuntu 7.04 and upgraded through to 9.04. Shares I made previously and made accessable by the same user CAN still be accessed, but new shares are not. 

I'm guessing it has to do with access rights of the files/folders itself in which case samba will have no effect on it?? (I tried chmod and chown adding the user, still no effect) 

Not sure where to look for the logs, still new to Linux :oops:

---

### Post by bobdobbs on 2009-07-20
> **Demented ZA said:**
> I'm having this exact same problem.

Feels like smb.conf is not making any effect on the system. And I did restart both pc's. 

I'm trying to share a 500GB drive formatted in NTFS so that two windows pc's can do backups to it over the network. 

Both pc's can see the shares fine, but once I try to open it, asks me for username and password. I type in the username and password, but it keeps saying invalid access. 

The system was installed as Ubuntu 7.04 and upgraded through to 9.04. Shares I made previously and made accessable by the same user CAN still be accessed, but new shares are not. 

I'm guessing it has to do with access rights of the files/folders itself in which case samba will have no effect on it?? (I tried chmod and chown adding the user, still no effect) 

Not sure where to look for the logs, still new to Linux :oops:

I have had very limited success with samba.
I failed to find out how to enable passworldless sharing.

Eventually, somebody sent me a copy of a smb.conf file that allowed passwordless sharing. But after a while, it just stopped working.

I figure that there is some magic to samba that I just can't figure out how to work.

At the moment I'm sharing across my linux boxes with ssh, made convenient by the gnome panel's ability to bookmark ssh locations.

However, short of using something like filezilla, my windows boxes don't have access. (This is fine for myself. But my less tech-minded flatmates have no way of sharing files across the network)

Sorry if that sounds discouraging. But I gave up months ago trying to get samba to work.

---

