---
title: "can't log into samba"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by c-m on 2009-03-03
I setup samba a long time ago now (about a month or so).

It seems though that when I try to log into my main machine (the one with the samba server) It does not accept my password.

I have tried creating a new one but I get the following error:

```
carl@carl-desktop:~$ sudo smbpasswd -L -a carl
[sudo] password for carl: 
New SMB password:
Retype new SMB password:
carl@carl-desktop:~$ sudo smbpasswd -L -e your_username
Failed to find user your_username in passdb backend.

```

---

### Post by dfme on 2009-03-03
hi,
there's a nice graphical tool which may help you set up samba:
Samba Server Configuration Tool
here you can also setup users with usernames and access configs.
just don't forget to restart samba once you've done any changes with:
```
sudo /etc/init.d/samba restart
```

---

