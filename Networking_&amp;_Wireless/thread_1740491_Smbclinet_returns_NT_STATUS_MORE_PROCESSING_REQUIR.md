---
title: "Smbclinet returns NT_STATUS_MORE_PROCESSING_REQUIRED"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by mati007 on 2011-04-27
Hi
I'm trying to connect to Windows Share folder. I'm calling:
smbclient //server/folder1 -U user_name -W domain -D /folder2 -d3

My folder is inside another and I don't have access to top folder.

Command produces following output:

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::862b:2bff:fec2:4616%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=10.123.5.24 bcast=10.123.5.255 netmask=255.255.255.0
Client started (version 3.5.4).
Enter user_name's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name nlsrv-home01<0x20>
resolve_wins: Attempting wins lookup for name nlsrv-home01<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name nlsrv-home01<0x20>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 10.96.196.1 at port 445
Doing spnego session setup (blob length=99)
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.3.6.1.4.1.311.2.2.10
got principal=nlsrv-fas01$@TTG.GLOBAL
Got challenge flags:
Got NTLMSSP neg_flags=0x60898205
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088205
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088205
spnego_parse_auth_response failed at 1
Failed to parse auth response
SPNEGO login failed: Invalid parameter
session setup failed: NT_STATUS_MORE_PROCESSING_REQUIRED
did you forget to run kinit?

I'm using Ubuntu 10.10. I tested same command on live CD and it works perfectly fine. Google didn't find any solution for this issue :(. Has anyone idea what causes this issue and how to solve it?

---

