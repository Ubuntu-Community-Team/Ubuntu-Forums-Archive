---
title: "smbclient can't connect to windows vista"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by briangoldberg on 2011-01-05
I use the smbclient command to see if my linux computer can see my windows shares. I have used the debug option. There are two windows computers with file sharing, one called cpu the other called goldberg-pc. Cpu is windows xp. goldberg-pc is windows vista.```
shoshana@ubuntu:~$ smbclient -U Goldberg%password -L goldberg-pc -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=fe80::219:7dff:fe28:8723%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.66 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.5.4).
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name goldberg-pc<0x20>
Connecting to 192.168.1.254 at port 445
[COLOR=Red]Connecting to 192.168.1.254 at port 139
Error connecting to 192.168.1.254 (Connection refused)
Connection to goldberg-pc failed (Error NT_STATUS_CONNECTION_REFUSED)[/COLOR]
shoshana@ubuntu:~$ 

```

but for the successful attempt
```
shoshana@ubuntu:~$ smbclient -U owner%password -L cpu  -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=fe80::219:7dff:fe28:8723%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.66 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.5.4).
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name cpu<0x20>
[COLOR=Green]Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[CPU] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_OK
resolve_lmhosts: Attempting lmhosts lookup for name cpu<0x20>[/COLOR]
[COLOR=Green]Connecting to 192.168.1.65 at port 139
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[CPU] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------[/COLOR]

```

As you can see the red is where the windows vista one doesn't work and the green is where the windows xp one does work. Also I tried the above with the highest debug level 10. Same results except for some missing english message file. And something about a duplicate pair.

```
shoshana@ubuntu:~$ smbclient -U Goldberg%password -L goldberg-pc -d10
INFO: Current debug levels:
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
doing parameter workgroup = workgroup
doing parameter netbios name = ubuntu
handle_netbios_name: set global_myname to: UBUNTU
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter encrypt passwords = yes
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
added interface eth1 ip=fe80::219:7dff:fe28:8723%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.66 bcast=192.168.1.255 netmask=255.255.255.0
Netbios name list:-
my_netbios_names[0]="UBUNTU"
Client started (version 3.5.4).
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/run/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
Cache entry with key = AD_SITENAME/DOMAIN/ couldn't be found 
sitename_fetch: No stored sitename for 
internal_resolve_name: looking up goldberg-pc#20 (sitename (null))
Cache entry with key = NBT/GOLDBERG-PC#20 couldn't be found 
no entry for goldberg-pc#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name goldberg-pc<0x20>
getlmhostsent: lmhost entry: 192.168.1.65 cpu 
getlmhostsent: lmhost entry: 192.168.1.254 goldberg-pc 
remove_duplicate_addrs2: looking for duplicate address/port pairs
namecache_store: storing 1 address for goldberg-pc#20: 192.168.1.254
Adding cache entry with key = NBT/GOLDBERG-PC#20 and timeout = Wed Jan  5 20:10:05 2011
 (660 seconds ahead)
internal_resolve_name: returning 1 addresses: 192.168.1.254:0 
Running timed event "tevent_req_timedout" 0x2182e9d0
Connecting to 192.168.1.254 at port 445
Running timed event "tevent_req_timedout" 0x2182ed00
Connecting to 192.168.1.254 at port 139
Error connecting to 192.168.1.254 (Connection refused)
lang_tdb_init: /usr/share/samba/en_US.utf8.msg: No such file or directory
Connection to goldberg-pc failed (Error NT_STATUS_CONNECTION_REFUSED)
shoshana@ubuntu:~$ 

```

---

### Post by PatchesTheCaveman on 2011-01-06
Do you have Windows Live Essentials installed on the Windows Vista machine?  Microsoft sometimes installs it via Windows Update, so you might not know you have it.

If so, theres a bug in Samba that prevents it from being able to access shares on the Windows Vista machine.  For more information and how to work around this bug, see this thread:
[http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)

---

