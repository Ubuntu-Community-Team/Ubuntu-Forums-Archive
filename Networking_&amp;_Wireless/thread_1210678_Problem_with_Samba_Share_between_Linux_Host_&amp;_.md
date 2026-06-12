---
title: "Problem with Samba Share between Linux Host &amp; VMWare Guest"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by Perfect_Tommy on 2009-07-11
My upgrade from Kubuntu 8.10 to Kubuntu 9.04 failed (keyboard & mouse locked and I could not remotely log in) and I had to do a clean reinstall.  The reinstall worked however I have a problem getting my VMPlayer guest OS to see my linux filesystem.  I have highlighted things I think are wrong but don't understand in [COLOR=Red]RED[/COLOR] for ease of finding them.  Outline headings will be [COLOR=RoyalBlue]BLUE[/COLOR]. 

[SIZE=2][COLOR=Red]SUMMARY:
I think the problem is described in heading 3.2 below and is that there are no files in /var/lib/samba/usershare.  I tried to create those files using the "net usershare add ..." command but nothing appeared in the appropriate directory.  I am also concerned that I don't see the file "/etc/samba/private/smbpasswd".[/COLOR][/SIZE]

********
For the purposes of this thread, I'll make the following definitions for my network:

  Linux host: ronin (IP=192.168.0.104, username=tah)
  VMWare (VMPlayer) Guest: saito (IP=192.168.0.105, username=tah, OS=Windows XP Professional)

What follows is my troubleshooting thought process.  (I've been pretty verbose so this could be of help to people who are unsure of how to troubleshoot.):

**[SIZE=3][COLOR=RoyalBlue]0.0) Did this ever work before?[/COLOR][/SIZE]**
Yes, I had this service working under various Kubuntu versions (from 7.04 to 8.10).  Therefore, there should be no hardware limitation to getting this to work.

[B][SIZE=3][COLOR=RoyalBlue]1.0) Basic information:
1.1) What am I linux OS am I running?[/COLOR][/SIZE][/B]

```
ronin{tah}% uname -a
Linux ronin 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

**[SIZE=3][COLOR=RoyalBlue]1.2) Is there a firewall running?[/COLOR][/SIZE]**
No, I haven't set it up yet but here is the double-check.

```
ronin{tah}% sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

[B][SIZE=3][COLOR=RoyalBlue]1.3) Is the network accessable between the two systems?
1.3.1) From Linux host to VMWare guest:[/COLOR][/SIZE][/B]

```
ronin{tah}% ping 192.168.0.105
PING 192.168.0.105 (192.168.0.105) 56(84) bytes of data.
64 bytes from 192.168.0.105: icmp_seq=1 ttl=128 time=5.30 ms
64 bytes from 192.168.0.105: icmp_seq=2 ttl=128 time=0.311 ms
64 bytes from 192.168.0.105: icmp_seq=3 ttl=128 time=0.311 ms
64 bytes from 192.168.0.105: icmp_seq=4 ttl=128 time=0.297 ms
64 bytes from 192.168.0.105: icmp_seq=5 ttl=128 time=0.235 ms
^C
--- 192.168.0.105 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.235/1.292/5.307/2.007 ms
```

**[SIZE=3][COLOR=RoyalBlue]1.3.2) From VMWare guest to Linux host:[/COLOR][/SIZE]**
In the VMPlayer I opened the DOS command prompt and ran "ping 192.168.0.104".  This worked.  (I don't have an image of this but could generate it if required.)

**[SIZE=3][COLOR=RoyalBlue]1.4) What version of Samba is installed? [/COLOR][/SIZE]**
From KPackageKit: Samba - 2:3.3.2-1ubuntu (i386)

**[SIZE=3][COLOR=RoyalBlue]1.5) Is Samba running?[/COLOR][/SIZE]**
Yes.

```
ronin{tah}% sudo /etc/init.d/samba status
[sudo] password for tah:
 * nmbd is running
 * smbd is running
```

**[SIZE=3][COLOR=RoyalBlue]1.6) What are the contents of /etc/samba/smb.conf?[/COLOR][/SIZE]**
Rather than post this file with the various comments, here are the results of "testparm".  I can post "smb.conf" upon request.

