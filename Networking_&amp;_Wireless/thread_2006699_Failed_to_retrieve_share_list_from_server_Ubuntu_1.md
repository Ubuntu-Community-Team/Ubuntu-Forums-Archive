---
title: "Failed to retrieve share list from server Ubuntu 12.04"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by pappo on 2012-06-19
I have tried a number of "solutions" and I still cannot see other computers from my Eeepc running Ubuntu 12.04.
All I can see is my own PC
Here is an output from some familiar samba command line entries:

pappo@Eeepc:~$ **smbclient** -L 192.168.1.43
Enter pappo's password: 
session setup failed: NT_STATUS_LOGON_FAILURE

pappo@Eeepc:~$ **findsmb**

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.43    EEEPC          [MSHOME] [Unix] [Samba 3.6.3]

pappo@Eeepc:~$ **sudo smbtree**
[sudo] password for pappo: 
added interface wlan0 ip=fe80::4a5d:60ff:fe4a:5f9d%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.43 bcast=192.168.1.255 netmask=255.255.255.0

Here is my smb.conf file:
========================================================
pappo@Eeepc:~$ cat /etc/samba/smb.conf
[global]
   workgroup = MSHOME
   name resolve order = bcast host
   server string = Ubuntu12
   hosts allow =  192.168.1.
;   printcap name = /etc/printcap
   load printers = yes
   printing = lprng
;   guest account = smbuser
   log file = /var/log/samba/%m.log
   ;max log size = 0
   security = user
   encrypt passwords = true
   smb passwd file = /etc/samba/smbpasswd
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   dns proxy = no 
   log level = 2
   debug level = 2

[Ubuntu_Home]
   path = /home/pappo
   writable = yes
   valid users = pappo,smbuser
   browseable = yes
   public = yes

[Toshiba300]
   path = /media/Toshiba300
   writable = yes
   valid users = pappo,smbuser
   browseable = yes
   public = yes

pappo@Eeepc:~$ 
==============================================================

Here are some other entries I have in my files which I added after reading other forum posts.  They **DID NOT** fix my problem either.

name resolve order = lmhosts wins bcast host

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Any help would be appreciated.

---

### Post by rukiaEnix on 2012-06-19
The IP (192.168.1.43) you want to see is in a windows domain?

---

### Post by pappo on 2012-06-19
> **rukiaEnix said:**
> The IP (192.168.1.43) you want to see is in a windows domain?

My home systems consists of four (4)PC's.  
1.  Windows 7 Ultimate 64bit 
2.  Ubuntu server (my homemade NAS) running Ubuntu 11.10
3.  Eeepc running Ubuntu 12.04
4.  Wife's PC running Ubuntu 11.10

I use MSHOME as my workgroup name.

Before the Ubuntu 12.04 install, I was running Mint12 on the Eeepc and did not have any problem seeing other PC's when I selected "browse network" in Nautilus.  Nothing changed except my change to Ubuntu 12.04 on this Eeepc.

---

### Post by bab1 on 2012-06-19
> **pappo said:**
> My home systems consists of four (4)PC's.  
1.  Windows 7 Ultimate 64bit 
2.  Ubuntu server (my homemade NAS) running Ubuntu 11.10
3.  Eeepc running Ubuntu 12.04
4.  Wife's PC running Ubuntu 11.10

I use MSHOME as my workgroup name.

Before the Ubuntu 12.04 install, I was running Mint12 on the Eeepc and did not have any problem seeing other PC's when I selected "browse network" in Nautilus.  Nothing changed except my change to Ubuntu 12.04 on this Eeepc.
The original question to you was > The IP (192.168.1.43) you want to see is in a windows domain?  So... is this address the NAS? 

Actually what are the addresses of the 4 hosts you mentioned e.g  ```
1.  Windows 7 Ultimate 64bit 
2.  Ubuntu server (my homemade NAS) running Ubuntu 11.10
3.  Eeepc running Ubuntu 12.04
4.  Wife's PC running Ubuntu 11.10
```

Part of your answer is right here```
pappo@Eeepc:~$ smbclient -L 192.168.1.43
Enter pappo's password:
**[COLOR="Red"]session setup failed: NT_STATUS_LOGON_FAILURE[/COLOR]**

```

---

