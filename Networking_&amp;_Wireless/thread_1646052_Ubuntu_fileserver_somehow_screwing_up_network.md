---
title: "Ubuntu fileserver somehow screwing up network"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by pfunkman on 2010-12-15
I posted a thread [here]("http://ubuntuforums.org/showthread.php?p=10176733") and got absolutely no help at all. Hopefully a new thread will get some attention...

I have a linux server running ubuntu servr 10.04 that serves as a backup/torrentbox/media streaming server. Somehow along the way its screwed kind of taken over my network.

I have this machine, 2 windows 7 machines a laptop and a netbook running kubuntu 10.04. I cannot access any windows shares currently from either linux laptop. 

When the server is running this is the output of smbtree:

```
michael@michael-n220:~$ smbtree
Enter michael's password:
WORKGROUP
        \\SERVER                        server server (Samba, Ubuntu)
                \\SERVER\IPC$                   IPC Service (server server (Samba, Ubuntu))
                \\SERVER\Backup
                \\SERVER\Pictures
                \\SERVER\Videos
                \\SERVER\Music
                \\SERVER\Complete
                \\SERVER\Torrents
                \\SERVER\print$                 Printer Drivers
        \\MICHAEL-GAMING                Michael-Gaming
cli_start_connection: failed to connect to MICHAEL-GAMING<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
        \\KATIE-PC
cli_start_connection: failed to connect to KATIE-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
```

If i shut the server down or unplug it from the router smbclient returns absolutely nothing and when i try to browse for shares in dolphin i get an error saying it found no workgroup.

It magically started working one day when i shut down my server but stopped working again.

Any ideas? Where could i see the actual errors from samba this generic catchall error is really annoying and not helpful at all.

---

### Post by pfunkman on 2010-12-15
If i unplug the server and reboot the windows machines then plug it back in everything will work like normal for a few days or hours.

Im stumped.

---

### Post by pfunkman on 2010-12-15
This is driving me up a wall. Everything used to work just fine it has to be some update to the server.

---

### Post by pfunkman on 2010-12-15
Is there a forum somewhere that would be better for this? Over 2 weeks and 2 threads with half a dozen bumps and 0 responses.

---

### Post by pfunkman on 2010-12-15
> **pfunkman said:**
> If i unplug the server and reboot the windows machines then plug it back in everything will work like normal for a few days or hours.

Im stumped.

This worked a couple times, lasted a few minutes and went back to not working, now it wont work at all.

---

### Post by drdos2006 on 2010-12-15
I just found your thread.

I am not a Samba expert, but from the report you posted it appears to me that the server is OK but " Error NT_STATUS_UNSUCCESSFUL " tells me it is a Windows problem.

Does your server have a static IP or does it get an IP from your router ?

regards

---

### Post by pfunkman on 2010-12-15
> **drdos2006 said:**
> I just found your thread.

I am not a Samba expert, but from the report you posted it appears to me that the server is OK but " Error NT_STATUS_UNSUCCESSFUL " tells me it is a Windows problem.

Does your server have a static IP or does it get an IP from your router ?

regards

That error is a general error that really means absolutely nothing if something goes wrong thats the error you will get most of the time regardless of the cause. Im curious how that tells you anything at all.

I can access both windows machines with no problems whatsoever *from* the server its only the netbook that cannot access them.

It has a static IP.

Im beginning to think its just the netbook, since i can no longer reproduce the way it "used" to work im thinking it was a coincidence that it worked when i shut down the server.

---

### Post by drdos2006 on 2010-12-15
You mentioned this.
I cannot access any windows shares currently from either windows box. 

Can you ping the server from either windows box ?

regards

---

### Post by pfunkman on 2010-12-15
> **drdos2006 said:**
> You mentioned this.
I cannot access any windows shares currently from either windows box. 

Can you ping the server from either windows box ?

regards

That was a typo, sorry. Communication to and from the server is flawless on every machine, the windows machines have no trouble sharing between themselves and the server. Neither my netbook or the wifes laptop with kubuntu 10.04 can access the windows machines. We can access the server just fine but same generic error when trying to access the windows machines.

Its like the server is dominating the other linux machines somehow.

---

### Post by drdos2006 on 2010-12-15
Run ipconfig on each Windows box and ifconfig on each linux box. Look for IPv4 IP addresses. 

regards

---

### Post by drdos2006 on 2010-12-15
Duty calls, will be away for a few hours.
I copied this from a previous posting for future use. It may be of some help to you......


You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

regards

---

### Post by redmk2 on 2010-12-15
> **pfunkman said:**
> ... Neither my netbook or the wifes laptop with kubuntu 10.04 can access the windows machines. We can access the server just fine but same generic error when trying to access the windows machines.

