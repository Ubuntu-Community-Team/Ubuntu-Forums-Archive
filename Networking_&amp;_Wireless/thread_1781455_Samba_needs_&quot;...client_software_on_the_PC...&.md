---
title: "Samba needs &quot;...client software on the PC...&quot;"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by kevcoder on 2011-06-13
from Samba.org at [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

What software is this referring to??

[INDENT]5. Run the command nmblookup -B ACLIENT `*'.
You should get the PC's IP address back. If you do not, then the client software on the PC isn't installed correctly, or isn't started, or you got the name of the PC wrong.  [/INDENT]

---

### Post by Joe of loath on 2011-06-13
It's referring to the samba client (smbclient) :p

---

### Post by kevcoder on 2011-06-13
> **Joe of loath said:**
> It's referring to the samba client (smbclient) :p
OK so this is some type of ftp clone... but is it required for SAMBA to work? I don't it see it mentioned in any other how-to's... not even the one on samba.org.

I'm trying to open a ubuntu share to a number of WIN7 machines.

---

### Post by capscrew on 2011-06-13
> **kevcoder said:**
> OK so this is some type of ftp clone... but is it required for SAMBA to work? I don't it see it mentioned in any other how-to's... not even the one on samba.org.

What do you mean by required?  It is the command line interface to the Samba daemon ***smbd***.  Of course you need it, but you don't have to use it if you don't want to.  :-)> 

I'm trying to open a ubuntu share to a number of WIN7 machines.

Are you having problems doing that?  If so, what errors do you get?  Did you pass the first two steps?

[LIST]
[*] What did you get with ```
testparm -s
```
[*] Can you ping *all* hosts from **all** hosts?
[/LIST]

---

### Post by kevcoder on 2011-06-13
kevcoder00 is the Ubuntu box
KLSTRFK is the WIN7 box
for right now I want this share to be wide open requiring no permissions
I can ping both boxes from each other by name and ip (i added an entry  in both c:\windows\system32\driver\etc\hosts and /etc/hosts)

testparm -S
```

dev@kevcoder00:~$ testparm -S
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = METALWAVE
    netbios name = KLSTRFK
    security = SHARE
    lanman auth = Yes
    client lanman auth = Yes

[Share]
    comment = kevcoder00 file share
    path = /srv/samba/share
    read only = No
    create mask = 0777
    guest ok = Yes

```

smbclient -L kevcoder00
```

Domain=[METALWAVE] OS=[Unix] Server=[Samba 3.5.8]

    Sharename       Type      Comment
    ---------       ----      -------
    Share           Disk      kevcoder00 file share
    IPC$            IPC       IPC Service (Samba 3.5.8)
Domain=[METALWAVE] OS=[Unix] Server=[Samba 3.5.8]

    Server               Comment
    ---------            -------
    KLSTRFK              Samba 3.5.8

    Workgroup            Master
    ---------            -------
    METALWAVE            KLSTRFK

```

smbclient -L KLSTRFK
```

Domain=[KLSTRFK] OS=[Windows 7 Ultimate N 7601 Service Pack 1] Server=[Windows 7 Ultimate N 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    Fax - HP Officejet 6500 E710n-z Printer   Fax - HP Officejet 6500 E710n-z
    HP Officejet 6500 E710n-z Printer   HP Officejet 6500 E710n-z
    IPC$            IPC       Remote IPC
    METALWAVE_PUBLIC Disk      THE PUBLIC FOLDER
    metalwave_share Disk      
    print$          Disk      Printer Drivers
    Users           Disk      
session request to KLSTRFK failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

nmblookup -B kevcoder00 __SAMBA__
```

querying __SAMBA__ on 127.0.1.1
192.168.2.2 __SAMBA__<00>

```

nmblookup -d 2 '*'
```

rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
added interface eth0 ip=fe80::d227:88ff:fe19:ce11%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.2.2 bcast=192.168.2.255 netmask=255.255.255.0
querying * on 192.168.2.255
Got a positive name query response from 192.168.2.2 ( 192.168.2.2 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
192.168.2.2 *<00>

``` 
I stopped there

and finally my share permissions
dev@kevcoder00:/srv/samba$ ls -l
```

total 4
drwxr-xr-x 4 nobody nogroup 4096 2011-06-12 00:49 share

```

---

### Post by capscrew on 2011-06-13
> **kevcoder said:**
> kevcoder00 is the Ubuntu box
KLSTRFK is the WIN7 box
for right now I want this share to be wide open requiring no permissions
I can ping both boxes from each other by name and ip (i added an entry  in both c:\windows\system32\driver\etc\hosts and /etc/hosts)

Can the Ubuntu host kevcoder00 can ping itself by name?

My comments below will be in **[COLOR="Red"]red[/COLOR]**> 

testparm -S
```

dev@kevcoder00:~$ testparm -S
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = METALWAVE
    netbios name = KLSTRFK  **[COLOR="Red"]<--This should be the Samba server machine[/COLOR]**
    security = SHARE  **[COLOR="Red"]<-- This means Linux directory and file perms only[/COLOR]**
    lanman auth = Yes  **[COLOR="Red"]<-- This is for Win95/98[/COLOR]**
    client lanman auth = Yes **[COLOR="Red"]<-- Also for win95/98[/COLOR]**

[Share]
    comment = kevcoder00 file share
    path = /srv/samba/share
    read only = No
    create mask = 0777
    guest ok = Yes  **[COLOR="Red"]<- this is for security = user[/COLOR]**

```

smbclient -L kevcoder00 
```

Domain=[METALWAVE] OS=[Unix] Server=[Samba 3.5.8]

    Sharename       Type      Comment
    ---------       ----      -------
    Share           Disk      kevcoder00 file share
    IPC$            IPC       IPC Service (Samba 3.5.8)
Domain=[METALWAVE] OS=[Unix] Server=[Samba 3.5.8]

    Server               Comment
    ---------            -------
    KLSTRFK  **[COLOR="Red"]<--???[/COLOR]**            Samba 3.5.8 [B]

    Workgroup            Master
    ---------            -------
    METALWAVE            KLSTRFK [COLOR="Red"]**<-- Which machine is this? **[/COLOR]

```

smbclient -L KLSTRFK
```

Domain=[KLSTRFK] OS=[Windows 7 Ultimate N 7601 Service Pack 1] Server=[Windows 7 Ultimate N 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    Fax - HP Officejet 6500 E710n-z Printer   Fax - HP Officejet 6500 E710n-z
    HP Officejet 6500 E710n-z Printer   HP Officejet 6500 E710n-z
    IPC$            IPC       Remote IPC
    METALWAVE_PUBLIC Disk      THE PUBLIC FOLDER
    metalwave_share Disk      
    print$          Disk      Printer Drivers
    Users           Disk      
session request to KLSTRFK failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available **[COLOR="Red"]<--Why is this desabled?[/COLOR]**

```

nmblookup -B kevcoder00 __SAMBA__ 
```

querying __SAMBA__ on 127.0.1.1
192.168.2.2 __SAMBA__<00>  

```

rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
added interface eth0 ip=fe80::d227:88ff:fe19:ce11%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.2.2 bcast=192.168.2.255 netmask=255.255.255.0
querying * on 192.168.2.255
Got a positive name query response from 192.168.2.2 ( 192.168.2.2 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
192.168.2.2 *<00>
[/CODE] 
I stopped there

and finally my share permissions
dev@kevcoder00:/srv/samba$ ls -l
```

total 4
drwxr-xr-x 4 nobody nogroup 4096 2011-06-12 00:49 share

```

[LIST]
[*] I think should comment out the "netbios name = " section.  
[*] Comment out the lanman auth entries
[*] See if the nmbd daemon is running ```
pgrep -l mbd
```

[/LIST]

See if that works.  It might not, but it is a start.


What are the IP addresses of all the hosts involved.  On the Ubuntu host, can you post the output of ```
cat /etc/hosts
```
I really don't like using *[COLOR="Red"]security = share[/COLOR]* you loose Samba control of the share.

---

### Post by kevcoder on 2011-06-14
if I didn't already say this, I've been running linux for a full 4 months now although I work as a .Net developer.  So I understand the concepts, but have almost no idea where anything is in linux/unbuntu...

* ... at work now so this is from memory...*

I added a new user/group (Kevin/Kevin) to  that matches my WIN7 user and password

Correcting the netbios name in smb.conf now allows me to see the samba share in Nautilus. :)

I'll change security to user and remove those lines form smb.conf.  I assume that this means I should run ```
chown -R Kevin:Kevin /srv/samba/Share
``` and set a password for samba with ```
smbpasswd -a Kevin
```In the output from smbclient -L kevcoder00 KLSTRFK is the WIN7 machine and METALWAVE is the workgroup name in WIN7 and smb.conf

I have no idea why NETBIOS over TCIP is disabled, or how to change it in Ubunto.
From the WIN7 machine ipconfig/all reports ```
NetBIOS over Tcpip ..... Enabled
```

Once again, I can ping both machines from each other and from themselves by name and ip.  I can reach the apache server from WIN7 and navigate the php files there fine.

thanks for any and all help... I appreciate it!
kevcoder

---

### Post by capscrew on 2011-06-14
> **kevcoder said:**
> if I didn't already say this, I've been running linux for a full 4 months now although I work as a .Net developer.  So I understand the concepts, but have almost no idea where anything is in linux/unbuntu...

I was there once.  :-)  I started with DOS in in the 1980's and moved on to SUN OS and later Solaris.  My first Linux machine was Debian potato some 11 or 12 years ago.> 

* ... at work now so this is from memory...*

I added a new user/group (Kevin/Kevin) to  that matches my WIN7 user and password.

This is correct including the smbpasswd -a command.  This adds the user to the Ubuntu and to Samba.  Note: the practice is to use all lower case in Linux.  The OS is case sensitive.  My login is capscrew not Capscrew.> 

Correcting the netbios name in smb.conf now allows me to see the samba share in Nautilus. :)

I'll change security to user and remove those lines form smb.conf.  I assume that this means I should run ```
chown -R Kevin:Kevin /srv/samba/Share
``` and set a password for samba with ```
smbpasswd -a Kevin
```

IMHO, Linux in general and Samba data in particular are best controlled by the correct use of groups.  For example I created a group called *smbusers* for my Samba users.  All users on the Ubuntu host that are also users of the Samba services are in that group.  

This makes the share much more flexible.  I don't care who *owns *the file since all users can access it via the group permissions.  If I want to restrict users I can always use the parameter *valid users = *for that purpose.  

Now guest users parameters make sense.  If a file is created it will be with the user nobody, but I *force group *to be smbusers. As you can see the smbusers group allows all files to be available to all Samba users.  I DO NOT put the user nobody in the smbusers group.
> 

In the output from smbclient -L kevcoder00 KLSTRFK is the WIN7 machine and METALWAVE is the workgroup name in WIN7 and smb.conf

I have no idea why NETBIOS over TCIP is disabled, or how to change it in Ubunto.

Netbios names are resolved by the daemon (service) *nmbd *this is also converts DNS (hosts) names to netbios names.  This means you really don't have to declare the netbiso name in the smb.conf file as you did.  We do have to make sure it is running though.  To check if nmbd is running youcan do this```
ps -e|grep mbd
```  This shuld return somthing like this ```
 ps -e| grep mbd
  943 ?        00:00:00 smbd
  978 ?        00:00:00 **[COLOR="Red"]nmbd[/COLOR]**
 1080 ?        00:00:00 smbd
 1629 ?        00:00:00 smbd

```> 

From the WIN7 machine ipconfig/all reports ```
NetBIOS over Tcpip ..... Enabled
```

Once again, I can ping both machines from each other and from themselves by name and ip.  I can reach the apache server from WIN7 and navigate the php files there fine....

I think we have the connectivity working fine, so that is not an issue.

---

### Post by kevcoder on 2011-06-15
... I'm back for more pain,  

I can do everything on that checklist but run the following from WIN7: both report that the machine is unreachable
```

net view \\kevcoder00
net use x: \\kevcoder00\share

```I assume that this is good: running ps -e|grep mbd gives
```

 2765 ?        00:00:00 smbd
 2768 ?        00:00:00 smbd
 2775 ?        00:00:00 nmbd
 2807 ?        00:00:00 smbd
 2816 ?        00:00:00 smbd
 2823 ?        00:00:00 smbd
 2878 ?        00:00:00 smbd

```smbclient //klstrfk/metalwave_public gets me to the WIN7 box and I can navigate around with read-only permissions... but how can this fail (the first line) if I'm able to run ls???
```

session request to KLSTRFK failed (Called name not present)
Domain=[KLSTRFK] OS=[Windows 7 Ultimate N 7601 Service Pack 1] Server=[Windows 7 Ultimate N 6.1]
smb: \> ls
  .                                  DR        0  Tue Mar 29 21:56:05 2011
  ..                                 DR        0  Tue Mar 29 21:56:05 2011
  Desktop                           DHR        0  Sat May  7 18:26:38 2011
  desktop.ini                       AHS      174  Tue Jul 14 00:08:58 2009
  Documents                          DR        0  Sun May 15 12:14:08 2011
  Downloads                          DR        0  Tue Jun  7 22:26:40 2011
  Favorites                         DHR        0  Mon Jul 13 22:04:25 2009
  Libraries                         DHR        0  Tue Jul 14 00:08:58 2009
  Music                              DR        0  Mon Jan 17 19:49:46 2011
  Pictures                           DR        0  Sun Apr  3 00:44:46 2011
  scheduled_tasks                     D        0  Tue Dec 21 02:05:04 2010
  Torrents                            D        0  Tue Apr 19 00:50:10 2011
  Videos                             DR        0  Wed Jun  8 22:58:12 2011

        37781 blocks of size 4194304. 13217 blocks available
smb: \> 

```I'm assuming that my issue is from the WIN7 machine.  Once I replace the fan in my daughters laptop I'll have a clean install of WIN7 to test this against.  

If anyone any words of wisdom, I'm listening... and thanks for your time... seriously

kevcoder

---

### Post by capscrew on 2011-06-15
> **kevcoder said:**
> ... I'm back for more pain,  

I can do everything on that checklist but run the following from WIN7: both report that the machine is unreachable
```

net view \\kevcoder00
net use x: \\kevcoder00\share

```
This is a networking connectivity issue.  Do you have any firewalls running that would get in the way?> 

I assume that this is good: running ps -e|grep mbd gives
```

 2765 ?        00:00:00 smbd
 2768 ?        00:00:00 smbd
 2775 ?        00:00:00 nmbd
 2807 ?        00:00:00 smbd
 2816 ?        00:00:00 smbd
 2823 ?        00:00:00 smbd
 2878 ?        00:00:00 smbd

```
Yes it's fine.  The multiple forks of smbd reflect multiple connections.> 

smbclient //klstrfk/metalwave_public gets me to the WIN7 box and I can navigate around with read-only permissions... but how can this fail(the first line) if I'm able to run ls???
```

session request to KLSTRFK failed (Called name not present)
Domain=[KLSTRFK] OS=[Windows 7 Ultimate N 7601 Service Pack 1] Server=[Windows 7 Ultimate N 6.1]
smb: \> ls
  .                                  DR        0  Tue Mar 29 21:56:05 2011
  ..                                 DR        0  Tue Mar 29 21:56:05 2011
  Desktop                           DHR        0  Sat May  7 18:26:38 2011
  desktop.ini                       AHS      174  Tue Jul 14 00:08:58 2009
  Documents                          DR        0  Sun May 15 12:14:08 2011
  Downloads                          DR        0  Tue Jun  7 22:26:40 2011
  Favorites                         DHR        0  Mon Jul 13 22:04:25 2009
  Libraries                         DHR        0  Tue Jul 14 00:08:58 2009
  Music                              DR        0  Mon Jan 17 19:49:46 2011
  Pictures                           DR        0  Sun Apr  3 00:44:46 2011
  scheduled_tasks                     D        0  Tue Dec 21 02:05:04 2010
  Torrents                            D        0  Tue Apr 19 00:50:10 2011
  Videos                             DR        0  Wed Jun  8 22:58:12 2011

        37781 blocks of size 4194304. 13217 blocks available
smb: \> 

```I'm assuming that my issue is from the WIN7 machine.  Once I replace the fan in my daughters laptop I'll have a clean install of WIN7 to test this against...

The problem does appear to be a Windows problem.

I believe the *"Called name not present..."* error is the WORKGROUP name getting lost.  This shouldn't stop you from looking at the share, but it might hinder GUI browse functions.

I can't see what you have done as far as your host name to IP mapping, so I can't really advise you directly.  Are the DNS (hosts) names the same as the COMPUTER NAMES?  Are you sure you can ping by hostname.  Remember hostnames are not COMPUTER NAMES.  Can you successfully use either *_smbclient_* or _*net view*_ with IP addresses?

What is the hostname of KLSTRFK?  What do you get from it using this command```
hostname
``` What do you get when you use ```
smbtree -d3
```

You might look at the log files for errors.  They are located at /var/log/samba.  You can use the command *tail* to view the last entries.  The default is the last 25 lines.  You can increase this with tail -50 or so.  the command looks like this in my case> tail -50 /var/log/samba/log.malibu

---

### Post by kevcoder on 2011-06-15
from the WIN7 machine, KLSTRFK,
```

c:\User\Kevin > hostname
KLSTRFK

c:\User\Kevin > net view \\kevcoder00
System error 53 has occurred
The network path was not found

```from linux machine, kevcoder00
smbtree -d3
```

lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::d227:88ff:fe19:ce11%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.2.2 bcast=192.168.2.255 netmask=255.255.255.0
Enter dev's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name METALWAVE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name METALWAVE<0x1d>
Got a positive name query response from 192.168.2.2 ( 192.168.2.2 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.2.2
Connecting to 192.168.2.2 at port 445
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
Got a positive name query response from 192.168.2.2 ( 192.168.2.2 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name METALWAVE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name METALWAVE<0x1d>
Got a positive name query response from 192.168.2.2 ( 192.168.2.2 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.2.2
Connecting to 192.168.2.2 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
METALWAVE
resolve_lmhosts: Attempting lmhosts lookup for name METALWAVE<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name METALWAVE<0x1d>
Got a positive name query response from 192.168.2.2 ( 192.168.2.2 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.2.2
Connecting to 192.168.2.2 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\KEVCODER00             Samba 3.5.8
Connecting to host=KEVCODER00
resolve_lmhosts: Attempting lmhosts lookup for name KEVCODER00<0x20>
resolve_wins: Attempting wins lookup for name KEVCODER00<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name KEVCODER00<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\KEVCODER00\IPC$               IPC Service (Samba 3.5.8)
        \\KEVCODER00\Share              kevcoder00 file share


``````

dev@kevcoder00:/var/log/samba$ tail log.smbd
[2011/06/14 23:25:08.191111,  1] smbd/service.c:1070(make_connection_snum)
  kevcoder00 (127.0.0.1) connect to service Share initially as user nobody (uid=65534, gid=65534) (pid 2823)
[2011/06/14 23:28:17.631288,  1] smbd/service.c:1070(make_connection_snum)
  kevcoder00 (127.0.0.1) connect to service Share initially as user dev (uid=1000, gid=1000) (pid 2844)
[2011/06/14 23:28:22.644107,  1] smbd/service.c:1251(close_cnum)
  kevcoder00 (127.0.0.1) closed connection to service Share
[2011/06/15 08:20:28.787993,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/06/15 08:20:48.796354,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown


```and finally I can use smbclient with ip address
```

dev@kevcoder00:/var/log/samba$ smbclient //192.168.2.3/metalwave_public
Enter dev's password: 
Domain=[KLSTRFK] OS=[Windows 7 Ultimate N 7601 Service Pack 1] Server=[Windows 7 Ultimate N 6.1]
smb: \> ls
  .                                  DR        0  Tue Mar 29 21:56:05 2011
  ..                                 DR        0  Tue Mar 29 21:56:05 2011
  Desktop                           DHR        0  Sat May  7 18:26:38 2011
  desktop.ini                       AHS      174  Tue Jul 14 00:08:58 2009
  Documents                          DR        0  Sun May 15 12:14:08 2011
  Downloads                          DR        0  Tue Jun  7 22:26:40 2011
  Favorites                         DHR        0  Mon Jul 13 22:04:25 2009
  Libraries                         DHR        0  Tue Jul 14 00:08:58 2009
  Music                              DR        0  Mon Jan 17 19:49:46 2011
  Pictures                           DR        0  Sun Apr  3 00:44:46 2011
  scheduled_tasks                     D        0  Tue Dec 21 02:05:04 2010
  Torrents                            D        0  Tue Apr 19 00:50:10 2011
  Videos                             DR        0  Wed Jun  8 22:58:12 2011

        37781 blocks of size 4194304. 13159 blocks available
smb: \> 


```

---

### Post by capscrew on 2011-06-15
> ```
Connecting to 127.0.1.1 at port 445

```

This is part of the problem.

Post the contents of```
/etc/hosts

and 

c:\windows\system32\driver\etc\hosts 
```

---

### Post by kevcoder on 2011-06-16
C:\Windows\System32\drivers\etc\hosts
```

    127.0.0.1        www.HomeApps.com
    192.168.2.2        kevcoder00

```

/etc/hosts
```

127.0.0.1    localhost
127.0.1.1    kevcoder00
192.168.2.3    KLSTRFK

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by capscrew on 2011-06-16
> **kevcoder said:**
> C:\Windows\System32\drivers\etc\hosts
```

    127.0.0.1        www.HomeApps.com
    192.168.2.2        kevcoder00

```

/etc/hosts
```

127.0.0.1    localhost
**[COLOR="Red"]127.0.1.1    kevcoder00[/COLOR]**
192.168.2.3    KLSTRFK

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

The use of the 127.0.0./8 network is ***_[COLOR="Red"]restricted to the local machine only [/COLOR]_*** (the loopback interface (lo)).  This means any host mapped to an address that starts with 127 can only be reached when you are at that machine (no remote connections).

If KLSTRFK is in the 192.168.2.0/24 network, then kevecoder00 must also be in that network.  The /etc/hosts file needs to reflect that that like this```

127.0.0.1    localhost
**[COLOR="DarkGreen"]192.168.2.2    kevcoder00[/COLOR]**
192.168.2.3    KLSTRFK
```

At its most basic level kevcoder00 can't find itself when KLSTRFK calls it by its name.

FYI -- the use of 127.0.1.1 is a Debian workaround for a bug in some applications that need a hostname on a machine with no NIC in it.  Bad business in my book.

---

### Post by kevcoder on 2011-06-16
> **capscrew said:**
> 

If KLSTRFK is in the 192.168.2.0/24 network, then kevecoder00 must also be in that network.  The /etc/hosts file needs to reflect that that like this```

127.0.0.1    localhost
**[COLOR=DarkGreen]192.168.2.2    kevcoder00[/COLOR]**
192.168.2.3    KLSTRFK
```At its most basic level kevcoder00 can't find itself when KLSTRFK calls it by its name.

FYI -- the use of 127.0.1.1 is a Debian workaround for a bug in some applications that need a hostname on a machine with no NIC in it.  Bad business in my book.

I'll try it.  So SAMBA acts as a proxy shuttling messages back and forth and it is not able to resolve the name to the IP?  Am I understanding that correctly?

And if so, and I'm no network guru here... but isn't that what a DHCP server/service does. Does Linux/Ubuntu/Debian come with such a service and would enabling it solve the issue.  As a developer I often find the hosts file convenient, but always assumed it was a workaround.  

Or am I trying to bite off more than I can chew?

---

### Post by capscrew on 2011-06-16
> **kevcoder said:**
> I'll try it.  So SAMBA acts as a proxy shuttling messages back and forth and it is not able to resolve the name to the IP?  Am I understanding that correctly?

Samba is is a suite of services and utilities. The daemons (services) are [LIST]
[*]nmbd = name services (translates DNS (host) names to NetBIOS names and manages NetBIOS services)
[*]smbd = Manages the the SMB reasorces (//Server and /shares)
[/LIST]

Samba checks the hosts and lmhosts files and wins, then broadcasts for host/NetBIOS names.  Like this (on kevcoder00)```
resolve_lmhosts: Attempting lmhosts lookup for name KEVCODER00<0x20>
resolve_wins: Attempting wins lookup for name KEVCODER00<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name KEVCODER00<0x20>

```
It then resolves them to the IP address.  Look at the error messages, you will see that the nmbd daemon did correctly (as you configured it) resolve the name to 127.0.1.1. ```
Connecting to 127.0.1.1 at port 445
``` 

The problem occurs when KLSTRFK trys to talk to 127.0.1.1.  It can only **talk to the loopback adapter on itself** as all 127.0.0.0/8 traffic goes only to that virtual adapter. 

> And if so, and I'm no network guru here... but isn't that what a DHCP server/service does. 
DHCP only hands out IP addresses that you configure it to hand out.  The IP range of 127.0.0.0/8 should not be available for DHCP usage.  

DNS is IP number to host name resolution.  The first part of DNS is the hostname and this can be handled either by /etc/hosts or DNS servers.  A FQDN (hostname.domainname.suffix) is handled only by DNS servers.  As we are only working with hostnames converted to NetBIOS names, we can use either /etc/host or DNS to resolve these names.  We are using /etc/hosts.   > 

Does Linux/Ubuntu/Debian come with such a service and would enabling it solve the issue.  As a developer I often find the hosts file convenient, but always assumed it was a workaround.
The hosts file is not a workaround at all.  it is the starting point for all DNS.  The DNS server could be considered a global hosts file: a hosts file on steroids.>   

Or am I trying to bite off more than I can chew?
Maybe  :D

---

### Post by kevcoder on 2011-06-20
Capscrew,

I got it working.... with a damn good helping of your help.  Thank you.

The issue was on the WIN7 side.  What i did (although I suspect that only the last two mattered):

[LIST=1]
[*]kicked the kids off the windows machine
[*]went into Local Security Policy -- Local Policies -- Security Options and set Network security:Mininum session security for NTLM SSP based client and servers to not require 128 bit encryption
[*]disabled IPV6
[*]in properties of IPV4 checked the "Validate settings upon exit"
[/LIST]
After OK'ing out ot the IPV4 property dialog, windows tossed up a dialog box stating that there were "problems" that would prevent access to other networks.  I let it do its thing and voila, I can see my Ubuntu shares on kevcoder00 instantly.

That's not a slam dunk 'cause, as usual, windows never detailed what the "problem" was.  But at least I can move on now.

Thanks dude... or dudette. I never checked.

ps: how do I mark this as solved?

---

### Post by capscrew on 2011-06-20
> **kevcoder said:**
> Capscrew,

I got it working.... with a damn good helping of your help.  Thank you.

The issue was on the WIN7 side.  What i did (although I suspect that only the last two mattered):

[LIST=1]
[*]kicked the kids off the windows machine
[*]went into Local Security Policy -- Local Policies -- Security Options and set Network security:Mininum session security for NTLM SSP based client and servers to not require 128 bit encryption
[*]disabled IPV6
[*]in properties of IPV4 checked the "Validate settings upon exit"
[/LIST]
After OK'ing out ot the IPV4 property dialog, windows tossed up a dialog box stating that there were "problems" that would prevent access to other networks.  I let it do its thing and voila, I can see my Ubuntu shares on kevcoder00 instantly.

That's not a slam dunk 'cause, as usual, windows never detailed what the "problem" was.  But at least I can move on now.

Thanks dude... or dudette. I never checked.

ps: how do I mark this as solved?

It's dude.  Glad you got it working.

I've never even started a thread, so I'm not sure how to do that kind of thing.  You can search on the term *solved* in the forum though.

---

### Post by vikrang on 2011-08-20
I had a detailed look at the thread..Looks like the problem was solved by specifying the Server and client address in /etc/host
 
I am also trying to setup Samba in vain...., these are the contents of smb.conf:
 
```

 
[global]
WORKGROUP = MSHOME
NETBIOS NAME = VIKRAM-VOSTRO-1500
server string =
name resolve order = bcast lmhosts wins host
preferred master = no
os level = 20
 

```
 
I am able to see my shared windows folder in my ubuntu , but except print$ folder in any folder I click I get the message "Unable to mount Failed to mount windows share"
 
I have not given the machine names in /etc/hosts as the network is able to list the shared files...Only problem , i am not able to view the contents
 
First I am trying to access only the windows shared folder and I am not going to access linux share from Win
 
Why am I not able to view the folders?

---

### Post by capscrew on 2011-08-20
A few of thoughts about posting to others threads:
1) This thread is marked [SOLVED].  Most folks won't look at it.
2) Your problem does not relate to the OP's problem
3) Rather than hijacking an old thread you should start a new thread where you can describe your problem more specifically.

> **vikrang said:**
> I had a detailed look at the thread..Looks like the problem was solved by specifying the Server and client address in /etc/host

 
I am also trying to setup Samba in vain...., these are the contents of smb.conf:
 
```

 
[global]
WORKGROUP = MSHOME
NETBIOS NAME = VIKRAM-VOSTRO-1500
server string =
name resolve order = bcast lmhosts wins host
preferred master = no
os level = 20
 

```
 
I am able to see my shared windows folder in my ubuntu , but except print$ folder in any folder I click I get the message "Unable to mount Failed to mount windows share"
 
I have not given the machine names in /etc/hosts as the network is able to list the shared files...Only problem , i am not able to view the contents
 
First I am trying to access only the windows shared folder and I am not going to access linux share from Win
 
Why am I not able to view the folders?
There are many ways to set up LAN side name services.  Hosts is only one of the was to provide name services.

Netbios names should be 15 characters or less.  I'm not sure if the parameter should be lower case, but all examples sure are.  I would edit the smb.conf file to reflect this ```

workgroup = MSHOME
netbios name  = [COLOR="DarkGreen"]SMALLER_NAME[/COLOR]

```
[COLOR="DarkGreen"]*You pick the name you want but make it less than 15 characters*[/COLOR]

---

