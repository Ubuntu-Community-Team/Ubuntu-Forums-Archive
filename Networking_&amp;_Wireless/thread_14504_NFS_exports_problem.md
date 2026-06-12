---
title: "NFS exports problem"
date: 2005-02-07
forum: Networking &amp; Wireless
---

### Post by toganet on 2005-02-07
Well, I've searched the forums, read the HOWTO and the FAQ's, but am still having trouble getting NFS running on my warty system.  Whenver I try to start nfs with:
sudo /etc/init.d/nfs-kernel-server restart
I get the follwoing:
* Stopping NFS kernel daemon...                                         [ ok ]
 * Unexporting directories for NFS kernel daemon...                      [ ok ]
 * Not starting NFS kernel daemon: No exports.

Now, I have set up /etc/exports in the usual fashion, exportfs -r gives no errors or warnings.

portmapper is running, and hosts.allow looks like this:

portmap: 192.168.1.0/255.255.255.0 127.0.0.1
rpc.mountd: 192.168.1.0/255.255.255.0 127.0.0.1
lockd: 192.168.1.0/255.255.255.0 127.0.0.1
rquotad: 192.168.1.0/255.255.255.0 127.0.0.1
statd: 192.168.1.0/255.255.255.0 127.0.0.1 

Not sure what to check next.  Any ideas?  This is especially frustrating, as everything I check seems ok, and the only error I get tells me something that is demonstrably not the case.

Thanks  in advance!

---

### Post by toganet on 2005-02-08
Nevermind -- I blew away my /etc/exports, recreated it line-for-line, and now it starts.

So, on to the next problem...

---

