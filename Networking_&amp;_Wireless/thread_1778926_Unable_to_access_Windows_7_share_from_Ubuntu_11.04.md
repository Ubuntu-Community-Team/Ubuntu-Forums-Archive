---
title: "Unable to access Windows 7 share from Ubuntu 11.04"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by foetus66 on 2011-06-09
I've read several threads on the subject but all seem to be related to problems I'm not having, or at least the troubleshooting loses me at some point where my results have differed too many times to ignore.

So, I'd like to start from scratch if anyone can help me.  I'm simply trying to access a folder shared on Windows 7.  The Windows computers on the network have no trouble accessing it with the username and password -- both XP and Win7 systems are able to access the share.

I can try going to Places > Network > Windows Network    -- but I get "**Unable to mount location.** Failed to retrieve share list from server"
I can try going to Places > Connect to Server  -- but I get "**Cannot display location "smb://192.168.1.8/".** Failed to retrieve share list from server."  (tried both computer name and local IP)

I currently have Windows Firewall turned off on the server for troubleshooting purposes.

I'm pretty new to Linux still -- are there any commands I can report on from Terminal that will help steer me in the right direction?  

Thank you.

---

### Post by capscrew on 2011-06-09
> **foetus66 said:**
> I've read several threads on the subject but all seem to be related to problems I'm not having, or at least the troubleshooting loses me at some point where my results have differed too many times to ignore.

So, I'd like to start from scratch if anyone can help me.  I'm simply trying to access a folder shared on Windows 7.  The Windows computers on the network have no trouble accessing it with the username and password -- both XP and Win7 systems are able to access the share.

I can try going to Places > Network > Windows Network    -- but I get "**Unable to mount location.** Failed to retrieve share list from server"
I can try going to Places > Connect to Server  -- but I get "**Cannot display location "smb://192.168.1.8/".** Failed to retrieve share list from server."  (tried both computer name and local IP)

I currently have Windows Firewall turned off on the server for troubleshooting purposes.

I'm pretty new to Linux still -- are there any commands I can report on from Terminal that will help steer me in the right direction?  

Thank you.

Sure...

```
smbtree -d3
```

and

```
smbclient -d3 -L  192.168.1.8
```

These may not reveal the exact cure, but it is close to what you tried with  debugging turned on.

---

### Post by foetus66 on 2011-06-09
That first one  gave me a long list of things that didn't sound good.

[B]$ smbtree -d3
[/B]```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan1 ip=fe80::214:a5ff:fe0f:9358%wlan1 bcast=fe80::ffff:ffff:ffff:ffff%wlan1 netmask=ffff:ffff:ffff:ffff::
added interface eth0:avahi ip=169.254.10.154 bcast=169.254.255.255 netmask=255.255.0.0
added interface wlan1 ip=192.168.1.18 bcast=192.168.1.255 netmask=255.255.255.0
Enter blip's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
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
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[A^[[A^[[A^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[A^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[A^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[A^[[A^[[A^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
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
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory

```**smbclient -d3 -L  192.168.1.8**
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan1 ip=fe80::214:a5ff:fe0f:9358%wlan1 bcast=fe80::ffff:ffff:ffff:ffff%wlan1 netmask=ffff:ffff:ffff:ffff::
added interface eth0:avahi ip=169.254.10.154 bcast=169.254.255.255 netmask=255.255.0.0
added interface wlan1 ip=192.168.1.18 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.5.8).
Enter blip's password: 
Connecting to 192.168.1.8 at port 445
Connecting to 192.168.1.8 at port 139
session request to 192.168.1.8 failed (Called name not present)
Connecting to 192.168.1.8 at port 445
Connecting to 192.168.1.8 at port 139
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
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE

