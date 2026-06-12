---
title: "mount.nfs: mount system call failed"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by magnetsandlasers on 2009-12-20
[FONT=monospace]If I see this error again I am going to pull out my hair! I cannot figure out what is wrong after hours and hours of fiddling, rebooting, restarting services, etc. 

My nfs server: laptop running karmic
My client: pc running ubuntu server

I have followed a few different HOWTOs to the letter. Installed all the bits for server and client nfs support. Everything is current. I can ping each machine from the other. I am controlling the server from the laptop via ssh. 

Samba works GREAT for my Windows shares. No problems, easy as pie. Set it up in minutes. Why is sharing between two machines running Ubuntu such an ordeal? Am I missing something? Could there be a better way?

And what does the mount system call failed actually mean?
[/FONT]

---

### Post by choochus on 2010-01-03
> **magnetsandlasers said:**
> [FONT=monospace]
And what does the mount system call failed actually mean?
[/FONT]

I had this exact same problem. I realized that I hadn't exported the shares (sudo exportfs -a) which required installing the nfs kernel server (sudo apt-get install nfs-kernel-server), then allowing my client machine in hosts:allow

---

### Post by jamb on 2010-01-03
> **magnetsandlasers said:**
> [FONT=monospace]If I see this error again I am going to pull out my hair! I cannot figure out what is wrong after hours and hours of fiddling, rebooting, restarting services, etc. 

My nfs server: laptop running karmic
My client: pc running ubuntu server

I have followed a few different HOWTOs to the letter. Installed all the bits for server and client nfs support. Everything is current. I can ping each machine from the other. I am controlling the server from the laptop via ssh. 

Samba works GREAT for my Windows shares. No problems, easy as pie. Set it up in minutes. Why is sharing between two machines running Ubuntu such an ordeal? Am I missing something? Could there be a better way?

And what does the mount system call failed actually mean?
[/FONT]

This is my NFS Karmic experience.
It may be somewhat related to your problem, but you do not say what distribution you have on the client side, I guess it is also Karmic. 

I have Karmic 9.10 Xubuntu (2.6.31-16) on one client and Gutsy 7.10 is my NFS server (shire). Both portmap and nfs-common must be installed on the client (which is not default by 9.10 Ubuntu but in Debian 5.0).
> 
sudo apt-get install portmap nfs-common
 
I have shared my /home/jamb/nfs from the server via NFS v3, to various laptops/systems. I have a few that I play around with, and I want access to this share regardless which one I'm working with.
Up to now, I have been using Debian Lenny 5.0 or Hardy 8.04 on the client systems.
On the NFS server my /etc/exports looks like this:
> 
/home/jamb 192.168.0.0/24(rw,no_subtree_check,no_root_squash,sync)


On all my clients I have the directory /home/jamb/nfs were I mount my NFS share.
On my Karmic client side, I could not get my usual mount stanza to work at boot time with this in /etc/fstab:
> 
shire.gigahome.net:/home/jamb/nfs  /home/jamb/nfs  nfs  rw,hard,intr,nfsvers=3  0  0

The fqdn above can be replaced with your IP like 192.168.0.X.
But typing the mount command, worked as expected:
> 
sudo mount shire.gigahome.net:/home/jamb/nfs  /home/jamb/nfs


I was in the belief that this was a new feature of Karmic accelerated upstart, and I prepared myself to write my mount command in /etc/rc.local

However, I was not satisfied with this, I noticed during start, that following message was echoed to the screen:
> 
mountall: Event failed
mount.nfs: rpc.statd is not running but is required for remote locking.
Either use '-o nolock' to keep locks local, or start statd.
mountall: mount /home/jamb/nfs [819] terminated with status 32
mountall: Filesystem could not be mounted: /home/jamb/nfs


I tried to get more information in various log files like
*syslog, debug, dmesg,messages, kernel, daemon.log* searching for mountall, but found nothing related to mountall. 
Finally I added the **nolock** to my /etc/fstab stanza:
> 
shire.gigahome.net:/home/jamb/nfs  /home/jamb/nfs  nfs  rw,hard,intr,nolock,nfsvers=3  0  0


After this I restarted the machine, and now the remote share was mounted!
Hope this help. The 'mountall: Event failed' remains, though.

---

### Post by birdsarah on 2010-02-03
Hi,  I had the same problem.

For me it was firestarter (firewall program) that I hadn't realised was running in the background was getting in the way.

Silly of me not to realize. Ho hum - we live an learn!

---

### Post by phantom_ on 2010-07-02
hi all,

had the same problem. my case was incorrectly binding portmapper service to localhost (127.0.0.1).

you can check/correct the service binding with ```
dpkg-reconfigure portmapper
``` command. don't forget to execute as root at shell.

---

### Post by nicegiving on 2010-09-07
> **birdsarah said:**
> Hi,  I had the same problem.

For me it was firestarter (firewall program) that I hadn't realised was running in the background was getting in the way.

Silly of me not to realize. Ho hum - we live an learn!

Yes, I got the same problem, and the reason is still IPTABLES (firewall problem). I once checked that whether I could mount the shared folder in the system itself, and it worked, but I mount it from other machines, there is a long time waiting and finally got the error "mount.nfs: mount system call failed". 

May be you should check it like me see if you got the same phenomenon. Generally speaking, the configuration of NFS is such easy, if you got problem, just think about the whole mount procedure and make sure privilege,network,firewall and configuration are all OK!

Good luck!

---

### Post by Minarion on 2011-02-03
> but if I mount it from other machines, there is a long time waiting and finally got the error "mount.nfs: mount system call failed

The same phenomenon here, however this error only occurs since using a new switch (netgear, managed gigabit). Before it used to work perfectly.

---