### Post by pappo on 2012-06-19
> **bab1 said:**
> The original question to you was   So... is this address the NAS? 
**[COLOR="red"]NO NAS is 192.168.1.100[/COLOR]**
Actually what are the addresses of the 4 hosts you mentioned e.g  ```
1.  Windows 7 Ultimate 64bit [B[COLOR="Red"]192.168.1.101[/COLOR]][/B]
2.  Ubuntu server (my homemade NAS) running Ubuntu 11.10 **[COLOR="Red"]192.168.1.100[/COLOR]]**
3.  Eeepc running Ubuntu 12.04  **[COLOR="Red"]192.168.1.43[/COLOR]]**
4.  Wife's PC running Ubuntu 11.10
```**[COLOR="Red"]192.168.1.200[/COLOR]]**

Part of your answer is right here```
pappo@Eeepc:~$ smbclient -L 192.168.1.43
Enter pappo's password:
**[COLOR="Red"]session setup failed: NT_STATUS_LOGON_FAILURE[/COLOR]**

```
**[COLOR="red"]Please explain why this is part of my answer.[/COLOR]**

---

### Post by bab1 on 2012-06-19
> **pappo said:**
> **[COLOR="red"]Please explain why this is part of my answer.[/COLOR]**

You have authentication problems.

Here is what I get when I do the same thing (local host)```

smbclient -L 192.168.1.3
Enter bab's password: 
Domain=[BEACH] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	Public          Disk      Public Share
	Backup          Disk      Backup Data Share
	IPC$            IPC       IPC Service (malibu)
	bab             Disk      Home Directory
Domain=[BEACHBEES] OS=[Unix] Server=[Samba 3.4.7]

	Server               Comment
	---------            -------
	MALIBU               malibu

	Workgroup            Master
	---------            -------
	BEACH                MALIBU

```

Post the results of this```
smbtree -d3
```

---

### Post by pappo on 2012-06-19
> **bab1 said:**
> You have authentication problems.

Here is what I get when I do the same thing (local host)```

smbclient -L 192.168.1.3
Enter bab's password: 
Domain=[BEACH] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	Public          Disk      Public Share
	Backup          Disk      Backup Data Share
	IPC$            IPC       IPC Service (malibu)
	bab             Disk      Home Directory
Domain=[BEACHBEES] OS=[Unix] Server=[Samba 3.4.7]

	Server               Comment
	---------            -------
	MALIBU               malibu

	Workgroup            Master
	---------            -------
	BEACH                MALIBU

```

Post the results of this```
smbtree -d3
```pappo@Eeepc:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::4a5d:60ff:fe4a:5f9d%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.43 bcast=192.168.1.255 netmask=255.255.255.0
Enter pappo's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
Connecting to host=192.168.1.43
Connecting to 192.168.1.43 at port 445
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
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
Connecting to host=192.168.1.43
Connecting to 192.168.1.43 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
MSHOME
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
Connecting to host=192.168.1.43
Connecting to 192.168.1.43 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WIN7X64        		
Connecting to host=WIN7X64
name_resolve_bcast: Attempting broadcast lookup for name WIN7X64<0x20>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\WIN7X64\win7x64_C      	
		\\WIN7X64\Users          	
		\\WIN7X64\print$         	Printer Drivers
		\\WIN7X64\IPC$           	Remote IPC
		\\WIN7X64\HP C4680       	HP Photosmart C4600 series
		\\WIN7X64\C$             	Default share
		\\WIN7X64\ADMIN$         	Remote Admin
	\\UBUNTU10-SERVER		ubuntu10-server server (Samba, Ubuntu)
Connecting to host=UBUNTU10-SERVER
name_resolve_bcast: Attempting broadcast lookup for name UBUNTU10-SERVER<0x20>
Got a positive name query response from 192.168.1.100 ( 192.168.1.100 )
Connecting to 192.168.1.100 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\UBUNTU10-SERVER\ubuntu-server phil-home	
		\\UBUNTU10-SERVER\HP-C4680       	HP-C4680
		\\UBUNTU10-SERVER\Backup300      	
		\\UBUNTU10-SERVER\Backup500      	
		\\UBUNTU10-SERVER\print$         	Printer Drivers
		\\UBUNTU10-SERVER\IPC$           	IPC Service (ubuntu10-server server (Samba, Ubuntu))
	\\KAREN-DESKTOP  		Karen_Ubuntu10
Connecting to host=KAREN-DESKTOP
name_resolve_bcast: Attempting broadcast lookup for name KAREN-DESKTOP<0x20>
Got a positive name query response from 192.168.1.200 ( 192.168.1.200 )
Connecting to 192.168.1.200 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
		\\KAREN-DESKTOP\IPC$           	IPC Service (Karen_Ubuntu10)
		\\KAREN-DESKTOP\Backups        	
		\\KAREN-DESKTOP\Ubuntu_Home    	
	\\EEEPC          		Ubuntu12
