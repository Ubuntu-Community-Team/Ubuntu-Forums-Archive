---
title: "NFS and Firewall Issue"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by derklempner on 2010-02-15
My file/web server is configured and running properly.  I have no issues sharing directories via NFS until my firewall becomes part of the equation.  But it's not as simple as it sounds...

First off, I'm using **ufw** and know which ports to open; my **ufw** config is fine.  The **/etc/exports** file also has the correct configuration for the shared folders.  When another computer on the same network is booted up, the NFS shares will not connect as they are configured in **/etc/fstab**.  In order to enable the connection of the shares, the server must have the firewall disabled, then the client can mount the shares (via **mount -a**).  At this point, the firewall on the server can be re-enabled with no ill effects on any of the clients.

That's right: *_the shares will stay connected after the firewall is re-enabled, but will not connect if the server's firewall is enabled when the client PC boots_*.

How do I know it's a firewall issue?  The other PCs also each have NFS shares that properly connect on boot of any other PC.  So the server, the media PC, and the workstation each have NFS shares -- but only the server's firewall causes an issue when either of the other two PCs boot.

Any ideas?

---

### Post by suseendran.rengabashyam on 2010-02-15
Hi,

portmap, rpc.nfsd and rpc.mountd are required to run a NFS server. I hope that you must have configured your UFW for accepting incoming connections on rpc.nfsd(2049 tcp/udp) and portmap(111 tcp/udp).

By default rpc.mountd listens on multiple ports so you have to bind rpc.mountd to a single port and then you can configure your UFW to accept incoming connection on that particular port.

Open the file /etc/default/nfs-kernel-server and comment out the line

```
RPCMOUNTDOPTS=--manage-gids
```

and add the following line

```
RPCMOUNTDOPTS="-p 33333 -g"
```

The 33333 is just an example, use something that is available on your system and isn't already defined in your /etc/services file.

Restart the NFS daemon

sudo /etc/init.d/nfs-server-kernel restart

for the changes to take effect.

Now configure the UFW to accept incoming connections on port 33333 apart from port 2049 and port 111.

Let me know if this helps.

---

### Post by derklempner on 2010-02-15
> **suseendran.rengabashyam said:**
> Open the file /etc/default/nfs-kernel-server and comment out the line

```
RPCMOUNTDOPTS=--manage-gids
```

and add the following line

```
RPCMOUNTDOPTS="-p 33333 -g"
```

The 33333 is just an example, use something that is available on your system and isn't already defined in your /etc/services file.

Restart the NFS daemon

sudo /etc/init.d/nfs-server-kernel restart

for the changes to take effect.

Now configure the UFW to accept incoming connections on port 33333 apart from port 2049 and port 111.

Let me know if this helps.
I had already changed it in hopes it would solve the issue.  My **/etc/default/nfs-kernel-server** line read:

```
RPCMOUNTDOPTS="--p 4002"
```
**rpcinfo -p** verified **mountd** was thus configured:

```
100005    1   udp   4002  mountd
100005    1   tcp   4002  mountd
100005    2   udp   4002  mountd
100005    2   tcp   4002  mountd
100005    3   udp   4002  mountd
100005    3   tcp   4002  mountd
```
...and as I stated in my original post, **ufw** was already configured to allow access to all the necessary ports:

```
111                        ALLOW   192.0.0.0/24
2049                       ALLOW   192.0.0.0/24
4002                       ALLOW   192.0.0.0/24
```
So the **RPCMOUNTDOPTS=** options were different, but I changed it to what you suggested and then restarted nfs-kernel-server.  I didn't even have to reboot my workstation to see the effects of the changes, as Nautilus stopped responding immediately, and playback of music files located on the server also stopped and froze Rhythmbox.  Nautilus finally recovered after two or three minutes and was able to reopen (after killing the running processes), and I was also able to restart Rhythmbox.

But just to be safe, I decided to reboot the server first and see what happens.  When it completed the reboot, my workstation was locked out of the shared folders again until I disabled the firewall on the server.  I think I may have finally figured out what is causing the issue, though:

