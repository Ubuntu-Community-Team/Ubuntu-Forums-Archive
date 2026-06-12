---
title: "Can't connect to my network storage drive anymore"
date: 2012-10-15
forum: Networking &amp; Wireless
---

### Post by ratdog on 2012-10-15
Hello,

I'm having trouble connecting to my dlink dns-321 nas drive.  I had gotten it set up as a server and it was automounting at one point.  I've moved and not tried accessing the drive for a few months and cannot connect to it now.  It can still be accessed from my wife's mac laptop, so I know it is working.  It seems something has changed on my computer, but I don't know what.

When trying to browse the Windows Network I get: "Unable to mount location.  Failed to retrieve share list from server."

I'm a networking novice and don't know much about samba, but here is some info.

photon@photon-laptop:~$ ps -ef|grep mbd

root       912     1  0 18:59 ?        00:00:00 smbd -F
root       966   912  0 18:59 ?        00:00:00 smbd -F
root      2219     1  0 19:00 ?        00:00:00 nmbd -D
photon    2588  2569  0 19:07 pts/0    00:00:00 grep mbd


photon@photon-laptop:~$ smbtree -d3

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::21e:65ff:fe56:cadc%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=172.16.0.3 bcast=172.16.0.255 netmask=255.255.255.0
Enter photon's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory


photon@photon-laptop:~$ nmblookup

Usage: [-?fMRSTrAV] [-?|--help] [--usage] [-B|--broadcast=BROADCAST-ADDRESS]
        [-f|--flags] [-U|--unicast=STRING] [-M|--master-browser]
        [-R|--recursion] [-S|--status] [-T|--translate] [-r|--root-port]
        [-A|--lookup-by-ip] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE]
        [-V|--version] [-O|--socket-options=SOCKETOPTIONS]
        [-n|--netbiosname=NETBIOSNAME] [-W|--workgroup=WORKGROUP]
        [-i|--scope=SCOPE] <NODE> ...

Thanks!

---

### Post by ratdog on 2012-10-29
I still haven't been able to connect to this drive.  What other info can I provide to help?

---

### Post by ratdog on 2012-11-05
bump of shame.  I could sure use some pointers.

---

