---
title: "Problem mounting NFS v3 in Karmic"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by Mahesh78 on 2009-10-31
I have a file server (hostname 'ubuntu') running Ubuntu Server 8.04, from which I have exported user home directories and some other dirs with NFS. My workstation (hostname 'kontor') is running Ubuntu Desktop 9.04 AMD64, and I have setup automounting of the NFS exports from the server--including user home directories--using autofs/NFS v3 mounts. 

This has been working very well, until I upgraded 'kontor' to 9.10 yesterday. Autofs refuses to mount the NFS shares from the server, making it impossible to login with X (since home dirs are not being mounted). Here is what shows up in /var/log/syslog:

```

Oct 31 19:33:39 kontor automount[6291]: >> mount.nfs: mount to NFS server 'ubuntu:/exports/home/chrisha' failed: RPC Error: Success
Oct 31 19:33:39 kontor automount[6291]: mount(nfs): nfs: mount failure ubuntu:/exports/home/chrisha on /home/chrisha
Oct 31 19:33:39 kontor automount[6291]: failed to mount /home/chrisha

```

I have checked that the /etc/auto.* files are unaltered by the upgrade. Here is my auto.master file:

```

/store	/etc/auto.ubuntu.rosef.local
/home	/etc/auto.home

```

And the auto.home file:

```

chrisha		-nosuid,rw,hard,intr,rsize=16384,wsize=16384	ubuntu:/exports/home/chrisha

```

I have tried to mount my home dir manually at a different mount point:

```

sudo mkdir /root/chrisha
sudo mount ubuntu:/exports/home/chrisha /root/chrisha

```

but this only replicates the error message from /var/log/syslog:

```

mount.nfs: mount to NFS server 'ubuntu:/exports/home/chrisha' failed: RPC Error: Success

```

Googling the error message leads me to [this page]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524760"), indicating that the error message may be related to a problem with incorrect NFS protocol version. If I try to force NFS v2, the dir mounts:

```

sudo mount ubuntu:/exports/home/chrisha /root/chrisha -o nfsvers=2

```

I have a laptop running Ubuntu Desktop 9.04 i386, running the same automount setup as 'kontor' (except for the home dir, which is stored locally), and on this laptop the automounts are working normally.

The versions of nfs-common are as follows:

On the 8.04 server ('ubuntu'): 1.1.2
On the 9.04 laptop: 1.1.4
On the 9.10 workstation: 1.2.0

I guess the workstation had 1.1.4 before the upgrade. The problem in [URL="http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=524760"]Debian bug
#524760[/URL] is related to 1.1.5. 

Is it possible that the problem might be related to changes from nfs-common version 1.1.4 -> 1.1.5 ? Would it be possible to downgrade nfs-common in 9.10 to version 1.1.4 to see if that solves the problem?

Suggestions are highly welcome!

---

### Post by Sparken on 2009-11-02
I can no longer connect to my NFS server since my client machine was upgraded to Karmic as well. I wiped the machine and did a complete install of karmic from scratch (to fix the broken wifi) and still was unable to mount my nfs shares.

Same error: mount.nfs mount to nfs server 'xxx.xxx.xxx.xxx:/mnt/remote' failed: rpc error: success

Neither the client nor the server have a firewall running and the client's IP is correct. The server doesn't even log a connection from the client. 

If I do **rpcinfo -p *server.ip.address***
I see the server is running on the std ports both udp and tcp, which is obvious because my 9.04 clients can still connect. What I did notice is the NFS version on the server is 2.

I'm wondering if there is a compatibility issue as Mahesh78 alluded to. 
Anyone have any ideas?

---

### Post by Sparken on 2009-11-03
After fiddling with it some more, that was the problem. The fix was to add the nfs version option to the command line or fstab on the client side.

From command line: 
*sudo mount -t nfs xxx.xxx.xxx.xxx:/export/dir /mnt/remote -o nfsvers=2*

in fstab:
[I]
xxx.xxx.xxx.xxx:/export/dir   /mnt/remote    nfs     user,sync,nfsvers=2[/I]

---

### Post by Mahesh78 on 2009-11-03
> **Sparken said:**
> After fiddling with it some more, that was the problem. The fix was to add the nfs version option to the command line or fstab on the client side.