Its like the server is dominating the other linux machines somehow.

The server doesn't *dominate *anything.  The host that you refer to as "server" is both a client and a server in reference to Samba.  When you are viewing the shares on a Windows host from the the "server" it is acting as a client and in this case the Windows host is acting as a server.  This is basic client/server architecture.

From a previous post:> That error is a general error that really means absolutely nothing if something goes wrong thats the error you will get most of the time regardless of the cause. Im curious how that tells you anything at all.
It is not a general error.  To see what it means you need to raise that debug level when issuing the **smbtree **command.  Like so```
smbtree -d6
```

This will provide all the gory details.  

Be aware that "*failure*" is not necessarily an error.  Samba will try various means to find the NetBIOS name of the host so it can connect.  A Samba resource is always //netBIOS_name/share_name.  Without this the client can't connect to the resource and the error that it can't connect will be displayed.  The magic comes from determining why this happened.   

You can reduce it a bit to```
smb -d4
```

This is less debug but it might be clearer.

In the end it does indeed sound like the "*netbook or the wifes laptop*" are not correctly configured.

---

### Post by redmk2 on 2010-12-15
> **drdos2006 said:**
> Duty calls, will be away for a few hours.
I copied this from a previous posting for future use. It may be of some help to you......


You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

regards

IPv6 is not the problem here.

---

### Post by pfunkman on 2010-12-15
Im not sure whats not configured right but they are both 100% fresh installs and i get the same error from the live CD.

```
        \\MICHAEL-GAMING                Michael-Gaming
Connecting to host=MICHAEL-GAMING
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm                                                                                                                               ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s                                                                                                                               uch file or directory
Attempt to open gencache.tdb has failed.
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm                                                                                                                               ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s                                                                                                                               uch file or directory
Attempt to open gencache.tdb has failed.
resolve_lmhosts: Attempting lmhosts lookup for name MICHAEL-GAMING<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file                                                                                                                                or directory
[COLOR="Red"]resolve_wins: Attempting wins lookup for name MICHAEL-GAMING<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.[/COLOR]
resolve_hosts: Attempting host lookup for name MICHAEL-GAMING<0x20>
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm                                                                                                                               ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s                                                                                                                               uch file or directory
Attempt to open gencache.tdb has failed.
[COLOR="Yellow"]Connecting to 67.63.55.33 at port 445
Connecting to 67.63.55.33 at port 139[/COLOR]
Error connecting to 67.63.55.33 (Success)
cli_start_connection: failed to connect to MICHAEL-GAMING<20> (0.0.0.0). Error N                                                                                                                               T_STATUS_UNSUCCESSFUL
```

The 2 things that stick out to me are the red and yellow. The red i will look into right now. When it gets to the yellow it hangs for a second or two, why is it communicating outside of my network?

---

### Post by pfunkman on 2010-12-15
I should mention i can connect via IP just fine.

```
michael@michael-n220:~$ smbclient -L 192.168.0.195
Enter michael's password:
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        D               Disk
        D$              Disk      Default share
        E$              Disk      Default share
        H$              Disk      Default share
        IPC$            IPC       Remote IPC
        Users           Disk
session request to 192.168.0.195 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

---

### Post by redmk2 on 2010-12-15
> **pfunkman said:**
> Im not sure whats not configured right but they are both 100% fresh installs and i get the same error from the live CD.

```
        \\MICHAEL-GAMING                Michael-Gaming
Connecting to host=MICHAEL-GAMING
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm                                                                                                                               ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s                                                                                                                               uch file or directory
Attempt to open gencache.tdb has failed.
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm                                                                                                                               ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s                                                                                                                               uch file or directory
Attempt to open gencache.tdb has failed.
resolve_lmhosts: Attempting lmhosts lookup for name MICHAEL-GAMING<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file                                                                                                                                or directory
[COLOR="Red"]resolve_wins: Attempting wins lookup for name MICHAEL-GAMING<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.[/COLOR]
resolve_hosts: Attempting host lookup for name MICHAEL-GAMING<0x20>
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm                                                                                                                               ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s                                                                                                                               uch file or directory
Attempt to open gencache.tdb has failed.
[COLOR="Yellow"]Connecting to 67.63.55.33 at port 445
Connecting to 67.63.55.33 at port 139[/COLOR]
Error connecting to 67.63.55.33 (Success)
cli_start_connection: failed to connect to MICHAEL-GAMING<20> (0.0.0.0). Error N                                                                                                                               T_STATUS_UNSUCCESSFUL
```

The 2 things that stick out to me are the red and yellow. The red i will look into right now. When it gets to the yellow it hangs for a second or two, why is it communicating outside of my network?

Try and not jump to conclusions.  Remember I said: "not all failures are not errors".  The red just means you don't have a WINS server.  YOU DO NOT NEED A WINS SERVER TO BE SUCCESSFUL.

The "yellow" (which is damn hard to read) is a problem.  This is: mediacomassist.infospace.com.  Who are they?  See [**_here_**]("http://www.reddit.com/r/programming/comments/9o3as/want_a_real_world_example_of_why_we_need_network/").  You need to correct whatever is misconfigured in in your DNS setup.

---

### Post by redmk2 on 2010-12-15
> **pfunkman said:**
> I should mention i can connect via IP just fine.

```
michael@michael-n220:~$ smbclient -L 192.168.0.195
Enter michael's password:
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        D               Disk
        D$              Disk      Default share
        E$              Disk      Default share
        H$              Disk      Default share
        IPC$            IPC       Remote IPC
        Users           Disk
