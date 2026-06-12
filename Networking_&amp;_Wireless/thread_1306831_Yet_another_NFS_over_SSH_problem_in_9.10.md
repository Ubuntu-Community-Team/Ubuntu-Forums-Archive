---
title: "Yet another NFS over SSH problem in 9.10"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by simonbaev on 2009-10-30
Hi Everybody!

I'm running the following environment:
1. Ubuntu Server 9.10, having dynamically assigned DNS record, say server.dynalias.org (real name is a bit different).
2. Ubuntu Desktop 9.10, having similar setup and name client.dynalias.org

Even though both machines are sitting in the same local network, I'm trying to setup NFS over SSH connectivity. I do realise that tones of different HOWTOs and tutorials are dedicated to such a topic, BUT unfortunately none of them worked for 100% in my case. 

First of all I have created a shared directory in the Server:
```

sudo mkdir /share
sudo chmod 0777 /share

```

I have also created similar directory on the Client side:
```

sudo mkdir /share
sudo chmod 0777 /share

```

It is assumed that both Server and Client have an account "alien" and both of them have associated pair of RSA keys for easy SSH communication. In particular, both machines have the following files:
```

/home/alien/.ssh/alien.pub
/home/alien/.ssh/alien
/home/alien/.ssh/authorized_keys

```
which makes possible running 
```

ssh -i ~/.ssh/alien server.dynalias.org

```
from the Client, and 
```

ssh -i ~/.ssh/alien client.dynalias.org

```
from the Server.

My next step was to install NFS server pakages (portmap nfs-kernel-server) on the Server side, and NFS client packages (portmap nfs-common) on the Client side. In particular
Client:
```

sudo apt-get install portmap nfs-common

```
Server:
```

sudo apt-get install portmap nfs-kernel-server

```

Then I have edited **/etc/exports** on the Server side to include the share:
```

/share 168.18.0.0/16(rw,sync,no_subtree_check)

```
where 168.18.0.0 is the network where both Client and Server are working. The following made the Server's share visible to the Client:
```

sudo exportfs -ra
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-kernel-server restart

```

Then, I wanted to set **mountd** to be bound to a certain port on the Server side as well as **nlockmgr**. So I did the following on the Server machine:
1. Edited **/etc/default/nfs-kernel-server** to include
```

RPCNFSDCOUNT=8 RPCMOUNTDOPTS='-p 2233'

```
2. Edited **/etc/modprobe.d/options.conf** to include
```

options lockd nlm_udpport=2232 nlm_tcpport=2232

```
and added **lockd** to the end of [/etc/modules]
3. Restarted the Server.

The above steps resulted in the following output of the **rpcinfo -p** command on the Server:
```

   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100021    1   udp   2232  nlockmgr
    100021    3   udp   2232  nlockmgr
    100021    4   udp   2232  nlockmgr
    100021    1   tcp   2232  nlockmgr
    100021    3   tcp   2232  nlockmgr
    100021    4   tcp   2232  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp   2233  mountd
    100005    1   tcp   2233  mountd
    100005    2   udp   2233  mountd
    100005    2   tcp   2233  mountd
    100005    3   udp   2233  mountd
    100005    3   tcp   2233  mountd

```

The next step is to create SSH tunnels from Client to Server (commands to be run on Client):
```

ssh -i ~/.ssh/alien -L 62233:server.dynalias.org:2233 server.dynalias.org -f sleep 10m
ssh -i ~/.ssh/alien -L 62049:server.dynalias.org:2049 server.dynalias.org -f sleep 10m

```
where parameter **10m** at the end of each line specifies that both tunnels will be active for 10 minutes (for the purpuse of experiment).

Upon creating both tunnels for **mountd** and **nfs** we are ready to mount the share (command to be envoked on Client):
```

sudo mount localhost:/share /share -o rw,tcp,port=62049,mountport=62233

```

This command results in:
```

mount.nfs: access denied by server while mounting localhost:/share

```

**Thoughts...**
1. There could be some issue originating from the difference in treating *localhost* and *client.dynalias.org* on the Client side;
2. When I run the same process locally on the Server side and try to connect to its share via SSH tunnels it works... In particular, I did the following on the Server:
```

ssh -i ~/.ssh/alien -L 62233:server.dynalias.org:2233 server.dynalias.org -f sleep 10m
ssh -i ~/.ssh/alien -L 62049:server.dynalias.org:2049 server.dynalias.org -f sleep 10m

```
then, I created two local mount points in HOME directory
```

mkdir ~/M1
mkdir ~/M2

```
and tried to mount the share in different ways:
a) Using not forwarded ports:
```

sudo mount server.dynalias.org:/share ~/M1 -o rw,tcp,port=2049,mountport=2233

```
resulted in
```

mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.

```
so I changed the command to
```

sudo mount server.dynalias.org:/share ~/M1 -o rw,tcp,port=2049,mountport=2233,nolock

```
and **it worked!!!**
b) Using forwarded ports:
```

sudo mount server.dynalias.org:/share ~/M2 -o rw,tcp,port=62049,mountport=62233,nolock

```
resulted in no response (console went blocked)

**PLEASE HELP... I checked so many resources and nothing helped... **

---

### Post by Out_Cold on 2010-01-23
Hi, I may not have any answers, but I was wondering why you don't have any info on the status port. I too am looking to install iptable rules for nfs and am stuck as well.

---

