---
title: "CIFS VFS: Unexpected Lookup Error -112"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2013-02-10
I am hoping someone can help. I am getting a ton of these errors shown on a couple of my tty sessions on my Ubuntu 10.04.4 command line only server. On tty1 and tty2 it keeps repeating the following errors
```
CIFS VFS: Unexpected lookup error -112
No response for cmd 50 mid 32952
```

the "no response for cmd" error, the 50 number changes from 50 to 114 every 5th or so line and the mid number changes every line I believe. Here's a pic I took since I can't capture the screen as it doesn't have a desktop manager and it's in tty1
[IMG]https://lh6.googleusercontent.com/-A5q9cS1gzcU/URhWDItlOqI/AAAAAAAABgo/gKLgOGuGlx0/s912/IMAGE_DEF0E0F4-A5C9-4C1F-B164-71BFF5BEA551.JPG[/IMG]

The errors are not in log.nmbd or log.smbd so I am not sure where the errors are coming from. the one error that looks weird within log.smbd is this
```
[2013/02/10 15:26:29,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2013/02/10 15:26:29,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.

```

Can anyone help please? If you need any other info let me know.


Also, a second issue is where my Western Digital My Book World Edition is becoming the Domain Master Browser for some reason despite my command line server having the proper smb.conf to make it the domain master browser. Here's the smb.conf for it.
```
[global]
    netbios name = dell
    server string = dell
    workgroup = LINUX
    encrypt passwords = true
#    guest ok = yes
    smb passwd file = /etc/samba/smbpasswd
    domain master = yes
    local master = yes
    preferred master = yes
    os level = 99
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
#   passdb backend = tdbsam
    null passwords = true
    username map = /etc/samba/username.map
name resolve order = lmhosts host wins bcast
#    hosts allow = 127.0.0.1 127.0.1.1 192.168.
#    hosts deny = 0.0.0.0/0
#   hostname lookups = yes
#   hosts equiv = /etc/samba/lmhosts 
   map to guest = Bad User   
   guest account = nobody
   wins support = no
#   smb ports = 139
    browse list = yes
    mangled names = yes
    default case = lower
    case sensitive = no
    preserve case = yes
    short preserve case = yes
    usershare allow guests = yes
unix extensions = no

```
The reason I think the WD My Book World Edition is the Domain Master Browser is from the log.nmbd here:
```
cat /var/log/samba/log.nmbd
[2013/02/10 07:45:01,  0] nmbd/nmbd.c:130(nmbd_sig_hup_handler)
  Got SIGHUP dumping debug info.
[2013/02/10 07:45:01,  0] nmbd/nmbd_workgroupdb.c:281(dump_workgroups)
  dump_workgroups()
   dump workgroup on subnet     192.168.0.5: netmask=  255.255.255.0:
  	LINUX(1) current master browser = CIRCLE
  		DELL 40899a03 (dell)

```
Circle is the hostname of the Western Digital My Book World Edition

---

### Post by bab1 on 2013-02-11
> **dannyboy79 said:**
> I am hoping someone can help. I am getting a ton of these errors shown on a couple of my tty sessions on my Ubuntu 10.04.4 command line only server. 