```
ronin{tah}% sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"                                                                                           
Processing section "[print$]"                                                                                             
Processing section "[HL2040]"                                                                                             
Loaded services file OK.                                                                                                  
Server role: ROLE_DOMAIN_PDC                                                                                              
Press enter to see a dump of your service definitions

[global]
        workgroup = RONINGRP
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 50
        printcap name = cups
        add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
        add machine script = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
        logon drive = Q:
        domain logons = Yes
        dns proxy = No
        wins support = Yes
        usershare allow guests = Yes
        usershare max shares = 10
        panic action = /usr/share/samba/panic-action %d
        comment = Home Directories for %S
        invalid users = root
        valid users = %S
        read only = No
        create mask = 0600
        directory mask = 0600
        browseable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = Yes
        create mask = 0700
        guest ok = Yes
        printable = Yes

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        write list = root, @adm
        guest ok = Yes

[HL2040]
        comment = Brother HL-2040
        path = /var/spool/samba
        create mask = 0700
        guest ok = Yes
        printable = Yes
        printer name = HL2040
```

**[SIZE=3][COLOR=RoyalBlue]1.7) What are the contents of "/etc/samba/smbusers"?[/COLOR][/SIZE]**

```
ronin{tah}% cat /etc/samba/smbusers
tah = "tah"
```

**[SIZE=3][COLOR=RoyalBlue]1.8) What are the group permission for user "tah"?[/COLOR][/SIZE]**

```
ronin{tah}% groups
tah adm dialout cdrom plugdev lpadmin admin sambashare
```

**[SIZE=3][COLOR=RoyalBlue]1.9) Did you add set up a samba password?[/COLOR][/SIZE]**
Yes.  Below is the most verbose output of "smbpasswd":

```
ronin{tah}% sudo smbpasswd -D 10 -a tah
Netbios name list:-                   my_netbios_names[0]="RONIN"           Attempting to register passdb backend ldapsam
Successfully added passdb backend 'ldapsam' Attempting to register passdb backend ldapsam_compat
Successfully added passdb backend 'ldapsam_compat' Attempting to register passdb backend NDS_ldapsam  Successfully added passdb backend 'NDS_ldapsam'    Attempting to register passdb backend NDS_ldapsam_compat
Successfully added passdb backend 'NDS_ldapsam_compat' Attempting to register passdb backend smbpasswd        Successfully added passdb backend 'smbpasswd'          Attempting to register passdb backend tdbsam           Successfully added passdb backend 'tdbsam'             Attempting to find a passdb backend to match tdbsam (tdbsam)
Found pdb backend tdbsam                                   pdb backend tdbsam has a valid init                        New SMB password:                                          Retype new SMB password:                                   tdbsam_open: successfully opened /var/lib/samba/passdb.tdb pdb_set_username: setting username tah, was                pdb_set_domain: setting domain RONIN, was                  pdb_set_nt_username: setting nt username , was             pdb_set_full_name: setting full name John Tiede, was       Home server: ronin                                         Substituting charset 'UTF-8' for LOCALE                    Substituting charset 'UTF-8' for LOCALE                    Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
pdb_set_homedir: setting home dir \\ronin\tah, was
pdb_set_dir_drive: setting dir drive Q:, was NULL
pdb_set_logon_script: setting logon script , was
Home server: ronin
pdb_set_profile_path: setting profile path \\ronin\tah\profile, was
pdb_set_workstations: setting workstations , was
account_policy_get: name: password history, val: 0
pdb_set_user_sid: setting user sid S-1-5-21-2963074956-1983721669-1367311648-3000
pdb_set_user_sid_from_rid:
       setting user sid S-1-5-21-2963074956-1983721669-1367311648-3000 from rid 3000
account_policy_get: name: maximum password age, val: -1
Finding user tah
Trying _Get_Pwnam(), username as lowercase is tah
Get_Pwnam_internals did find user [tah]!
account_policy_get: name: password history, val: 0
pdb_set_username: setting username tah, was
pdb_set_domain: setting domain RONIN, was
pdb_set_nt_username: setting nt username , was
pdb_set_full_name: setting full name John Tiede, was
Home server: ronin
pdb_set_homedir: setting home dir \\ronin\tah, was
pdb_set_dir_drive: setting dir drive Q:, was NULL
pdb_set_logon_script: setting logon script , was
Home server: ronin
pdb_set_profile_path: setting profile path \\ronin\tah\profile, was
pdb_set_workstations: setting workstations , was
account_policy_get: name: password history, val: 0
pdb_set_user_sid: setting user sid S-1-5-21-2963074956-1983721669-1367311648-3000
pdb_set_user_sid_from_rid:
       setting user sid S-1-5-21-2963074956-1983721669-1367311648-3000 from rid 3000
account_policy_get: name: password history, val: 0
account_policy_get: name: maximum password age, val: -1
account_policy_get: name: password history, val: 0
Storing account tah with RID 3000
Locking key 555345525F6A777400
Allocated locked data 0x0xba059ab8
Unlocking key 555345525F6A777400
Locking key 5249445F303030303062
Allocated locked data 0x0xba059400
Unlocking key 5249445F303030303062
```

