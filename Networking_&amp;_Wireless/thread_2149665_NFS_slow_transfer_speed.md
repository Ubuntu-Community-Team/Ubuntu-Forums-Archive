---
title: "NFS slow transfer speed"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by cormu7 on 2013-05-29
Hello,

I setup a NFS system based on the following Set up tutorial --->  [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I'm using Ubuntu 10.04 LTS on both the client and server.

The file system is setup fine with server and client. I can see the folders and directories of the server on my client. I can access them too. The issue is that when copying files, on the client, from client directory to server directories/folder, it takes much longer than coping files locally.

For example, here is test I ran locally:

```
 time dd if=/dev/zero of=/test-client/test.dd bs=16k count=1638416384+0 records in
16384+0 records out
268435456 bytes (268 MB) copied, 0.173925 s, 1.5 GB/s


real    0m0.176s
user    0m0.000s
sys    0m0.180s
```

But when I try to run the same test and put a file on the server, I get this:

```
 time dd if=/dev/zero of=/test-server/test.dd bs=16k count=1638416384+0 records in
16384+0 records out
268435456 bytes (268 MB) copied, 23.1473 s, 11.6 MB/s


real    0m23.170s
user    0m0.000s
sys    0m0.220s
```

When trying to reach a server directory using a simple "ls" command, the client freezes and locks up at times. The transfer is extremely slow.



I'm not sure what is going here? I've searched online and haven't come across a solution.  

I've tried troubleshooting using iperf on the client, here are my results:

```


[on server] iperf -s

[on client] iperf -c server-name------------------------------------------------------------
Client connecting to server-name, TCP port XXXX
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local XXX.XXX.XX.XX port XXXXX connected with XXX.XXX.XX.XX port XXXX
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    102 MBytes  85.2 Mbits/sec



```

So, I would suspect I could have a larger transfer rate than the 11.6 MB/S using the test copying files to the server from the client.

I've read about bugs regarding slow nfs on ubuntu--->  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561210](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561210)
                                                                           [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1006446](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1006446)

Here is my setup for my /etc/exports file:

```
# /etc/exports: the access control list for filesystems which may be exported#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#


/export/test-server client_name(rw,nohide,insecure,no_subtree_check,async)
/export/test-server2 client_name(rw,nohide,insecure,no_subtree_check,async)



```

Here is the output from nfsstat -m:

```
nfsstat -m/test-server from server_name:/export/test-server
 Flags:    rw,relatime,vers=3,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,mountaddr=xxx.xxx.xx.xx,mountvers=3,mountproto=tcp,addr=xxx.xxx.xx.xx


/test-server2 from server_name:/export/test-server2
 Flags:    rw,relatime,vers=3,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,mountaddr=xxx.xxx.xx.xx,mountvers=3,mountproto=tcp,addr=xxx.xxx.xx.xx



```


I'm just at a lost right now, and would appreciate any input, advice or suggestions.

Thanks,

corm

---

