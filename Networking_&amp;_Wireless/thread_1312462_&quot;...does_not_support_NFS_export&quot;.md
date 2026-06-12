---
title: "&quot;...does not support NFS export&quot;"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Steeperton on 2009-11-03
I have just upgraded to Karmic with a clean install. I'm trying to set up my NFS shares (to enable my laptop to see the "Public" folder on my desktop machine within my network. 

/etc/exports:
```
/media/tunes      	192.168.1.0/24(rw,no_subtree_check,async)
/home/qwerty/Public	192.168.1.0/24(rw,no_subtree_check,async)

```

however, when running ```
sudo /etc/init.d/nfs-kernel-server restart
``` I get the following error message:

*exportfs: Warning: /home/qwerty/Public does not support NFS export.*

The only difference I can see between "tunes" and "Public" is that tunes is ext3, whereas Public is on ext4.

What am I doing wrong?

---

### Post by Steeperton on 2009-11-25
Think it's time for a bump ;)

Anyone got any idea?

---

### Post by W3ird_N3rd on 2010-02-05
> **Steeperton said:**
> I have just upgraded to Karmic with a clean install. I'm trying to set up my NFS shares (to enable my laptop to see the "Public" folder on my desktop machine within my network. 

/etc/exports:
```
/media/tunes      	192.168.1.0/24(rw,no_subtree_check,async)
/home/qwerty/Public	192.168.1.0/24(rw,no_subtree_check,async)

```

however, when running ```
sudo /etc/init.d/nfs-kernel-server restart
``` I get the following error message:

*exportfs: Warning: /home/qwerty/Public does not support NFS export.*

The only difference I can see between "tunes" and "Public" is that tunes is ext3, whereas Public is on ext4.

What am I doing wrong?
[s]After a lengthy search I found the solution at [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/197499](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/197499).

On the server side, use double quotes. Like "/home/blaat/my game files" (mind the double quotes!). You'll get an error saying it does not support NFS export but you have to ignore that, it'll still work. On the client site, use \040. Like /home/blaat/my\040game\040files.[/s]

Sorry, I confused this with another problem. You don't have spaces, although they produce the same error. In my case I wasn't able to mount a directory with spaces that was in my home directory, while directories on an external drive in /media could be mounted without problems. In my case, both the external drive and home are ext4, so the FS doesn't seem to be the problem in this case.

---

### Post by gurnani on 2010-02-12
I'm running into the exact same problem...switched to ext4 and I'm getting this error. Any ideas?

---

### Post by lfitz on 2010-07-07
"...does not support NFS export" 

I have tried two different directories /exports and /export (notice the 's') 

in /etc/exports i have tried both with and without 'fsid=0'

here is /etc/exports

```
/exports/lfitz              satellite(rw,sync,no_subtree_check,nohide) # and (fsid=0)
/exports/ftproot         satellite(rw,sync,no_subtree_check,nohide)
/exports/webroot     satellite(rw,sync,no_subtree_check,nohide)

```

i have tried exporting only one dir with 'fsid=0' on/off.

i thought maybe /etc/hosts.allow was the issue, at first, but
```

nfsd: ALL

```
does nothing.

modprobe nfsd returns nothing, so i guess it successfully loads the module.

/etc/init.d/nfs-kernel-server is started / restarted successfully except for the no NFS support error.

any ideas of what I could do to fix this?  it works on debian and arch. ( these are no longer options as i have grown to prefer ubuntu :p, sambe is no longer an option either. well these are preferences, however, i would like to stay with nfs, if possible )

ubuntu 9.04 kernel 2.6.30.2 #11 on a sheevaplug

---