[B][SIZE=3][COLOR=RoyalBlue]2.0) What is happening on the VMPlayer guest system?
2.1) What guest OS am I running?[/COLOR][/SIZE][/B]
Windows XP Professional

[B][SIZE=3][COLOR=RoyalBlue]2.2) What happens when I try to "map network drive"?
[/COLOR][/SIZE][/B]
  Start -> Control Panel -> Tools -> Map Network Drive
  Q: \\RONIN\tah

  First popup window (Title=Map Network Drive)
  "Attempting to connect to \\RONIN\tah"
  Second popup window (Title=Windows)
  "The mapped network drive could not be created because the following error has occurred:
  [COLOR=Red]The specified network name is no longer available.[/COLOR]"

[B][SIZE=3][COLOR=RoyalBlue]3.0) What do the samba log files say?
3.1) Here is the tail of the file "var/log/samba/log.smbd"[/COLOR][/SIZE][/B]

```
ronin{tah}% /usr/bin/tail --lines=8 log.smbd
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/07/09 06:51:36,  0] lib/util_sock.c:get_peer_addr_internal(1676)
  getpeername failed. Error was Transport endpoint is not connected
[2009/07/10 08:18:59,  0] lib/util_sock.c:get_peer_addr_internal(1676)
  getpeername failed. Error was Transport endpoint is not connected
[2009/07/11 09:45:33,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
```

I don't know what the ERROR above means.  When I restarted, everything looks okay.

**[SIZE=3][COLOR=RoyalBlue]3.2) Here is the tail of the file "/var/log/samba/log.saito"[/COLOR][/SIZE]**

```
ronin{tah}% /usr/bin/tail --lines=6 log.saito
[2009/07/11 10:02:14,  0] smbd/service.c:make_connection_snum(996)
  [COLOR=Red]Can't become connected user![/COLOR]
[2009/07/11 10:02:15,  0] param/loadparm.c:process_usershare_file(8322)
  process_usershare_file: [COLOR=Red]stat of /var/lib/samba/usershares/tah failed. No such file or directory[/COLOR]
[2009/07/11 10:02:15,  0] smbd/service.c:make_connection(1284)
  saito (192.168.0.105) couldn't find service tah
```

[COLOR=Red]I went to the directory "/var/lib/samba/usershare" and it was indeed empty:[/COLOR]

```
ronin{tah}% ls -la /var/lib/samba/usershares/
total 8.0K
drwxrwx--T 2 root sambashare 4.0K 2009-07-04 15:41 ./
drwxr-xr-x 5 root root       4.0K 2009-07-11 12:04 ../
```

From here is searched the web and found the "net" command.  I haven't had to use this before but I pretty much game for anything.  After reading the "man" page, I ran this command:

```
ronin{tah}% sudo net usershare add tah /home/tah "tah's share" alc guest_ok=y
net usershare add: share name tah is already a valid system user name

```

