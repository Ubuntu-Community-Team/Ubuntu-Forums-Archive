---
title: "Cannot execute scripts mounted from NFS v3"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by castor_fou on 2012-10-22
hi

it worked in 12.04.
It doesn't work anymore since my migration to 12.10 last week.

Here is the fstab line :
nas:/volume1/dropbox		/home/guillaume/NasDropbox		nfs	defaults,user,nolock,nfsvers=3,exec	0	0

and here is the result:

```
guillaume@htpc-arctic:~/NasDropbox/Dropbox/scripts/unison$ ./unison_photos_gentoo.sh
-bash: ./unison_photos_gentoo.sh: Permission non accordée

guillaume@htpc-arctic:~/NasDropbox/Dropbox/scripts/unison$ l unison_photos_gentoo.sh
-rwxrwxr-x 1 guillaume guillaume 71 May 11  2011 unison_photos_gentoo.sh
```



which in English is something like permission denied.
In 12.04 I added exec in the fstab line to make it happen.

---

### Post by dccarson on 2012-10-31
Do not use the 'user' option.  This will result in a 'noexec' setting even if you have specified the 'exec' option.  Have a look at the output of "mount" without arguments to see what settings were actually applied.

I'm not sure if there is a way to get both 'user' and 'exec' to be applied.

---