From command line: 
*sudo mount -t nfs xxx.xxx.xxx.xxx:/export/dir /mnt/remote -o nfsvers=2*


I'm aware that the 'nvsvers=2' option makes a connection possible. There are, however, several reasons for not using NFS v2, take a look here: [http://nfs.sourceforge.net/#section_a](http://nfs.sourceforge.net/#section_a)

For instance, there's a 2GB file limit, and also a limit on the max size of read/write operations, possibly degrading performance.

I'm currently working on switching to NFS v4, which seems to work in Ubuntu 9.10. I was assuming that you need a Kerberos server (or similar) in order to launch NFS v4 file sharing, but this is not the case. I'll report back when I have it up and running.

We should probably bug report the lack of NFSv3-connectivity in Ubuntu 9.10. Don't see why this shouldn't work, at least as longs as NFSv2 is working!

---

### Post by Mies on 2009-11-04
Since upgrading to Ubuntu 9.10 I'm getting the aforementioned error as well :

```
mount.nfs: mount to NFS server 'some-server-location' failed: RPC Error: Success
```

I'm a bit stumped as to what this is as after my first boot all seemed ok (actually got some faster upload speeds with my wireless network) and my NFS shares worked. Only since yesterday the NFS mounts started failing.

Note : I did a clean Ubuntu 9.10 install as well.

---

### Post by uflotest on 2009-11-04
Exactly the same problem:

I upgraded to 9.10 from 9.04. My nfs in 9.04 works great, but after the upgrade this is the error:

mount.nfs: mount to NFS server '192.168.0.1:/var/www' failed: RPC Error: Success

OK RESOLVED.
My server is version 2, and my client in ubuntu9.10 is version 3.
Used what [Sparken]("http://ubuntuforums.org/member.php?u=78362") sggested.

> in fstab:
[I]
xxx.xxx.xxx.xxx:/export/dir   /mnt/remote    nfs     user,sync,nfsvers=2[/I]

---

### Post by chiwi on 2009-11-04
Same problem here folks, I have a file server running karmic, and I can't connect anymore from OS X.

I can't run NFSv2 since I have larger than 2GB files in my file server which I access from the client.

I'm subscribing to this thread, I hope this gets fixed soon!

Thanks all.

---

### Post by Mahesh78 on 2009-11-04
> **uflotest said:**
> Exactly the same problem:

I upgraded to 9.10 from 9.04. My nfs in 9.04 works great, but after the upgrade this is the error:

mount.nfs: mount to NFS server '192.168.0.1:/var/www' failed: RPC Error: Success

OK RESOLVED.
My server is version 2, and my client in ubuntu9.10 is version 3.
Used what [Sparken]("http://ubuntuforums.org/member.php?u=78362") sggested.

I would not call using NFSv2 solving the problem; NFS version 2 has limitations compared to version 3. See post #4 in this thread.

Support for NFSv4 is *not* broken in Karmic, so if your servers supports NFSv4, try using that version. There are some good howtos around.

---

### Post by Mahesh78 on 2009-11-04
> **chiwi said:**
> Same problem here folks, I have a file server running karmic, and I can't connect anymore from OS X.

I can't run NFSv2 since I have larger than 2GB files in my file server which I access from the client.

I'm subscribing to this thread, I hope this gets fixed soon!

Thanks all.

We should probably file a bug report on this. Anyone knows how to do that?

---

### Post by chiwi on 2009-11-04
> **Mahesh78 said:**
> We should probably file a bug report on this. Anyone knows how to do that?

Please disregard my previous post. I've discovered that somehow the server's IP changed, that's why i couldn't connect from OS X anymore.
I used the new IP and voilà, worked.

Now I need to figure out why the IP has changed on it's own.

Thanks

---

### Post by Mies on 2009-11-05
I might have an external problem, well external to my Ubuntu 9.10 machine, causing my issue. I might be looking at an about to happen disk failure. I have to fix that first and then see if my NFS mount problem is solved.

---

### Post by guillermolisi on 2009-11-06
I've solved this NFSv3 issue changing to NFSv4 without Kerberos at the server side and making some changes in /etc/fstab for the NFS mount entries at the client side. I do not need Kerberos authentication because it is a home LAN with only one user at all (just me).

I followed [this tutorial]("https://help.ubuntu.com/community/NFSv4Howto"). It is not complete but just enough as starting point.

---

