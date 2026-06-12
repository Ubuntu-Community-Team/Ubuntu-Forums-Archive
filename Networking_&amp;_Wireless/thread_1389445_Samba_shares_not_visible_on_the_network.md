---
title: "Samba shares not visible on the network"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by miceagol on 2010-01-24
I'm trying to share some folders over the network, but the shared folders are not visible on another computer. This is through double clicking my computer from the Network list in Nautilus. However, I can access the share by typing the full address (<computer name>/<share name>) in "File > Connect to Server...".

Since I can't type the address manually from my blu-ray drive, I need to get the shares to show on the network. What is wrong with my settings?

The share was configured by clicking "Sharing Options" on a folder in Nautilus.

---

### Post by miceagol on 2010-01-28
bump!

---

### Post by johnson.d on 2010-02-03
Since the share is not visible in the network and you are able to connect to the path directly by entering it, You can probably map a network drive to browse through the folder if running windows.

Procedure:

1) Goto my computer -> right click -> map network drive
2) Select drive letter 
3) Folder: \\<ip address>\<share name>
4) Check "Reconnect at logon"

If running Linux you can mount the partition in a local folder and browse through.

Procedure:
1) type the following command
$ mount //<ip address>/share /<mount point> -o user=<username>
2)Enter password

You can make it permanent by adding the following line '/etc/fstab' file
//<ip-address>/<share>  /<mount-point>  cifs   user=<username>,password=<password>  0 0

If you want the share to be visible directly under the network computers, you can share the folders through different methods such as editing the /etc/samba/smb.conf file on the server wherein you can set the folder's visibility.

Procedure:

1) Add the following lines to the file /etc/samba/smb.conf

[<share-name>]
     path = /<path>
     read only = no
     browseable = yes
     guest ok = yes

2) Restart the service using the following command

$ /etc/init.d/samba restart

---

