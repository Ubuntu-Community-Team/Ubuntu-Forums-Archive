---
title: "NFS &amp; TFTP server won't work right."
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by xPreatorianx on 2011-04-02
I'm running Ubuntu 10.10 latest IIRC and I'm trying to setup a network boot using NFS and TFTP for my PS3 so I can boot gentoo. I can't seem to find where the problem is. I believe I have all the ports forwarded correctly but I'm not sure. I have all the files correctly edited from the guide I followed and it does boot into the vmlinux image I guess. But it can't mount the NFS directory.

I'm a noob when it comes to linux so I'm still learning. But I do learn quickly. Hopefully these are the correct logs you guys need because I had to take a video with my camera to get the logs from my PS3. I know I have my PS3 configured correctly besides maybe a port or two in relation to NFS or TFTP so I don't need any help with that, at least I hope.  I just need help server side.

Here are the logs from my PS3, ubuntu machine,  and all my edited files.

Here's where I have my files stored for tftp, nfs, and my mnt. 

```
/mnt/experimental 
```vmlinux
```
/var/lib/tftpboot
```IP's I'm using : 
Ubuntu machine with nfs server : 192.168.1.2
/mnt/experimental is on : 192.168.1.2
PS3 is on : 192.168.1.3

I also have latent IP's like 192.168.1.4 because I was troubleshooting. Please let me know where I am going wrong. Thank you for your help in advance. 



[37.474692] rpcbind: server 192.168.1.3 not responding. timed out
[37.476342] Root-NFS: Unable to get nfsd port number from server, using default.
[37.479697] Looking up port of RPC 100005/1 on 192.168.1.3
[72.646690] rpcbind : Server 192.168.1.3 not responding, timed out
[72.548512] Root-NFS: Unable to get mountd port number from server, using default.
[107.610727] Root-NFS : Server returned error -110 while mounting /mnt/experimental
[107.622308] VFS : Unable to mount root fs via NFS, trying floppy.
[107.624762] VFS : Cannot open root device "nfs" or unknown-block (2,0)
[107.626594] Please append a correct  "root=" boot option; here are the available partitions : (there aren't any it just does a stack trace and freezes. 

dhcpd.conf 

```
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#
#
#
#


default-lease-time 600;
max-lease-time 7200;
ddns-update-style none;
authoritative;
log-facility local7;
subnet 192.168.1.0 netmask 255.255.255.0{ 
range 192.168.1.1 192.168.1.254;
}
next-server 192.168.1.2;
filename "kboot.conf";
option routers 192.168.1.1;

host PS3{
hardware ethernet 00:1f:a7:81:1d:72; # MAC address of PS3
fixed-address 192.168.1.3; # PS3 IP address, you decide.
}

```exports 
```
# /etc/exports: the access control list for filesystems which may be exported
#        to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/mnt/experimental 192.168.1.2(rw,async,no_root_squash,no_subtree_check,anonuid=0,anongid=0)
#/mnt/experimental 192.168.1.4/16(rw,async,no_root_squash,no_subtree_check,anonuid=0,anongid=0) 

```kboot.conf 
```
linux='vmlinux video=ps3fb:mode:2 root=/dev/nfs rw ip=dhcp nfsroot=192.168.1.3:/mnt/experimental panic=5' 
```rpcinfo 
```
prea@prea-dev:~$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  59496  status
    100024    1   tcp  58250  status
    100021    1   udp  37426  nlockmgr
    100021    3   udp  37426  nlockmgr
    100021    4   udp  37426  nlockmgr
    100021    1   tcp  33013  nlockmgr
    100021    3   tcp  33013  nlockmgr
    100021    4   tcp  33013  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100005    1   udp  47827  mountd
    100005    1   tcp  50681  mountd
    100005    2   udp  47827  mountd
    100005    2   tcp  50681  mountd
    100005    3   udp  47827  mountd
    100005    3   tcp  50681  mountd

```

---

### Post by xPreatorianx on 2011-04-05
Bump still having problems getting this to work.

---

### Post by xPreatorianx on 2011-04-09
Bump with updated information that I have tried, still having problems!

I have tried changing my exports to this : 
```
/mnt/experimental 192.168.1.0/24(rw,async,no_root_squash,no_subtree_check,anonuid=0,anongid=0)

```

I have also restarted the services several times as well. I have portmap installed as well (from my previous logs.)

I still can't get it to boot it still has the same errors.

---

