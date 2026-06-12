---
title: "mount error: could not resolve address for Diskstation: Unknown error"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by ffonz on 2012-10-19
Hi,

I try to mount my NAS onto Ubuntu 12.04. This is my situation:
```
$ smbtree
WORKGROUP
    \\PX-EH                  PX-EH
        \\PX-EH\lp                 
        \\PX-EH\ADMIN$             IPC Service (PX-EH)
        \\PX-EH\IPC$               IPC Service (PX-EH)
        \\PX-EH\Guest              
        \\PX-EH\disk               LAN disk
    \\DISKSTATION            
        \\DISKSTATION\IPC$               IPC Service ()
        \\DISKSTATION\home               home
        \\DISKSTATION\homes              user home
        \\DISKSTATION\NetBackup          System default shared folder
        \\DISKSTATION\Share              DiskStation 212

```Then I try this
```
$ sudo smbmount //Diskstation/home samba
mount error: could not resolve address for Diskstation: Unknown error

```I even tried Diskstation with capitals and with non-capitals, but no success.
When I do
```
$ nmblookup -R -U <<IP-address>> diskstation
querying diskstation on  <<IP-address>>
 <<IP-address>> diskstation<00>

```It seems there are some non-printable odd characters behind 'diskstation'. 

With the PX-EH nas, I have the same problems, so it is not caused by the others side.

I don't want to type an IP-address. I want to use names, that's what they're for.

How can I mount my NAS with its name?
And if I need to add the name to some hosts file, why can I browse the samba drives with Nautilus without such a hosts file?

---

### Post by bab1 on 2012-10-20
> **ffonz said:**
> Hi,

I try to mount my NAS onto Ubuntu 12.04.  ...I try this
```
$ sudo smbmount //Diskstation/home samba
mount error: could not resolve address for Diskstation: Unknown error

```
Where are you attempting to mount //Diskstation/home to?  The location *samba *seems incorrect.> 

```
$ nmblookup -R -U <<IP-address>> diskstation
querying diskstation on  <<IP-address>>
 <<IP-address>> diskstation<00>

```It seems there are some non-printable odd characters behind 'diskstation'. 
These are part of the NETBIOS protocol.  They identify the type of node (i.e server or master browser or client). > 
With the PX-EH nas, I have the same problems, so it is not caused by the others side.

How can I mount my NAS with its name?
And if I need to add the name to some hosts file, why can I browse the samba drives with Nautilus without such a hosts file?
I'll bet the mount command is incorrect.  ;-)  Where are you trying to mount //Diskstation/home to?  What's the mount point?

---

### Post by ffonz on 2012-10-21
Hi bab1,

'samba' is a directory in /mnt. So I try to be less ambiguous. Here is another attempt:
```
~$ sudo smbmount //Diskstation/home /mnt/samba
mount error: could not resolve address for Diskstation: Unknown error
~$ ls -l /mnt
total 4
drwxr-xr-x 2 root root 4096 Nov 12  2010 samba

```

Does the samba directory have the correct permissions?

---

### Post by bab1 on 2012-10-21
> **ffonz said:**
> Hi bab1,

'samba' is a directory in /mnt. So I try to be less ambiguous. Here is another attempt:
```
~$ sudo smbmount //Diskstation/home /mnt/samba
mount error: could not resolve address for Diskstation: Unknown error
~$ ls -l /mnt
total 4
drwxr-xr-x 2 root root 4096 Nov 12  2010 samba

```

Does the samba directory have the correct permissions?

The directory permissions are not a problem for mounting the share.  You are having a problem resolving the name.  What do you get with this command```
smbclient -L diskstation
```

The COMPUTER name is case insensitive so caps are not needed at the CLI on Ubuntu.

---

### Post by ffonz on 2012-10-22
Hi bab1,

This is the result:
```
~$ smbclient -L diskstation
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.8]

    Sharename       Type      Comment
    ---------       ----      -------
    Share           Disk      DiskStation 212
    NetBackup       Disk      System default shared folder
    homes           Disk      user home
    home            Disk      home
    IPC$            IPC       IPC Service ()
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.8]

    Server               Comment
    ---------            -------
    PX-EH                PX-EH
    DISKSTATION          

    Workgroup            Master
    ---------            -------
    WORKGROUP            PX-EH

```

---

### Post by bab1 on 2012-10-22
> **ffonz said:**
> Hi bab1,

This is the result:
```
~$ smbclient -L diskstation
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.8]

    Sharename       Type      Comment
    ---------       ----      -------
    Share           Disk      DiskStation 212
    NetBackup       Disk      System default shared folder
    homes           Disk      user home
    home            Disk      home
    IPC$            IPC       IPC Service ()
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.8]

    Server               Comment
    ---------            -------
    PX-EH                PX-EH
    DISKSTATION          

    Workgroup            Master
    ---------            -------
    WORKGROUP            PX-EH

```

This shows that the name is being resolved correctly.  I'll bet you need to use a more current mount command.  The command *smbmount *is part of the deprecated smbfs package.  The newer package CIFS-UTIL will work better.  The basic command is something like ```
mount -t cifs //SERVER/share /path/to/mountpoint -o options

or 

