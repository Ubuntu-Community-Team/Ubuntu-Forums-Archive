---
title: "samba broken? I reinstalled samba"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2013-01-20
as I kept getting samba crashes on boots.
Now, I dont see any crashes, BUT cant connect to any windows shares.
All the window7 boxes can explore other windows7 shares.
All the the PC's are on the 192.168.1.xxx lan network.

Ubuntu sees the machines but can not browse shares.
Ubuntu can not connect to server windows file shares
Windows7 firewalls are off

Is there some other way to do file sharing instead of samba?

I seem to get lots of issues with samba, from time to time mostly in my history it does not work.
I just wish it would work.

first picture shows errors which after a PURGE reinstall of samba, I no longer get.

second picture shows what happens in browse network

---

### Post by sdowney717 on 2013-01-20
oddly that Tricia-pc can see my ubuntu scott-p5qc shares while scott-pc can not.

scott-pc shows the machine name but then says network path does not exist

---

### Post by sdowney717 on 2013-01-20
you can see iptables are not blocking anything
```
scott@scott-P5QC:~$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 65504 packets, 29M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 66309 packets, 11M bytes)
 pkts bytes target     prot opt in     out     source               destination         
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2013-01-20
After letting it sit for a while, scott-pc can browse the ubuntu shares, I dont like it, crazy, unreliable.
scott-p5qc still can not browse any windows shares.

---

### Post by sdowney717 on 2013-01-20
just checked again and scott-pc cant browse shares.
see what I mean by untrustworthy?

so what is my crazy ubuntu pc doing?

---

### Post by sdowney717 on 2013-01-20
diggin a deeper hole, tried sharing another folder in Nautilus and get this error

```
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Pipe broken.
```

---

### Post by sdowney717 on 2013-01-20
following some bug, I tried the suggestions here

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/592610)

using the samba gui, added a share. then samba crashed

---

### Post by sdowney717 on 2013-01-20
I used synaptic and completely purged everything to do with samba.
rebooted
followed this guide
[http://www.jonathanmoeller.com/screed/?p=3608](http://www.jonathanmoeller.com/screed/?p=3608)

I got it all back, except scott-pc when clicked continues to say

"Failed to retrieve share list from server"

scott-pc is sharing files onto tricia-pc just fine

those 2 are win7 pc.

---

### Post by sdowney717 on 2013-01-20
Solved, It was the win7 pc needing to be rebooted


```
scott@scott-P5QC:~$ sudo smbclient -L 192.168.1.106
Enter root's password: 
protocol negotiation failed: NT_STATUS_INSUFFICIENT_RESOURCES
scott@scott-P5QC:~$ sudo smbclient -L 192.168.1.107
Enter root's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	test            Disk      
	IPC$            IPC       IPC Service (scott-P5QC server (Samba, Ubuntu))
	HP-LaserJet-4000-Series Printer   HP LaserJet 4000 Series
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	SCOTT-P5QC           scott-P5QC server (Samba, Ubuntu)
	SCOTT-PC             
	TRICIA-PC            

	Workgroup            Master
	---------            -------
	WORKGROUP            SCOTT-P5QC
scott@scott-P5QC:~$ sudo smbtree
Enter root's password: 
WORKGROUP
	\\TRICIA-PC      		
		\\TRICIA-PC\Users          	
		\\TRICIA-PC\IPC$           	Remote IPC
		\\TRICIA-PC\C$             	Default share
		\\TRICIA-PC\ADMIN$         	Remote Admin
	\\SCOTT-PC       		
	\\SCOTT-P5QC     		scott-P5QC server (Samba, Ubuntu)
		\\SCOTT-P5QC\HP-LaserJet-4000-Series	HP LaserJet 4000 Series
		\\SCOTT-P5QC\IPC$           	IPC Service (scott-P5QC server (Samba, Ubuntu))
		\\SCOTT-P5QC\test           	
		\\SCOTT-P5QC\print$         	Printer Drivers
scott@scott-P5QC:~$ sudo smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::222:15ff:fe54:faa6%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.107 bcast=192.168.1.255 netmask=255.255.255.0
Enter root's password: 
Connecting to host=192.168.1.107
Connecting to 192.168.1.107 at port 445
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
Got a positive name query response from 192.168.1.107 ( 192.168.1.107 )
Connecting to host=192.168.1.107
Connecting to 192.168.1.107 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
Connecting to host=192.168.1.107
Connecting to 192.168.1.107 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\TRICIA-PC      		
Connecting to host=TRICIA-PC
Connecting to 192.168.1.105 at port 445
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
		\\TRICIA-PC\Users          	
		\\TRICIA-PC\IPC$           	Remote IPC
		\\TRICIA-PC\C$             	Default share
		\\TRICIA-PC\ADMIN$         	Remote Admin
	\\SCOTT-PC       		