Connecting to host=EEEPC
name_resolve_bcast: Attempting broadcast lookup for name EEEPC<0x20>
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
Connecting to 192.168.1.43 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\EEEPC\Eeepc-pappo    	
		\\EEEPC\IPC$           	IPC Service (Ubuntu12)
		\\EEEPC\Toshiba300     	
		\\EEEPC\Ubuntu_Home    	
pappo@Eeepc:~$

---

### Post by bab1 on 2012-06-19
> **pappo said:**
> pappo@Eeepc:~$ ```
smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::4a5d:60ff:fe4a:5f9d%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.43 bcast=192.168.1.255 netmask=255.255.255.0
Enter pappo's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
Connecting to host=192.168.1.43
Connecting to 192.168.1.43 at port 445
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
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
Connecting to host=192.168.1.43
Connecting to 192.168.1.43 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
MSHOME
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
Connecting to host=192.168.1.43
Connecting to 192.168.1.43 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WIN7X64        		
Connecting to host=WIN7X64
name_resolve_bcast: Attempting broadcast lookup for name WIN7X64<0x20>
Got a positive name query response from 192.168.1.101 ( 192.168.1.101 )
Connecting to 192.168.1.101 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\WIN7X64\win7x64_C      	
		\\WIN7X64\Users          	
		\\WIN7X64\print$         	Printer Drivers
		\\WIN7X64\IPC$           	Remote IPC
		\\WIN7X64\HP C4680       	HP Photosmart C4600 series
		\\WIN7X64\C$             	Default share
		\\WIN7X64\ADMIN$         	Remote Admin
	\\UBUNTU10-SERVER		ubuntu10-server server (Samba, Ubuntu)
Connecting to host=UBUNTU10-SERVER
name_resolve_bcast: Attempting broadcast lookup for name UBUNTU10-SERVER<0x20>
Got a positive name query response from 192.168.1.100 ( 192.168.1.100 )
Connecting to 192.168.1.100 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\UBUNTU10-SERVER\ubuntu-server phil-home	
		\\UBUNTU10-SERVER\HP-C4680       	HP-C4680
		\\UBUNTU10-SERVER\Backup300      	
		\\UBUNTU10-SERVER\Backup500      	
		\\UBUNTU10-SERVER\print$         	Printer Drivers
		\\UBUNTU10-SERVER\IPC$           	IPC Service (ubuntu10-server server (Samba, Ubuntu))
	\\KAREN-DESKTOP  		Karen_Ubuntu10
Connecting to host=KAREN-DESKTOP
name_resolve_bcast: Attempting broadcast lookup for name KAREN-DESKTOP<0x20>
Got a positive name query response from 192.168.1.200 ( 192.168.1.200 )
Connecting to 192.168.1.200 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
		\\KAREN-DESKTOP\IPC$           	IPC Service (Karen_Ubuntu10)
		\\KAREN-DESKTOP\Backups        	
		\\KAREN-DESKTOP\Ubuntu_Home    	
	\\EEEPC          		Ubuntu12
Connecting to host=EEEPC
name_resolve_bcast: Attempting broadcast lookup for name EEEPC<0x20>
Got a positive name query response from 192.168.1.43 ( 192.168.1.43 )
Connecting to 192.168.1.43 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\EEEPC\Eeepc-pappo    	
		\\EEEPC\IPC$           	IPC Service (Ubuntu12)
		\\EEEPC\Toshiba300     	
		\\EEEPC\Ubuntu_Home    	
pappo@Eeepc:~$
```

It seems to have negotiated the smbtree command okay.  When posting output please put the data between ```
 blocks. You can use the #icon at the top of the editor (near the quote icon) to do this.

Post the output of the command you used for smbclient (if you didn't use a password then don't use one now).[CODE]smbclient -d3 -L 192.168.1.43
```

---

### Post by pappo on 2012-06-20
> **bab1 said:**
> I
Post the output of the command you used for smbclient (if you didn't use a password then don't use one now).```
smbclient -d3 -L 192.168.1.43
```

