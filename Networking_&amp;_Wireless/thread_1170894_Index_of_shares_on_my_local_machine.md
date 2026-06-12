---
title: "Index of shares on my local machine?"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by Aped on 2009-05-26
Is there a command or something (a file? /etc/bla) where I can see just what my shares are on a local machine? I forget just what I mapped some shares to and wanna see what all is 'enabled'.

---

### Post by superprash2003 on 2009-05-27
yea type **smbtree**

---

### Post by loopduplicate on 2011-01-07
This will show you the actual location of all your shares:
```
#!/bin/sh
shares=$(ls -l /var/lib/samba/usershares | awk '{print "/var/lib/samba/usershares/"$8}')
for i in $shares
do
cat $i | grep path
done

```This will show you just the share names:
```
ls -l /var/lib/samba/usershares | awk '{print $8}'
```The next command displays all the shares on the network including shares from other connected computers:
```
smbtree
```This will unshare all of your shares at once if you need to lock your stuff down:
```
#!/bin/sh
shares=$(ls -l /var/lib/samba/usershares | awk '{print $8}')
for i in $shares
do
net usershare delete $i
done

```And just for fun, the following command will list some other cool stuff about your computer's configuration:
```
ifconfig
```

---

