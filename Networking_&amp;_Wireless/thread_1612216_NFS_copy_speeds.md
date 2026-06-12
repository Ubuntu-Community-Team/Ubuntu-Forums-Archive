---
title: "NFS copy speeds"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by clievers on 2010-11-02
Hi.

I am working on syncing a bunch of files using rsync to a new fileserver. Up until now, I've just used rsync over ssh (rsync <options> myfolder user@host:/folder).
It works pretty good most of the time, getting basically 10 MB/s (from using the --progress flag).

However I thought I'd try something different, using NFS share. I set up the client/server according to various articles/guides I've found on google and the ubuntu forums, trying some variations as well.

My issue, is that it starts out with some fast speeds, like 17-20 MB/s, but then drops all the way down to 3 MB/s. Sometimes it will speed up and then slow down, etc. Ultimately, when rsync finishes the file, the average time reported is around 8MB/s, so slower then using SSH. Any ideas / suggestions as to why?

Thanks very much in advance.

Also, my server /etc/exports is:
```
/mounts/array	192.168.0.0/255.255.255.0(rw,sync,no_subtree_check)
```

And my client /etc/fstab is:
```
myhost:/mounts/array /mounts/myhost/array nfs rw,hard,timeo=14,rsize=8192,wsize=8192,intr 0 0
```

(I've tried changing the rsize/wsize values, the hard from soft, etc).

---

### Post by SeijiSensei on 2010-11-03
Change the server from "sync" to "async".  It makes a big difference in terms of performance, I've found.  The speed-up/slow-down behavior you see reflects the need to wait for the server to sync.  

Still I've found rsync's raw transfer performance pretty respectable. You do have the overhead of the TCP ACK packets the target must send back.  NFS, using UDP as the transport, just blasts the packets out and expects the other end to receive them.  That could give a slight performance nod to the NFS method, but I'll bet you won't see much difference between the methods in practice.

---

### Post by clievers on 2010-11-03
Well, that does start off quicker, well over 20 MB/s, but then it continually drops in speed still down to the 7MB/s, still finishing and averaging off around the 10 MB/s. Still slightly better using async then sync, but why this dramatic reduction in speed? Why wouldn't it stay fairly constant, as rsync over ssh does?

Thanks.

---

