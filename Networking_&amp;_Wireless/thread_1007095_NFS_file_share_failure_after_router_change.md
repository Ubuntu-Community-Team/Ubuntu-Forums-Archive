---
title: "NFS file share failure after router change"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by izziere on 2008-12-10
I have lost my NFS share since changing my router, but I think it comes down to mounting the shared drive.  When i changed my router my external IP changed, but this does not appear in any of the configuration files.  Both server and client are working on Xubuntu 8.04 (Hardy).

Samba works fine, it is just the NFS mount.

The error codes I get are:

*sudo mount -a:*

[INDENT]mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered
mount.nfs: internal error[/INDENT]

[I]sudo /etc/init.d/networking restart:
[/I]
[INDENT]* Reconfiguring network interfaces...                                           
* Starting portmap daemon...
 * Already running.
   ...done.
 * Starting NFS common utilities
   ...done.
mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered
mount.nfs: internal error[/INDENT]

I guess this is just repeating the mount command

My configurations are as follows-

Server side:
*/etc/hosts*
[INDENT]192.168.n.nnn server_alias
192.168.n.NNN client_alias

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/INDENT]

Client side:
*/etc/fstab*
[INDENT]192.168.n.nnn:/media/server_drive /media/network nfs auto,rsize=32768,wsize=32768,proto=tcp,noatime,timeo=14,intr 0 0
[same problem happens if I use alias rather than IP address][/INDENT]

*/etc/hosts*
[INDENT]192.168.n.NNN   client_alias
192.168.n.nnn   server_alias

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/INDENT]

*/etc/network/interfaces:*
[INDENT]auto lo
iface lo inet loopback

iface ath0 inet static
 address 192.168.n.NNN
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 192.168.1.1

wireless-key xxxx
wireless-essid xxxxxx

auto ath0
[/INDENT]

I am sure I have missed something, but I have spent hours trying to rectify and am now googled out.  My former router was Linksys WRT54GR and am now on Linksys WRT160Nv2.

---

### Post by RomanIvanov on 2008-12-10
be sure that nfs-kernel-server and nfs-common packages are installed, and run 
```
sudo /etc/init.d/nfs-kernel-server restart
```
after each changes on source(with share folder) PC.

---

### Post by izziere on 2008-12-10
> **RomanIvanov said:**
> be sure that nfs-kernel-server and nfs-common packages are installed, and run 
```
sudo /etc/init.d/nfs-kernel-server restart
```
after each changes on source(with share folder) PC.

Good point - thanks.  

Problem is now solved.  The suggestion to restart nfs kernel server worked but was slow.  Investigations showed it to be unable to reach localhost.  It seems that the loopback had dropped from ifconfig.  This then moved problem onto /etc/hosts.allow - I had fiddled here trying to fix this before.  I deleted the line supposedly allowing the client, restarted networking on the client and server and bosh - fixed.

Thanks for help RomanIvanov - I needed to be pointed in the right direction!

---

