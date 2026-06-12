---
title: "Access Windows shares from Lubuntu?"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by sikander3786 on 2010-10-17
How can I access Windows shares from Lubuntu? I can't find any thing like Network Locations or Connect to Server as it is in Gnome.

---

### Post by Morbius1 on 2010-10-17
Gigolo - that's not an accusation it's an application :) :

[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by msherman123 on 2010-10-17
you will need to install smbfs. 

A good walk through on smb is here: 
[http://tldp.org/HOWTO/SMB-HOWTO-8.html](http://tldp.org/HOWTO/SMB-HOWTO-8.html)

If you do not like running the command each time, you can add to your /etc/fstab file so they mount at startup.

---

### Post by sikander3786 on 2010-10-17
> **Morbius1 said:**
> Gigolo - that's not an accusation it's an application :) :

[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)
Thanks Morbius. That was exactly what I was looking for. Really appreciated.

In addition, can the shares be listed in web browsers say Firefox? The way you type smb://ipaddress for accessing samba shares on Windows, what will be the URL for Windows shares?

> If you do not like running the command each time, you can add to your /etc/fstab file so they mount at startup.

Actually it is a USB install of Lubuntu, aimed to run at different PCs and different networks. Where ever I am forced to use Windows, I boot from this Lubuntu USB and I am in Linux :-)

Mounting shares permanently in fstab will not work therefore. I need to see the network computers and shares in order to mount them.

Thanks for the input.

---

### Post by Morbius1 on 2010-10-17
> In addition, can the shares be listed in web browsers say Firefox? The  way you type smb://ipaddress for accessing samba shares on Windows, what  will be the URL for Windows shares?To be honest I never thought of doing that so I just tried it. 

You will get a list of the shares but you can only open those that have guest access enabled. Trying to access an authenticated share does nothing.

---

### Post by sikander3786 on 2010-10-17
> You will get a list of the shares

That is exactly what I am looking for.

Can you guess what would be the URL for Windows Shares?

---

### Post by Morbius1 on 2010-10-17
> **sikander3786 said:**
> Can you guess what would be the URL for Windows Shares?
Just what you said it would be. In firefox:
```
smb://192.168.0.100
```
If you mean the other way around - firefox from windows - it doesn't work.

You could go to "My Computer" in windows and type: \\192.168.0.101

You could also go to Start > Run > \\192.168.0.101

---

### Post by sikander3786 on 2010-10-18
Samba shares can be accessed from firefox from both Windows and Linux. No problem there. But to access Windows shares from firefox on Linux, I couldn't figure out the URL.

Is it possible to see those shares from command line? The way we mount those shares

```
sudo mount //192.168.0.100/Data ~/Data
```

Can we have a list of all the shares on //192.168.0.100?

---

### Post by mechanic on 2010-11-16
Mounting remote shares:
[http://www.mkssoftware.com/docs/man1/mount.1.asp](http://www.mkssoftware.com/docs/man1/mount.1.asp)
[http://bund.com.au/~foo/linux/smb.html](http://bund.com.au/~foo/linux/smb.html)

To list shares on a remote server, use 'smbclient -L <hostname>'
[EDIT] or 'smbtree' for network information [/EDIT]

---

### Post by Morbius1 on 2010-11-16
If you want to keep it in the gvfs / gigolo family.

To mount from the command line:
```
 gvfs-mount smb://192.168.0.100/Data
```That will produce a mount point at: /home/username/.gvfs/data on 192.168.0.100

To unmount from the command line:
```
 gvfs-mount -u smb://192.168.0.100/Data
```To get a list of shares from the command line:
```
gvfs-ls smb://192.168.0.100
```
OR
```
gvfs-tree smb://192.168.0.100
```

---

