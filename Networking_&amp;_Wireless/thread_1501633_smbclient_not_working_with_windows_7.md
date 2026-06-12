---
title: "smbclient not working with windows 7"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by miragemonger on 2010-06-04
I have been using Ubuntu for a while now and have never run into something like this that I haven't been able to find on the forums. My problem is quite similar to this post [http://ubuntuforums.org/showthread.php?t=1501277&highlight=windows+smbclient](http://ubuntuforums.org/showthread.php?t=1501277&highlight=windows+smbclient)

Description: 

I have a Windows 7 x64 machine and a Ubuntu 10.04 Server machine. I also have a share called "stuff" on the Windows machine. I can run the following command and it mounts the share successfully : 

```
sudo mount -t cifs //windows_machine/stuff -o user=usr,password=pswd /path/local/folder
```

However, if I run smbclient it fails with this error 
> session setup failed: SUCCESS - 0

The command I run is : 
```
smbclient //192.168.1.101/Stuff/ 
```

I tried running that command with -d10 option to get the debug output and here it is: 

> INFO: Current debug levels:
  all: True/10
  tdb: False/0
  printdrivers: False/0
  lanman: False/0
  smb: False/0
  rpc_parse: False/0
  rpc_srv: False/0
  rpc_cli: False/0
  passdb: False/0
  sam: False/0
  auth: False/0
  winbind: False/0
  vfs: False/0
  idmap: False/0
  quota: False/0
  acls: False/0
  locking: False/0
  msdfs: False/0
  dmapi: False/0
  registry: False/0
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
lp_servicenumber: couldn't find homes
set_server_role: role = ROLE_STANDALONE
Attempting to register new charset UCS-2LE
Registered charset UCS-2LE
Attempting to register new charset UTF-16LE
Registered charset UTF-16LE
Attempting to register new charset UCS-2BE
Registered charset UCS-2BE
Attempting to register new charset UTF-16BE
Registered charset UTF-16BE
Attempting to register new charset UTF8
Registered charset UTF8
Attempting to register new charset UTF-8
Registered charset UTF-8
Attempting to register new charset ASCII
Registered charset ASCII
Attempting to register new charset 646
Registered charset 646
Attempting to register new charset ISO-8859-1
Registered charset ISO-8859-1
Attempting to register new charset UCS2-HEX
Registered charset UCS2-HEX
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
added interface eth1 ip=fe80::290:27ff:fe1b:c12d%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::2a0:c9ff:fed7:e3f4%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=99.235.198.159 bcast=99.235.199.255 netmask=255.255.254.0
added interface eth1 ip=192.168.1.1 bcast=192.168.1.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="RESPIRO"
Client started (version 3.4.7).
Enter <username>'s password:
s3_event: Added timed event "tevent_req_timedout": 0x21b94c68
s3_event: Added timed event "tevent_req_timedout": 0x21b95068
Running timed event "tevent_req_timedout" 0x21b94c68
s3_event: Destroying timer event 0x21b94c68 "tevent_req_timedout"
s3_event: Added timed event "tevent_req_timedout": 0x21b94bc8
Connecting to 192.168.1.101 at port 445
s3_event: Added timed event "tevent_req_timedout": 0x21b957a8
s3_event: Destroying timer event 0x21b957a8 "tevent_req_timedout"
s3_event: Destroying timer event 0x21b94bc8 "tevent_req_timedout"
Socket options:
        SO_KEEPALIVE = 0
        SO_REUSEADDR = 0
        SO_BROADCAST = 0
        TCP_NODELAY = 1
        TCP_KEEPCNT = 9
        TCP_KEEPIDLE = 7200
        TCP_KEEPINTVL = 75
        IPTOS_LOWDELAY = 0
        IPTOS_THROUGHPUT = 0
        SO_SNDBUF = 16384
        SO_RCVBUF = 87380
        SO_SNDLOWAT = 1
        SO_RCVLOWAT = 1
        SO_SNDTIMEO = 0
        SO_RCVTIMEO = 0
 session request ok
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
cli_chain_cork: mid=1
handle_incoming_pdu: got mid 1
Doing spnego session setup (blob length=336)
SPNEGO login failed: Invalid parameter
lang_tdb_init: /usr/share/samba/en_CA.UTF-8.msg: No such file or directory
session setup failed: SUCCESS - 0


Furthermore, running ```
smbclient -L <windows_machine>
``` also returns an error: 
>  session setup failed: SUCCESS - 0 

I would really appreciate some thoughts on this issue ...

---

### Post by miragemonger on 2010-06-17
From my reading online it seems that this may be a windows vista/7 problem that they have introduced ... but still looking to see if anyone knows a way around this?

---

### Post by sebjames on 2010-07-26
I have the same issue. A call to mount.cifs successfully mounts the Windows 7 share, but a call to smbtree does not list the share and an attempt to access it using smbclient also fails, with log messages exactly as posted by the originator of this post.

---

### Post by petersaints on 2010-09-12
Same problem here. I'm getting crazy with this problem. I already tried tweaking so many settings and I get always da same result.

Uso mount with cifs works but using GVFS from Nautilus and smbclient don't.

Is there any workaround for this??

---

### Post by tian.hack on 2010-11-17
Exactly the same problem here.

---

### Post by tian.hack on 2010-11-17
This bug (patched) seems to be the root cause: [https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

---

### Post by hurricanehrndz on 2010-12-06
How do I apply this patch because smb client is still not working for me?

---

### Post by mucm on 2012-02-25
I know this is old but I just had this problem too.  Once I turned on debug level 2 in the smbclient command line, I had better error messages to google.  I eventually found these:

[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)
[https://bugzilla.redhat.com/show_bug.cgi?id=651722](https://bugzilla.redhat.com/show_bug.cgi?id=651722)
[http://www.mail-archive.com/backuppc-users@lists.sourceforge.net/msg20377.html](http://www.mail-archive.com/backuppc-users@lists.sourceforge.net/msg20377.html)
[http://fubar.school.nz/techblog.php?action=show&id=59](http://fubar.school.nz/techblog.php?action=show&id=59)

So, if patching and rebuilding samba on the backup server isn't an option for you (or upgrading... seems broken in samba 3.3.2, fixed in 3.5.8 but not sure exactly when in there it happened) , another work-around might be un-installing Windows Live Essentials on the Windows 7 clients.

---