mount.cifs //SERVER/share /path/to/mountpoint -o options 
```

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.swerdna.net.au/susesambacifs.html") and [**._[COLOR="Blue"]here[/COLOR]_**]("http://linhost.info/2012/05/mount-a-network-share-in-linux-ubuntu/") for info.

---

### Post by ffonz on 2012-10-23
Hi bab1,

I forgot to mention that I already tried mount -t cifs, with the same result:
```
~$ sudo mount -t cifs //diskstation/home /mnt/samba
mount error: could not resolve address for diskstation: Unknown error

```

If I do
```
sudo mount -t cifs //192.168.0.2/home /mnt/samba
```
I am being asked for a password, so I can contact my NAS.

I am getting a little frustrated. This isn't the first time Ubuntu lets me down :sad:
If  nautilus can translate names to ip's (and mount them), why can't I do  it on a CLI?! Which command should translate the names to the ip's?

Regards,

ffonz

---

### Post by bab1 on 2012-10-23
> **ffonz said:**
> Hi bab1,

I forgot to mention that I already tried mount -t cifs, with the same result:
```
~$ sudo mount -t cifs //diskstation/home /mnt/samba
mount error: could not resolve address for diskstation: Unknown error

```

If I do
```
sudo mount -t cifs //192.168.0.2/home /mnt/samba
```
I am being asked for a password, so I can contact my NAS.

I am getting a little frustrated. This isn't the first time Ubuntu lets me down :sad:
If  nautilus can translate names to ip's (and mount them), why can't I do  it on a CLI?! Which command should translate the names to the ip's?

Regards,

ffonz

The  NETBIOS NAME DISKSTATION is being resolved by Samba.  You can see that by the smbclient command.  I'm sure that this will work too```
nmblookup diskstation
```

The mount command does have problems.  What is the output of ```
cat etc/hosts
```

---

### Post by ffonz on 2012-10-24
Hi bab1,

OK, thanks. The nmblookup command works. This is something I can start with.

The hosts file is
```
~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    alfons-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```I'm not so fond of adapting hosts files. As far as I know, then I have to manually adapt the hosts file on every machine in the network. Or are you thinking in a different direction?

Regards,

Alfons

---

### Post by bab1 on 2012-10-24
> **ffonz said:**
> Hi bab1,

OK, thanks. The nmblookup command works. This is something I can start with.

The hosts file is
```
~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    alfons-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```I'm not so fond of adapting hosts files. As far as I know, then I have to manually adapt the hosts file on every machine in the network. Or are you thinking in a different direction?

Regards,

Alfons

At this point it appears there is no DNS resolution.  We do have NETBIOS resolution because nmblookup works.  All Ubuntu hosts resolve hostnames by first looking in the hosts file.  If therre is no mapping then DNS is tried.  We can see if a hostname mapping in /etc/hosts works by mapping the host diskstation to the IP address in /etc/hosts like this```
127.0.0.1    localhost
127.0.1.1    alfons-laptop

# Temp mapping of Diskstation to its IP address
192.168.0.2  diskstation
```...If this works, it confirms that you do not have local DNS name services working.  

Try to mount the share via //diskstation/share  We shall see what happens with the temp config in your /etc/hosts file.  This is only a test right now.

---

### Post by ffonz on 2012-11-03
Hi bab1,

I did the test as you described, and I could contact my NAS. This is the result:
```
alfons@alfons-laptop:~$ sudo mount -t cifs //diskstation/home /mnt/samba
Password: 
mount error(13): Permission denied

```I still have to find out the account details as you can see, but that shouldn't be a problem. So I need to setup a DNS in my network?

Thanks,

Alfons

---

### Post by bab1 on 2012-11-03
> **ffonz said:**
> Hi bab1,

I did the test as you described, and I could contact my NAS. This is the result:
```
alfons@alfons-laptop:~$ sudo mount -t cifs //diskstation/home /mnt/samba
Password: 
mount error(13): Permission denied

```
it does appear that the there is no LAN DNS running (on your local network).  But you now know how to cure that.> 

I still have to find out the account details as you can see, but that shouldn't be a problem. 
Do you have a way to configure your Diskstation's users.  If this is just for you you might just allow everyone.> 
So I need to setup a DNS in my network?

Thanks,

Alfons

That's really a question only you can answer.  Technically no.  As you can see you can manually just add a mapping in all the /etc/hosts files of all your machines.  It becomes a problem when you have a lot of machines to add the mapping to.  With DNS you just add the mapping in one file on one system and it is available for all machines.  You might look into DNSmasq for a small network DNS.

---

### Post by ffonz on 2012-11-06
Thanks bab1 for the information.

I know now how to figure it out. 

Alfons

---

### Post by MonoAM on 2012-11-12
Hello,

I have exactly this same problem. However, I do find it hard to believe that I must have a local DNS server OR that I edit the /etc/hosts file in order to make it work. It just sounds way too primitive, manual and cumbersome. Besides, the machines I want to mount are laptops or other computers with dynamic IP addresses. So having a thing that converts names to static IP addresses is not really a solution.

Is there not really a way of mounting a server using the server's name other than by setting up a local DNS server? It really sounds too odd as smbtree, smbclient and nmblookup can clearly see the server via its name without employing DNS server of any kind. Surely this should be able to happen when mounting the server. Basically what I'm saying is that if there's NETBIOS resolution, then the mounting process should be able to work with that NETBIOS resolution.

---

### Post by bab1 on 2012-11-12
> **MonoAM said:**
> Hello,

I have exactly this same problem. However, I do find it hard to believe that I must have a local DNS server OR that I edit the /etc/hosts file in order to make it work. It just sounds way too primitive, manual and cumbersome. Besides, the machines I want to mount are laptops or other computers with dynamic IP addresses. So having a thing that converts names to static IP addresses is not really a solution.I'll bet you don't have the exact same problem, but rather the same symptoms.  All IP traffic that has a destination that is identified with a human readable name (i.e. destination, DESTINATION, etc.) must first be resolved to an IP address.  This is can be achived either by IP to hostname (FQDN) with DNS or its primative, hostnames, via /etc/hosts or by NETBIOS name to IP address with a WINS server or by broadcasting NETBIOS names.  In simple terms a chart would look like this```