On tty1 and tty2 it keeps repeating the following errors
```
CIFS VFS: Unexpected lookup error -112
No response for cmd 50 mid 32952
```the "no response for cmd" error, the 50 number changes from 50 to 114 every 5th or so line and the mid number changes every line I believe...
Maybe you'll find them in the log *dmesg *.  You can check the last 25 entires with this command```
tail -n25 /var/log/dmesg
```These errors can be caused by lack of connectivity ( the mount can't be found or it has been dropped.).
> 
The errors are not in log.nmbd or log.smbd so I am not sure where the errors are coming from. 
I believe the smbd and nmbd logs are more concerned wit whether the daemons are running, not the connectivtiy I mentioned above.
> 
the one error that looks weird within log.smbd is this
```
[2013/02/10 15:26:29,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2013/02/10 15:26:29,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  [COLOR="Red"]getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = No route to host.[/COLOR]

```Note the connectivity loss above (noted in **[COLOR=Red]RED[/COLOR]**).  Same problem from a different viewpoint.> 

Also, a second issue is where my Western Digital My Book World Edition is becoming the Domain Master Browser for some reason despite my command line server having the proper smb.conf to make it the domain master browser.
This also is due to the connectivity issues.  When the MASTER BROWSER disappears the other servers on the LAN elect a new MASTER BROWSER.  This is normal and to be expected.>  


Here's the smb.conf for it.
```
[global]
    netbios name = dell
    server string = dell
    workgroup = LINUX
    encrypt passwords = true
#    guest ok = yes
    smb passwd file = /etc/samba/smbpasswd
    domain master = yes
    local master = yes
    preferred master = yes
    os level = 99
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
#   passdb backend = tdbsam
    null passwords = true
    username map = /etc/samba/username.map
name resolve order = lmhosts host wins bcast
#    hosts allow = 127.0.0.1 127.0.1.1 192.168.
#    hosts deny = 0.0.0.0/0
#   hostname lookups = yes
#   hosts equiv = /etc/samba/lmhosts 
   map to guest = Bad User   
   guest account = nobody
   wins support = no
#   smb ports = 139
    browse list = yes
    mangled names = yes
    default case = lower
    case sensitive = no
    preserve case = yes
    short preserve case = yes
    usershare allow guests = yes
unix extensions = no

```For a single segment LAN the  default smb.conf file needs little modification if you have the basic networking correcctly set up.  This means *host files *and LAN side DNS if you wish.  The only changes needed are to add the proper WORKGROUP and your shares> 

The reason I think the WD My Book World Edition is the Domain Master Browser is from the log.nmbd here:
```
cat /var/log/samba/log.nmbd
[2013/02/10 07:45:01,  0] nmbd/nmbd.c:130(nmbd_sig_hup_handler)
  [COLOR="Red"]Got SIGHUP dumping debug info[/COLOR].
[2013/02/10 07:45:01,  0] nmbd/nmbd_workgroupdb.c:281(dump_workgroups)
  dump_workgroups()
   dump workgroup on subnet     192.168.0.5: netmask=  255.255.255.0:
      LINUX(1) current master browser = CIRCLE
          DELL 40899a03 (dell)

```Circle is the hostname of the Western Digital My Book World EditionYes indeed, see the [COLOR="Red"]**red**[/COLOR] here also.

You can set the MASTER BROWSER but it won't help if the server looses continuity.  I would take a look at how the network provides LAN side host/DNS naming services amd reset all the defaults (except the WORKGROUP and SHARES in you smb.conf file.

---

### Post by dannyboy79 on 2013-02-11
There's nothing in dmesg related to samba I looked.

what I don't get about the connectivity error within log.smbd is that is can't connect to itself? read_fd_with_timeout: client 0.0.0.0 read error = No route to host.

The master browser should never disappear because my server is always ON. it's never shut off and it's uptime is 07:02:44 up 13 days,  4:38,  4 users,  load average: 1.10, 1.08, 1.03

the network provides LAN side host/DNS naming by way of hosts files on each machine and the DNS is handled by the Dlink DIR-655 router. I never had the domain master browser issue prior to getting the Western Digital My Book World Edition.

The machine with all the errors only has the following in it's fstab file so it only has 1 smb share which is mounted and working. The My Book World Edition is always on.
```
//192.168.0.39/public	/mnt/circle	cifs	noexec,nounix,username=daniel,passsword=,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
```

---

### Post by bab1 on 2013-02-11
> **dannyboy79 said:**
> There's nothing in dmesg related to samba I looked.

There are a number of places that you should check.  All of them are at /var/log or /var/log/samba.  I'd try the syslog of kern log.  If you see them on the screen, the errors are logged.  You just need to find them.> 

what I don't get about the connectivity error within log.smbd is that is can't connect to itself? read_fd_with_timeout: client 0.0.0.0 read error = No route to host.
Certainly that's possible.  If the daemon can't connect to an IP address then you get the timeout.[/QUOTE]

The master browser should never disappear because my server is always ON. it's never shut off and it's uptime is 07:02:44 up 13 days,  4:38,  4 users,  load average: 1.10, 1.08, 1.03
[/QUOTE]Just because the host is on and up doen't mean that it has connectivity to network.  Your error messages show that.> 

the network provides LAN side host/DNS naming by way of hosts files on each machine and the DNS is handled by the Dlink DIR-655 router. I never had the domain master browser issue prior to getting the Western Digital My Book World Edition.
Have you configured the hosts file on the WD device (circle)?  What DNS is configured on the DLink?  It looks as if the only reliable host is circle.  When the host with the *master browse list* disconnects, the WD host wins the election and becomes the MB.  I would investigate why your server disconnects.

Are you running a AD domain or is this a workgroup network?  > 

The machine with all the errors only has the following in it's fstab file so it only has 1 smb share which is mounted and working. The My Book World Edition is always on.
```
//192.168.0.39/public	/mnt/circle	cifs	noexec,nounix,username=daniel,passsword=,uid=1000,gid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
```

So are you looking at both the server and the clients logs?  The server should show something.  The client should show only the lack of connectivity (dropped connection to the server).

---

### Post by dannyboy79 on 2013-02-12
there is nothing within kern.log or syslog on the server or the client I am sitting at as I have already stated.

This error (on the server)
```
[2013/02/11 12:19:47,  1] smbd/service.c:1063(make_connection_snum)
  winxp (192.168.0.37) connect to service fat32 initially as user daniel (uid=1000, gid=1000) (pid 1683)
[2013/02/11 14:02:09,  0] lib/util_sock.c:743(write_data)
[2013/02/11 14:02:09,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2013/02/11 14:02:09,  0] smbd/process.c:62(srv_send_smb)
  Error writing 220 bytes to client. -1. (Transport endpoint is not connected)
[2013/02/11 14:02:09,  0] lib/util_sock.c:743(write_data)
[2013/02/11 14:02:09,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2013/02/11 14:02:09,  0] smbd/process.c:62(srv_send_smb)
  Error writing 53 bytes to client. -1. (Transport endpoint is not connected)
[2013/02/11 14:02:09,  1] smbd/service.c:1240(close_cnum)

```
doesn't make sense to me since it's states the client is 0.0.0.0, which I thought was itself. 

there is no hosts file on the My Book world edition that I am aware of, it only has a webserver config page that I log onto.

the network is just a workgroup network.

the server just posted this in the dmesg output
```
CIFS VFS: No response for cmd 50 mid 6929
```

here's the log.smbd from the server
```
  crystalbuntu (192.168.0.40) connect to service WDMBWE1TB initially as user daniel (uid=1000, gid=1000) (pid 4269)
[2013/02/12 15:59:55,  1] smbd/service.c:1063(make_connection_snum)
  crystalbuntu (192.168.0.40) connect to service fat32 initially as user daniel (uid=1000, gid=1000) (pid 4271)
[2013/02/12 16:01:34,  1] smbd/service.c:1240(close_cnum)
  crystalbuntu (192.168.0.40) closed connection to service fat32
[2013/02/12 16:01:34,  1] smbd/service.c:1240(close_cnum)
  crystalbuntu (192.168.0.40) closed connection to service WDMBWE1TB

```

and the log.nmbd
```
[2013/02/10 07:45:01,  0] nmbd/nmbd.c:130(nmbd_sig_hup_handler)
  Got SIGHUP dumping debug info.
[2013/02/10 07:45:01,  0] nmbd/nmbd_workgroupdb.c:281(dump_workgroups)
  dump_workgroups()
   dump workgroup on subnet     192.168.0.5: netmask=  255.255.255.0:
  	LINUX(1) current master browser = CIRCLE
  		DELL 40899a03 (dell)
[2013/02/10 22:29:22,  0] nmbd/nmbd_namequery.c:108(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.0.5 for name LINUX<1d>.
  This response was from IP 192.168.0.39, reporting an IP address of 192.168.0.39.

```

and there's nothing in the servers kern.log or syslog related to networking at all except for this in the kern.log
```
Feb 12 07:47:42 dell kernel: [1229033.456035]  CIFS VFS: No response for cmd 50 mid 6929
```

---

### Post by bab1 on 2013-02-12
> **dannyboy79 said:**
> there is nothing within kern.log or syslog on the server or the client I am sitting at as I have already stated.
Except for what you said at the bottom of you last post.  ;-)  > 

This error (on the server)
```
[2013/02/11 12:19:47,  1] smbd/service.c:1063(make_connection_snum)
  winxp (192.168.0.37) connect to service fat32 initially as user daniel (uid=1000, gid=1000) (pid 1683)
[2013/02/11 14:02:09,  0] lib/util_sock.c:743(write_data)
[2013/02/11 14:02:09,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2013/02/11 14:02:09,  0] smbd/process.c:62(srv_send_smb)
  Error writing 220 bytes to client. -1. (Transport endpoint is not connected)
[2013/02/11 14:02:09,  0] lib/util_sock.c:743(write_data)
[2013/02/11 14:02:09,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Broken pipe
[2013/02/11 14:02:09,  0] smbd/process.c:62(srv_send_smb)
  Error writing 53 bytes to client. -1. (Transport endpoint is not connected)
[2013/02/11 14:02:09,  1] smbd/service.c:1240(close_cnum)

```
doesn't make sense to me since it's states the client is 0.0.0.0, which I thought was itself. 
Well, for starters, 0.0.0.0 is everyone (all hosts).  I think you need to look more carefully at what you are posting.  There are plenty of clues.  No golden bullet, but plenty of information for you to ponder over.  What do you think this means```
[COLOR="Blue"]getpeername failed. Error was Transport endpoint is not connected
[/COLOR]
```> 

there is no hosts file on the My Book world edition that I am aware of, it only has a webserver config page that I log onto.

How do you expect it to know what the other devices hostnames are? > 

the network is just a workgroup network.
I would recommend retuning the smb.conf file to its defaults.  No DOMAIN MASTER.  The only thing you need to change is the WORKGROUP and add you shares at the bottom. > 

the server just posted this in the dmesg output
```
CIFS VFS: No response for cmd 50 mid 6929
```

the "No response" is more importand than what the "cmd 50" means.  I'll tell you that it is a SMB Trans2 request that is not being responded to. > 

here's the log.smbd from the server
```
  crystalbuntu (192.168.0.40) connect to service WDMBWE1TB initially as user daniel (uid=1000, gid=1000) (pid 4269)
[2013/02/12 15:59:55,  1] smbd/service.c:1063(make_connection_snum)
  crystalbuntu (192.168.0.40) connect to service fat32 initially as user daniel (uid=1000, gid=1000) (pid 4271)
[2013/02/12 16:01:34,  1] smbd/service.c:1240(close_cnum)
  crystalbuntu (192.168.0.40) closed connection to service fat32
[2013/02/12 16:01:34,  1] smbd/service.c:1240(close_cnum)
  crystalbuntu (192.168.0.40) closed connection to service WDMBWE1TB

```
Ah ha...> 

and the log.nmbd
```
[2013/02/10 07:45:01,  0] nmbd/nmbd.c:130(nmbd_sig_hup_handler)
  Got SIGHUP dumping debug info.
[2013/02/10 07:45:01,  0] nmbd/nmbd_workgroupdb.c:281(dump_workgroups)
  dump_workgroups()
   dump workgroup on subnet     192.168.0.5: netmask=  255.255.255.0:
  	LINUX(1) current master browser = CIRCLE
  		DELL 40899a03 (dell)
[2013/02/10 22:29:22,  0] nmbd/nmbd_namequery.c:108(query_name_response)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.0.5 for name LINUX<1d>.
  This response was from IP 192.168.0.39, reporting an IP address of 192.168.0.39.

```
What do you think this means```
[COLOR="Blue"]Multiple (2) responses received for a query on subnet 192.168.0.5 for name LINUX<1d>.
  This response was from IP 192.168.0.39, reporting an IP address of 192.168.0.39.[/COLOR]
```> 

and there's nothing in the servers kern.log or syslog related to networking at all except for this in the kern.log
```
Feb 12 07:47:42 dell kernel: [1229033.456035]  CIFS VFS: No response for cmd 50 mid 6929
```
Except...

Once again: you are better off starting at the beginning and reconfiguring the smb.conf file on your server.  I think you also need to configure either DNS or hosts for all of the devices.  This INCLUDES the WD device.  They all need to be able to communicate all the time by hostname or by bcast.  You might be able to see this by using the tis command from the client> smbtree -d3

My suspicion is that you are having name service problems and the host gets dropped because the user can't connect to the share.  Secondarily the WD wins the election (as it should) when you server disappears.

When you use Domain Master you alter the action of the nmbd daemon (the naming processes).  Simple is better. Return to the defaults.  If you continue to have problems it will be easier to diagnose.  THe WD is not the problem but it sure makes the problem come to the surface.

---

### Post by dannyboy79 on 2013-02-13
the My Book doesn't need to know any other hosts names as it doesn't mount anything to itself, it only shares out. Wouldn't my router do bcast anyway as a backup to hosts files?

I ran that command you suggested on the client and this is what it returned, I entered the correct smb password for ubu (which is the same as the sudo password) so I am not sure why I got permission denied on the gencache.tdb file
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::219:66ff:fe06:c6fd%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Enter ubu's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name LINUX<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LINUX<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LINUX<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LINUX<0x1b>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to host=192.168.0.5
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

the weird thing is that all my shares are working so I just am not sure what the errors are for? I'll comment out everything in the server's smb.conf file and reboot it to see if the errors disappear from the tty sessions. THanks thus far for your help.

---

### Post by bab1 on 2013-02-13
> **dannyboy79 said:**
> the My Book doesn't need to know any other hosts names as it doesn't mount anything to itself, it only shares out. Wouldn't my router do bcast anyway as a backup to hosts files?

I ran that command you suggested on the client and this is what it returned, I entered the correct smb password for ubu (which is the same as the sudo password) so I am not sure why I got permission denied on the gencache.tdb file
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::219:66ff:fe06:c6fd%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.3 bcast=192.168.0.255 netmask=255.255.255.0
Enter ubu's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name LINUX<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LINUX<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LINUX<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LINUX<0x1b>
Got a positive name query response from 192.168.0.5 ( 192.168.0.5 )
Connecting to host=192.168.0.5
Connecting to 192.168.0.5 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>

```

the weird thing is that all my shares are working so I just am not sure what the errors are for? I'll comment out everything in the server's smb.conf file and reboot it to see if the errors disappear from the tty sessions. THanks thus far for your help.

Send ALL of the output.  There is more that what you sent.  Redirect the output to a text file and attach that to the response.

---

### Post by dannyboy79 on 2013-02-13
that's all there was man. maybe it's because the password is failing?

---

### Post by bab1 on 2013-02-13
> **dannyboy79 said:**
> that's all there was man. maybe it's because the password is failing?

The last line```
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
```...should at least have a response.  This is where the client has asked "who has the Master Browse list".  It should at the very least have a reply even if it is an error.  Again; the output may be longer than you terminal displays so redirect the output to a text file and attach it to your response. 

The line ```
tdb(/var/run/samba/gencache.tdb): 
  tdb_open_ex: could not open file /var/run/samba/gencache.tdb: 
    Permission denied

```... is nothing.  It's not due to your password failing, nor is it relevant to you problem.

I'm beginning to sound like a broken record here, start with a default smb.conf file and all the basic networking correct.  What are the hostnames of all your network devices?  What does the hosts file look like for your workstation or laptop client?  Are you using Ethernet or Wireless for Layer 2 connectivity? 

Post the smb.conf file you are using at this time.

Post the output of this command ```
testparm -s
```

---

