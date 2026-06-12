---
title: "NFS configuration problem. 9.04 Server, 9.04 Wubi client cannot connect"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by drubdrub on 2009-05-15
NFS configuration problem. 9.04 Server, 9.04 Wubi client cannot connect

Confused.  Can't seem to get a very simple NFS export to function.  It's been awhile since I've configured NFS, so I'm probably doing something bone-headed.

--------------------------------------
**System A (ldrub)**
Export the FS, the server side.
9.04
Intel CPU, 4GB RAM
--------------------------------------
Make sure the NFS packages are installed.
```
$ dpkg -l | grep -i nfs
ii  liblockfile1          1.08-3             NFS-safe locking library, includes dotlockfi
ii  libnfsidmap2          0.21-2             An nfs idmapping library
ii  nfs-common            1:1.1.4-1ubuntu1   NFS support files common to client and serve
ii  nfs-kernel-server     1:1.1.4-1ubuntu1   support for NFS kernel server

```
Make sure portmapper is installed.
```
$ dpkg -l | grep -i nfs
ii  portmap               6.0-9ubuntu1       RPC port mapper

```
Configure /etc/exports.
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/home1/j	192.168.2.0/24(rw,no_root_squash,async,no_subtree_check)
#/home1/j	192.168.2.0/255.255.255.0(rw,no_root_squash,async,no_subtree_check)
#/home1/j	192.168.2.220(rw,no_root_squash,async,no_subtree_check)

```
So, it looks like the required NFS packages are installed.  After each /etc/exports change, portmapper was restarted.  In fact, even networking was restarted to make sure NFS was restarted.

--------------------------------------
**System B**
Mount the exported FS, the client side.
9.04
Intel CPU, 2GB RAM, laptop
--------------------------------------
```
$ dpkg -l | grep -i nfs
ii  liblockfile1         1.08-3               NFS-safe locking library, includes dotlockfi
ii  libnfsidmap2         0.21-2               An nfs idmapping library
ii  nfs-common           1:1.1.4-1ubuntu1     NFS support files common to client and serve

```
```
$ dpkg -l | grep -i portmap
ii  portmap             6.0-9ubuntu1          RPC port mapper

```
```
$showmount --exports ldrub
Export list for ldrub:
/home1/j 192.168.2.220,192.168.2.0/24

```
It looks like the export side of the connection is functional.  showmount() shows that the FS is available to the laptop, the client side system. It is 192.168.2.200.
```
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:13:02:12:be:6a  
          inet addr:192.168.2.220  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe12:be6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1441693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:577928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1047572430 (1.0 GB)  TX bytes:63227567 (63.2 MB)

```
System B is at the expected IP address, which is the IP configured in
/etc/hosts on System A.
```

$ sudo mount -v -t nfs4 ldrub:/home1/j /home/david/j
mount.nfs4: timeout set for Fri May 15 16:27:44 2009
mount.nfs4: text-based options: 'clientaddr=192.168.2.220,addr=192.168.2.200'
mount.nfs4: mount(2): No such file or directory
mount.nfs4: mounting ldrub:/home1/j failed, reason given by server:
  No such file or directory

```
/home/david/j certainly exists on the client system.

Looking at the /etc/exports file, you can see that different attempts have been made to make the export less and less restrictive and allow more clients to mount the FS.  They all have failed.  After changing /etc/exports "exportfs -a" is run to publish the changes.

Both systems appear to function normally for all other network activities; the web, FTP, Samba, etc, etc.  

I have worked through other NFS recipes, on and off this forum, with the same results.  See
[LIST]
[*][http://www.quietearth.us/articles/2006/09/28/Ubuntu-How-to-setup-an-nfs-server](http://www.quietearth.us/articles/2006/09/28/Ubuntu-How-to-setup-an-nfs-server)
[*][http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
[*][http://www.cyberciti.biz/faq/how-to-ubuntu-nfs-server-configuration-howto/](http://www.cyberciti.biz/faq/how-to-ubuntu-nfs-server-configuration-howto/)
[/LIST]

What the heck am I overlooking?  Coaching is greatly appreciated.

BTW, also tried mounting with an 8.10 client with the same results.

---

### Post by drubdrub on 2009-05-31
Any ideas.  Still unable to get these 2 systems talking NFS.  Double darn.

They talk SMB, but I don't want to stoop that low.

Thanks!

---

### Post by Jose Catre-Vandis on 2009-05-31
I always start off simple, then build up. Have you tried the basics using the great howto by Malco on the forum: -> [here]("http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS")

Get it working with this, then build up from there.

FWIW, it looks to me like you need to make your exports and file locations a bit more obvious, use IP addresses instead of hostnames, and make sure portmap and nfs-common are on your clients.

---

### Post by drubdrub on 2009-05-31
Thank you for your thoughts!

Well, I was *trying* to make it dead simple:
[LIST]
[*]Export /home/j from system A
[*]Mount the exported /home/j into /home/user/j on system B
[/LIST]

Good point, coulda used an IP on the mount() command.

This /etc/fstab entry worked, on system B.  Note, the system A's name was used successfully in this case.  The IP was not required.

```
ldrub:/home1/j  /home/frog/j   nfs rsize=8192,wsize=8192,timeo=14,intr
```

I was unable to mount the the same resource with mount().  Guess I'm just fouling up the use of mount(), cuz it's working fine when configured in /etc/fstab.   
```
sudo mount -v -t nfs ldrub:/home1/j /home/frog/j
```

So it is functioning, but I [COLOR="DarkOrange"]haven't yet figured out the correct mount() incantation[/COLOR].  Any additional coaching is muchly appreciated.

All the best!

---

### Post by Jose Catre-Vandis on 2009-06-01
> **drubdrub said:**
> 
```
sudo mount -v -t nfs ldrub:/home1/j /home/frog/j
```

So it is functioning, but I [COLOR="DarkOrange"]haven't yet figured out the correct mount() incantation[/COLOR].  Any additional coaching is muchly appreciated.

All the best!

Try dropping all the options in the mount command. What happens?
```
sudo mount ldrub:/home1/j /home/frog/j
```
the system should be looking in your fstab for an entry so you won't need any additional options.

Also you may be having some permissions issues depending upon where/what
```
/home1
``` is. You may need the same user (with the same UID) on both client and server for things to work properly and give you the access you need.

---

### Post by drubdrub on 2009-06-08
OMG, that was way too easy.  Rather embarrassing, actually.  But, at least I get to embarrass myself in a _very public_ place.  

Thank you, Jose.  Good coaching.  Thank you for your thoughts.

A very simple mount worked just fine.  No need for "-f nfs", etc.  Wow.  Now able to mount on the command line as well as using "mount -a" and /etc/fstab.

> **Jose Catre-Vandis said:**
> Try dropping all the options in the mount command. What happens?
```
sudo mount ldrub:/home1/j /home/frog/j
```
the system should be looking in your fstab for an entry so you won't need any additional options.

Also you may be having some permissions issues depending upon where/what
```
/home1
``` is. You may need the same user (with the same UID) on both client and server for things to work properly and give you the access you need.

---

### Post by Jose Catre-Vandis on 2009-06-13
:)

---

