---
title: "Samba setting permissions problem"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by Zymonick on 2011-06-28
Dear everybody,

I am experiencing strange difficulties with Samba. The permissions aren't set correctly, when creating a file or a folder on the mounted samba share.

My smb.conf looks as follows:
```
[shareOffice]
  path = /home/shareOffice
  writable = yes
  browseable = yes 	
  create mode = 0777
  directory mask = 0777
  force create mode = 0777
  force directory mode = 0777

```

Now if I create a regular file on the folder:
```
touch testFile; ls -l 
```
the permissions turn out to be:

```
-rwxr-xrwx 1 simon share 0 2011-06-28 21:42 testFile 
```

Does anyone have any idea, why the w bit on the group is missing? If I play around with the create mode / force create mode, I get every other possible permission output --- except the write access for group members.

Thank you very much for your help

---

### Post by e79 on 2011-06-28
Could you try, at the root of your share (which is ShareOffice I presume) the following :

```
chmod g+w /home/shareOffice
```and see if it helps ? That would tell your system that the group called 'share' with w/e users in it should be able to write into that directory.

---

### Post by Zymonick on 2011-06-28
Thanks for your suggestion. The group did already have write access on the folders above.

Perhaps I should mention, that ```
chmod 0777 testFile
``` does indeed lead to the correct permissions. So I think the problem must be somewhere around the settings of smb.conf.

Please let me know, if you got any other idea. This is slowly driving me crazy.

---

### Post by e79 on 2011-06-28
Maybe adding 'valid users = @group' (group being 'share' in your case) in your smb.conf would help ?

---

