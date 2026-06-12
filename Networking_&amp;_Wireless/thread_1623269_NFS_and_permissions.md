---
title: "NFS and permissions"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by holocene on 2010-11-16
Greetings,

I've been playing around with NFS and have some questions:

As root, I created this directory structure:
/var/share/iso

and copied some files out there.

Then, I set up my exports file to share that as rw.

On the client, I set up this structure as root, and I am not sure here at work how I set permissions for the user:
/media/nfs_share

And the client could mount and read the share. 

The problem arose when the client tried to write to the share, which would return a permission denied type error. This is true even though the server exported it as rw.

What I discovered was that I had to set the server's /var/share/iso permissions to 777.

So, my questions are:
1. When a root owned directory of files needs to be exported rw, it seems the directory to  be shared permissions needs to be set rw to the users.  Is that right? 
2. On the client, do the root permissions on the /media/nfs_share need to be modified for the user, from the root settings?
3. Can I assume that root exporting a share is to be avoided if the same files can be shared with a non-root account? Probably so!
4. I have been reading the NFS HOWTO about security and portmapper. I don't understand why the /etc/hosts.deny with "portmap: ALL"
does not change the output of rpcinfo -p with or without the hosts.deny line.

Sorry if these are simple questions. 

Any info or tips appreciated.
Admin wannabe.

---

### Post by SeijiSensei on 2010-11-17
In /etc/exports on the server add "no_root_squash" to the options and restart NFS.  The line should read something like

```

/var/share/iso     192.168.1.0/24(rw,no_root_squash)

```

I use "async,insecure" in my options list as well.  "man exports" for details.

---

### Post by sedawk on 2010-11-17
Basically, for non-root users the ownership and permissions should
be what you really want them to be. No tricks there.
(But keep in mind that users and groups are represented by
 numbers=IDs internally. E.g. if the same user has a different ID
 on two machines you might get unexpected results ...)

There are special rules for root users. Normally if
server A shares a drive you do not want the root user
of server B to have full root access on that shared drive.
You have to enable that root access with special NFS parameters
when sharing and not with permissions on the file system.
(E.g. you want to share a drive with lots of software to be
 used by other computers but you do not trust the root user
 on these computers and you do not want them to delete your
 software (by accident)).

---

### Post by holocene on 2010-11-17
> **sedawk said:**
> Basically, for non-root users the ownership and permissions should
be what you really want them to be. No tricks there.
(But keep in mind that users and groups are represented by
 numbers=IDs internally. E.g. if the same user has a different ID
 on two machines you might get unexpected results ...)

There are special rules for root users. Normally if
server A shares a drive you do not want the root user
of server B to have full root access on that shared drive.
You have to enable that root access with special NFS parameters
when sharing and not with permissions on the file system.
(E.g. you want to share a drive with lots of software to be
 used by other computers but you do not trust the root user
 on these computers and you do not want them to delete your
 software (by accident)).

Very good. 

Sounds like you are saying that if a network user as Write access to a NFS shared directory on a server, that user better exist on the server with the same userid # ?? Sounds like a coordination effort. Is it common for users to have accounts on the server? I would say yes if /home is on the server. I guess if you are providing filespace on the server for users, they better have accounts there. True?

In my case, I setup a directory /var/share/ owned by root/ the subdir /var/share/iso that I made rw for all users. Is this sensible? I wanted users to be able to get to existing ISO's and to write them out to the server if new ones arise. 

I think that just experimenting to see what works will go a long way to building an understanding. However, I want to keep track of Best Practice also.

Thanks much
Steve.

---