```
rpcinfo -p

program vers proto   port
100000    2   tcp    111  portmapper
100000    2   udp    111  portmapper
100024    1   udp   4000  status
100024    1   tcp   4000  status
100003    2   udp   2049  nfs
100003    3   udp   2049  nfs
100003    4   udp   2049  nfs
100021    1   udp  46175  nlockmgr
100021    3   udp  46175  nlockmgr
100021    4   udp  46175  nlockmgr
100021    1   tcp  38333  nlockmgr
100021    3   tcp  38333  nlockmgr
100021    4   tcp  38333  nlockmgr
100003    2   tcp   2049  nfs
100003    3   tcp   2049  nfs
100003    4   tcp   2049  nfs
100005    1   udp   4002  mountd
100005    1   tcp   4002  mountd
100005    2   udp   4002  mountd
100005    2   tcp   4002  mountd
100005    3   udp   4002  mountd
100005    3   tcp   4002  mountd
```
As you can see, the only random port being assigned is to **nlockmgr**.  Unfortunately, it was difficult and very time-consuming to find any solution to setting **nlockmgr** to a specific port.  All the information I found by Googling was distro-specific for anything except Ubuntu, until I found this Launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/28706](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/28706)

One post recommends rebooting after creating a **/etc/modprobe.d/options** file and adding the following (the port numbers are of my choosing):

```
options lockd nlm_udpport=4001 nlm_tcpport=4001
```
Doing so does set the **nlockmgr** port accordingly, so it works quite nicely in that regard:

```
rpcinfo -p
program vers proto   port
100000    2   tcp    111  portmapper
100000    2   udp    111  portmapper
100024    1   udp   4000  status
100024    1   tcp   4000  status
100021    1   udp   4001  nlockmgr
100021    3   udp   4001  nlockmgr
100021    4   udp   4001  nlockmgr
100021    1   tcp   4001  nlockmgr
100021    3   tcp   4001  nlockmgr
100021    4   tcp   4001  nlockmgr
100003    2   udp   2049  nfs
100003    3   udp   2049  nfs
100003    4   udp   2049  nfs
100003    2   tcp   2049  nfs
100003    3   tcp   2049  nfs
100003    4   tcp   2049  nfs
100005    1   udp   4002  mountd
100005    1   tcp   4002  mountd
100005    2   udp   4002  mountd
100005    2   tcp   4002  mountd
100005    3   udp   4002  mountd
100005    3   tcp   4002  mountd
```
And **ufw** now has all the appropriate open ports:

```
111                        ALLOW   192.0.0.0/24
2049                       ALLOW   192.0.0.0/24
4001                       ALLOW   192.0.0.0/24
4002                       ALLOW   192.0.0.0/24
4000                       ALLOW   192.0.0.0/24
```
So you think I'd be good-to-go, right?  Wrong.  :(

Unfortunately for me, it doesn't actually solve my problem.  I'm still unable to connect to the shares on the firewalled server until I disable the firewall and then mount the shares on each client.  And just like before, I can then re-enable the firewall without disconnecting the shares on each client.

---

### Post by derklempner on 2010-02-15
> **derklempner said:**
> And **ufw** now has all the appropriate open ports:

```
111                        ALLOW   192.0.0.0/24
2049                       ALLOW   192.0.0.0/24
4001                       ALLOW   192.0.0.0/24
4002                       ALLOW   192.0.0.0/24
4000                       ALLOW   192.0.0.0/24
```
Well, I can't say how foolish I feel for posting this, fretting over it for a few more hours, and then rereading my post to see the answer right in front of me...

My **ufw** rules clearly state the 192.0.0.0/24 subset, and yet all the computers on my local network are in the 198.162.2.x subset.  Since I had changed their IP addresses from 10.0.0.x to 192.168.2.x, I neglected to change the rules properly, which had previously listed the 10.0.0.0/24 subset.

So, kids, the moral of the story is: double-check *_all_* your changes and make sure there are no errors.

---

