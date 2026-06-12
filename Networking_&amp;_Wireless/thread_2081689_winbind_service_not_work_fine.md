---
title: "winbind service not work fine"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by sadam20 on 2012-11-07
i setup samba at fedora, ubuntu, centos and worked fine, but when i installed winbind, all the commands works fine ( getent passwd, getent group , wbinfo -u , wbinfo -g, kinit administrator, klist ), but when i login from AD win2k8 to the shared files, it doesnt ask me for password as the first and i used the cmd to connect with any user, i start the connecting succefuly but without requiring password till i try to access my home directory linux user asks for password but doesnt accespt and require enter again and not works.
i also try to logging at the linux machine with AD user and works fine
Any help plz???
 

/etc/samba/smb.conf
[global]
        security = ads
        realm = LOCAL.SERVER
        workgroup = LOCAL
        winbind separator = /
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        winbind enum users = yes
        winbind enum groups = yes
        template homedir = /home/%D/%U
        template shell = /bin/bash

/etc/nsswitch.conf

passwd:         files winbind
group:            files winbind
shadow:         files

---

