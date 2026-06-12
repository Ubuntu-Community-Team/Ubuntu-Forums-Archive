---
title: "Fairly sure this is a samba problem."
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Jay2001 on 2010-05-28
I have asked this over on Launchpad and have found bugs filed on the eclipse bug tracker but it seems to be going nowhere so I guess ill ask here.

I am using Eclipse for some development work and having saved a file, defocus the eclipse window (to test changes in a browser) when I refocus the eclipse window I get the following error...

The file 'path\to\my\file' has been changed on the file system.
Do you want to replace the editor contents with these changes?

I have searched and searched and this seems to be a CIFS/SAMBA problem. I even found one solution suggesting that changing his mounts from cifs to smbfs fixed his problem however that would appear not to be an option for me since using smbfs in the fstab causes cifs mounts. This problem would seem to occur in Bluefish as well as some other IDE's so it is not an Eclipse issue.

Any one any idea how I can make this go away?

---------- LINKS TO RELATED ----------
[Launchpad Question](https://answers.launchpad.net/ubuntu/+source/samba/+question/111480)
[Eclipse Bug](https://bugs.eclipse.org/bugs/show_bug.cgi?id=137011)
--------------------------------------

---

### Post by GreenDevil on 2010-06-18
I'm having the exact same issue, and not finding any resolutions either. It's getting really annoying.

---

### Post by GreenDevil on 2010-06-22
Ok, so after searching and searching I have found a solution which seems to be working for me. In my /etc/fstab I have added nounix and iocharset=utf8 to the line where my files are saved while working with Eclipse. The line now looks like this:

```
//<ip address>/<share> /media/<folder>   cifs  auto,username=<username>,password=<password>,nounix,iocharset=utf8,nocase,noperm,file_mode=0777,dir_mode=0777,uid=1000,umask=000,user   0 0
```

So far so good, but I'll report back if results change

---

