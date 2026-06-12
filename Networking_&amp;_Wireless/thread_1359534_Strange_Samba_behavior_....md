---
title: "Strange Samba behavior ..."
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by cknight725 on 2009-12-19
Mythbuntu 9.10 connecting to Vista shares, UAC disabled.

I have my samba mounts (all basically like the one below) in /etc/fstab:

```
//192.168.1.9/country    /var/lib/mythtv/music/country        cifs    credentials=/root/.smbcredentials,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777  0 0
```

Upon restarting, the mounts will not connect with error:
```
[95459.089134] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[95459.089148]  CIFS VFS: Send error in SessSetup = -13
[95459.089163]  CIFS VFS: cifs_mount failed w/return code = -13

```

Once I do a "normal" mount of the exact same share, mount -a works just fine:
```
sudo mount -t cifs -o username=mythtv,password=BLABLAH //192.168.1.9/country /var/lib/mythtv/music/country

```

So the question is -- whats going on?  The Vista host machine is firing the permission denied no doubt, but WHY?  The Vista machine is a domain member, but the username and account is a local account -- perhaps a change to the username in the credentials file? (Office-Vista\mythtv)

---

### Post by cknight725 on 2010-01-03
Bump -- really?  Nobody has anything?

---

