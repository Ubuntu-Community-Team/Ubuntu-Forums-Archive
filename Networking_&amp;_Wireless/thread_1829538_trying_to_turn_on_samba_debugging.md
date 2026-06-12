---
title: "trying to turn on samba debugging"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2011-08-20
im having problems with 1 mount from several shared, AFAIK identically from windows Vista Home
> root@server2:~# mount.cifs -v     //gaia/thunderbirdMail   /mnt/gaia -o user=guest,password='',domain=WORKGROUP, debug=8
mount.cifs kernel mount options: ip=192.168.2.6,unc=\\gaia\thunderbirdMail,,ver=1,user=guest,domain=WORKGROUP,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
root@server2:~# 

this is the tail  of /var/log/messages
> Aug 20 12:41:13 server2 kernel: [1622963.902072] CIFS: Unknown mount option debug
Aug 20 12:41:28 server2 kernel: [1622978.782105] CIFS: Unknown mount option debug
Aug 20 12:41:44 server2 kernel: [1622994.646450] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
Aug 20 12:44:41 server2 kernel: [1623171.286869] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
root@server2:~# 
 
 im getting the same output with whatever the setting is for debug = 

how do i turn debugging on so i can see what the problem is ?

---

### Post by capscrew on 2011-08-20
> **pdc124 said:**
> im having problems with 1 mount from several shared, AFAIK identically from windows Vista Home

this is the tail  of /var/log/messages
 
 im getting the same output with whatever the setting is for debug = 

how do i turn debugging on so i can see what the problem is ?

From the man pages```
       [COLOR="Red"]--verbose[/COLOR]
           Print additional debugging information for the mount. Note that
           this parameter must be specified before the -o. For example:

           mount -t cifs //server/share /mnt [COLOR="Red"]--verbose[/COLOR] -o user=username

```

---

