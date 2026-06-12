---
title: "Nothing in home directory after nfs mounting"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by narnie on 2010-01-07
Hello,

I have an interesting problem I have had some trouble finding answers to with researching. The answer is probably so obvious that I should be able to see it. 

Here is my prob.

I am trying to mount a root directory onto the same system (just for testing purposes)

I am using nfs and have nfs-kernal-server nfs-common and portmap installed.

if I have this in my /etc/exports

```
/ 192.168.1.0/24(rw,no_root_squash,async)

```

then do
```
sudo /etc/init.d/nfs-kernal-server restart
sudo exportfs -a ; # for good measure
```


then mount to /mnt with

```
sudo mount 192.168.1.50:/ /mnt
```

Then there is a successful mount.

I can go into the /mnt/home directory, but it is empty.
everything else is present in /mnt such as /mnt/bin /mnt/etc and everything else that should be there, but the home dirs are absent.

If I have this in my /etc/exports file:

```
/home 192.168.1.0/24(rw,no_root_squash,async)
```

and mount it as:

```
sudo mount 192.168.1.50:/home /mnt/
ls /mnt
```

I get a nice beautiful listing of users' home directories.

Why the different behavior and how to make the home dirs show up when it is mounted as / vs /home?

With thanks,
Narnie

---

### Post by narnie on 2010-01-09
Well, I have the problem solved.

I failed to mention that /home is on another partition. Another person from another forum pointed this out as a possibility.

NFS won't export a mountpoint on another filesystem. That is why it shows up when mounted by itself.

The only workaround is just exporting them both.

Narnie

---

