---
title: "Ubuntu 9.04 add bookmark to ReadyNAS NV+ share with password"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by 8daysaweek.co.uk on 2009-05-23
I have recently (re)installed Ubuntu 9.04 on my computer using Wubi.

I used to have a bookmark set up to connect to a WD MyBookWorld II which worked fine.  After reliability issues with the MyBookWorld I have moved all the data to a ReadyNAS NV+

I haven't done a lot of configuration on the ReadyNAS, other than set up 2 new shares and give 1 of them a password.  So I have 4 shares.  At the moment 3 of them are unsecured and the 4th is secured with a password.

If I type smb://servername/ into the location I can see these 4 shares listed.  I can connect to the 3 unsecured shares without any problems, so I assume this means smb is working fine.

However, if I try to connect to the 4th (secure) share I am prompted with: 

```
Password required for share <sharename> on <servername>
Username: <my ubuntu username filled in here>
Domain: WORKGROUP
Password:
o Forget password immediately
o Remember password until you logout
o Remember forever
                                                                [Cancel]  [Connect]
```

Obviously I haven't set up a username, just a share password, and on Windows I just enter \\computername\login (or just local windows username) and the share password then the drive is mapped.

But in Ubuntu, if I leave the above as is and just enter the share password I get:
```
Unable to mount location
Failed to mount Windows share
[OK]
```

I've tried to mount the drive from the command line, but no joy there so far, and I'd rather just have the bookmark work if possible.  Any help would be greatly appreciated.

---

### Post by joecrappa on 2009-07-29
I'm having the same issue, I solved it using an NFS mount with the IP, but the write speed is deplorable; about 2MB/sec. I would like to get this working with CIFS or another, faster method if possible. 

Please let me know if you come up with an answer.

---

