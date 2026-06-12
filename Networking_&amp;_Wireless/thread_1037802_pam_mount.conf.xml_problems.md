---
title: "pam_mount.conf.xml problems"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by mo0on on 2009-01-12
Hello,

for version 7.10 of ubuntu I had a pam_mount.conf to automount windows shares from a server.
Now in Version 8.10 the format of the configuration file changed and the script, provided to convert the file, doesn't work. After a few tries and some hours there is no light at the and of the tunnel. So maybe here I can get some help.

first my old configuration
```
volume * cifs server.domain.de //kserver/linhome/& /home/SCHULE/&/winhome
uid=&,gid=users,dir_mode=0700,file_mode=0600,iocharset=utf8,codepage=cp850,ttl=10000 - -
```

and now my new one
```
<volume fstype="cifs" server="server.domain.de" path="//kserver/linhome/%(USER)" mountpoint="/home/SCHULE/%(USER)/winhome" 
options="iocharset=utf8,uid=%(USER),gid=users,dir_mode=0700,file_mode=0600" />
```


Both are simply added to the end of the configuration file and nothing else was changed.
Hope to get some help here

---

