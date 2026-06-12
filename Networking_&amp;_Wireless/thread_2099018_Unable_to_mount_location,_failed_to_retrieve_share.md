---
title: "Unable to mount location, failed to retrieve share list from server"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by Ausghostdog on 2012-12-28
Hey all,
Running 12.04 and have been having nothing but issues with connecting with my Windows 7 machine (GHOSTDOG-PC) 

It would work for a while then stop, then work again and stop and always stopped in the middle of moving a folder between the two systems. 

The computer is showing up in the network browser but when I click on it it gives me the error of "Unable to mount location, failed to retrieve share list from server"

I tried 
> gksudo gedit /etc/hosts   and add computer ip address and name in hosts file. Save and exit.
  Sample ip and name:  
  192.168.0.69    GHOSTDOG-pc I also tried 
> so off to /etc/samba and we sudo pico smb.conf
  The name resolve order uses hosts files first and broadcasts last and it is commented out! Maybe we change that to:
  name resolve order = bcast host   and then restart the servers with service smbd restart and service nmbd restart
Using SMBtree -d3 I get 
> ghostdog@ghostdog-VirtualBox:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::a00:27ff:fedd:1ac0%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.71 bcast=192.168.0.255 netmask=255.255.255.0
Enter ghostdog's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.70 ( 192.168.0.70 )
Connecting to host=192.168.0.70
Connecting to 192.168.0.70 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.70 ( 192.168.0.70 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.70 ( 192.168.0.70 )
Connecting to host=192.168.0.70
Connecting to 192.168.0.70 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.70 ( 192.168.0.70 )
Connecting to host=192.168.0.70
Connecting to 192.168.0.70 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\TIM-PC                 
Connecting to host=TIM-PC
resolve_lmhosts: Attempting lmhosts lookup for name TIM-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TIM-PC<0x20>
resolve_wins: Attempting wins lookup for name TIM-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name TIM-PC<0x20>
resolve_hosts: getaddrinfo failed for name TIM-PC [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name TIM-PC<0x20>
Got a positive name query response from 192.168.0.70 ( 192.168.0.70 )
Connecting to 192.168.0.70 at port 445
Doing spnego session setup (blob length=336)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\TIM-PC\Users              
        \\TIM-PC\IPC$               Remote IPC
        \\TIM-PC\C$                 Default share
        \\TIM-PC\ADMIN$             Remote Admin
    \\GHOSTDOG-PC            
Connecting to host=GHOSTDOG-PC
resolve_lmhosts: Attempting lmhosts lookup for name GHOSTDOG-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name GHOSTDOG-PC<0x20>
resolve_wins: Attempting wins lookup for name GHOSTDOG-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name GHOSTDOG-PC<0x20>
Connecting to 192.168.0.69 at port 445
failed negprot: NT_STATUS_INSUFFICIENT_RESOURCES
ghostdog@ghostdog-VirtualBox:~$ 
I'm stuck here any help would be awesome, I just want it to work so I can move my stuff around.

---

