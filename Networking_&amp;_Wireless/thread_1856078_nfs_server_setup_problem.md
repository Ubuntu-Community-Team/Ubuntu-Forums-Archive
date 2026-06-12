---
title: "nfs server setup problem"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by SnoopFogg on 2011-10-07
Hi, I'm trying to set up my netbook as an nfs server.  However, I'm getting the following error after updating etc/exports:

russ@russ-netbook:~$ /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                             exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: can't lock /var/lib/nfs/etab for writing
                                                                         [ OK ]
 * Exporting directories for NFS kernel daemon...                               exportfs: invalid netmask `50' for 192.168.0.1


What am I doing wrong?  

Cheers

---

### Post by Jonathan L on 2011-10-07
> **SnoopFogg said:**
> Hi, I'm trying to set up my netbook as an nfs server.  However, I'm getting the following error after updating etc/exports:

russ@russ-netbook:~$ /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                             exportfs: could not open /var/lib/nfs/.etab.lock for locking: errno 13 (Permission denied)
exportfs: can't lock /var/lib/nfs/etab for writing
                                                                         [ OK ]
 * Exporting directories for NFS kernel daemon...                               exportfs: invalid netmask `50' for 192.168.0.1


What am I doing wrong?  

Cheers

Hi Snoop

Looks to me like you have two problems:
1. You need root permission to start nfs, or it can't do much, and can't write in /var/lib/nfs
```
[COLOR=Red]sudo[/COLOR] /etc/init.d/nfs-kernel-server restart
```2.  Looks like you have a typo in your /etc/exports, specifically in your specification of the allowed client IP address.  Could you should it to us?

Kind regards,
Jonathan.

---

### Post by SnoopFogg on 2011-10-07
Thanks, think that has sorted out the first problem:

russ@russ-netbook:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: invalid netmask `50' for 192.168.0.1
                                                                         [fail]


/etc/exports - I've added:

/export       192.168.0.1/50(rw,fsid=0,insecure,no_subtree_check,async)
/export/russ  192.168.0.1/50(rw,nohide,insecure,no_subtree_check,async)

Really I only need to export to 198.168.0.21.  Just thought I'd leave my options open.

Thanks again for your help

---

### Post by jwcalla on 2011-10-07
The max is /24 I believe.

192.168.0.1/24 would correspond to the range of IP addresses from 192.168.0.1 through 192.168.0.254.

---

### Post by Jonathan L on 2011-10-08
> **SnoopFogg said:**
> Thanks, think that has sorted out the first problem:

russ@russ-netbook:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: invalid netmask `50' for 192.168.0.1
                                                                         [fail]


/etc/exports - I've added:

/export       192.168.0.1/50(rw,fsid=0,insecure,no_subtree_check,async)
/export/russ  192.168.0.1/50(rw,nohide,insecure,no_subtree_check,async)

Really I only need to export to 198.168.0.21.  Just thought I'd leave my options open.

Thanks again for your help

Hi Again Snoop

The error message here is slightly misleading: you have an inaccurate network specification (not really a 'mask') in /50.

