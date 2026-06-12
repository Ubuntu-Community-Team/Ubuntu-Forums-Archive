---
title: "Dynamic NFS Permissions"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Jimage on 2009-08-03
Is it possible to setup an NFS share that only overrides certain permissions instead of setting every file/directory to the same value?

For example, it would be nice if it only set the x flag to files that are actually set to executable on the host machine, but also override the read and write permissions to make sure the client can access and modify them.

But I get the impression NFS permissions aren't designed to work this way.

---

### Post by Jimage on 2009-08-03
Oh, wait... looks like it already does this fine. I must've been navigating a Samba share that was still mounted and forced to 0x777. Now I'm actually in the NFS mount permissions are correct. Sveet.

---

### Post by toupeiro on 2009-08-03
I still use NFSv3 primarily, so if you are using version 4 I am afraid I can't help you.  one way you could do it is use the ro,rw and root switches as default mount options and specify a list of machines those would/could apply to, and have user specific read and write set by the file permissions themselves.

so for example, if I were exporting /media/sata1 I sould say for my options:

sec=sys,rw=host1.domain.com:host2.domain.com,ro=host3.domain.com:@many_hosts,root=adminserver.domain.com

What this line would imply is that host1, and host 2, will have rw access to the nfs export, with individual file permissions to lock it down further.  host 3 will have read only, even if file permissions permit more for that particular user because they are mounting it from host3.  @Many_hosts would be an example of using netgroups if you were in an environment where you could use them, to specify multiple machines with a single name. and finally, the root account on adminserver will have root privledges over the exported share, but no other root account on any other server will.

---

### Post by Jimage on 2009-08-03
Nice. I'll keep that in mind when I experiment with some of the more advanced features down the track. For the moment full RW accessible to the local network is sufficient. Now I'm no longer reliant on Samba for Linux-to-Linux, that's the main thing.

It looks like another issue is copying from an NTFS partition, where everything is assumed to be 0x777. Must remember to use EXT for backup purposes next time.

---

