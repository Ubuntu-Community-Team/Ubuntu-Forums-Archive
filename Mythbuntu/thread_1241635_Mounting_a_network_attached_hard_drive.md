---
title: "Mounting a network attached hard drive"
date: 2009-08-16
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-08-16
I have a network attached hard drive which I would like to use to back up my Mythbuntu system.

I have got as far as creating a mount point for it and being able to mount it manually. I can do this with the following command, which works perfectly.

```
sudo mount //[ip address]/[share name] /[mount point]
```

I have attempted to make it connect permanently by adding the following line to my fstab file:

```
//[ip address]/[share name] /[mount point]	auto	defaults	0	0
```

but that doesn't work.

Does anyone know what I've done wrong? The external drive doesn't need any kind of authentication to allow connections.

Thanks
NM

---

### Post by benrb on 2009-08-16
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by NautiusMaximus on 2009-08-16
Thanks for the suggestion, but it doesn't help very much, as it seems to assume a standard Ubuntu installation, rather than Mythbuntu. It references various menu items that simply don't exist in Mythbuntu.

However, perhaps there is a useful principle: would it be better to use a script that runs at startup instead of using fstab?

If so, how do I make a script run at startup in Mythbuntu?

Thanks
NM

---

### Post by derrick1985 on 2009-08-16
Use this one.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

It worked fine for me and mythbuntu.

---

### Post by ahood on 2009-08-16
> **NautiusMaximus said:**
> I have a network attached hard drive which I would like to use to back up my Mythbuntu system.

I have got as far as creating a mount point for it and being able to mount it manually. I can do this with the following command, which works perfectly.

```
sudo mount //[ip address]/[share name] /[mount point]
```

I have attempted to make it connect permanently by adding the following line to my fstab file:

```
//[ip address]/[share name] /[mount point]	auto	defaults	0	0
```

but that doesn't work.

Does anyone know what I've done wrong? The external drive doesn't need any kind of authentication to allow connections.

Thanks
NM

So far, I have edited/used /etc/fstab to automagically mount a network drive. Maybe I can help (???)

Regarding the following fstab entry...

```
//[ip address]/[share name] /[mount point]	auto	defaults	0	0
```

1. defaults - According to the Ubuntu Help on [**[COLOR="Blue"]Fstab[/COLOR]**]("https://help.ubuntu.com/community/Fstab"), this option will allow only root access the shared drive. 

Try replacing defaults with parameters specific for the file system type of the network share.

Note: The specific options used depends on the file system type (see [**[COLOR="Blue"]Fstab[/COLOR]**]("https://help.ubuntu.com/community/Fstab").

2. auto - Try replacing auto with the file system (ext3, cifs, etc.) of the network share.

Note: If the file system type is a samba share, then I recommend cifs with an relatively recent version of Ubuntu (8.04 or more recent).

I hope this helps.

---

### Post by Bucky Ball on 2009-08-16
In fstab:

```
[IP of server]:/folder/on/server /media/local_mountpoint
```ie:

```
# Entry for network partition
192.168.0.111:/media/Myfiles/Music /media/MyfilesMusicMount
```for NFS:

```
192.168.0.111:/media/Myfiles/Music /media/MyfilesMusicMount  nfs users,rsize=8192,wsize=8192,timeo=14,intr

```You need to be a little more specific about how you are attempting to do this. Static IPs? Samba, NFS, FTP?? There are a lot of ways of going about it; some very involved and others more straight forward. :)


ps: It is different to mounting a local drive so look at it from a slightly different angle. ;-)

---

### Post by NautiusMaximus on 2009-08-16
> **Bucky Ball said:**
> 
You need to be a little more specific about how you are attempting to do this. Static IPs? Samba, NFS, FTP?? There are a lot of ways of going about it; some very involved and others more straight forward. :)



Actually, I have no idea whether it's Samba, NFS etc. I do know that my network storage has a static IP address, and that's how I'm attempting to identify it. 

If it helps, it's a Buffalo Linkstation. It's set up to allow file sharing, and if I try to do so manually with the "sudo mount" command, then it just works.

Does that help?

BTW, I noticed that your code has a colon, which mine doesn't have. Could that be the reason why it's not working?

---

### Post by Bucky Ball on 2009-08-16
Yep.

Those commands should work then. Just make sure you are going for a folder on a partition, not the whole drive. ie:

```
/media/partition/folder_on_server
```NOT just the share name. You need to identify where on the partition on the server (your network drive) the share is.

Quick and easy way is to open a window from 'Places', get to the 'media' folder, find your external drive, find the directory on it you want to share. In the location bar, you can have blocks or the actual address. Make it the actual address and just copy that and paste to fstab of the client (your machine). Just add the server address and mount point after that as in the first command I gave you and let us know.

---