You either specify a network prefix length (from /0, the whole internet, to /32, one computer) or a mask (from 0.0.0.0 to 255.255.255.255).  The most usual one for a home network is /24 or 255.255.255.0.
Take a look at [http://en.wikipedia.org/wiki/Subnetwork](http://en.wikipedia.org/wiki/Subnetwork) for explanation.

```
/export       192.168.0.1/[COLOR=Red]24[/COLOR](rw,fsid=0,insecure,no_subtree_check,async)
/export/russ  192.168.0.1/[COLOR=Red]24[/COLOR](rw,nohide,insecure,no_subtree_check,async)

```Hope that gets you working.  Let us know how you get on.

There's a point of view which says you should explicitly export to particular machines, and add them when you need them, so you'd just have 192.168.0.21(rw,...) with no network specification.    For a home network I'd add the /24 and keep the convenience.

Kind regards,
Jonathan.

---

### Post by SnoopFogg on 2011-10-09
Thanks Jonathan.  That seems to have fixed the server problem:

russ@russ-netbook:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [ OK ] 

Now I am having problems mounting it on the client which I set a fixed ip address using /etc/network/interfaces so that ifconfig now shows:

russ@russ-netbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:68:85:9e  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe68:859e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31894 (31.8 KB)  TX bytes:32827 (32.8 KB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32180 (32.1 KB)  TX bytes:32180 (32.1 KB)

wlan0     Link encap:Ethernet  HWaddr 7c:4f:b5:bc:04:36  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::7e4f:b5ff:febc:436/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150469 (150.4 KB)  TX bytes:25175 (25.1 KB)


However on the client I would just get:

russ@russ-desktop:~$ sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.0.18:/ /media/netbook
mount.nfs4: mount system call failed

Then I tried changing to the IP address of the wlan0 (at the time was 192.168.0.24).  This worked and I was able to connect.  But I was confused as I thought it should be the 192.168.0.18 that i have fixed for the eth0.  As this is a netbook I am using wireless.  Should I be trying to fix the wlan0 address and then getting the client to look for that?  If so, do you know how to do that?

My /etc/network currently looks like this:

auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static
address 192.168.0.18
netmask 255.255.255.0
gateway 192.168.1.1

Since rebooting the server, the wlan0 address is 192,168.0.25.  However, I get the mount.nfs4: mount system call failed error when I try to connect using this address.  Really needs to be a fixed address. Any ideas on this one? 

Thanks again

---

### Post by Jonathan L on 2011-10-09
> **SnoopFogg said:**
> Thanks Jonathan.  That seems to have fixed the server problem:

russ@russ-netbook:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [ OK ] 

Now I am having problems mounting it on the client which I set a fixed ip address using /etc/network/interfaces so that ifconfig now shows:

russ@russ-netbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:68:85:9e  
          inet addr:192.168.0.18  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe68:859e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31894 (31.8 KB)  TX bytes:32827 (32.8 KB)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:368 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32180 (32.1 KB)  TX bytes:32180 (32.1 KB)

wlan0     Link encap:Ethernet  HWaddr 7c:4f:b5:bc:04:36  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::7e4f:b5ff:febc:436/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150469 (150.4 KB)  TX bytes:25175 (25.1 KB)


However on the client I would just get:

russ@russ-desktop:~$ sudo mount -t nfs4 -o proto=tcp,port=2049 192.168.0.18:/ /media/netbook
mount.nfs4: mount system call failed

Then I tried changing to the IP address of the wlan0 (at the time was 192.168.0.24).  This worked and I was able to connect.  But I was confused as I thought it should be the 192.168.0.18 that i have fixed for the eth0.  As this is a netbook I am using wireless.  Should I be trying to fix the wlan0 address and then getting the client to look for that?  If so, do you know how to do that?

My /etc/network currently looks like this:

auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static
address 192.168.0.18
netmask 255.255.255.0
gateway 192.168.1.1

Since rebooting the server, the wlan0 address is 192,168.0.25.  However, I get the mount.nfs4: mount system call failed error when I try to connect using this address.  Really needs to be a fixed address. Any ideas on this one? 

Thanks again

Hi Snoop

Glad that last part gave you some progress.

I notice a couple of things which don't look quite right or are just a little bit unusual.

1. you have two working network interfaces onto the apperently the same network; it's unusual but nothing inherently wrong with it other than it can be confusing.  Whichever interface you want to mount on, try to get it to be a fixed ip address.  Won't much matter if you use your wifi or your eth0, but the wired one will probably be faster. Your gateway is incompatible with your ip address and mask for eth0, but it would work as your client is 192.168.0.21 and so on the same local network.
```
iface eth0 inet static
address 192.168.0.18
netmask 255.255.255.0
gateway 192.168.[COLOR=Red]0[/COLOR].1
```2. I'd suggest a static address for your wlan0 if you're intending to use it; I believe you can just edit /etc/network/interfaces and add auto wlan0 inet static and the addresses; I do mine in the DHCP server (ie, I put the fixed address for my laptop wlan0 into my router's dhcp table, with my wlan0 ethernet address.)
3. you're using TCP for your nfs, and though that's reasonable, I'd always use UDP, and default 'nfs' and port number.

4. Another problem, I think, is that you're appear to be trying to mount the root of your server.  I'd try this:
```
sudo mount -t nfs 192.168.0.18:[COLOR=Red]/export/russ[/COLOR] /media/netbook
```Hope that helps

Let us know how you get on

Jonathan

---

### Post by SnoopFogg on 2011-10-10
Hi, I seem to have set up a static ip address for wlan0 using router as you suggested.  Though I'm not sure how did that as I've not made any changes to the nfs server - does that sound feasible?  I have rebooted a few times and always get the same ip address.  

However whether the client then mounts is intermittent.  Though as I am writing this I just checked and it seems to have mounted again which is great news.  I'm going to check it out again tomorrow before I mark this thread solved.  So many thanks for your all your help.

---

### Post by Jonathan L on 2011-10-11
> **SnoopFogg said:**
> Hi, I seem to have set up a static ip address for wlan0 using router as you suggested.  Though I'm not sure how did that as I've not made any changes to the nfs server - does that sound feasible?  I have rebooted a few times and always get the same ip address.  

However whether the client then mounts is intermittent.  Though as I am writing this I just checked and it seems to have mounted again which is great news.  I'm going to check it out again tomorrow before I mark this thread solved.  So many thanks for your all your help.

Hi Snoop

"static" on DHCP: The dhcp server is free to give out whichever addresses it likes.  If it looks at the ether address of the dhcp client and always gives it the same address you'll see what you describe.

Sounds like you're running to me.  My guess is once things are stable and you're not making changes you'll find it works 100 percent.

Kind regards
Jonathan

---

### Post by SnoopFogg on 2011-10-11
Hi Jonathan, I am pleased to report this is all working fine now.  Not only that but I understand a little more about networking and my router which can only be good for next time.  

Thanks again for your help.

---

