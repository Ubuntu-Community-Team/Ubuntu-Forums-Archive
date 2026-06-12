---
title: "Trouble getting write permission over NFS"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by freakalad on 2009-06-07
Jaunty-64

[Followed]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html") [guides]("https://help.ubuntu.com/community/SettingUpNFSHowTo") for basic NFS configuration.
Can read data OK, but can't get write access.

Have the same UID & GID (apt-cacher-ng, 1220) ownerships set on both server & client for the directories I'm trying to write to. 
The directories associated with my default UID & GID (1000) seem to be OK. 

/media/vm.data/apt-cacher-ng$ `ls -al` results are identical on server & client locations
```

...
drwxrwsr-x  3 apt-cacher-ng apt-cacher-ng 4096 2008-11-24 14:07 archive.canonical.com
drwxrwsr-x  3 apt-cacher-ng apt-cacher-ng 4096 2009-02-23 16:27 archive.ubuntu.com
drwxrwsr-x  4 apt-cacher-ng apt-cacher-ng 4096 2008-12-11 12:13 packages.medibuntu.org
drwxrwsr-x  3 apt-cacher-ng apt-cacher-ng 4096 2008-11-24 14:07 security.ubuntu.com
...

```

server /etc/exports
```

/media/vm/vm.data	10.0.0.0/24(rw,async,no_subtree_check)

```

client /etc/fstab
```

10.0.0.100:/media/vm/vm.data  /media/vm.data  nfs  defaults  0  0

```

Am I missing something?

- Thanks

---

### Post by netztier on 2009-06-07
> **freakalad said:**
> 
client /etc/fstab
```

10.0.0.100:/media/vm/vm.data  /media/vm.data  nfs  defaults,[COLOR="Red"]**rw**[/COLOR]  0  0

```


In my client side fstab, I have an "rw" in the options - will that change anything?

regards

Marc

---

### Post by freakalad on 2009-06-07
I've tried that too. Initially I set my settings via webmin (makes these pesky little tasks a lot simpler & quicker to configure).
Will try again (thanks)

The settings provided was given to me by one of my mates that is pretty well-versed in the kung-fu of ubuntu.
It's the minimalist config to get things going; didn't want to muddy the issue with needless settings at this time.
Besides, I suspect the problem could be a permission-related issue on the server-end

I have write access to other resources on the sames mapped share (i.e. /media/vm.data/distros); just not in this "apt-cacher-ng" subdirectory, even though the UID & GUI values are the same on both the client & server for that particular resource.
I can probably resolve the issue quick & dirty by chmod'ing the files & subs to 777, but this is a very security-weak cop-out.

My next resort would be to implement NIS, but that seems like a lot of needless complication for a network consisting of less than 10 nodes.

---

### Post by netztier on 2009-06-08
> **freakalad said:**
> 
My next resort would be to implement NIS, but that seems like a lot of needless complication for a network consisting of less than 10 nodes.

NIS in that case might be what we call "using a cannon to shoot at sparrows". 

Another of the "obvious" questions: the process that is attempting to write to these dirs is actually running as user apt-cacher-ng, isn't it?


regards

Marc

---

### Post by freakalad on 2009-06-08
> **netztier said:**
> NIS in that case might be what we call "using a cannon to shoot at sparrows". 

Another of the "obvious" questions: the process that is attempting to write to these dirs is actually running as user apt-cacher-ng, isn't it?


correct & correct.
I'd like to avoid anything resembling directory services, like NIS, LDAP or even YP, as this would needlessly complicate things, and cause me more headaches down the road.

The apt-cacher-ng is a repository caching proxy, that I make extended use of in setting up my VM's, such as this very apt-cacher-ng that I'm trying to set up. virtio should give me pretty good NIC performance.
I'm planning on keeping all my important data (like the apt cache, MySQL data, web sites, mail, media, etc) outside of my VM's (as they could be pretty volatile) & make use of NFS to mount the resources as I need them.
Should centralize data for ease of backup.

---