IP to FQND (hostname) = DNS (hostname.domain.tld) 
IP to hostname = hosts via /etc/hosts (hostname)

NETBIOS name to IP address = WINS (NETBIOS name)
NETBIOS NAME TO IP address = broadcasts

```

Whether it's primitive or not is irrelevent.  It is what it is.  No one said that DNS names can't be resolved.  Most modern DNS iplimentations can do this.  This can be done by NETBIOS.  In fact resolving the NETBIOS name to a IP address was the original intention.  A dynamic address is not a problem as the NAME is mapped to whatever IP address the host is using.> 
Is there not really a way of mounting a server using the server's name other than by setting up a local DNS server? It really sounds too odd as smbtree, smbclient and nmblookup can clearly see the server via its name without employing DNS server of any kind. Surely this should be able to happen when mounting the server. Basically what I'm saying is that if there's NETBIOS resolution, then the mounting process should be able to work with that NETBIOS resolution.
It's more a matter of how the NETBIOS resolution is handled and whether you have control of the host that is resolving the NETBIOS names.  The OP was not in control of the NAS unit.  The most simple method for him was to resolve the IP address to that specific host via the /etc/hosts entry on his local host.  If you want to browse Samba shares then the hostname (or FQDN) must be resolved to the NETBIOS name.  ALL browisng is via NETBIOS names.  This is handled by the Samba daemon NMBD.  In that sense you are correct as the resolution is somewhat convoluted.  You can think of it as this```
hostname to NETBIOS name to IP address
```...that's really simplistic but it is basically right.

If you want to have dynamic IP addressing and use NETBIOS to resolve the COMPUTER name for Samba browsing see [**_[SIZE="2"][COLOR="Blue"]here[/COLOR][/SIZE]_**]("http://ubuntuforums.org/showthread.php?t=2072989").  

Read ALL of it before doing anything.  Ask questions if you don't understand.

---

### Post by MonoAM on 2012-11-13
Hi bab1,

Thanks for your help. Now I think I understand a little bit better how this works. I read the other thread you pointed to and yes, it looks like my problem is more similar to the one described in that thread. So, I followed the whole thread but it still doesn't work. The conclusion of that thread was that there was a problem in the (windows) client machine configuration that couldn't connect to the  (ubuntu) samba server machine. Well, it looks like I might have the same problem, except that in my case both machines are Ubuntu.

So, I have one server machine (which is just a laptop with a shared drive) on which I've made all the changes suggested in the tread you pointed me to, namely: 

```

netbios name = COMPUTER_NAME
# What naming service and in what order should we use to resolve host names
# to IP addresses
name resolve order = bcast

```

I made the same changes in the client computer (obviously the client's name), but without any success in mounting the servers' drive on the client machine.

Another question, how do you reload the smbd daemon as everytime I make a change I have to reboot the machine?

Thanks a lot in advance for your help!!!

A

---

### Post by bab1 on 2012-11-13
> **MonoAM said:**
> Hi bab1,

Thanks for your help. Now I think I understand a little bit better how this works. I read the other thread you pointed to and yes, it looks like my problem is more similar to the one described in that thread. So, I followed the whole thread but it still doesn't work. The conclusion of that thread was that there was a problem in the (windows) client machine configuration that couldn't connect to the  (ubuntu) samba server machine. Well, it looks like I might have the same problem, except that in my case both machines are Ubuntu.
Maybe, maybe not.  I would say you need to diagose  the problem rather than jumping to conclusions based on symptoms.> 

So, I have one server machine (which is just a laptop with a shared drive) on which I've made all the changes suggested in the tread you pointed me to, namely: 

```

netbios name = COMPUTER_NAME
# What naming service and in what order should we use to resolve host names
# to IP addresses
name resolve order = bcast

```

I made the same changes in the client computer (obviously the client's name), but without any success in mounting the servers' drive on the client machine.
What failed?  What error messages did you have? I suggest diagnosing one machine at a time.> 

Another question, how do you reload the smbd daemon as everytime I make a change I have to reboot the machine?
Everytime you reconfigure the smb.conf file you need to reload the smbd daemon.

Let's work only with the Samba server.  What is the output of this ```
smbtree -d3
```

What is the output of this```
cat /etc/samba/smb.conf
```

---

### Post by MonoAM on 2012-11-13
Hi,

> **bab1 said:**
> 
What failed?  What error messages did you have? 


So this is the command I run and the error I get:
```

