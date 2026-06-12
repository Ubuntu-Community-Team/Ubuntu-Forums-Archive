---
title: "unable to mount location failed to retrieve list from server"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by 9000cse on 2011-06-18
Hi,I keep getting this, ever time I try to map a shared drive on other systems with my small network. 'unable to mount location failed to retrieve list from server'. This used to work.
Main System UNBUNTU 10.10, GNOME ver. 2.32
Sys2 Windows XP Pro, SP3
Sys3 Windows XP Home SP3
Sys4 Windows XP Home SP3
Sys5 Windows 7

Mine is used as a server for the above, and also for me to work on.
For some reason, I keep getting permission failure.
Setting up a share on sys2. sys3, sys4, sys5 can see and read it. My main sys cannot.
None of the systems can see the Main one & the main one cannot read any of the others.

> 
Chain ufw-after-forward (1 references)
target prot opt source destination

Chain ufw-after-input (1 references)
target prot opt source destination
ufw-skip-to-policy-input udp -- anywhere anywhere udp dpt:netbios-ns
ufw-skip-to-policy-input udp -- anywhere anywhere udp dpt:netbios-dgm
ufw-skip-to-policy-input tcp -- anywhere anywhere tcp dpt:netbios-ssn
ufw-skip-to-policy-input tcp -- anywhere anywhere tcp dpt:microsoft-ds
ufw-skip-to-policy-input udp -- anywhere anywhere udp dpt:bootps
ufw-skip-to-policy-input udp -- anywhere anywhere udp dpt:bootpc
ufw-skip-to-policy-input all -- anywhere anywhere ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target prot opt source destination
LOG all -- anywhere anywhere limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] '

Chain ufw-after-logging-input (1 references)
target prot opt source destination
LOG all -- anywhere anywhere limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] '

Chain ufw-after-logging-output (1 references)
target prot opt source destination
LOG all -- anywhere anywhere limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] '

Chain ufw-after-output (1 references)
target prot opt source destination

Chain ufw-before-forward (1 references)
target prot opt source destination
ufw-user-forward all -- anywhere anywhere

Chain ufw-before-input (1 references)
target prot opt source destination
ACCEPT all -- anywhere anywhere
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
ufw-logging-deny all -- anywhere anywhere state INVALID
DROP all -- anywhere anywhere state INVALID
ACCEPT icmp -- anywhere anywhere icmp destination-unreachable
ACCEPT icmp -- anywhere anywhere icmp source-quench
ACCEPT icmp -- anywhere anywhere icmp time-exceeded
ACCEPT icmp -- anywhere anywhere icmp parameter-problem
ACCEPT icmp -- anywhere anywhere icmp echo-request
ACCEPT udp -- anywhere anywhere udp spt:bootps dpt:bootpc
ufw-not-local all -- anywhere anywhere
ACCEPT all -- base-address.mcast.net/4 anywhere
ACCEPT all -- anywhere base-address.mcast.net/4
ufw-user-input all -- anywhere anywhere

Chain ufw-before-logging-forward (1 references)
target prot opt source destination
LOG all -- anywhere anywhere state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] '

Chain ufw-before-logging-input (1 references)
target prot opt source destination
LOG all -- anywhere anywhere state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] '

Chain ufw-before-logging-output (1 references)
target prot opt source destination
LOG all -- anywhere anywhere state NEW limit: avg 3/min burst 10 LOG level warning prefix `[UFW AUDIT] '

Chain ufw-before-output (1 references)
target prot opt source destination
ACCEPT all -- anywhere anywhere
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
ufw-user-output all -- anywhere anywhere

Chain ufw-logging-allow (0 references)
target prot opt source destination
LOG all -- anywhere anywhere limit: avg 3/min burst 10 LOG level warning prefix `[UFW ALLOW] '

Chain ufw-logging-deny (2 references)
target prot opt source destination
LOG all -- anywhere anywhere limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] '

Chain ufw-not-local (1 references)
target prot opt source destination
RETURN all -- anywhere anywhere ADDRTYPE match dst-type LOCAL
RETURN all -- anywhere anywhere ADDRTYPE match dst-type MULTICAST
RETURN all -- anywhere anywhere ADDRTYPE match dst-type BROADCAST
ufw-logging-deny all -- anywhere anywhere limit: avg 3/min burst 10
DROP all -- anywhere anywhere

