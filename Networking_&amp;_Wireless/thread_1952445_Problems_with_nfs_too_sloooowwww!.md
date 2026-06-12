---
title: "Problems with nfs: too sloooowwww!"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by martinlillo on 2012-04-04
Hi! I've got this problem:
I work in a room with 20 pc's. All of them have Lubuntu 11.10 installed. I use Ldap for authenticating against a server, on wich every user's home is to find. So, clients pc's authenticate against the server, and then load their home from that server. Now, when I had Ubuntu 10.04, it was everything ok, but now, it's almost impossible to work with non local users. Nfs fails and the user must wait forever, and when finally the home is loaded, the work is extremly slow!! Local users don't have this problem. If I uninstall nfs and log in with local users, everything goes well.
It did not happen before I updated to 11.10. I noticed that on 10.04, there was a package named nfs-client, but now with 11.10, there is not such package. Now, there is just nfs-common. I don't know what to touch to optimize this. 
Problem is with nfs. Ldap is ok!
Could there be too much traffic on the net? how can I know?
If someone could help me, please, I would appreciate!!
Thanks in advance!!!

---

### Post by lisanels47 on 2012-04-18
Not sure what's going on, but I have about the same setup.  10 clients running NFS home directories.  They seem to run fine.
  
Clients run ubntu 11.10 with all the updates.  Server is Ubuntu server 11.10.

#mount
data:/data on /data type nfs (rw,-rw,hard,intr,sloppy,vers=4,addr=192.168.2.21,clientaddr=192.168.2.25)


# cat nfs-common
NEED_STATD=
STATDOPTS=
NEED_IDMAPD=yes
NEED_GSSD=

---

### Post by SeijiSensei on 2012-04-18
Could it be a name resolution problem?  How is the NFS mount defined in /etc/fstab?  If it's "servername:/share" try using "ip.addr.of.server/share" and see if that helps.

I also bump up the clients' read/write buffers in fstab like this:

```
192.168.100.100:/home   /media/shared    nfs    defaults,rsize=32768,wsize=32768 0 0
```

Adding "async" to the list of options in the server's /etc/exports can also *substantially* improve performance.  It opens up a small  possibility of data loss, but that's pretty unlikely in practice using a server with a good UPS.

---

