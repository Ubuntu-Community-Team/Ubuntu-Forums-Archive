---
title: "need help: proftpd directory limits"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by LoveJoyDK on 2010-08-20
Hi all.
Could use a little help here.
 
 
```
 
<Global>
AllowRetrieveRestart on
AllowStoreRestart on
tcpNoDelay on
DefaultRoot ~
AllowOverwrite on
RootLogin off
UseFtpUsers off
<Limit SITE_CHMOD>
Deny all
</Limit>
</Global>
ServerType standalone
Port 21
DefaultServer on
Group proftpd
User proftpd
<Anonymous /share/public>
 User proftpd
 Group proftpd
 UserAlias anonymous proftpd
DirFakeGroup on ~
DirFakeUser on ~
 
  <Directory /share/public>
   Umask 022 022
AllowOverwrite off
#<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
#DenyAll 
#</Limit>
  </Directory>
  <Directory /share/public/download>
#   Umask 022 022
<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
DenyAll 
</Limit>
  </Directory>
  <Directory /share/public/upload>
Umask 022 022
AllowOverwrite on
 <Limit READ RMD DELE>
       DenyAll
     </Limit>
     <Limit STOR CWD MKD>
       AllowAll
     </Limit>
  </Directory>
</Anonymous>
MaxInstances 10

```
 
That is my conf file for proftpd.
 
My problem is that with that setup I can finaly put files and dirs in upload. But it would not work before I # out the limits on public.
 
But now it is also posible to upload to public. 
 
At the same time, I would like to prevent files from being deleted in upload. Not much fun in one anonymous uploading a file and the next deletes it. By mistake off cause. 
But they can all be deleted, so that is proberly also posible in public. But do not dare try.
I realy don't get why 
<Limit READ RMD DELE>
DenyAll
does not stop a user from deleting in upload.
 
So can someone help with those limit rules? Tried to google, but found very little helpfull.
 
Might be best to mention, that the share/public Dir. is also a samba / Ldap share on the LAN. I do have a suspision of the samba permissions might overrule the proftpd settings. Files uploaded seems to follow the samba settings of 755 rather than the proftpd setting of 022. which I have tried to fix with DirFakeMode 0022.
 
I use WinSCP as the FTP client.
 
Thanks in advance

---

### Post by LoveJoyDK on 2010-08-22
Did I place this in the wrong thread?
 
If so I am sorry, and if some kind person would let me know where it should had been. he/she would be welcome.

---

### Post by LoveJoyDK on 2010-08-25
Ehmm. This is kind of emparessing. But just hide and not tell, will let the lecture go to waste. 
 
So here is the lecture:
Alwas notice the difference between
/share/public/Upload
and
/share/public/upload
 
 
Sorry for wastings everybodies time.
Mark this solved, or better yet. Delete it.

---

