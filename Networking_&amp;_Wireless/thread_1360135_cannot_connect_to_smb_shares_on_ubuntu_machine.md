---
title: "cannot connect to smb shares on ubuntu machine"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2009-12-20
I have an Ubuntu laptop running 9.10, and am sharing folders using SMB protocol.

I am able to connect to these shares from my Mac, but I am not able to connect to these shares using another laptop which has Ubuntu 8.04 installed on it.

Any ideas/experiences?

---

### Post by slakkie on 2009-12-20
I have hardy sharing smb with my debian/ubuntu laptop and our windows network. No problems at all. This is in my fstab:

```

\\hardy-box\homes                /mnt/hardy-box/home cifs    user,uid=wesleys,gid=root,credentials=/home/wesleys/.smb,iocharset=utf8,codepage=unicode,unicode,noauto 0  0
\\hardy-box\public-admin         /mnt/hardy-box/public cifs  user,uid=wesleys,gid=root,credentials=/home/wesleys/.smb,iocharset=utf8,codepage=unicode,unicode,noauto 0  0

# Login to domain server
\\work-server\data$                 /mnt/oa/work-server cifs user,uid=wesleys,gid=root,credentials=/home/wesleys/.smb-work,workgroup=mywork,iocharset=utf8,codepage=unicode,unicode,noauto 0  0

```

Credential files looks like this:
```

username=wesleys
password=supersecret

```

---

### Post by jamesisin on 2009-12-20
What sort of error are you receiving when you attempt to connect from the Ubu machine?

How are the permissions arranged on the share (both Samba and Unix)?

---