```
Seems like an awful lot of files and/or directories missing in that first one.  Am I missing something that needs to be installed?

---

### Post by pricetech on 2011-06-09
You don't mention how you installed Samba.  I recommend installing via Synaptic and searching for "system-config-samba" which installs Samba plus a dandy GUI configuration tool since you'll probably want to share back the other way at some point.

Once that's done and you have say a sample share or test share set up on your Linux box, open a terminal and type:

```
sudo smbpasswd -a username
```

Where "username" is your username.  You'll be prompted first for your password by sudo, then prompted twice more by smbpasswd.

Try again after that and see what happens.

---

### Post by capscrew on 2011-06-09
> **foetus66 said:**
> That first one  gave me a long list of things that didn't sound good.

[B]$ smbtree -d3
[/B]```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan1 ip=fe80::214:a5ff:fe0f:9358%wlan1 bcast=fe80::ffff:ffff:ffff:ffff%wlan1 netmask=ffff:ffff:ffff:ffff::
added interface eth0:avahi ip=169.254.10.154 bcast=169.254.255.255 netmask=255.255.0.0
added interface wlan1 ip=192.168.1.18 bcast=192.168.1.255 netmask=255.255.255.0
Enter blip's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
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
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[A^[[A^[[A^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[A^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[A^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
^[[A^[[A^[[A^[[A^[[A^[[Atdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
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
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory

```**smbclient -d3 -L  192.168.1.8**
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan1 ip=fe80::214:a5ff:fe0f:9358%wlan1 bcast=fe80::ffff:ffff:ffff:ffff%wlan1 netmask=ffff:ffff:ffff:ffff::
added interface eth0:avahi ip=169.254.10.154 bcast=169.254.255.255 netmask=255.255.0.0
added interface wlan1 ip=192.168.1.18 bcast=192.168.1.255 netmask=255.255.255.0
Client started (version 3.5.8).
Enter blip's password: 
Connecting to 192.168.1.8 at port 445
Connecting to 192.168.1.8 at port 139
session request to 192.168.1.8 failed (Called name not present)
Connecting to 192.168.1.8 at port 445
Connecting to 192.168.1.8 at port 139
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
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE

```
Seems like an awful lot of files and/or directories missing in that first one.  Am I missing something that needs to be installed?

Well that's just plain ugly.  All that for you to be a samba client?  Did you install Samba at all.  By what you say, this is one of those times when you DID NOT need to install anything.  To *access * shares on another machine you only need the samba client software which is installed by default.

It appears that you are running 2 interfaces on this host.  I see a wlan0 address and a a eth0 avahi assigned address.  Is this something you did on purpose.  Two active interfaces are never a good thing.

---

### Post by capscrew on 2011-06-09
> **pricetech said:**
> You don't mention how you installed Samba.  I recommend installing via Synaptic and searching for "system-config-samba" which installs Samba plus a dandy GUI configuration tool since you'll probably want to share back the other way at some point.

Once that's done and you have say a sample share or test share set up on your Linux box, open a terminal and type:

```
sudo smbpasswd -a username
```

Where "username" is your username.  You'll be prompted first for your password by sudo, then prompted twice more by smbpasswd.

Try again after that and see what happens.

Why is it whenever someone mentions shares that we think Samba server? The OP was very explicit. e.g. "I'm simply trying to access a folder shared on Windows 7."

Try and not muddy the water.

---

### Post by e79 on 2011-06-09
> **capscrew said:**
> Well that's just plain ugly.  All that for you to be a samba client?  Did you install Samba at all.  By what you say, this is one of those times when you DID NOT need to install anything.  To *access * shares on another machine you only need the samba client software which is installed by default.

It appears that you are running 2 interfaces on this host.  I see a wlan0 address and a a eth0 avahi assigned address.  Is this something you did on purpose.  Two active interfaces are never a good thing.

@ capscrew
The OP is using a laptop and is using its wireless card (192.168.1.1). His ethernet interface is also turned on but not configured/connected (169.254.10.154 is a self-assigned address by the wireless card itself because it was unable to find a DHCP server).

@ foetus66
Have you tried specifying the folder name of your share or just tried to connect with the IP (refer to the screenshot) ? 
As capscrew specified, the samba client is installed by default and should not need any tweaking to access a simple windows share.

---

### Post by capscrew on 2011-06-09
> **e79 said:**
> @ capscrew
The OP is using a laptop and is using its wireless card (192.168.1.1). His ethernet interface is also turned on but not configured/connected (169.254.10.154 is a self-assigned address by the wireless card itself because it was unable to find a DHCP server).

Yes, I know that.  I turn avahi off on my hosts.  What I don't know is what happens if the interface is up, and the interface is disconnected.  I would down the interface. > 

@ foetus66
Have you tried specifying the folder name of your share or just tried to connect with the IP (refer to the screenshot) ? 
As capscrew specified, the samba client is installed by default and should not need any tweaking to access a simple windows share.

---

### Post by pricetech on 2011-06-10
> **capscrew said:**
> Why is it whenever someone mentions shares that we think Samba server? The OP was very explicit. e.g. "I'm simply trying to access a folder shared on Windows 7."

Try and not muddy the water.

I'll try to avoid helping in the future.

---

### Post by foetus66 on 2011-06-11
> **e79 said:**
> 
The OP is using a laptop and is using its wireless card (192.168.1.1). His ethernet interface is also turned on but not configured/connected (169.254.10.154 is a self-assigned address by the wireless card itself because it was unable to find a DHCP server).

It's actually desktop machine -- it has a wireless PCI card installed and two completely separate Ethernet NICs, both on the motherboard. There is no network cable plugged into either of them.

> **e79 said:**
> 
Have you tried specifying the folder name of your share or just tried to connect with the IP (refer to the screenshot) ? 
As capscrew specified, the samba client is installed by default and should not need any tweaking to access a simple windows share.
Yep, I've tried everything I can think of in this dialogue box and get the same result when it can actually do the test,.

---

### Post by capscrew on 2011-06-11
> **foetus66 said:**
> It's actually desktop machine -- it has a wireless PCI card installed and two completely separate Ethernet NICs, both on the motherboard. There is no network cable plugged into either of them.


Yep, I've tried everything I can think of in this dialogue box and get the same result when it can actually do the test,.

How did you create the shares?

Post the output of ```
testparm-s
```

---

### Post by refayetbd on 2011-07-20
> **capscrew said:**
> How did you create the shares?

Post the output of ```
testparm-s
```

rezaur@rezaur-Aspire-5742Z:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Movies]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Movies]
    path = /media/Other/Movies
    guest ok = Yes

---

### Post by capscrew on 2011-07-20
> **refayetbd said:**
> rezaur@rezaur-Aspire-5742Z:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Movies]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[Movies]
    path = /media/Other/Movies
    guest ok = Yes

I thought this was just a Samba client accessing Windows shares.  It looks as if you are also sharing files from this host.  Is this correct?

What name do you want this machine to be identified as when you are browsing?  The hostname is too long to be used.  NetBIOS has a restriction of 15 characters.

---

### Post by Justin Buser on 2011-09-14
> **capscrew said:**
> I thought this was just a Samba client accessing Windows shares.  It looks as if you are also sharing files from this host.  Is this correct?

What name do you want this machine to be identified as when you are browsing?  The hostname is too long to be used.  NetBIOS has a restriction of 15 characters.

server string isn't the netbios name which defaults to the machine name if netbios name = WHATEVER isn't set.

The problem that he is having is caused by the fact that smbtree/smbclient inappropriately lookup the workgroup name as a domain name.  The following is the smb.conf I ended up with after spending hours trying to resolve this myself. The key was setting domain master = yes (even though the server isn't a domain controller)  

[global]
netbios name = PacketSlut
server string = Will do anal for data
workgroup = WORKGROUP
security = user
hosts allow = 10.0.0.
interfaces = eth1
bind interfaces only = yes
remote announce = 10.0.0.255
printcap name = /dev/null
load printers = no
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = yes
domain master = yes
preferred master = yes
domain logons = no
os level = 33
name resolve order = wins lmhosts bcast
wins support = yes
wins proxy = yes
obey pam restrictions = yes
enable spoolss = no
client plaintext auth = no
disable netbios = no
update encrypted = yes
pam password change = yes
passwd chat timeout = 120
username map = /etc/samba/smbusers
passdb backend = tdbsam
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
winbind cache time = 10

[homes]
comment = Home Directories
read only = no
browseable = no

---

### Post by Morbius1 on 2011-09-14
> Originally Posted by **capscrew**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11069497#post11069497")                 
                 [I]I thought this was just a Samba  client accessing Windows shares.  It looks as if you are also sharing  files from this host.  Is this correct?

What name do you want this machine to be identified as when you are  browsing?  The hostname is too long to be used.  NetBIOS has a  restriction of 15 characters.[/I]
> **Justin Buser said:**
> server string isn't the netbios name which  defaults to the machine name if netbios name = WHATEVER isn't set.That observation in at least this part of your post is correct ( although capscrew never mentioned anything about server string ). What you may not have noticed is the users machine name:
> rezaur-Aspire-5742ZIt's 19 characters long. It can only be 15 characters long as capscrew indicated. It can be fixed with a "netbios name" which looks like where capscrew was heading.

---

### Post by capscrew on 2011-09-14
> **Morbius1 said:**
> That observation in at least this part of your post is correct ( although capscrew never mentioned anything about server string ). What you may not have noticed is the users machine name:
It's 19 characters long. It can only be 15 characters long as capscrew indicated. It can be fixed with a "netbios name" which looks like where capscrew was heading.
@ Morbius1:
The "server string" is just a label that the user sees when browsing.  It has nothing to do with client lookup tools.  In the OP's case the "server string" uses the hostname (%h) as this label.

@Justin Buser:
The SMB client tools never use the workgroup name as "domain name" .  The workgroup name is a contrivance to group **//hosts/shares** by an arbitrary name (e.g. **sales **or **West Coast**).  Multiple workgroups won't affect lookups and illogical names won't affect lookups.  The only thing that the client needs to browse is the ability to see the *browse list* hosted on the Master Browser.  This ability to locate the Master Browser is by NetBIOS name resolving to IP address and that is why you need some sort of naming convention.  In a pure Windows environment this is all by NetBIOS.  In a Samba environment the *nmbd *daemon has the ability to resolve DNS (hostname) to NetBIOS names and then to IP address.

I notice that you have enabled this host to be a WINS server.  Are you using a multi segmented network?  For a simple LAN Samba recommends not using a WINS server.

Why do you have a parameter for winbind (winbind cache time = 10)?  If you are not using this host in a domain situation you don't need winbind at all.

---

