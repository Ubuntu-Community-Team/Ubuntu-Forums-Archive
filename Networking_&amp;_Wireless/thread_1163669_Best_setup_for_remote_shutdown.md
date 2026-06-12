---
title: "Best setup for remote shutdown?"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by TheForkOfJustice on 2009-05-18
I wish to be able to reboot/update/shutdown my fileserver remotely from a desktop on the same network.  I don't need to have it running when I'm not using it.  Wastes electricity.

Also, I managed to get filesharing working but I'm not certain if it is via NFS or Samba since I did both at the same time.  How do I check to make sure which one it is?

---

### Post by dmizer on 2009-05-19
If you're just connected by GUI, you're probably sharing via samba. If you still have doubts, try disabling one and accessing the share.
```
sudo /etc/init.d/samba stop
```
If you can't access your shares after that command, then your fileserver is configured to share via samba.

To shutdown your server, install openssh server on the fileserver:
```
sudo apt-get install openssh-server
```
Then you can ssh into your file server with the following command:
ssh [noparse]fileserver-username@fileserver.ip.address[/noparse]
(if you use windows, you can accomplish the same with [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/))

Type this command to shutdown the server:
```
sudo halt
```

To start the server, you'll need to configure WOL (wake on lan). Howto here:
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

---

### Post by TheForkOfJustice on 2009-05-19
> **dmizer said:**
> If you're just connected by GUI, you're probably sharing via samba. If you still have doubts, try disabling one and accessing the share.
```
sudo /etc/init.d/samba stop
```
If you can't access your shares after that command, then your fileserver is configured to share via samba.

I found out something accidentally.  If you switch your Nautilus filepath view from buttons to text you'll see "smb:/media/whatever"

It was obviously Samba :)

> 
To shutdown your server, install openssh server on the fileserver:
```
sudo apt-get install openssh-server
```
Then you can ssh into your file server with the following command:
ssh [noparse]fileserver-username@fileserver.ip.address[/noparse]
(if you use windows, you can accomplish the same with [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/))

Type this command to shutdown the server:
```
sudo halt
```

To start the server, you'll need to configure WOL (wake on lan). Howto here:
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

I'll get right on that.  Thank you.

---

