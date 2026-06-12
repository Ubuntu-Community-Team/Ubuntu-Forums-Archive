---
title: "Connecting Mac OS X to Ubuntu NFS share"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by Rebajas on 2012-09-24
Hiya, I have a Ubuntu server (11.10) with the following in exports:

```

/raid/media/data                192.168.0.0/24(rw,sync,root_squash)
/raid/development/data          192.168.0.0/24(rw,sync,root_squash)
/raid/stuff/data                192.168.0.0/24(rw,sync,root_squash)

```

And I have a Ubuntu desktop with this in fstab:

```

192.168.0.100:/raid/media/data                  /home/tony/Media        nfs     rw,hard                 0       0
192.168.0.100:/raid/development/data            /home/tony/Development  nfs     rw,hard                 0       0
192.168.0.100:/raid/stuff/data                  /home/tony/Stuff        nfs     rw,hard                 0       0

``` 

And all seems well enough - I can read, write and delete successfully.

How do I connect my Mac OS X to this with the similar read, write and delete functions?

I have been searching around for a while now and I seem to be no closer.


Thanks in advance,


Tony.

---

### Post by LewisTM on 2012-09-24
You should search the Mac forums for this. All I know is that MacOS has a GUI for connecting and mounting NFS shares.
Two things to keep in mind:

1) Add the 'insecure' option to your exports. Mac often tries to connect though a nonstandard NFS port and will fail if you don't add that switch.

2) Mac users usually don't have the same UID as Ubuntu users, not even in the same range. You could try to change that on the Mac side, for instance to UID 1000 which should match the primary Ubuntu user on your server, or to whichever owns the files. 
Another way would be to force all of your machines to connect as a single user (e.g. 1000), using this syntax:
> /raid/stuff/data   192.168.0.0/24(rw,sync,insecure,all_squash,anonuid=1000,anongid=1000)

Cheers!

---

### Post by Bushflyr on 2012-09-26
See [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=1895084"). It details all the steps pretty well. Be sure to read the whole thing, there are some errors in the initial bit.

---