Since I've been screwing around to get this to work and wanted to show what happened when I initiated this, I did this:

```
ronin{tah}% sudo net usershare delete tah
net usershare delete: unable to remove usershare /var/lib/samba/usershares/tah. Error was No such file or directory

```

[COLOR=Red]I already knew that this file didn't exist from the attempt above.  So, I seem to exist as a share but not where samba thinks I should.  ???[/COLOR]

```
ronin{tah}% sudo net usershare list
ronin{tah}%
```

This may be the problem but I am stuck on what I did wrong and how to fix this problem.

[COLOR=RoyalBlue]**[SIZE=3]3.3)  Here is the tail of the file "var/log/samba/log.nmbd"[/SIZE]**[/COLOR]

```
ronin{tah}% /usr/bin/tail --lines=58 log.nmbd                                                                           
  *****                                                                                                                 
[2009/07/11 09:45:33,  0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(292)                                
  become_domain_master_browser_bcast:                                                                                   
  Attempting to become domain master browser on workgroup RONINGRP on subnet 172.16.30.1
[2009/07/11 09:45:33,  0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(305)
  become_domain_master_browser_bcast: querying subnet 172.16.30.1 for domain master browser on workgroup RONINGRP
[2009/07/11 09:45:33,  0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(292)
  become_domain_master_browser_bcast:
  Attempting to become domain master browser on workgroup RONINGRP on subnet 172.16.53.1
[2009/07/11 09:45:33,  0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(305)
  become_domain_master_browser_bcast: querying subnet 172.16.53.1 for domain master browser on workgroup RONINGRP
[2009/07/11 09:45:33,  0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(292)
  become_domain_master_browser_bcast:
  Attempting to become domain master browser on workgroup RONINGRP on subnet 192.168.0.104
[2009/07/11 09:45:33,  0] nmbd/nmbd_become_dmb.c:become_domain_master_browser_bcast(305)
  become_domain_master_browser_bcast: querying subnet 192.168.0.104 for domain master browser on workgroup RONINGRP
[2009/07/11 09:45:37,  0] nmbd/nmbd_logonnames.c:become_logon_server_success(121)
  become_logon_server_success: Samba is now a logon server for workgroup RONINGRP on subnet 172.16.30.1
[2009/07/11 09:45:37,  0] nmbd/nmbd_logonnames.c:become_logon_server_success(121)
  become_logon_server_success: Samba is now a logon server for workgroup RONINGRP on subnet 172.16.53.1
[2009/07/11 09:45:37,  0] nmbd/nmbd_logonnames.c:become_logon_server_success(121)
  become_logon_server_success: Samba is now a logon server for workgroup RONINGRP on subnet 192.168.0.104
[2009/07/11 09:45:41,  0] nmbd/nmbd_become_dmb.c:become_domain_master_stage2(110)
  *****

  Samba server RONIN is now a domain master browser for workgroup RONINGRP on subnet 172.16.30.1

  *****
[2009/07/11 09:45:41,  0] nmbd/nmbd_become_dmb.c:become_domain_master_stage2(110)
  *****

  Samba server RONIN is now a domain master browser for workgroup RONINGRP on subnet 172.16.53.1

  *****
[2009/07/11 09:45:41,  0] nmbd/nmbd_become_dmb.c:become_domain_master_stage2(110)
  *****

  Samba server RONIN is now a domain master browser for workgroup RONINGRP on subnet 192.168.0.104

  *****
[2009/07/11 09:51:03,  0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(395)
  *****

  Samba name server RONIN is now a local master browser for workgroup RONINGRP on subnet 172.16.30.1

  *****
[2009/07/11 09:51:03,  0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(395)
  *****

  Samba name server RONIN is now a local master browser for workgroup RONINGRP on subnet 172.16.53.1

  *****
[2009/07/11 09:51:03,  0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(395)
  *****

  Samba name server RONIN is now a local master browser for workgroup RONINGRP on subnet 192.168.0.104
```

**[SIZE=3][COLOR=RoyalBlue]3.3.1) What are the IP addresses 172.16.30.1, 172.16.53.1 above?[/COLOR][/SIZE]**
These are the addresses associated with vmnet1 and vmnet8.  Here's the output of "ifconfig":