sudo mount -t cifs //PHOENIX/hitachi /media/phoenix
mount error: could not resolve address for PHOENIX: Unknown error

```

PHOENIX is the samba server.

Outputs:
```
smbtree -d3
```

```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::211:43ff:fe4b:d6ec%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=fe80::212:f0ff:fe02:47bd%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.5 bcast=192.168.1.63 netmask=255.255.255.192
added interface eth0 ip=192.168.1.15 bcast=192.168.1.63 netmask=255.255.255.192
Enter amguerra's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.5 ( 192.168.1.15 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.1.15
Connecting to 192.168.1.15 at port 445
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
Got a positive name query response from 192.168.1.5 ( 192.168.1.15 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.5 ( 192.168.1.15 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.1.15
Connecting to 192.168.1.15 at port 445
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
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.5 ( 192.168.1.15 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.1.15
Connecting to 192.168.1.15 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\PHOENIX        		phoenix server (Samba, Ubuntu)
Connecting to host=PHOENIX
name_resolve_bcast: Attempting broadcast lookup for name PHOENIX<0x20>
Got a positive name query response from 192.168.1.5 ( 192.168.1.15 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to 192.168.1.15 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\PHOENIX\amguerra       	Home Directories
		\\PHOENIX\IPC$           	IPC Service (phoenix server (Samba, Ubuntu))
		\\PHOENIX\print$         	Printer Drivers
		\\PHOENIX\hitachi        	Hitachi external hard drive
		\\PHOENIX\homes          	Home Directories

```

```
cat /etc/samba/smb.conf
```

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

netbios name = PHOENIX
# previous line: alfredo added 13-Nov-2012
# What naming service and in what order should we use to resolve host names
# to IP addresses
# OLD:   name resolve order = bcast lmhosts host wins
   name resolve order = bcast

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



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.

security = user
username map = /e/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes
   writeable = Yes
   valid users = amguerra

[hitachi]
  comment = Hitachi external hard drive
  browseable = yes
  path = /media/HITACHI
  writeable = Yes
  valid users = amguerra

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

> **bab1 said:**
> 
Everytime you reconfigure the smb.conf file you need to reload the smbd daemon.


What's the command to do that?

---

### Post by bab1 on 2012-11-13
> **MonoAM said:**
> ...this is the command I run and the error I get:
```

sudo mount -t cifs //PHOENIX/hitachi /media/phoenix
mount error: could not resolve address for PHOENIX: Unknown error

```

PHOENIX is the samba server.

Outputs:
```
smbtree -d3
```

```
...

		\\PHOENIX\amguerra       	Home Directories
		\\PHOENIX\IPC$           	IPC Service (phoenix server (Samba, Ubuntu))
		\\PHOENIX\print$         	Printer Drivers
		\\PHOENIX\hitachi        	Hitachi external hard drive
		\\PHOENIX\homes          	Home Directories

```

```
cat /etc/samba/smb.conf
```

```
...
#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes
   writeable = Yes
   valid users = amguerra

[COLOR="Red"][B][hitachi]
  comment = Hitachi external hard drive
  browseable = yes
  path = /media/HITACHI
  writeable = Yes
  valid users = amguerra[/B][/COLOR]

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

...

```



What's the command to do that?

The smb.conf file looks fine until we get to this```
[homes]
   comment = Home Directories
   browseable = yes
   writeable = Yes
   valid users = amguerra

[B][COLOR="Red"][hitachi]
  comment = Hitachi external hard drive
  browseable = yes
  path = /media/HITACHI
  writeable = Yes
  valid users = amguerra[/COLOR][/B]

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S
```

I believe it should be this```

[homes]
   comment = Home Directories
   browseable = yes
   writeable = Yes
   valid users = amguerra

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

[B][COLOR="Red"][hitachi]
  comment = Hitachi external hard drive
  browseable = yes
  path = /media/HITACHI
  writeable = Yes
  valid users = amguerra[/COLOR][/B]
```

You will always have wierd problems when you create a share in the middle of another share.  I have put the share [hitachi] at the end (in red).

When the Samba daemon encounters a share name ([share]) it starts a new share and all the parameters are to that share until it encouters another share name definition ([share2]).  Additionally you have made the [homes] share browseable.  Did you mean to do that?  You also made the user amguerra the only valid user for **all** [homes] shares.  You should not do that.  Read this for the correct method```
# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S
```
In fact, you should read all of the comments to setup the [homes] share.  You can set up all users private home shares with 1 [homes] share.

I think we should stick to diagnosing one machine at a time here.  Although it appears that NETBIOS naming is working I'd like to be sure.  These are the incantations to reload Samba```
sudo service smbd restart
sudo service nmbd restart
```

From the host phoenix what do you get with these 2 commands```
smbclient -L phoenix
```...and ```
testparm -s
```

For completeness what is the output of these 2 commands```
hostname

```...and ```
cat /etc/hosts
```

I see that smbtree browses the network correctly.  I also regularly mount a Samba share via /etc/fstab so I know that part will work once we figure out what is going on with your naming services.

---

### Post by MonoAM on 2012-11-13
> **bab1 said:**
> 
You will always have wierd problems when you create a share in the middle of another share.  I have put the share [hitachi] at the end (in red).


I've placed the [hitachi] share at the end as indicated.

> **bab1 said:**
> 
Additionally you have made the [homes] share browseable.  Did you mean to do that?  You also made the user amguerra the only valid user for **all** [homes] shares.  You should not do that.  Read this for the correct method```
# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S
```
In fact, you should read all of the comments to setup the [homes] share.  You can set up all users private home shares with 1 [homes] share.


Well, I'm the only person who uses that machine, so I just wanted to *make sure that only my username can connect to the server*. I realise this is not the best practice, but since I'm the only user I thought that would be OK.

Here's the output to the commands you asked me to run:

```
amguerra@phoenix:~$ smbclient -L phoenix
Enter amguerra's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	homes           Disk      Home Directories
	hitachi         Disk      Hitachi external hard drive
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (phoenix server (Samba, Ubuntu))
	Canon-i560      Printer   Canon i560
	amguerra        Disk      Home Directories
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Server               Comment
	---------            -------
	PHOENIX              phoenix server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            PHOENIX
```


```
amguerra@phoenix:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[hitachi]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /e/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[homes]
	comment = Home Directories
	valid users = amguerra
	read only = No

[hitachi]
	comment = Hitachi external hard drive
	path = /media/HITACHI
	valid users = amguerra
	read only = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

```

```
amguerra@phoenix:~$ hostname
phoenix
```


```
amguerra@phoenix:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	phoenix

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Thanks!

---

### Post by bab1 on 2012-11-13
So far so good!  The host pheonix seems to be working fine.  Just to be sure, tell me what you get from ```
nmblookup phoenix
```... and confirm that you have this line in the smb.conf file on the host phoenix```
netbios name = phoenix
```

Now we need to ***move to a client machine***.  A host that you want to mount the share located on PHOENIX to the clients local file system. What is the hostname of that machine?  From that client what to you get from this command```
smbtree
```... and ```
smbclient -L phoenix
```

I assume you have no firewalls between these 2 hosts.  :-)

---

### Post by MonoAM on 2012-11-14
Here's the output from these commands on phoenix:

```

amguerra@phoenix:~$ nmblookup phoenix
querying phoenix on 192.168.1.63
192.168.1.15 phoenix<00>

```


In /etc/samba/smb.conf on phoenix I have:

```

netbios name = PHOENIX

```

I used to have PHOENIX in lower case before (i.e. phoenix) but that didn't work either. I can change it back to lowercase if you want to just to be sure...

Now, running commands on the client machine (isoflautox):

```

alfredo@isoflautox:~$ smbtree 
Enter alfredo's password: 
WORKGROUP
	\\PHOENIX        		phoenix server (Samba, Ubuntu)
		\\PHOENIX\Canon-i560     	Canon i560
		\\PHOENIX\IPC$           	IPC Service (phoenix server (Samba, Ubuntu))
		\\PHOENIX\print$         	Printer Drivers
		\\PHOENIX\hitachi        	Hitachi external hard drive
		\\PHOENIX\homes          	Home Directories

```

```

alfredo@isoflautox:~$ smbclient -L phoenix
Enter alfredo's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	homes           Disk      Home Directories
	hitachi         Disk      Hitachi external hard drive
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (phoenix server (Samba, Ubuntu))
	Canon-i560      Printer   Canon i560
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Server               Comment
	---------            -------
	PHOENIX              phoenix server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            PHOENIX

```


> **bab1 said:**
> 
I assume you have no firewalls between these 2 hosts.  :-)

No, the two machines are connected to the same router. By the way, the two machines are connected to the router via direct cable AND wifi. Not sure if that's important or not.
	
Thanks again! 
A.

---

### Post by bab1 on 2012-11-14
> **MonoAM said:**
> Here's the output from these commands on phoenix:

```

amguerra@phoenix:~$ nmblookup phoenix
querying phoenix on 192.168.1.63
192.168.1.15 phoenix<00>

```


In /etc/samba/smb.conf on phoenix I have:

```

netbios name = PHOENIX

```

I used to have PHOENIX in lower case before (i.e. phoenix) but that didn't work either. I can change it back to lowercase if you want to just to be sure...

Now, running commands on the client machine (isoflautox):

```

alfredo@isoflautox:~$ smbtree 
Enter alfredo's password: 
WORKGROUP
	\\PHOENIX        		phoenix server (Samba, Ubuntu)
		\\PHOENIX\Canon-i560     	Canon i560
		\\PHOENIX\IPC$           	IPC Service (phoenix server (Samba, Ubuntu))
		\\PHOENIX\print$         	Printer Drivers
		\\PHOENIX\hitachi        	Hitachi external hard drive
		\\PHOENIX\homes          	Home Directories

```

```

alfredo@isoflautox:~$ smbclient -L phoenix
Enter alfredo's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Sharename       Type      Comment
	---------       ----      -------
	homes           Disk      Home Directories
	hitachi         Disk      Hitachi external hard drive
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (phoenix server (Samba, Ubuntu))
	Canon-i560      Printer   Canon i560
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]

	Server               Comment
	---------            -------
	PHOENIX              phoenix server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	WORKGROUP            PHOENIX

```




No, the two machines are connected to the same router. By the way, the two machines are connected to the router via direct cable AND wifi. Not sure if that's important or not.
	
Thanks again! 
A.
So far everything looks great.  You should be able to browse the network and mount a share from phoenix on isoflautox.  Can you do that via Nautilus (GNOME)?

What version of Ubuntu are you using on isoflautox?

---

### Post by MonoAM on 2012-11-14
> **bab1 said:**
> So far everything looks great.  You should be able to browse the network and mount a share from phoenix on isoflautox.  Can you do that via Nautilus (GNOME)?

What version of Ubuntu are you using on isoflautox?

Yes, if I type smb://phoenix/hitachi for example on the location field in a folder explorer window in Ubuntu (not sure if that's nautilus or gnome, but it's the default thing it comes with Ubunt) from isoflautox it connects no problem. The only thing I cannot do is to mount the share as a traditional unix mount. The only reason I need to mount it that way is because not all software (esp. command line tools) is able to understand locations such as smb://phoenix/hitachi (which I find quite annoying to be honest, but that's a separate issue). 

isoflautox is running the latest version of Ubuntu (12.10). phoenix is running Ubuntu 10.04.4.

---

### Post by bab1 on 2012-11-14
> **MonoAM said:**
> Yes, if I type smb://phoenix/hitachi for example on the location field in a folder explorer window in Ubuntu (not sure if that's nautilus or gnome, but it's the default thing it comes with Ubunt) from isoflautox it connects no problem. 
I'll bet that you can browse the shares too.  GNOME is the desktop environment.  Nautilus is the file manager built into GNOME. > 
The only thing I cannot do is to mount the share as a traditional unix mount. 
This is most likely due to the fstab entry being wrong.  Sometimes the error codes aren't real clear.  I usually have to fiddle with it to get it right.> 
The only reason I need to mount it that way is because not all software (esp. command line tools) is able to understand locations such as smb://phoenix/hitachi (which I find quite annoying to be honest, but that's a separate issue).
Please expand upon this please.>  

isoflautox is running the latest version of Ubuntu (12.10). phoenix is running Ubuntu 10.04.4.
I have a setup  like this and I mount one share via fstab.  Here is what I use```
//SERVER/share / cifs user,username=xxxx,credentials=/path/to/cred/file,uid=xxxx,gid=xxx,nbrl,noauto,iocharset=utf8
```
This allows the mortal user (user) to mount the share and it is not mounted at boot time (noauto).  It also sets the uid and gid of the intended user as owner and groupuid, gid).  All of these are explained in the man pages```
man mount.cifs

man mount
```
If you don't have the *mount.cifs* man pages you should install the *cifs-utils* package.  Do you have this package installed?  Maybe this is the problem.

---

### Post by MonoAM on 2012-11-14
Hi,

> **bab1 said:**
> I'll bet that you can browse the shares too.  


Yes, that's right. 

> **bab1 said:**
> Please expand upon this please.
What I mean is that not all programs are able to understand a samba address. For example, you cannot run either of these commands:

```

cp file.txt smb://phoenix/hitachi
cp file.txt //phoenix/hitachi

```

Whereas on Windows (XP, Vista, 7) you can use the same UNC address \\phoenix\hitachi on ANY program and it just works, whether it's on the location field on Windows Explorer or a command like

```

copy file.txt \\phoenix\hitachi

```

I added this line to my fstab (based on yours), but doesn't seem to work. It doesn't give any error messages but the "mounted" directory is empty:
```
//PHOENIX/hitachi /media/phoenix cifs user,username=amguerra,credentials=/root/.cifscredentials_homefs_amguerra,uid=amguerra,gid=amguerra,nbrl,noauto,iocharset=utf8
```
I do have cifs-utils installed.

Thanks!
A.

---

### Post by bab1 on 2012-11-14
> **MonoAM said:**
> Hi,

> ...I'll bet that you can browse the shares too. 

Yes, that's right. 
So your original question about mounting a share without using DNS has been answered.  The real problem is you are having problems using fstab to mount the share.  Let's see what we can do about that.> 

What I mean is that not all programs are able to understand a samba address. For example, you cannot run either of these commands:

```

cp file.txt smb://phoenix/hitachi
cp file.txt //phoenix/hitachi

```

Whereas on Windows (XP, Vista, 7) you can use the same UNC address \\phoenix\hitachi on ANY program and it just works, whether it's on the location field on Windows Explorer or a command like

```

copy file.txt \\phoenix\hitachi

```

The UNC is not the same as a SMB mount.  In fact if you mounted a share at something like this /smb/test (//SERVER/share /smb/test) and had a subdir like this /smb/test/junk (junk is a subdir in the share) you could copy the file using the path (i.e. cp test.txt /smb/test/junk)  No need to use the Samba resource (e.g. //SERVER/share).

I added this line to my fstab (based on yours), but doesn't seem to work. It doesn't give any error messages but the "mounted" directory is empty:
```
//PHOENIX/hitachi /media/phoenix cifs user,username=amguerra,credentials=/root/.cifscredentials_homefs_amguerra,uid=amguerra,gid=amguerra,nbrl,noauto,iocharset=utf8
```
I do have cifs-utils installed.

Thanks!
A.

With the share unmounted what do you get with this command```
ls la /media/phoenix
```

What do you get from the same command with the share mounted?

Do you have a particular reason for using /media for mounting the shares?

---

### Post by MonoAM on 2012-11-14
Well I don't think any mounting is actually taking place. This is what I did: I commented out the line I added to my fstab file. Then I restarted the computer. Then I ran:
```

ls la /media/phoenix
ls: cannot access la: No such file or directory
/media/phoenix:

```

Then, I uncommented that line in fstab, ran sudo mount -a and then ran:
```

ls la /media/phoenix
ls: cannot access la: No such file or directory
/media/phoenix:

```

Also, if I mount manually I get:
```

sudo mount -t cifs //PHOENIX/hitachi /media/phoenix
mount error: could not resolve address for PHOENIX: Unknown error

```

And as usual, I can browse smb://phoenix/hitachi with Nautilus.

---

### Post by MonoAM on 2012-11-14
Just realised this is probably what you meant I should run:

Unmounted:
```

ls -la /media/phoenix/
total 8
drwxr-xr-x  2 root root 4096 Nov 12 23:25 .
drwxr-xr-x 10 root root 4096 Nov 12 23:25 ..

```

Mounted:
```

ls -la /media/phoenix/
total 8
drwxr-xr-x  2 root root 4096 Nov 12 23:25 .
drwxr-xr-x 10 root root 4096 Nov 12 23:25 ..

```

I also forgot to answer your other question:
> Do you have a particular reason for using /media for mounting the shares?
The only reason is that when you insert a USB memory stick you get it mounted under /media. So I thought I would just mount all removable and mountable drives there. Basically, the same location for all external disks. That's it.

---

### Post by bab1 on 2012-11-14
> **MonoAM said:**
> Just realised this is probably what you meant..
Oops!  My fault I left out the - (dash).  Let's try something.  With the share _*umounted*_ put a file in that directory.  We can do that like this```
touch /media/phoenix/test.txt
```
This puts a 0 byte file in that directory.  Check to see if it's there with; ls -la (with the dash) ;-)

Then mount the share and see if the file is still there.  You should NOT be able to see the file with the share mounted.> 

The only reason is that when you insert a USB memory stick you get it mounted under /media. So I thought I would just mount all removable and mountable drives there. Basically, the same location for all external disks. That's it.
The reason I ask is that the /media is a special directory for automounting removable media.  You can mount the share anywhere in the file system hierarchy.  I mount my Samba shares at /smb.  I have always mounted shares and general data outside of /home and never on /media or /mnt.  I use /mnt as a temporary mount location.  But to each his own.  I store web page files for my Apache install at /data.

---

### Post by MonoAM on 2012-11-15
So I tried this before mounting:
```
sudo touch /media/phoenix/test.txt
```

and file is there:

```

ls -la /media/phoenix/
total 8
drwxr-xr-x  2 root root 4096 Nov 15 23:38 .
drwxr-xr-x 10 root root 4096 Nov 12 23:25 ..
-rw-r--r--  1 root root    0 Nov 15 23:38 test.txt

```

After mounting:

```

ls -la /media/phoenix/
total 8
drwxr-xr-x  2 root root 4096 Nov 15 23:38 .
drwxr-xr-x 10 root root 4096 Nov 12 23:25 ..
-rw-r--r--  1 root root    0 Nov 15 23:38 test.txt

```

And file is still there. :(

---

### Post by bab1 on 2012-11-15
> **MonoAM said:**
> So I tried this before mounting:
```
sudo touch /media/phoenix/test.txt
```

and file is there:

```

ls -la /media/phoenix/
total 8
drwxr-xr-x  2 root root 4096 Nov 15 23:38 .
drwxr-xr-x 10 root root 4096 Nov 12 23:25 ..
-rw-r--r--  1 root root    0 Nov 15 23:38 test.txt

```

After mounting:

```

ls -la /media/phoenix/
total 8
drwxr-xr-x  2 root root 4096 Nov 15 23:38 .
drwxr-xr-x 10 root root 4096 Nov 12 23:25 ..
-rw-r--r--  1 root root    0 Nov 15 23:38 test.txt

```

And file is still there. :(

This means the share is not being mounted.  The file would be obscured with the share mounted at /media/phoenix.

Normally I would make the mount point (/media/phoenix) be owned by a group that all users can use.  Ubuntu has a group that does just this for Samba.  It is called *sambashare*.  You should already be a member.  You can check with this command ```
getent group |grep sambashare
```... you should be in that group.

To change the group ownership of the mount point we should use this command```
sudo chgrp sambashare /media/phoenix
```... check it using ```
ls -ld /media/phoenix
```

Now lets change the permissions on that mountpoint so you will have access ```
sudo chmod 775 /media/phoenix
```

Use this incantation to mount the share ```
sudo mount -t cifs //PHOENIX/hitachi  /media/phoenix -o username=amguerra

```

I notice your login is *alfredo* but your valid user is *amguerra*.  This may be part of the problem.  You need to be consistant in naming.  My local login and my share login are the same on all of my machines.

I have tested this on my network (using my server and share names).  I even used the mount point /media/phoenix.  It works as expected so you should have no problems mounting the share.

---

### Post by ffonz on 2012-11-17
Hi guys,

I also continued my journey. Maybe I can help with my results & solutions.

MonoAM, Bab1 mentioned it in message #15, but maybe a WINS server might fit your needs.  I never knew what a WINS server was until last week. If I understand it  correctly, it is some kind of DNS server for the NetBios protocol.

[Here]("http://cumptrnrd.wordpress.com/2012/02/20/configuring-an-ubuntu-debian-server-for-dns-dhcp-and-wins/") I found a page where they describe how to setup a WINS server.

I also created a small script to work around the error, called namelookup.sh:

```
#!/bin/sh
nmblookup $1 | grep "$1<00>" | cut -d" " -f0

```And I call the script like this:
```
mount -t cifs //$(./namelookup.sh phoenix)/disk samba
```

But as I said, it's only a work around.

For me the journey ends here, since I discovered that the software of my Synology NAS has a mounting option which can resolve samba/netbios names. So my problem is solved.

I hope this info could be of any help.

Success,

alfons

---

### Post by MonoAM on 2012-11-21
Hi there,

Sorry for the delay in replying.

Bab1: I tried your commands but they didn't work out. Here are the commands and the output:

```

ls -ld /media/phoenix
drwxr-xr-x 2 root sambashare 4096 Nov 15 23:38 /media/phoenix

sudo chmod 775 /media/phoenix

sudo mount -t cifs //PHOENIX/hitachi  /media/phoenix -o username=amguerra
mount error: could not resolve address for PHOENIX: Unknown error

```

> **bab1 said:**
> 
I notice your login is *alfredo* but your valid user is *amguerra*.  This may be part of the problem.  You need to be consistant in naming.  My local login and my share login are the same on all of my machines.


Yes, I know, this is a bit of an inconsistency on my part. Basically, my username on phoenix is amguerra whilst on my main computer (the client) is alfredo. That's why I need to connect as a different user on the share. Now, in theory that shouldn't be a problem. But yes, it's not ideal.

Alfons: Your workaround worked like a charm! Yes, it's just a workaround but it works and it's dynamic. So, I think I'll use that for now at least. Ideally I would like to make this thing work properly, but there doesn't seem to be a solution, or at least it's not obvious. Looks like it's one of those Ubuntu glitches that just occur for some reason and unless you are willing to spend A LOT of time you'll have to learn with it. And well, Alfons' workaround works fine for the time being.

Thanks a lot guys for your help!!! :)

P.S. Alfons: I had to correct the line of your script to this:
```
nmblookup $1 | grep "$1<00>" | cut -d" " -f1
```
got an error message from cut saying that "fields and positions are numbered from 1".

---

### Post by masgeeks on 2013-04-19
I had the same error mounting a share on my NAS from command line using cifs - I installed winbind and edited /etc/nsswitch.conf like so...  hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4  This worked for me.

---

### Post by sergey1369 on 2013-12-18
I've lost a lot of time to make ubuntu (kubuntu) cifs  working with android's samba file sharing.
It works great with Krusader, but not with cifs.utils. Forum does help, but not in one place. 
So I've put it all together here. Maybe it will be useful for someone else. 

My errors messages was:
 mount error: could not resolve address for SGN3: Unknown error
 cifs_mount failed w/return code = -5
 cifs_mount failed w/return code = -111
 cifs_mount failed w/return code = -112


I've fixed it with this changes:

1. /etc/samba/smb.conf:
name resolve order = **bcast** 

2. /etc/nsswitch.conf
hosts:          files **wins** dns

3. /etc/fstab
//SGN3/sdcard       /home/sergey/pda    cifs    username=sergey,uid=sergey,user,**sec=ntlmv2**         0       0

And now it works as expected:
(ku:~)$ mount pda
Password for sergey@//SGN3/sdcard: 
(ku:~)$ umount pda

---

### Post by chanklor-m on 2014-09-15
> **bab1 said:**
> At this point it appears there is no DNS resolution.  We do have NETBIOS resolution because nmblookup works.  All Ubuntu hosts resolve hostnames by first looking in the hosts file.  If therre is no mapping then DNS is tried.  We can see if a hostname mapping in /etc/hosts works by mapping the host diskstation to the IP address in /etc/hosts like this```
127.0.0.1    localhost
127.0.1.1    alfons-laptop

# Temp mapping of Diskstation to its IP address
192.168.0.2  diskstation
```...If this works, it confirms that you do not have local DNS name services working.  

Try to mount the share via //diskstation/share  We shall see what happens with the temp config in your /etc/hosts file.  This is only a test right now.


This solution worked for me, thanks a lot.

I had the same problem, added that line to /etc/hosts and worked perfectly. But I'm afraid that if my computer changes ip it will stop working since it's hardcoded into the /etc/hosts. Do you know how to correct this?

Thanks!

---

### Post by JohnnyComeL8ly on 2014-09-15
You are only accessing the NAS locally, right?  Do you have a router?  If that is the case, then you can find out how to make your router give a "static" DHCP address to the NAS.  After doing that, then you can either update [FONT=courier new]/etc/hosts[/FONT] to match the assigned IP from the router, or have the router give a hostname to the NAS so that you can access it from other devices without editing their hosts file (if even possible, e.g., iPad).

I should be able to help with the router setup as long as I know which one it is. :KS

---

