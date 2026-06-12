---
title: "entry deleted from /etc/hosts - sudo stops working"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by yoyek on 2006-05-07
Hallo,

I accidentaly deleted my hostname from /etc/hosts and now i can't run sudo... it says - "sudo: unable to lookup myhome via gethostbyname()"

How can I correct it?... without sudo. Or maybe is there possibility to temporary set "myhome" host name to resolve properly, then run sudo and corrent /etc/hosts file?

need help... thanks in advance

PS: sorry for my english

---

### Post by jrib on 2006-05-07
reboot and choose recovery mode from the grub menu

Then you can use nano to edit the files.  Just do 'nano /etc/hosts' and 'nano /etc/hostname'

You should make sure your /etc/hosts has this on the first line:
```
127.0.0.1 localhost.localdomain localhost ubuntu
```
and that your /etc/hostname matches up with:
```
ubuntu
```

Change ubuntu to whatever hostname you want, then just reboot.

---

### Post by yoyek on 2006-05-07
Thank you very much jason

---

### Post by gbinal on 2006-05-14
[QUOTE=_jason]reboot and choose recovery mode from the grub menu

Then you can use nano to edit the files.  Just do 'nano /etc/hosts' and 'nano /etc/hostname'

You should make sure your /etc/hosts has this on the first line:
```
127.0.0.1 localhost.localdomain localhost ubuntu
```
and that your /etc/hostname matches up with:
```
ubuntu
```

Change ubuntu to whatever hostname you want, then just reboot.[/QUOTE]


This was exactly what I was looking for (I managed to make the same mistake), but when I follow your directions (after logging in the failsafe gnome or failsafe terminal mode) I am not allowed to save the changes to the file.  Any suggestions?  

Note: after reading a related post, I tried adding 'sudo' before the word nano.  

Peace and thank you so much for any help/ideas.  You're very good to be helping like this.  

Gray B.

---

### Post by nolongerlivecd on 2006-05-15
But in recovery mode, it should be root@somethingican'tremember

---

### Post by gbinal on 2006-05-19
Thanks, boss.  I realized my mistake of trying to correct the problem in the failsafe modes, not in the recovery mode found in the menu one can access just after logging in (there's a 2-3 second countdown to do so).  Thanks again and peace,

---