Connecting to host=SCOTT-PC
Connecting to 192.168.1.106 at port 445
**failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES**
	\\SCOTT-P5QC     		scott-P5QC server (Samba, Ubuntu)
Connecting to host=SCOTT-P5QC
Connecting to 192.168.1.107 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SCOTT-P5QC\HP-LaserJet-4000-Series	HP LaserJet 4000 Series
		\\SCOTT-P5QC\IPC$           	IPC Service (scott-P5QC server (Samba, Ubuntu))
		\\SCOTT-P5QC\test           	
		\\SCOTT-P5QC\print$         	Printer Drivers
scott@scott-P5QC:~$ 

```
rebooted windows pc and now it works, I had some property pages open on the windows PC.


```
scott@scott-P5QC:~$ sudo smbtree
Enter root's password: 
WORKGROUP
	\\TRICIA-PC      		
		\\TRICIA-PC\Users          	
		\\TRICIA-PC\IPC$           	Remote IPC
		\\TRICIA-PC\C$             	Default share
		\\TRICIA-PC\ADMIN$         	Remote Admin
	\\SCOTT-PC       		
		\\SCOTT-PC\Videos         	
		\\SCOTT-PC\video          	
		\\SCOTT-PC\vid2           	
		\\SCOTT-PC\Users          	
		\\SCOTT-PC\sharetest1     	
		\\SCOTT-PC\share1         	
		\\SCOTT-PC\IPC$           	Remote IPC
		\\SCOTT-PC\C$             	Default share
		\\SCOTT-PC\ADMIN$         	Remote Admin
	\\SCOTT-P5QC     		scott-P5QC server (Samba, Ubuntu)
		\\SCOTT-P5QC\HP-LaserJet-4000-Series	HP LaserJet 4000 Series
		\\SCOTT-P5QC\IPC$           	IPC Service (scott-P5QC server (Samba, Ubuntu))
		\\SCOTT-P5QC\test           	
		\\SCOTT-P5QC\print$         	Printer Drivers
scott@scott-P5QC:~$ 

```

[B][SIZE="4"]smbtree -d3 showed no error anymore!
```
scott@scott-P5QC:~$ sudo smbtree -d3[/SIZE][/B]
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::222:15ff:fe54:faa6%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.107 bcast=192.168.1.255 netmask=255.255.255.0
Enter root's password: 
Connecting to host=192.168.1.107
Connecting to 192.168.1.107 at port 445
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
Got a positive name query response from 192.168.1.107 ( 192.168.1.107 )
Connecting to host=192.168.1.107
Connecting to 192.168.1.107 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
Connecting to host=192.168.1.107
Connecting to 192.168.1.107 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\TRICIA-PC      		
Connecting to host=TRICIA-PC
Connecting to 192.168.1.105 at port 445
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
		\\TRICIA-PC\Users          	
		\\TRICIA-PC\IPC$           	Remote IPC
		\\TRICIA-PC\C$             	Default share
		\\TRICIA-PC\ADMIN$         	Remote Admin
	\\SCOTT-PC       		
Connecting to host=SCOTT-PC
Connecting to 192.168.1.106 at port 445
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
		\\SCOTT-PC\Videos         	
		\\SCOTT-PC\video          	
		\\SCOTT-PC\vid2           	
		\\SCOTT-PC\Users          	
		\\SCOTT-PC\sharetest1     	
		\\SCOTT-PC\share1         	
		\\SCOTT-PC\IPC$           	Remote IPC
		\\SCOTT-PC\C$             	Default share
		\\SCOTT-PC\ADMIN$         	Remote Admin
	\\SCOTT-P5QC     		scott-P5QC server (Samba, Ubuntu)
Connecting to host=SCOTT-P5QC
Connecting to 192.168.1.107 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SCOTT-P5QC\HP-LaserJet-4000-Series	HP LaserJet 4000 Series
		\\SCOTT-P5QC\IPC$           	IPC Service (scott-P5QC server (Samba, Ubuntu))
		\\SCOTT-P5QC\test           	
		\\SCOTT-P5QC\print$         	Printer Drivers
scott@scott-P5QC:~$ 

```

---

