---
title: "Samba Sharing - Failed to retrieve..."
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by PeggySue on 2012-08-13
I have two computers, both new installs of 12.04.  One called vostro the other asus.  No windows machines in sight!

After installing Samba on both I was getting the "Failed to retrieve share list from server message" when trying to access vostro.

I followed a number of threads and made numerous changes (which I tried to reverse) and am now in an unknown state so I need to diagnose where I am from the error messages.

On asus I can access the shared folder on asus (itself) but can't access vostro.
On vostro I get the "failed to retrieve" message when trying to open WORKGROUP.

On vostro I get the following code showing that asus (192.168.0.103) can be seen but not vostro itself (192.168.0.102):
```
peter@vostro:~$ smbclient -d3 -L 192.168.0.102
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::219:b9ff:fe81:5797%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.101 bcast=192.168.0.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter peter's password: 
Connecting to 192.168.0.102 at port 445
Connecting to 192.168.0.102 at port 139
Error connecting to 192.168.0.102 (No route to host)
Connection to 192.168.0.102 failed (Error NT_STATUS_HOST_UNREACHABLE)



peter@vostro:~$ smbclient -d3 -L 192.168.0.103
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::219:b9ff:fe81:5797%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.0.101 bcast=192.168.0.255 netmask=255.255.255.0
Client started (version 3.6.3).
Enter peter's password: 
Connecting to 192.168.0.103 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (asus server (Samba, Ubuntu))
	dataAsus        Disk      
	print$          Disk      Printer Drivers
	Stylus-Photo-RX620 Printer   EPSON Stylus Photo RX620
	Photosmart_5510 Printer   HP 5510
	data Asus       Disk      
Connecting to 192.168.0.103 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	ASUS                 asus server (Samba, Ubuntu)
	VOSTRO               vostro server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP         
```

I believe the error lies in vostro but am at a loss where to look now.  Even removing samba and reinstalling didn't help which is odd because I have never had a problem with Samba on any previous version.  Any pointers would be most welcome.

---

### Post by rukiaEnix on 2012-08-13
Check if port 445 and 139 are open at the vostro

---

### Post by PeggySue on 2012-08-13
> **rukiaEnix said:**
> Check if port 445 and 139 are open at the vostro

I think this says they are open:
```
peter@vostro:~$ netstat -anltp | grep "LISTEN"
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
peter@vostro:~$ 

```

---

### Post by rukiaEnix on 2012-08-13
Have you tried using localhost instead of your assigned IP?

---

### Post by PeggySue on 2012-08-13
> **rukiaEnix said:**
> Have you tried using localhost instead of your assigned IP?

smbclient -d3 -L localhost gave sensible results on vostro 
smbclient -d3 -L 192.168.0.102 doesn't.  And neither machine will open the shared folders on the other.

So there appears to be a host name issue.  I have tried adding netios name = vostro to smb.conf but that was a shot in the dark that didn't work.  Is there a "hosts allow" feature some where?

I can't think where I should be looking.  I really need a site that gives a tutorial on how Samba works!

---

### Post by rukiaEnix on 2012-08-13
Please search for this section at your samba configuration file:

```

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes


```
Uncomment the line interfaces and set your IP and interface to bind the service to that IP and not to localhost.
And change bind interfaces only to yes.
Let's see if that works.

---

### Post by PeggySue on 2012-08-13
I added "interfaces = 192.168.0.102 eth0" and uncommented the "bind interfaces only = yes" but neither the IP or localhost would respond to "smbclient -d3 -L xxxxx".
The restart of nmdb failed so I rebooted the machine to be sure.

I will have another search tomorrow.  A new day a new hope!

---

### Post by PeggySue on 2012-08-14
I have had another shot at getting samba to link my two 12.04 computers but have only one more clue:
Using PyNeighborhood I am able to link from vostro to asus but I only see the blank directory not any of the files in it.  I wrote a text file to the directory on asus and it can be seen on both machines but as a folder not a file!
Other things I tried include a fresh install of 12.04 then samba only and using the smb.conf file from ubuntu 10.10 which works on 10.10 but not 12.04 also I opened up the share to guests - still no go.
Unless any one has any other ideas I will have to use Pyneighborhood to mount the share or I might use fstab but the computers are often not on at the same time.
Either way - thanks for your support rukiaEnix.

---

### Post by PeggySue on 2012-08-15
In case anyone is researching the same issue; 

I gave up on samba and went to nfs.  Initially this didn't work either but my problem was that I have two routers and a laptop which has 2 MAC codes, one for ethernet, one for wireless.  I didn't have the routers set up to assign the IP addresses correctly.  I fixed this and nfs works a dream.  (not much help if you have any windows machines)  Samba still doesn't work even with the IPs sorted out.

---