Chain ufw-reject-forward (1 references)
target prot opt source destination

Chain ufw-reject-input (1 references)
target prot opt source destination

Chain ufw-reject-output (1 references)
target prot opt source destination

Chain ufw-skip-to-policy-forward (0 references)
target prot opt source destination
DROP all -- anywhere anywhere

Chain ufw-skip-to-policy-input (7 references)
target prot opt source destination
DROP all -- anywhere anywhere

Chain ufw-skip-to-policy-output (0 references)
target prot opt source destination
ACCEPT all -- anywhere anywhere

Chain ufw-track-input (1 references)
target prot opt source destination

Chain ufw-track-output (1 references)
target prot opt source destination
ACCEPT tcp -- anywhere anywhere state NEW
ACCEPT udp -- anywhere anywhere state NEW

Chain ufw-user-forward (1 references)
target prot opt source destination

Chain ufw-user-input (1 references)
target prot opt source destination
ACCEPT tcp -- anywhere anywhere tcp dpt:ftp

Chain ufw-user-limit (0 references)
target prot opt source destination
LOG all -- anywhere anywhere limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] '
REJECT all -- anywhere anywhere reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target prot opt source destination
ACCEPT all -- anywhere anywhere

Chain ufw-user-logging-forward (0 references)
target prot opt source destination

Chain ufw-user-logging-input (0 references)
target prot opt source destination

Chain ufw-user-logging-output (0 references)
target prot opt source destination

