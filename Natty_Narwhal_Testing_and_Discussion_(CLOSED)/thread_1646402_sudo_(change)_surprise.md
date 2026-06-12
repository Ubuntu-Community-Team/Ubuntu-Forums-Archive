---
title: "sudo (change) surprise"
date: 2010-12-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by efflandt on 2010-12-15
Just a heads up that if you accept the maintainer's version of /etc/sudoers for a recent update, it removes **admin** group as a default sudoer from that file, leaving you unable to sudo anything if you are not a member of **sudo** group (which nobody is unless specifically added).

So you might want to add yourself to sudo group before doing updates.  Or if like me, you were unaware of that, you can boot a (recovery) kernel and edit /etc/group from a root shell.  It is a comma separated list of users in that group like:

```
sudo:x:27:efflandt,deffland
```

---

### Post by inportb on 2010-12-15
Yup, noticed this as well... promptly rebooted into a root shell and fixed it.
Another way to achieve the same effect is to simply run `adduser *username* sudo` as root ;)

---

### Post by mc4man on 2010-12-15
report on
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/690873](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/690873)

---

### Post by cariboo on 2010-12-15
There was just another update to sudo1.7.4p4-5ubuntu2, that fixes the problem

---

### Post by coffeecat on 2010-12-16
Having so many times in the past had the maintainer's version of grub configuration bork my multibooting systems, I went with 'N' for the sudoers file. Now that I am reading this, I am glad I did! :)

---

### Post by tokyobadger on 2010-12-16
If you have been hit with this and need more detailed guidance on how to recover (as opposed to reinstall), I suggest [looking at this guide](http://psychocats.net/ubuntu/fixsudo)

---