```
pappo@Eeepc:~$ smbclient -d3 -L 192.168.1.43
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::4a5d:60ff:fe4a:5f9d%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.43 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter pappo's password: 
Connecting to 192.168.1.43 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	Ubuntu_Home     Disk      
	Toshiba300      Disk      
	IPC$            IPC       IPC Service (Ubuntu12)
	Eeepc-pappo     Disk      
Connecting to 192.168.1.43 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	EEEPC                Ubuntu12
	KAREN-DESKTOP        Karen_Ubuntu10
	UBUNTU10-SERVER      ubuntu10-server server (Samba, Ubuntu)
	WIN7X64              

	Workgroup            Master
	---------            -------
	MSHOME  
```       EEEPC
pappo@Eeepc:~$

---

### Post by bab1 on 2012-06-20
> **pappo said:**
> ```
pappo@Eeepc:~$ smbclient -d3 -L 192.168.1.43
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::4a5d:60ff:fe4a:5f9d%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.1.43 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter pappo's password: 
Connecting to 192.168.1.43 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	Ubuntu_Home     Disk      
	Toshiba300      Disk      
	IPC$            IPC       IPC Service (Ubuntu12)
	Eeepc-pappo     Disk      
Connecting to 192.168.1.43 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	EEEPC                Ubuntu12
	KAREN-DESKTOP        Karen_Ubuntu10
	UBUNTU10-SERVER      ubuntu10-server server (Samba, Ubuntu)
	WIN7X64              

	Workgroup            Master
	---------            -------
	MSHOME  
```       EEEPC
pappo@Eeepc:~$

Now all seems to be working.  Did it heal itself?  The host now seems to be able to see the other hosts on the network.  Can you now browse these shares with the GUI?

---

### Post by pappo on 2012-06-20
> **bab1 said:**
> Now all seems to be working.  Did it heal itself?  The host now seems to be able to see the other hosts on the network.  Can you now browse these shares with the GUI?

```
NO.  Same "failed to retrieve ... etc. etc." message when I first selected Browse Network in Nautilus.  But, when I selected "Browse Network" a second time the MSHOME folder popped up and then I could see all my other PC's.. ????  Go figure ??.

Thanks for all your help.  I never really changed anything.  Do you know why it just started working ?  Is it because of the "d3" modifiers you added to the smbtree command ?
```

---

### Post by bab1 on 2012-06-20
> **pappo said:**
> NO.  Same "failed to retrieve ... etc. etc." message when I first selected Browse Network in Nautilus.  But, when I selected "Browse Network" a second time the MSHOME folder popped up and then I could see all my other PC's.. ????  Go figure ??.

Thanks for all your help.  I never really changed anything.  Do you know why it just started working ?  Is it because of the "d3" modifiers you added to the smbtree command ?

The error, if we want to call it that, is due to the host (EEEPC) failing to find the list of available shares.  These are held in the Master Browse List (_MSBROWSE_ ).  Sometimes this list is *temporarily *unavailable.  It is usually remade in a short time.  But you will also get this error message when there is a permanent problem, usually caused by misconfiguration.

What I did with the -d3 switch was to turn on debug display to the screen to see what (if any) problems you were having.  The -d3 switch is NOT a cure in itself.

I did not cure it, but we did provide a pause... as the system rebuilt the Master Browse List.  I see this error message every once in a while when first starting up the my network hosts.

---

### Post by pappo on 2012-06-20
> **bab1 said:**
> The error, if we want to call it that, is due to the host (EEEPC) failing to find the list of available shares.  These are held in the Master Browse List (_MSBROWSE_ ).  Sometimes this list is *temporarily *unavailable.  It is usually remade in a short time.  But you will also get this error message when there is a permanent problem, usually caused by misconfiguration.

What I did with the -d3 switch was to turn on debug display to the screen to see what (if any) problems you were having.  The -d3 switch is NOT a cure in itself.

I did not cure it, but we did provide a pause... as the system rebuilt the Master Browse List.  I see this error message every once in a while when first starting up the my network hosts.

```
Well I am glad it is working now.  Again, thank you for taking the time walk me through the repair/solution.  I learned a lot in the process.  How do I mark the thread solved?
```

---

### Post by bab1 on 2012-06-20
> **pappo said:**
> Well I am glad it is working now.  Again, thank you for taking the time walk me through the repair/solution.  I learned a lot in the process.  How do I mark the thread solved?

:)  The code blocks were only for the code (output of the commands), not your normal reply.

At the top of the page under the heading "Thread Tools" is a link to mark the thread "solved".

---

### Post by pappo on 2012-06-20
> **bab1 said:**
> :)  The code blocks were only for the code (output of the commands), not your normal reply.

At the top of the page under the heading "Thread Tools" is a link to mark the thread "solved".

Again, thanks for the instruction.  I marked it solved.

---

