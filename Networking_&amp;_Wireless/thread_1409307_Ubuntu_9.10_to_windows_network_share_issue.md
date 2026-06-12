---
title: "Ubuntu 9.10 to windows network share issue"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by jdscott on 2010-02-17
I try and I try but I cannot get the folder I want on the Ubuntu machine to share out to my windows network. It gives me this error. net usershare' returned error 255: net usershare add: cannot convert name "everyone" to a SID.  Access Denied.  Here's my smb.conf file:

[global]
    security = ads
    realm = HTBZN.LOCAL
    password server = 192.168.168.2
    workgroup = HTBZN
    winbind separator = +
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    winbind enum users = yes
    winbind enum groups = yes
    template homedir = /home/%D/%U
    template shell = /bin/bash
    client use spnego = yes
    client ntlmv2 auth = yes
    encrypt passwords = yes
    winbind use default domain = yes
    restrict anonymous = 2
    usershare owner only = false
    usershare max shares = 100
    usershare owner only = false
    usershare path = /home/HTBZN

[HTBZN]
    comment = Main Share
    path = /home/HTBZN
    browseable = yes
    writable = yes       
    read only = no
    public = yes
    guest ok = yes

I've got winbind and everything working, but I just can't seem to be able to share anything, which is the whole dern point of this.

---