```
ronin{tah}% sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:ae:67:f3
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:feae:67f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3517604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1409970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2339481327 (2.3 GB)  TX bytes:137194742 (137.1 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:223961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:29133312 (29.1 MB)  TX bytes:29133312 (29.1 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01
          inet addr:172.16.53.1  Bcast:172.16.53.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:172.16.30.1  Bcast:172.16.30.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

**[SIZE=3][COLOR=RoyalBlue]3.4) Does the file "/etc/samba/private/smbpasswd" exist?[/COLOR][/SIZE]**
[COLOR=Red]No.  I didn't expect this to be missing.  Does this version of samba not use this file?  There appears to be a file "/var/lib/samba/passdb.tdb".[/COLOR]

```
ronin{tah}% sudo file passdb.tdb
passdb.tdb: TDB database version 6, little-endian hash size 131 bytes
```

I am going to assume that this is the password file but I could be wrong.

This is the end of my troubleshooting.  I think I'm close but missing something.  Thanks in advance for any help.

---

### Post by bernied on 2009-07-11
Have you tried to map the network drive using the host's ip address, instead of the name?
Likewise, have you tried to ping the host using its name?

---

### Post by Perfect_Tommy on 2009-07-11
When I try to connect using "Q: \\192.168.0.104\tah", it fails. 

When I open the DOS command prompt and "ping RONIN", the ping works.

---

### Post by bernied on 2009-07-11
Sorry, I was distracted by all your network info. So didn't see how you were defining your shares in smb.conf

I don't use the usershare thingy in samba, but that seems to be where things are going wrong for you.

---

### Post by Perfect_Tommy on 2009-07-11
In my "/etc/samba/smb.conf", I commented out the "usershare" lines.  Then I restarted samba with

```
ronin{tah}% sudo vi smb.conf
ronin{tah}% sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                                                           [ OK ]
 * Starting Samba daemons                                                                                            [ OK ]

```

Next, I attempted to map my network drive to "Q: \\RONIN\tah".  This failed again.

---

### Post by bernied on 2009-07-11
> **Perfect_Tommy said:**
> In my "/etc/samba/smb.conf", I commented out the "usershare" lines.  Then I restarted samba with

```
ronin{tah}% sudo vi smb.conf
ronin{tah}% sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                                                           [ OK ]
 * Starting Samba daemons                                                                                            [ OK ]

```

Next, I attempted to map my network drive to "Q: \\RONIN\tah".  This failed again.
But without the usershare options, do you have any shares defined at all?
I see only printers there.

Does this help:
[http://www.suselinuxsupport.de/wikka.php?wakka=HowToSambaUsershares](http://www.suselinuxsupport.de/wikka.php?wakka=HowToSambaUsershares)

---

### Post by Perfect_Tommy on 2009-07-11
I read the link that you suggested.  Based on that I added the following lines to "/etc/samba/smb.conf" at the end of the shares section...

```
[FONT=monospace]
[/FONT][SHAREFOLDER]
path = /home/tah
guest ok = yes
read only = no

```

I restarted samba and then tried to map my network.  It failed.  I am continuing to read this link.

---

### Post by Perfect_Tommy on 2009-07-11
bernied, you are the man.  My "/etc/samba/smb.conf" file was incomplete.  I removed the share stansa in message #7 above.  I appended the following lines to "/etc/samba/smb.conf" in the "Share Definitions" section...

```

[HOMES]
  comment = Home Directories
  valid users = %S
  read only = no
  create mask = 0644
  driectory mask = 0700

[netlogon]
  path = /var/lib/samba/profiles
  guest ok = yes

```

I restarted the samba service.  When I mapped the network drive it worked.  I am marking this one as solved.  Thanks very much.  Your work here is done.  :-)

---

### Post by gm.matias on 2010-02-12
I am using VMPlayer and in the configuration I enabled the Share Files options but it did not work for me. I read some more articles and found a good solution that works for me. I put in here: [http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12](http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12)

Hope it helps.

---