session request to 192.168.0.195 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
[COLOR="Red"]**NetBIOS over TCP disabled -- no workgroup available**[/COLOR]

```

The problem is not IP connectivity for sure.  :D

The problem is noted in red above!!!!  You need to allow sharing on this host.

---

### Post by pfunkman on 2010-12-15
> **redmk2 said:**
> The problem is not IP connectivity for sure.  :D

The problem is noted in red above!!!!  You need to allow sharing on this host.

What do you mean? If sharing was not enabled how could i connect even via IP? In dolphin i can add the share on that machine via IP and browse it like normal.

Not to mention my fileserver and the other windows machine can connect.

None of that would be possible if sharing was not configured properly on the host.

Do you mean something else?

---

### Post by redmk2 on 2010-12-15
> **pfunkman said:**
> What do you mean? If sharing was not enabled how could i connect even via IP? In dolphin i can add the share on that machine via IP and browse it like normal.

Not to mention my fileserver and the other windows machine can connect.

None of that would be possible if sharing was not configured properly on the host.

Do you mean something else?

Can we name the hosts so we are talking about specific machines a little more clearly?

There are more layers to this onion called SMB/CIFS (samba in Linux speak).  Browsing the shares requires NetBIOS resolution on each individual host. The data you posted shows the failure.

Looking for shares on another host can be preformed by the client routines e.g. SMBFS.  These should be installed by default.  They are part of Samba but are not *the *Samba Server.  In addition you are using KDE and that also may have routines built in.  I have no knowledge of KDE, I use Gnome.  Samba still works the same though.

Edit:  Sharing != Browsing (!= means *does not *equal)

---

### Post by pfunkman on 2010-12-15
> **redmk2 said:**
> Can we name the hosts so we are talking about specific machines a little more clearly?

There are more layers to this onion called SMB/CIFS (samba in Linux speak).  Browsing the shares requires NetBIOS resolution on each individual host. The data you posted shows the failure.

Looking for shares on another host can be preformed by the client routines e.g. SMBFS.  These should be installed by default.  They are part of Samba but are not *the *Samba Server.  In addition you are using KDE and that also may have routines built in.  I have no knowledge of KDE, I use Gnome.  Samba still works the same though.

Edit:  Sharing != Browsing (!= means *does not *equal)

I dont get your meaning, even with that error i can browse *and* access all my files. Like i have said a million times the windows 7 machines are set up right. They have worked just fine with linux machines since win 7 launched its just recently these problems sprang up. Thats why i assumed it was an update or something to the server because i literally changed nothing else.

FYI i fixed it. Switched over to a different DNS server and everything works fine. That also explains why it worked intermittently before. 

My ISP is mediacom and they have an awful search redirect that no matter how many times you opt out of keeps returning.

Thanks for the help.

---

### Post by redmk2 on 2010-12-15
> **pfunkman said:**
> I dont get your meaning, even with that error i can browse *and* access all my files. Like i have said a million times the windows 7 machines are set up right. They have worked just fine with linux machines since win 7 launched its just recently these problems sprang up. Thats why i assumed it was an update or something to the server because i literally changed nothing else.

FYI i fixed it. Switched over to a different DNS server and everything works fine. That also explains why it worked intermittently before. 

My ISP is mediacom and they have an awful search redirect that no matter how many times you opt out of keeps returning.

Thanks for the help.

My guess is that the NetBIOS routines were not allowed to fail gracefully or get local DNS (there is a way to avoid this).  By connecting to an outside DNS (via there non-standard redirect) the whole thing just created errors.

Could you confirm this by posting from the same host:```
smbtree -d4
```

Please mark this thread as solved.

---

### Post by pfunkman on 2010-12-15
```
michael@michael-n220:~$ smbtree -d4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter wins support = no
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface wlan0 ip=fe80::7ae4:ff:fef8:d145%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.190 bcast=192.168.0.255 netmask=255.255.255.0
Enter michael's password:
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.0.197(137) header: id=27015 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char ......   hex 0000C0A800C5
Got a positive name query response from 192.168.0.197 ( 192.168.0.197 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=192.168.0.197
Connecting to 192.168.0.197 at port 445
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
nmb packet from 192.168.0.197(137) header: id=2428 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=259200
    answers   0 char ......   hex 8000C0A800C5
Got a positive name query response from 192.168.0.197 ( 192.168.0.197 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
nmb packet from 192.168.0.197(137) header: id=1915 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .SERVER            hex 07534552564552202020202020202020
    answers  10 char ...SERVER          hex 00040053455256455220202020202020
    answers  20 char   ...SERVER        hex 20200304005345525645522020202020
    answers  30 char      ....__MSBRO   hex 2020202020040001025F5F4D5342524F
    answers  40 char WSE__....WORKGRO   hex 5753455F5F02018400574F524B47524F
    answers  50 char UP      ...WORKG   hex 55502020202020201D0400574F524B47
    answers  60 char ROUP      ...WOR   hex 524F55502020202020201E8400574F52
    answers  70 char KGROUP      ....   hex 4B47524F555020202020202000840000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ................   hex 00000000000000000000000000000000
    answers  a0 char .............   hex 00000000000000000000000000
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.0.197(137) header: id=30326 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char ......   hex 0000C0A800C5
Got a positive name query response from 192.168.0.197 ( 192.168.0.197 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
found master browser WORKGROUP, 192.168.0.197
Connecting to host=192.168.0.197
Connecting to 192.168.0.197 at port 445
WORKGROUP
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.0.197(137) header: id=30630 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char ......   hex 0000C0A800C5
Got a positive name query response from 192.168.0.197 ( 192.168.0.197 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to host=192.168.0.197
Connecting to 192.168.0.197 at port 445
        \\SERVER                        server server (Samba, Ubuntu)
Connecting to host=SERVER
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name SERVER<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name SERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SERVER<0x20>
resolve_hosts: getaddrinfo failed for name SERVER [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name SERVER<0x20>
nmb packet from 192.168.0.197(137) header: id=27075 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=SERVER<20> rr_type=32 rr_class=1 ttl=259200
    answers   0 char ......   hex 0000C0A800C5
Got a positive name query response from 192.168.0.197 ( 192.168.0.197 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.197 at port 445
                \\SERVER\IPC$                   IPC Service (server server (Samba, Ubuntu))
                \\SERVER\Backup
                \\SERVER\Pictures
                \\SERVER\Videos
                \\SERVER\Music
                \\SERVER\Complete
                \\SERVER\Torrents
                \\SERVER\print$                 Printer Drivers
        \\MICHAEL-GAMING                Michael-Gaming
Connecting to host=MICHAEL-GAMING
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name MICHAEL-GAMING<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name MICHAEL-GAMING<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MICHAEL-GAMING<0x20>
resolve_hosts: getaddrinfo failed for name MICHAEL-GAMING [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name MICHAEL-GAMING<0x20>
nmb packet from 192.168.0.195(137) header: id=26184 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=MICHAEL-GAMING<20> rr_type=32 rr_class=1 ttl=300000
    answers   0 char @.....   hex 4000C0A800C3
Got a positive name query response from 192.168.0.195 ( 192.168.0.195 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
Connecting to 192.168.0.195 at port 445
Doing spnego session setup (blob length=336)
SPNEGO login failed: Invalid parameter
                \\MICHAEL-GAMING\Users
                \\MICHAEL-GAMING\IPC$                   Remote IPC
                \\MICHAEL-GAMING\H$                     Default share
                \\MICHAEL-GAMING\E$                     Default share
                \\MICHAEL-GAMING\D$                     Default share
                \\MICHAEL-GAMING\D
                \\MICHAEL-GAMING\C$                     Default share
                \\MICHAEL-GAMING\ADMIN$                 Remote Admin
```

All seems well.

---

### Post by redmk2 on 2010-12-15
> **pfunkman said:**
> ```
michael@michael-n220:~$ smbtree -d4
...

resolve_hosts: Attempting host lookup for name MICHAEL-GAMING<0x20>
resolve_hosts: getaddrinfo failed for name MICHAEL-GAMING [Name or service not known]
[COLOR="Red"]**name_resolve_bcast: Attempting broadcast lookup for name MICHAEL-GAMING<0x20>**[/COLOR]
nmb packet from 192.168.0.195(137) header: id=26184 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=MICHAEL-GAMING<20> rr_type=32 rr_class=1 ttl=300000
    answers   0 char @.....   hex 4000C0A800C3
Got a positive name query response from 192.168.0.195 ( 192.168.0.195 )

...

Connecting to 192.168.0.197 at port 445
                \\SERVER\IPC$                   IPC Service (server server (Samba, Ubuntu))
                \\SERVER\Backup
                \\SERVER\Pictures
                \\SERVER\Videos
                \\SERVER\Music
                \\SERVER\Complete
                \\SERVER\Torrents
                \\SERVER\print$                 Printer Drivers
        \\MICHAEL-GAMING                Michael-Gaming
Connecting to host=MICHAEL-GAMING
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name MICHAEL-GAMING<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name MICHAEL-GAMING<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MICHAEL-GAMING<0x20>
resolve_hosts: getaddrinfo failed for name MICHAEL-GAMING [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name MICHAEL-GAMING<0x20>
nmb packet from 192.168.0.195(137) header: id=26184 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=MICHAEL-GAMING<20> rr_type=32 rr_class=1 ttl=300000
    answers   0 char @.....   hex 4000C0A800C3
Got a positive name query response from 192.168.0.195 ( 192.168.0.195 )...

Connecting to 192.168.0.195 at port 445
...
                \\MICHAEL-GAMING\Users
                \\MICHAEL-GAMING\IPC$                   Remote IPC
                \\MICHAEL-GAMING\H$                     Default share
                \\MICHAEL-GAMING\E$                     Default share
                \\MICHAEL-GAMING\D$                     Default share
                \\MICHAEL-GAMING\D
                \\MICHAEL-GAMING\C$                     Default share
                \\MICHAEL-GAMING\ADMIN$                 Remote Admin
```

All seems well.

Yes indeed.  Now that the NetBIOS resolution can be handled locally via b'cast the system is happy.  Watch your ISP for redirects.  I believe you can opt out of redirects.  You will have to check.

Remember to use the Thread tools at the top of the page to make this solved.  :-)

---

### Post by pfunkman on 2010-12-15
> **redmk2 said:**
> Yes indeed.  Now that the NetBIOS resolution can be handled locally via b'cast the system is happy.  Watch your ISP for redirects.  I believe you can opt out of redirects.  You will have to check.

Remember to use the Thread tools at the top of the page to make this solved.  :-)

Thats just it, about every 3-6 weeks the redirects come back and i have to opt out again. Its a real pain.

---

### Post by redmk2 on 2010-12-15
> **pfunkman said:**
> Thats just it, about every 3-6 weeks the redirects come back and i have to opt out again. Its a real pain.
I use my router to host my local DNS.  The only requests forwarded are non-local i.e not Private Addresses.  You can also use google DNS it is 8.8.8.8 and 8.8.4.4.  There is no absolute need to use the ISP's DNS servers.

In addition I'll bet that if you look at the smb.conf files you can declare the netBIOS name like this```
netbios name = <YOUR_HOST_NAME>
```

The only caveat is that it must be less than 15 characters.

The complete annotated smb.conf file parameters is located [**_here _**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

---

### Post by pfunkman on 2010-12-15
> **redmk2 said:**
> I use my router to host my local DNS.  The only requests forwarded are non-local i.e not Private Addresses.  You can also use google DNS it is 8.8.8.8 and 8.8.4.4.  There is no absolute need to use the ISP's DNS servers.

In addition I'll bet that if you look at the smb.conf files you can declare the netBIOS name like this```
netbios name = <YOUR_HOST_NAME>
```

The only caveat is that it must be less than 15 characters.

The complete annotated smb.conf file parameters is located [**_here _**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

Im using googles DNS, for some reason when i set my router to handle it i was still getting redirected. Odd because i have a nice router too.

---

### Post by redmk2 on 2010-12-15
> **pfunkman said:**
> Im using googles DNS, for some reason when i set my router to handle it i was still getting redirected. Odd because i have a nice router too.

I can give you some advice on how to overcome this, but it will have to be tomorrow (+12 hours from now).  Let me know if you want to do something then.

---

### Post by pfunkman on 2010-12-16
> **redmk2 said:**
> I can give you some advice on how to overcome this, but it will have to be tomorrow (+12 hours from now).  Let me know if you want to do something then.

I figured it out on the router but ran into some performance problems. Set it up with the OpenDNS servers and its all smooth as butter. I think im done screwing with it for now. :p

Thanks for the help.

---

