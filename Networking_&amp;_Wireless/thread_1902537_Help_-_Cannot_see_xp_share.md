---
title: "Help - Cannot see xp share"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by l07 on 2011-12-31
I set up a workgroup in xp, but clicking on it says it's not accessible. I shared one folder.

Network magic somehow fixed it for xp: I can now see both ubuntu and xp shares.

I'd like to work on making sure ubuntu is able to see it too (it can see  its own share). The problem remains on ubuntu's side. After disabling  ufw, I was able to enter windows network to see both computers (prior to  that it said "Unable to mount location: Failed to retrieve share list  from server"), but now upon clicking on xp, it says the same thing.

Once I get this fixed, I'd like to reenable ufw, but I need an  explanation of the needed allowed rules: is it in or out, and why.

After I changed
wins support = no
to
wins support = yes
in smb.conf, it started displaying message "opening ...", but in the end displays the same error.

But pinging xp hostname works.

---

### Post by 2F4U on 2011-12-31
Did you already run through the troubleshooting section of the community documentation?

[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

And here are some more tutorials on how to get it working:

[http://www.liberiangeek.net/2010/03/how-to-quickly-access-windows-shares-from-ubuntu/](http://www.liberiangeek.net/2010/03/how-to-quickly-access-windows-shares-from-ubuntu/)
[http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/](http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/)
[http://www.liberiangeek.net/2011/05/connect-ubuntu-11-04-and-windows-systems-via-sambapart-two/](http://www.liberiangeek.net/2011/05/connect-ubuntu-11-04-and-windows-systems-via-sambapart-two/)
[http://www.liberiangeek.net/2011/05/connect-ubuntu-11-04-and-windows-systems-via-sambapart-three/](http://www.liberiangeek.net/2011/05/connect-ubuntu-11-04-and-windows-systems-via-sambapart-three/)

---

### Post by l07 on 2012-01-03
I've read all that and it doesn't help.

---

### Post by BLTicklemonster on 2012-01-03
I'm not reading all those, but I will ask, did you edit /etc/samba/smb.conf to show the linux box workgroup name the same as the windows workgroup?

That's the main number one problem I have. Updates somehow mess smb.conf up and I have found that I just have to go back and make sure that's correct every time.

---

### Post by Morbius1 on 2012-01-03
**** Give this a shot:**

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section - right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```Then restart samba:
```
sudo service smbd restart
``````
sudo service nmbd restart
```Then wait about 5 minute for the network reset itself.

** ** wins support**
> wins support = noThis is the default setting of Samba.
> wins support = yesThis has turned your Linux box into a WINS server. Nothing wrong with that if that's what you want to do but you will have to take steps to make that happen. You will need to give that Linux box a static ip address and you will have to modify the network configuration of all the other machines on your network to point to that ip address for name resolution to take place.

** ** ufw**

[1] If you look at the following file all of the rules for Samba have already been provided to you: /etc/ufw/applications.d/samba. Or you can run the following command to get a concise view:
```
sudo ufw app info Samba
```So to enable Samba through ufw:
```
sudo ufw allow Samba
```[2] Unfortunately there is an oversight in the basic ufw default setup that needs to be fixed:

Edit the file as root: /etc/default/ufw 

Look these lines:
# extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc"

And make the last line look like this:
# extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc [COLOR=#0000ff]**nf_conntrack_netbios_ns**[/COLOR]"


Then restart ufw

---

### Post by l07 on 2012-01-06
None of it helped. "name resolve order = bcast host lmhosts wins" actually made even xp not work. enabling and disabling wins didn't make any difference (it was initially enabled).

---

### Post by l07 on 2012-01-08
When the trial of Network magic expired it stopped working on xp, and now I don't see ubuntu's shares.

---

### Post by Morbius1 on 2012-01-09
Without any detailed information on how your Linux machine is set up all that anyone can do on this tread is take a WAG.

Please post the output of the following commands:
```
hostname
``````
testparm -s
``````
net usershare info --long
``````
smbtree
```

---

### Post by l07 on 2012-01-09
```
$ hostname
n-pc
$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    interfaces = 127.0.0.0/8, eth1
    bind interfaces only = Yes
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = No
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
$ net usershare info --long
[files media]
path=/media/files
comment=
usershare_acl=Everyone:R,N-PC\n:F,
guest_ok=n

[files]
path=/home/n/Desktop/files
comment=
usershare_acl=Everyone:R,N-PC\n:F,
guest_ok=n

$ smbtree
cli_start_connection: failed to connect to 192.168.1.36<20> (192.168.1.36). Error NT_STATUS_CONNECTION_REFUSED
cli_start_connection: failed to connect to N-PC<20> (192.168.1.36). Error NT_STATUS_CONNECTION_REFUSED
```

---

### Post by Morbius1 on 2012-01-09
Your smb.conf looks factory fresh except for all this stuff:
> interfaces = 127.0.0.0/8, eth1
    bind interfaces only = YesCan you explain the logic on wanting to do this? Is there a eth0 or wlan that you don't want samba to work with? And is eth1 the Ethernet port that you have connected to the router? I would comment out those lines unless there's a reason you have them there.

Assuming there a good reason for having them there then who or what is [B]192.168.1.36 ?

[/B]Is that your Linux box? Why not install nmap:
```
sudo apt-get install nmap
```Run the following command:
```
sudo nmap -sS -sU -T4 192.168.1.36
```And see if the samba ports are open:
> PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm


---

### Post by l07 on 2012-01-09
> **Morbius1 said:**
> And is eth1 the Ethernet port that you have connected to the router?
eth1 is that ethernet port.  I thought those lines would offer greater security. Turning those options off didn't restore connectivity.

```
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
```139 and 445 are closed, but ufw lists them: ```
139,445/tcp (Samba)        ALLOW IN    Anywhere

```

---

### Post by Morbius1 on 2012-01-09
Disable your firewall please:
```
sudo ufw disable
```
Then run smbtree again and see if the errors go away.

---

### Post by l07 on 2012-01-09
They did.```
WORKGROUP
    \\XP                     
    \\N-PC                   n-pc server (Samba, Ubuntu)
        \\N-PC\files media        
        \\N-PC\files              
        \\N-PC\IPC$               IPC Service (n-pc server (Samba, Ubuntu))
        \\N-PC\print$             Printer Drivers

```

---

### Post by Morbius1 on 2012-01-09
Now run this command again [COLOR=Blue]but change the ip address to the XP machine[/COLOR]:
```
 sudo nmap -sS -sU -T4 192.168.1.36
```
Are all of the samba ports open there as well?

---

### Post by l07 on 2012-01-09
I noticed that after disabling ufw, ubuntu became accessible for a bit from xp, but soon the connection was dropped with "the specified net name is no longer available."

```
135/tcp  open   msrpc
139/tcp  open   netbios-ssn
445/tcp  open   microsoft-ds
137/udp  open   netbios-ns
5355/udp closed unknown

```

---

### Post by terry2001 on 2012-01-09
Hi all,
         I had similar problem and found from a previous post that adding "ALL: ALL @192.168.1.1/24" to the end of /etc/hosts.allow file.

Worked for me hope it helps
                                         Terry

---

### Post by l07 on 2012-01-09
That didn't work.

---

### Post by Morbius1 on 2012-01-09
You need to disable whatever firewall you have on XP long enough to see if it's getting in the way.

Since I have never personally seen the following error message:
> "the specified net name is no longer available."
I Googled it and got only 2 hits and one of them was your post. 

You might want to go to a Windows forum and see if they have a clue what it means.

---

### Post by redmk2 on 2012-01-09
> **l07 said:**
> They did.```
WORKGROUP
    \\XP                     
    \\N-PC                   n-pc server (Samba, Ubuntu)
        \\N-PC\files media        
        \\N-PC\files              
        \\N-PC\IPC$               IPC Service (n-pc server (Samba, Ubuntu))
        \\N-PC\print$             Printer Drivers

```


I don't see any shares for \\XP.  For all the details try running ```
smbtree -d3 
```

Post the output back here.

---

### Post by l07 on 2012-01-09
> **Morbius1 said:**
> You need to disable whatever firewall you have on XP long enough to see if it's getting in the way.

Since I have never personally seen the following error message:

I Googled it and got only 2 hits and one of them was your post. 

You might want to go to a Windows forum and see if they have a clue what it means.

Searching for the error message without quotes works. Disabling all firewalls didn't make it work.
```

$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface eth1 ip=fe80::2e0:18ff:fee8:701d%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.36 bcast=192.168.1.255 netmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
```

---

### Post by redmk2 on 2012-01-10
> **l07 said:**
> 
```

$ smbtree -d3
...
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
[B][COLOR="Red"]Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot[/COLOR][/B]
...
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
...
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
[B][COLOR="Red"]Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot[/COLOR][/B]

```

What you sent doesn't appear to be the complete output.  But with what I do see, the info in red usually indicates a failed login.

The 2 entries are: 

[LIST]
[*]Failed connection to the Local Master Browser (LMB)
[*]Failed attempt to connect to resolve the WORKGROUP name (//XP ?)
[/LIST] 

As well as the shares on this host, it appears that the LMB is 192.168.1.27 (//XP ?) as well.

---

### Post by l07 on 2012-01-10
That was  the complete output. xp is 192.168.1.27. What do I need to do to fix this?

---

### Post by l07 on 2012-01-12
.

---

### Post by l07 on 2012-01-13
.

---

### Post by l07 on 2012-01-14
.

---

### Post by l07 on 2012-01-14
Still unsolved.

---

### Post by pytheas22 on 2012-01-14
I'm afraid I'm not much of a samba guy and don't have suggestions for figuring out why your workgroup share isn't working beyond what's already been offered.  Some further ideas for testing would be to install a Windows XP virtual machine inside your Ubuntu system and see whether it can access the shared folder; if it can, then you'll know it's not a firewall or other network-connectivity issue on either the Ubuntu or XP end, but a problem with the way the Ubuntu client is configured.

But thinking a little more outside the box for other approaches to your problem, maybe a fallback solution would be to use a different file-sharing protocol altogether.  One option would be to install an NFS server on Ubuntu and NFS client on Windows.  You could also try sshfs, for which there is [apparently a Windows client]("http://dokan-dev.net/en/download/#sshfs").

Neither of these approaches is ideal, and it's possible that they'll also be affected by whichever networking issue is causing your current share to fail, but perhaps at this point they're worth a try.

---

### Post by CharlesA on 2012-01-14
Are you able to connect via ip address?

---

### Post by l07 on 2012-01-14
No, connecting via ip doesn't work as far as I can tell. I tried ```
nautilus smb://192.169.1.27
``` which returns ```
Could not display "smb://192.169.1.27/".
Error: Failed to retrieve share list from server
Please select another viewer and try again.
``` But ```
nautilus smb://192.168.1.36
``` (ubuntu's ip) does work.

pytheas22, I'll see if I can test using a virtual machine. I'll also take a look at the other protocols you suggested.

---

### Post by CharlesA on 2012-01-15
Well the problem isn't with Ubuntu (.36) then, it's a problem with the way the XP box is configured. I can connect to shares on an XP box just fine from my Lucid box.

Do you have any shares defined on the XP box? if there are no shares, you wouldn't be able to connect.

---

### Post by Morbius1 on 2012-01-15
@CharlesA, although I agree with your conclusion I disagree with how you got it :wink:

> Could not display "smb://192.169.1.27/".
Error: Failed to retrieve share list from server
Please select another viewer and try again.Based on the other info posted here 192.169.1.27 is not the ip address of the WinXP box. More likely it's 192.168.1.27 - especially since his Ubuntu box is also in the 192.168.1.x range.

---

### Post by CharlesA on 2012-01-15
Wow, I totally missed that typo in the ip address. Thanks.

---

### Post by l07 on 2012-01-15
Yes, it's 168. I only made that mistake in the last attempt to connect via ip; the result is the same with the correct ip.

Yes, there is a single share on xp. How do I determine what's wrong with xp's configuration?

---

### Post by CharlesA on 2012-01-15
Try connecting to it from another Windows box.

In the previous smbtree, it didn't show any shares on the XP box.

---

### Post by l07 on 2012-01-15
I don't have another xp pc. To check the shares I used shareenum, which didn't show any. So I went to the properties of the folder I was sharing, and found out that it was no longer shared. I think network magic disabled it when trial expired. So I enabled it, which restored ubuntu's visibility from xp. Although shareenum still doesn't list any shares, it's working in xp, but not in ubuntu. Ubuntu can now enter the Windows Network, but there is nothing in there.

smbtree doesn't return anything currently.

```
$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface eth1 ip=fe80::2e0:18ff:fee8:701d%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.36 bcast=192.168.1.255 netmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
Connecting to 192.168.1.27 at port 139
Error connecting to 192.168.1.27 (Success)
cli_start_connection: failed to connect to 192.168.1.27<20> (192.168.1.27). Error NT_STATUS_UNSUCCESSFUL

```If I disable firewall on xp, the connectivity isn't restored, but the output changes:

```
$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface eth1 ip=fe80::2e0:18ff:fee8:701d%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.36 bcast=192.168.1.255 netmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215

```

and smbtree returns WORKGROUP.

---

### Post by CharlesA on 2012-01-15
Well, even if you don't have any shares on the machine, it should look something like this:

```

charles@Lucid:~$ smbtree
Enter charles's password:
WORKGROUP
        \\THOR
                \\THOR\IPC$             IPC Service ()
                \\THOR\Shared           Shared Folder
                \\THOR\Music            Music Folder
                \\THOR\ISOs             ISO Folder
                \\THOR\DVDs             DVD Folder
                \\THOR\Charles          Charles' Folder

        \\SOL
                \\SOL\C$                Default share
                \\SOL\ADMIN$            Remote Admin
                \\SOL\IPC$              Remote IPC

```

Thor is my Ubuntu box, Sol is my XP box.

```
charles@Lucid:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::a00:27ff:fef6:73aa%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.32 bcast=192.168.1.255 netmask=255.255.255.0
Enter charles's password:
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to host=192.168.1.2
Connecting to 192.168.1.2 at port 445
Connecting to 192.168.1.2 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to host=192.168.1.2
Connecting to 192.168.1.2 at port 445
Connecting to 192.168.1.2 at port 139
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
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to host=192.168.1.2
Connecting to 192.168.1.2 at port 445
Connecting to 192.168.1.2 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\THOR
Connecting to host=THOR
resolve_lmhosts: Attempting lmhosts lookup for name THOR<0x20>
resolve_wins: Attempting wins lookup for name THOR<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name THOR<0x20>
Connecting to 192.168.1.2 at port 445
Connecting to 192.168.1.2 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\THOR\IPC$             IPC Service ()
                \\THOR\Shared           Shared Folder
                \\THOR\Music            Music Folder
                \\THOR\ISOs             ISO Folder
                \\THOR\DVDs             DVD Folder
                \\THOR\Charles          Charles' Folder
        \\SOL
Connecting to host=SOL
resolve_lmhosts: Attempting lmhosts lookup for name SOL<0x20>
resolve_wins: Attempting wins lookup for name SOL<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SOL<0x20>
Connecting to 192.168.1.40 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\SOL\C$                Default share
                \\SOL\ADMIN$            Remote Admin
                \\SOL\IPC$              Remote IPC

```

---

### Post by l07 on 2012-01-16
But the tree isn't printed.

---

### Post by CharlesA on 2012-01-16
> **l07 said:**
> But the tree isn't printed.
That tells me that something is not right with the config on the XP machine.

Is it a Home or Professional version? Have you turned off "Simple file sharing?"

---

### Post by l07 on 2012-01-16
Professional. Yes, it's set to Classic.

---

### Post by CharlesA on 2012-01-16
Going off the results of the smbtree -d3 command that you ran that doesn't work and the one I ran that does work - it looks like port 139 is closed. Can you confirm this with nmap?

---

### Post by l07 on 2012-01-16
It seems to be open:

```
$ sudo nmap -sS -sU -T4 192.168.1.27
Not shown: 998 open|filtered ports, 997 filtered ports
PORT     STATE  SERVICE
135/tcp  open   msrpc
139/tcp  open   netbios-ssn
445/tcp  open   microsoft-ds
137/udp  open   netbios-ns
5355/udp closed unknown

$ sudo nmap -sS -sU -T4 192.168.1.36
Not shown: 1992 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
68/udp   open|filtered dhcpc
123/udp  open          ntp
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
1900/udp open|filtered upnp
5353/udp open|filtered zeroconf
```

---

### Post by CharlesA on 2012-01-16
I would try to connect with another Windows box and go from there. I think we have reached the limit of what we can do from Linux, as nothing is making sense.

---

### Post by l07 on 2012-01-21
I have inserted a different drive into the ubuntu pc with xp on it and was able to connect to the lan. Both pc's are accessible from each other. What do I need to do next?

---

### Post by CharlesA on 2012-01-21
The next step would be to try to connect to the Ubuntu box from a different Windows box.

Did you set the smbpasswd of the samba users?

---

### Post by l07 on 2012-01-29
No, I didn't set it. After your post I tried: sudo smbpasswd -a n
/etc/samba/smbusers: n = "n"

Now it lists the shares on xp, but trying to open a share generates a login box that doesn't accept the xp username and password and just keeps reappearing.

Currently trying to connect to ubuntu from another xp pc isn't working out. If it's really necessary I could reinstall xp on a different pc, since just plugging in the hard drive into a different pc doesn't work well neither with xp nor ubuntu.
```
$ smbtree
WORKGROUP
    \\XP                     
    \\N-PC                   n-pc server (Samba, Ubuntu)
        \\N-PC\files media        
        \\N-PC\files              
        \\N-PC\IPC$               IPC Service (n-pc server (Samba, Ubuntu))
        \\N-PC\print$             Printer Drivers
``````

$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
interpret_interface: using netmask value 8 from config file on interface lo
added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
added interface eth1 ip=fe80::2e0:18ff:fee8:701d%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.36 bcast=192.168.1.255 netmask=255.255.255.0
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to host=192.168.1.27
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\XP                     
Connecting to host=XP
resolve_lmhosts: Attempting lmhosts lookup for name XP<0x20>
resolve_wins: Attempting wins lookup for name XP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name XP<0x20>
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\N-PC                   n-pc server (Samba, Ubuntu)
Connecting to host=N-PC
resolve_lmhosts: Attempting lmhosts lookup for name N-PC<0x20>
resolve_wins: Attempting wins lookup for name N-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name N-PC<0x20>
Connecting to 127.0.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\N-PC\files media        
        \\N-PC\files              
        \\N-PC\IPC$               IPC Service (n-pc server (Samba, Ubuntu))
        \\N-PC\print$             Printer Drivers

```

After I tried again, it no longer even shows the login box, but gives a different error: "Failed to mount Windows share."

---

### Post by CharlesA on 2012-01-29
Not sure what else to do except purging and reinstalling Samba and seeing what happens.

---

### Post by l07 on 2012-01-30
How would I do that?

---

### Post by CharlesA on 2012-01-30
```
sudo apt-get purge samba
```

```
sudo apt-get update && sudo apt-get install samba
```

---

### Post by l07 on 2012-01-30
Is there a command to backup all the config files before purging? If I knew the file paths, I could just copy them. I think it's /etc/samba/*, /var/lib/samba/*. Is there anything else or a more specific pattern?

---

### Post by CharlesA on 2012-01-30
The only one you really need to back up is /etc/samba/smb.conf

I just want to get a clean slate.

---

### Post by l07 on 2012-02-26
Reinstalled. What's next?

---

### Post by CharlesA on 2012-02-27
Try setting up the shares again and see what happens.

---

### Post by l07 on 2012-02-28
The shares on ubuntu are still there, they weren't deleted. Maybe the reinstallation didn't clean everything?

---

### Post by CharlesA on 2012-02-28
It should have if you wiped the drive and reinstalled from scratch. Hmm..

---

### Post by Morbius1 on 2012-02-29
@CharlesA,
> **l07 said:**
> The shares on ubuntu are still there, they weren't deleted. Maybe the reinstallation didn't clean everything?
> **CharlesA said:**
> It should have if you wiped the drive and reinstalled from scratch. Hmm..
He purged and reinstalled the package "samba" not the whole OS. The problem is that smb.conf doesn't come from "samba" it comes from the package "samba-common". So after reinstalling "samba" his old smb.conf file was still in place and in charge.

Here's what is probably my last guess on this dilemma. The OP did not use WinXP's "Simple Sharing" to creae the share so he's running in "Win2K" or Win7" mode where all network users are expected to be other Windows machines and as such are expected to pass a username and password automatically. Combine that with Windows perpetual confusion over how to handle the "everyone" group and the "guest" and "anonymous logon" users and you end up with a mess.

I'm betting that if the OP where to run the following derivation of the smbtree command he just might see \\XP expand to it's shares:
```
smbtree -U winxp-user-name
```If true then run the following command:
```
 nautilus smb://winxp-user-name@192.169.1.27
```If a miracle happens and Nautilus actually opens up to that location bookmark the darn thing: Bookmarks > Add bookmark. It will show up on the left panel of nautilus just like a "mapped drive" does on explorer.

If that doesn't work it's the best I've got. My recommendation at that point is to install Dukto ( [http://code.google.com/p/dukto/downloads/list](http://code.google.com/p/dukto/downloads/list) ) on both the WinXP machine and the Ubuntu machine and "push" individual files from one OS to the other as needed. It's not a replacement for samba or any other file sharing protocol it just allows a person to transfer a file from A to B.

---

### Post by CharlesA on 2012-02-29
That makes sense. Thanks Morbius1. If that doesn't work, I don't know what else to do.

---

### Post by l07 on 2012-03-04
It produces the same output regardless of whether I input the correct password:
$ smbtree -U Owner
cli_start_connection: failed to connect to 192.168.1.36<20> (192.168.1.36). Error NT_STATUS_CONNECTION_REFUSED
cli_start_connection: failed to connect to N-PC<20> (192.168.1.36). Error NT_STATUS_CONNECTION_REFUSED

I could reinstall samba-common (smb.conf comes from this package) if that would help solve this.

---

### Post by l07 on 2012-03-16
Any suggestions?

---

### Post by BLTicklemonster on 2012-03-17
Sorry, mate. The smb.conf file I sent you got my network working with Ubuntu, Windows 7, and Windows XP. I can't help you at all, because you certainly did make sure your firewall on your windows machine was off. I've tried different things with it, but turning it completely off (W 7, also) is the only way to get network connectivity with Ubuntu here. I just trust my firewall on the router to do it's job and I don't keep sensitive information here. (like if your life can be ruined because someone hacked your computer, than you're way too trusting in my book anyway. They're neat toys that you can also use for work, in my opinion. And I know other folks disagree, so they don't have to come in here and voice their opinions...)

No wait. I just read and replied to your message. Do exactly what I say in the new message.

---

### Post by l07 on 2012-03-17
I changed two lines in BLTicklemonster's smb.conf to:
```
workgroup = WORKGROUP
   netbios name = xp
```Firewalls on both xp and ubuntu are disabled.

Using BLTicklemonster's smb.conf, ```
smbtree -U Owner
``` now shows the shares on xp, but it still says "Failed to retrieve share list from server" when clicking on xp in nautilus, and ```
nautilus smb://192.169.1.27
``` still results in an error:
```
Could not display "smb://192.168.1.27/".
Error: Failed to retrieve share list from server
Please select another viewer and try again.
``````

$ smbtree
Enter n's password:
WORKGROUP
    \\XP                    
    \\N-PC                   n-pc server (Samba, Ubuntu)
        \\N-PC\files media        
        \\N-PC\files              
        \\N-PC\IPC$               IPC Service (n-pc server (Samba, Ubuntu))
        \\N-PC\print$             Printer Drivers

``````

$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=fe80::2e0:18ff:fee8:701d%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.36 bcast=192.168.1.255 netmask=255.255.255.0
Enter n's password:
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
Connecting to host=192.168.1.36
Connecting to 192.168.1.36 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
Connecting to host=192.168.1.36
Connecting to 192.168.1.36 at port 445
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
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
Connecting to host=192.168.1.36
Connecting to 192.168.1.36 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\XP                    
Connecting to host=XP
name_resolve_bcast: Attempting broadcast lookup for name XP<0x20>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\N-PC                   n-pc server (Samba, Ubuntu)
Connecting to host=N-PC
name_resolve_bcast: Attempting broadcast lookup for name N-PC<0x20>
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
Connecting to 192.168.1.36 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\N-PC\files media        
        \\N-PC\files              
        \\N-PC\IPC$               IPC Service (n-pc server (Samba, Ubuntu))
        \\N-PC\print$             Printer Drivers

``````

$ smbtree -U Owner
Enter Owner's password:
WORKGROUP
\\XP
\\XP\Printer Microsoft XPS Document Writer
\\XP\network
\\XP\SharedDocs
\\XP\print$ Printer Drivers
\\XP\IPC$ Remote IPC
\\N-PC n-pc server (Samba, Ubuntu)
\\N-PC\files media
\\N-PC\files
\\N-PC\IPC$ IPC Service (n-pc server (Samba, Ubuntu))
\\N-PC\print$ Printer Drivers
``````

$ smbtree -d3 -U Owner
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth1 ip=fe80::2e0:18ff:fee8:701d%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.36 bcast=192.168.1.255 netmask=255.255.255.0
Enter Owner's password:
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
Connecting to host=192.168.1.36
Connecting to 192.168.1.36 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
Connecting to host=192.168.1.36
Connecting to 192.168.1.36 at port 445
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
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
Connecting to host=192.168.1.36
Connecting to 192.168.1.36 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
    \\XP                    
Connecting to host=XP
name_resolve_bcast: Attempting broadcast lookup for name XP<0x20>
Got a positive name query response from 192.168.1.27 ( 192.168.1.27 )
Connecting to 192.168.1.27 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\XP\Printer            Microsoft XPS Document Writer
        \\XP\network            
        \\XP\SharedDocs        
        \\XP\print$             Printer Drivers
        \\XP\IPC$               Remote IPC
    \\N-PC                   n-pc server (Samba, Ubuntu)
Connecting to host=N-PC
name_resolve_bcast: Attempting broadcast lookup for name N-PC<0x20>
Got a positive name query response from 192.168.1.36 ( 192.168.1.36 )
Connecting to 192.168.1.36 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\N-PC\files media        
        \\N-PC\files              
        \\N-PC\IPC$               IPC Service (n-pc server (Samba, Ubuntu))
        \\N-PC\print$             Printer Drivers
```

---

### Post by Morbius1 on 2012-03-17
```
nautilus smb://Owner@192.169.1.27
```

---

### Post by BLTicklemonster on 2012-03-17
Actually, try this [http://ubuntuforums.org/showthread.php?t=1502265&highlight=bill-GF6100-M754&page=6](http://ubuntuforums.org/showthread.php?t=1502265&highlight=bill-GF6100-M754&page=6) Your name is 16 characters long.


> **Morbius1 said:**
> The biggest problem is the name of BILL-GF6100-M754. It's 16 characters long. It can only be 15 characters long. You can fix that for samba purposes within samba itself:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
``` Add the following line to the [global] section right under the "workgroup" line so you can find it later:
```
netbios name = bill-M754
```Save smb.conf and restart samba:
```
sudo service smbd restart
```Wait a few minutes for the network to settle down after a samba restart and try it again.

---

### Post by l07 on 2012-03-17
> **Morbius1 said:**
> ```
nautilus smb://Owner@192.168.1.27
```
That produces the same result.

> **BLTicklemonster said:**
> Actually, try this [http://ubuntuforums.org/showthread.php?t=1502265&highlight=bill-GF6100-M754&page=6](http://ubuntuforums.org/showthread.php?t=1502265&highlight=bill-GF6100-M754&page=6) Your name is 16 characters long.
But both computers have names with fewer than 16 characters: n-pc and xp. Those are exact names.

---

### Post by Morbius1 on 2012-03-17
Then you need to go back and put your Windows box and your Linux box in whatever state it was in that made this possible:
> **l07 said:**
> 
$ smbtree -U Owner
Enter Owner's password:
WORKGROUP
\\XP
\\XP\Printer Microsoft XPS Document Writer
\\XP\network
\\XP\SharedDocs
\\XP\print$ Printer Drivers
\\XP\IPC$ Remote IPC
\\N-PC n-pc server (Samba, Ubuntu)
\\N-PC\files media
\\N-PC\files
\\N-PC\IPC$ IPC Service (n-pc server (Samba, Ubuntu))
\\N-PC\print$ Printer Drivers

---

### Post by l07 on 2012-03-17
smbtree -U Owner still lists shares on xp, but they're still inaccessible in nautilus.

---

### Post by BLTicklemonster on 2012-03-17
Sorry, but I thought you were using 

smbtree -U Owner

for a netbios name for some reason, lol. Admittedly, I thought it strange, but considering the troubles, I thought you were being fatalistic in your name choise.

I'm drawing a blank, sorry.

---

### Post by l07 on 2012-03-18
Does the latest dukto release work on 10.10? I installed dukto_5.0-1_i386_ubuntu_11.04.deb, but upon launching it, the program window is blank.

---

### Post by Morbius1 on 2012-03-19
Dukto found itself in a bit of a quandary.  In the good old days there was only one Dukto ( one for each OS - Linux, Windows, Mac ) and as far as I could tell ran on everything. Gnome3 made a mess of that and when you add Unity on top of that it was too much for it. Since then the developer has had to create different versions for each desktop and even for each desktop version.

The one you downloaded will run on Ubuntu 11.04 - not 11.10 or 10.10 - but for 11.04.

You've got 2 choices:

* Download the one for your desktop: DuktoR4-Linux.tar.gz
It's OK if Linux is at Version4 and Windows is at Version5.

* Use Transfer-On-Lan instead: [http://code.google.com/p/transfer-on-lan/downloads/list](http://code.google.com/p/transfer-on-lan/downloads/list)

It's java based which may be an issue since all your OS's have to have java installed. But then Java itself handles the interface issues between the application and the desktop so the application itself doesn't have the problem that Dukto ended up with. 

Either way will work since they both use the same underlying protocol.

Give DuktoR4 a shot first. I have both installed.

---

### Post by l07 on 2012-04-05
DuktoR4 works. What about getting samba working?

---

### Post by Morbius1 on 2012-04-05
You've pretty much exhausted everything you can do on the Linux end so until you figure out what's wrong with your XP install I'd stick with Dukto.

---

### Post by CharlesA on 2012-04-05
> **Morbius1 said:**
> You've pretty much exhausted everything you can do on the Linux end so until you figure out what's wrong with your XP install I'd stick with Dukto.
+1 to that.

---

