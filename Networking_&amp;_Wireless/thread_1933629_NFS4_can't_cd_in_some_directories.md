---
title: "NFS4 can't cd in *some* directories"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by thenilly on 2012-02-29
Hi all,

Time to get another opinion. I have two 11.10 Ubuntu machines, one is the NFS server, the other is the client. I am using NFS4 (I checked!) because I don't want to manually force identical UID/GIU.

On the server, 172.27.76.44 I have a user and group 'maria' with ID 1000. On the client, I have a user and group 'maria' with ID 1001. I have idmapd running and NFS configured to use it.

I can mount the home directory /home/maria without a problem using ```

sudo mount -t nfs4 -o proto=tcp,port=2049 slinky.stanford.edu:/maria /home/maria

```
and ls -la shows the owner and group as 'maria'

Now, here is the weird part. If I try cd-ing into the directory .ssh, I get a "Permission Denied" error. The permissions on the server are 
```

drwx------  2 maria  maria    4096 2012-02-28 14:54 .ssh

```

If I change the permissions to 
```

drwx-----x  2 maria  maria    4096 2012-02-28 14:54 .ssh

``` 
and remount, then I can cd without a problem. 

My /etc/exports looks like this:
```
/export 172.27.76.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/maria 172.27.76.0/24(rw,nohide,insecure,no_subtree_check,async,no_root_squash)

```

What is going on?

---