Chain ufw-user-output (1 references)
target prot opt source destination
So I tried this.
> 
asjmm@asjmm-Saviour:~$ smbclient -L ROMULUS
Enter asjmm's password:
Connection to ROMULUS failed (Error NT_STATUS_CONNECTION_REFUSED)
asjmm@asjmm-Saviour:~$ ps -ef|grep mbd
root 1179 1 0 13:39 ? 00:00:00 smbd -F
root 1288 1179 0 13:39 ? 00:00:00 smbd -F
root 1815 1 0 13:40 ? 00:00:00 nmbd -D
asjmm 2878 2747 0 14:28 pts/0 00:00:00 grep --color=auto mbd
Next this.
> 
asjmm@asjmm-Saviour:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.cm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::225:22ff:fe11:916e%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.69 bcast=192.168.1.255 netmask=255.255.255.0
Enter asjmm's password:
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1d>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1b>
resolve_wins: Attempting wins lookup for name SAVIOUR<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1b>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
asjmm@asjmm-Saviour:~$ nautilus smb://192.168.1.70
asjmm@asjmm-Saviour:~$ nautilus smb://192.168.1.70
asjmm@asjmm-Saviour:~$ nautilus smb://192.168.1.51
asjmm@asjmm-Saviour:~$ samba smb://192.168.1.70
The program 'samba' is currently not installed. You can install it by typing:
sudo apt-get install samba4
So next.
> 
asjmm@asjmm-Saviour:~$ sudo restart nmbd
[sudo] password for asjmm:
nmbd start/running, process 2955
asjmm@asjmm-Saviour:~$ uname -a
Linux asjmm-Saviour 2.6.35-30-generic #54-Ubuntu SMP Tue Jun 7 18:41:54 UTC 2011 x86_64 GNU/Linux
> 
asjmm@asjmm-Saviour:~$ cat /etc/hostname
asjmm-Saviour
asjmm@asjmm-Saviour:~$ cat /etc/host
cat: /etc/host: No such file or directory
asjmm@asjmm-Saviour:~$ cat /etc/hostname/interface
cat: /etc/hostname/interface: Not a directory
asjmm@asjmm-Saviour:~$ cat /etc/hostname/interfaces
cat: /etc/hostname/interfaces: Not a directory
> 
asjmm@asjmm-Saviour:~$ sudo apt-get install samba4
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
linux-headers-2.6.35-29 linux-headers-2.6.35-29-generic
chromium-browser-inspector
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
libdcerpc0 libgensec0 libldb0 libndr-standard0 libndr0 libregistry0
libsamba-hostconfig0 libsamba-util0 libtevent0 python-dnspython python-ldb
python-samba python-tdb samba-ldb-tools samba4-common-bin
Suggested packages:
bind9 phpldapadmin swat2
The following NEW packages will be installed:
libdcerpc0 libgensec0 libldb0 libndr-standard0 libndr0 libregistry0
libsamba-hostconfig0 libsamba-util0 libtevent0 python-dnspython python-ldb
python-samba python-tdb samba-ldb-tools samba4 samba4-common-bin
0 upgraded, 16 newly installed, 0 to remove and 2 not upgraded.
Need to get 7,897kB of archives.
After this operation, 37.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libtevent0 amd64 0.9.9~git20100522-3ubuntu1 [24.5kB]
Get:2 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libldb0 amd64 1:0.9.13~git20100908-2ubuntu1 [95.5kB]
Get:3 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libsamba-hostconfig0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [39.2kB]
Get:4 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libsamba-util0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [344kB]
Get:5 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libndr0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [164kB]
Get:6 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libndr-standard0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [789kB]
Get:7 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libgensec0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [1,159kB]
Get:8 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libregistry0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [87.9kB]
Get:9 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe libdcerpc0 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [1,183kB]
Get:10 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick-updates/main python-dnspython all 1.8.0-1ubuntu0.1 [91.3kB]
Get:11 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe python-ldb amd64 1:0.9.13~git20100908-2ubuntu1 [25.5kB]
Get:12 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe python-tdb amd64 1.2.1-2 [12.9kB]
Get:13 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe python-samba amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [1,664kB]
Get:14 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe python-samba amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [1,664kB]
Get:15 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe samba-ldb-tools amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [92.5kB]
Get:16 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe samba4-common-bin all 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [12.8kB]
Get:17 [http://ubuntu.retrosnub.co.uk/ubuntu/](http://ubuntu.retrosnub.co.uk/ubuntu/) maverick/universe samba4 amd64 4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1 [2,112kB]
Fetched 7,412kB in 4min 18s (28.7kB/s)
Preconfiguring packages ...
Selecting previously deselected package libtevent0.
(Reading database ... 219125 files and directories currently installed.)
Unpacking libtevent0 (from .../libtevent0_0.9.9~git20100522-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libldb0.
Unpacking libldb0 (from .../libldb0_1%3a0.9.13~git20100908-2ubuntu1_amd64.deb) ...
Selecting previously deselected package libsamba-hostconfig0.
Unpacking libsamba-hostconfig0 (from .../libsamba-hostconfig0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libsamba-util0.
Unpacking libsamba-util0 (from .../libsamba-util0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libndr0.
Unpacking libndr0 (from .../libndr0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libndr-standard0.
Unpacking libndr-standard0 (from .../libndr-standard0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgensec0.
Unpacking libgensec0 (from .../libgensec0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libregistry0.
Unpacking libregistry0 (from .../libregistry0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libdcerpc0.
Unpacking libdcerpc0 (from .../libdcerpc0_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-dnspython.
Unpacking python-dnspython (from .../python-dnspython_1.8.0-1ubuntu0.1_all.deb) ...
Selecting previously deselected package python-ldb.
Unpacking python-ldb (from .../python-ldb_1%3a0.9.13~git20100908-2ubuntu1_amd64.deb) ...
Selecting previously deselected package python-tdb.
Unpacking python-tdb (from .../python-tdb_1.2.1-2_amd64.deb) ...
Selecting previously deselected package python-samba.
Unpacking python-samba (from .../python-samba_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package samba-ldb-tools.
Unpacking samba-ldb-tools (from .../samba-ldb-tools_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package samba4-common-bin.
Unpacking samba4-common-bin (from .../samba4-common-bin_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_all.deb) ...
Selecting previously deselected package samba4.
Unpacking samba4 (from .../samba4_4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libtevent0 (0.9.9~git20100522-3ubuntu1) ...
Setting up libldb0 (1:0.9.13~git20100908-2ubuntu1) ...
Setting up python-dnspython (1.8.0-1ubuntu0.1) ...
Setting up python-ldb (1:0.9.13~git20100908-2ubuntu1) ...
Setting up python-tdb (1.2.1-2) ...
Setting up samba4-common-bin (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libndr0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libndr-standard0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libsamba-hostconfig0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libsamba-util0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libgensec0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libdcerpc0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up samba-ldb-tools (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up libregistry0 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Setting up python-samba (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
Processing triggers for python-central ...
Setting up samba4 (4.0.0~alpha13+git+bzr12984.dfsg1-0ubuntu1) ...
* Starting Samba 4 daemon samba Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
[ OK ]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
asjmm@asjmm-Saviour:~$ name resolve order = bcast host lmhosts wins
No command 'name' found, did you mean:
Command 'named' from package 'bind9' (main)
Command 'namei' from package 'util-linux' (main)
Command 'lame' from package 'lame' (universe)
Command 'cname' from package 'cfs' (universe)
Command 'uname' from package 'coreutils' (main)
Command 'nama' from package 'nama' (universe)
Command 'mame' from package 'mame' (universe)
Command 'nam' from package 'nam' (universe)
[COLOR=Red]name: command not found[/COLOR]
> 
asjmm@asjmm-Saviour:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.cm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::225:22ff:fe11:916e%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.69 bcast=192.168.1.255 netmask=255.255.255.0
Enter asjmm's password:
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1d>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name SAVIOUR<0x1b>
resolve_wins: Attempting wins lookup for name SAVIOUR<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name SAVIOUR<0x1b>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not openunable to mount location failed to retrieve list from server file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
asjmm@asjmm-Saviour:~$
I have been reading up on another thread, that's where most of my input has come from.  threads and trying to solve the problem myself. Getting nowhere.
I'm beging to think that this is not just one problem, but 2 or three. Router setup??? My system??? 
Routers are a LinksysWAG-160N, direct to BB.
And a BT Home hub 2 linked to linksys via RJ45.
Both running wifi, BT one for my sons DS, the other for Sys4 & 5. All others wired.
I want to upgrade the UBUNTU 11, but need to sort out these problems first.
Not knowing enough about UBUNTU is driving me mad.
So, now calling for help.
Cheers
Andy

Now I'm getting this?
> 
Could not display "network:///".
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.


PERMISSIONS...The Permissions of "SMB" could not be determined.

---

### Post by capscrew on 2011-06-18
> **9000cse said:**
> Hi,I keep getting this, ever time I try to map a shared drive on other systems with my small network. 'unable to mount location failed to retrieve list from server'. This used to work.
Main System UNBUNTU 10.10, GNOME ver. 2.32
Sys2 Windows XP Pro, SP3
Sys3 Windows XP Home SP3
Sys4 Windows XP Home SP3
Sys5 Windows 7

Mine is used as a server for the above, and also for me to work on.
For some reason, I keep getting permission failure.
Setting up a share on sys2. sys3, sys4, sys5 can see and read it. My main sys cannot.
None of the systems can see the Main one & the main one cannot read any of the others.

So I tried this.
Next this.
So next.
I have been reading up on another thread, that's where most of my input has come from.  threads and trying to solve the problem myself. Getting nowhere.
I'm beging to think that this is not just one problem, but 2 or three. Router setup??? My system??? 
Routers are a LinksysWAG-160N, direct to BB.
And a BT Home hub 2 linked to linksys via RJ45.
Both running wifi, BT one for my sons DS, the other for Sys4 & 5. All others wired.
I want to upgrade the UBUNTU 11, but need to sort out these problems first.
Not knowing enough about UBUNTU is driving me mad.
So, now calling for help.
Cheers
Andy

Now I'm getting this?


PERMISSIONS...The Permissions of "SMB" could not be determined.

When you use the *QUOTE button * instead of the* CODE button *the above is what I get.  I'm not going to take the time to re-enter your work.

I will tell you that you have installed Samba v4 over Samba v3.  This is not what you want to do.  Samba v4 is Alpha experimental at this stage.  It is intended to replace Windows Server AD domains.

A lot of your errors are from mistyping so we need to work on that.  You can either **[COLOR="Red"]Edit your post[/COLOR]** or repost it again using the [COLOR="Purple"]**CODE BLOCKS (# button)**[/COLOR].

Rest assured you are either going to purge Samba4 from Ubuntu or reinstall the whole OS so you can install Samba3.

---

