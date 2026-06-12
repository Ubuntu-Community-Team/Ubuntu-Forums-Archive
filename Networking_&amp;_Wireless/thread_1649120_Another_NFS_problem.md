---
title: "Another NFS problem"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by timnbron on 2010-12-19
Ubuntu 10.04.1 LTS server edition (2.6.32-26-generic-pae #48-Ubuntu SMP)

I've mapped plenty of networked drives (mostly in Arch Linux) but this one has me stumped. When I call [FONT=Courier New]mount[/FONT], it sites there for 60 seconds, and then responds 
[FONT=Courier New]mount.nfs: mount system call failed

[/FONT]I'm linking to a NetGear ReadyNAS NV+, however it has the same effect if I try a shared folder on another server. 

I have portmap, nfs-common and nfs-kernel-server installed. /etc/hosts.allow and hosts.deny are blank (commented out). The NAS has the server's IP already in it because a previous machine used the same shares and IP address. 

rpcinfo -p gives me:
```
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  54643  status
    100024    1   tcp  48395  status
    100021    1   udp  43909  nlockmgr
    100021    3   udp  43909  nlockmgr
    100021    4   udp  43909  nlockmgr
    100021    1   tcp  52459  nlockmgr
    100021    3   tcp  52459  nlockmgr
    100021    4   tcp  52459  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  48542  mountd
    100005    1   tcp  46657  mountd
    100005    2   udp  48542  mountd
    100005    2   tcp  46657  mountd
    100005    3   udp  48542  mountd
    100005    3   tcp  46657  mountd
```If I telnet to the NAS on port 2049, it connects (but closes after a couple of line feeds). I don't think it's a firewall issue. [FONT=Courier New]ufw status[/FONT] returns "Status: inactive". (There is a separate firewall server, but if telnet can connect, I presume it's letting us through.)

The entry in /etc/fstab reads:
[FONT=Courier New]fs001.kncluster000:/KN-NS-Share/kn_files /data/u00/www/kn_files nfs defaults 0 0[/FONT]

It doesn't seem to matter what options I put in; it just times out!

According to ps aux, nfsd, nfsd4, portmap are all running. I'd give you the full list, but I'll save your eyes for an strace on the mount command:

```
#strace mount /data/u00/www/kn_files

. . .

getuid32()                              = 0
geteuid32()                             = 0
readlink("/data", 0xbfe2ceab, 4096)     = -1 EINVAL (Invalid argument)
readlink("/data/u00", 0xbfe2ceab, 4096) = -1 EINVAL (Invalid argument)
readlink("/data/u00/www", 0xbfe2ceab, 4096) = -1 EINVAL (Invalid argument)
readlink("/data/u00/www/kn_files", 0xbfe2ceab, 4096) = -1 EINVAL (Invalid argument)
umask(077)                              = 022
open("/etc/fstab", O_RDONLY|O_LARGEFILE) = 3
umask(022)                              = 077
fstat64(3, {st_mode=S_IFREG|0644, st_size=1786, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75bd000
read(3, "# /etc/fstab: static file system"..., 4096) = 1786
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb75bd000, 4096)                = 0
readlink("/dev", 0xbfe2ce6b, 4096)      = -1 EINVAL (Invalid argument)
readlink("/dev/fd0", 0xbfe2ce6b, 4096)  = -1 EINVAL (Invalid argument)
getcwd("/root", 4095)                   = 6
readlink("/root/fs001.kncluster000:", 0xbfe2ce6b, 4096) = -1 ENOENT (No such file or directory)
getcwd("/root", 4095)                   = 6
readlink("/root/fs001.kncluster000:", 0xbfe2ce6b, 4096) = -1 ENOENT (No such file or directory)
getcwd("/root", 4095)                   = 6
readlink("/root/fs001.kncluster000:", 0xbfe2ce6b, 4096) = -1 ENOENT (No such file or directory)
readlink("/dev", 0xbfe2ce6b, 4096)      = -1 EINVAL (Invalid argument)
readlink("/dev/fd0", 0xbfe2ce6b, 4096)  = -1 EINVAL (Invalid argument)
getcwd("/root", 4095)                   = 6
readlink("/root/fs001.kncluster000:", 0xbfe2ce6b, 4096) = -1 ENOENT (No such file or directory)
getcwd("/root", 4095)                   = 6
readlink("/root/fs001.kncluster000:", 0xbfe2ce6b, 4096) = -1 ENOENT (No such file or directory)
getcwd("/root", 4095)                   = 6
readlink("/root/fs001.kncluster000:", 0xbfe2ce6b, 4096) = -1 ENOENT (No such file or directory)
stat64("/sbin/mount.nfs", {st_mode=S_IFREG|S_ISUID|0755, st_size=80412, ...}) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb77277b8) = 3511
wait4(-1,

(hangs for 60 seconds)

mount.nfs: mount system call failed
[{WIFEXITED(s) && WEXITSTATUS(s) == 32}], 0, NULL) = 3511
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(32)                          = ?

```I've hunted through forums (I hate having to ask when a quick Google brings up the answer) but I've run out of ideas. Is there anything I've missed?

---

### Post by timnbron on 2010-12-19
btw, it's a HP DL360 G4 server, running as the root login (i.e. no sudo)

Tim

---

### Post by drdos2006 on 2010-12-20
What do you have in your server /etc/exports file ?

regards

---

### Post by timnbron on 2010-12-20
Nothing. But I thought the exports file was for the nfs server, which would be the ReadyNAS box? I'm setting up the HP server as a client.

---

### Post by HermanAB on 2010-12-20
Howdy,

I have seen this kind of thing due to an incompatibility between the default server and client versions.  You may need to force the client to use an older version to connect, e.g. option nfsvers=3

---

### Post by Jose Catre-Vandis on 2010-12-20
Also try using the IP address instead of the server name (just in case this is causing a problem)

---

### Post by timnbron on 2010-12-21
I recall I had an issue with nfs versions on another server. I tried nfsvers=2, nfsvers=3 and nfs4, but it didn't make any difference.

However, going through all the options, I got it working with proto=udp. So my problem is solved, but any comments on why this was the issue?

---

### Post by timnbron on 2010-12-21
False alarm. It's not actually working - it appears to mount, but any attempt to read it just hangs with a process status of D - waiting on disk. I presume this is because udp is a one way protocol, and it's got no way of telling if it actually mounted or not!

---

### Post by timnbron on 2010-12-21
The firewall is pfctl, running on an old BSD linux box. It's definitely allowing ports 111 and 2049:

pass out quick on $int_if proto tcp from any to any port {2049,111} tagged FRM_KN_DMZ modulate state flags S/SA
pass out quick on $int_if proto udp from any to any port {3074,2049,111} tagged FRM_KN_DMZ modulate state

One thought is that it's possibly plugged into the wrong VLAN on the switch, but wouldn't I see a No Route To Host error if that was the case?

I've attempted again to connect to folders on other servers, paying attention to the contents of the /etc/exports file, but I get the same problem so I don't think it's the ReadyNAS box.

Is there something in Ubuntu that might be stopping it? I've tried stopping apparmor, but no difference.

---

### Post by timnbron on 2010-12-21
I won't let this thing beat me...

Just tried it on a different server, also on Ubuntu 10.4, and it worked fine.

I bet it's plugged in the wrong hole...

...nope. It's definitely in the same vlan as another server which is able to mount the folder.

---

### Post by timnbron on 2010-12-21
OK. My last for the day. 

I can mount to a folder on a server in the same VLAN, but not outside it. The ubuntu server has the same settings in /etc/network/interfaces as the others on its VLAN:

iface eth0 inet static
        address 10.91.6.2
        netmask 255.255.254.0
        gateway 10.91.7.254

It can connect to nfs on 10.91.6.3, but not the ReadyNAS on 10.91.8.66. However, the Arch Linux server at 10.91.6.3 can connect to the ReadyNAS.

?!

---

### Post by timnbron on 2011-01-05
Solved! 
I opened port 4127, which was the tcp port used by the NAS box for mountd, as discovered using rpcinfo -p fs001:

   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100011    1   udp   1015  rquotad
    100011    2   udp   1015  rquotad
    100011    1   tcp   1018  rquotad
    100011    2   tcp   1018  rquotad
    100024    1   udp  32765  status
    100024    1   tcp  32765  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp   3072  nlockmgr
    100021    3   udp   3072  nlockmgr
    100021    4   udp   3072  nlockmgr
    100021    1   tcp   3512  nlockmgr
    100021    3   tcp   3512  nlockmgr
    100021    4   tcp   3512  nlockmgr
    100005    1   udp   3074  mountd
    100005    1   tcp   4127  mountd
    100005    2   udp   3074  mountd
    100005    2   tcp   4127  mountd
    100005    3   udp   3074  mountd
    100005    3   tcp   4127  mountd

where fs001 is the name of the NAS box

Hence I opened ports 111, 2049 and 4127.

---

