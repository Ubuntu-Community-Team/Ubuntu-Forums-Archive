---
title: "sshfs works local, but not with dyndns"
date: 2012-04-17
forum: Networking &amp; Wireless
---

### Post by wonderfullyrich on 2012-04-17
I recently moved to a new box and haven't been able to get the remote mount to work outside home.  

SSH works both inside and outside the router.  I can run ssh for [email]user@mydomain.homedns.org[/email] be prompted for my password and find a terminal.  However ever time I run sshfs I get:
```
SSHFS version 2.2
read: Connection reset by peer

```

I'm using this commandline (copy and pasted, changed only names not syntax, spaces, or punctuation)

```
sudo sshfs user@mydomain.homedns.org:/a/location/dir/ /media/mountpoint/ -o allow_other -o idmap=user -o uid=1000 -o gid=1000 -o sshfs_debug
```

I've already done the following:
* run sudo adduser <local user> fuse (for my username) on both machines
* verified i have a /media/mountpoint/ directory
* change permission on /media/mountpoint/ to 775 and group to 
* ssh-keygen -f "/home/user/.ssh/known_hosts" -R mydomain.homedns.org
* fully removed the known_hosts file and started a fresh
* tried sshfs in version one with the -1 command
* tried adding -o allow_root,uid=0
and all produce the same result.

The frustrating part is that it works locally within the network with this command:

```
sudo sshfs user@machinename.local:/a/location/dir/ /media/mountpoint/ -o allow_other -o idmap=user -o uid=1000 -o gid=1000 -o sshfs_debug
```


Anyone else have any ideas as to what causes a connection reset by peer?

Thanks,
Rich

---

### Post by wonderfullyrich on 2012-04-18
I solved it.  I added -o debug,sshfs_debug,loglevel=debug in order to get more verbose info to my sshfs command.  

I turned out to be the known_hosts issues, but for root.  In addition to changing your users known_hosts with 
```
ssh-keygen -f "/user/home/.ssh/known_hosts" -R mydomain.homedns.org  
```you also need to run 
```
ssh-keygen -f "/root/.ssh/known_hosts" -R mydomain.homedns.org
```

or just remove both known_host files.

Rich

---

