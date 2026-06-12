---
title: "Samba"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by fukeu2man on 2010-04-01
Ok i must be not be doing something right when it come to the conf file for samba, i m trying to setup that my external hard drive is shared over my network, i m running xubuntu, i ve searched and i can't seem to find how to configure samba in xubuntu or terminal, help would be appreciated.

---

### Post by johnson.d on 2010-04-01
You can install Samba in Xubuntu using the following command:

```
$ sudo apt-get install samba
```

Now you need to edit the file /etc/samba/smb.conf and append the following lines: 

```
[<share-name>]
path = /<mount point of the external drive>
browseable = yes
read only = no
guest ok = yes
```

Now save the file and restart the Samba service using the following command:

```
$ sudo /etc/init.d/samba restart
```

Now try accessing the share from another machine

---

### Post by swerdna on 2010-04-09
And if it's an external drive, it's 99% sure to have a windows format, fat32 or ntfs, so check that it's mounted drwxrwxrwx to allow guests to write to it over the network.

---

