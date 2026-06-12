---
title: "Samba shares not accessible - restart fix"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by atomicben on 2011-05-04
Since the latest update for Maverick (about a week ago) my samba isn't working right.  I tried updating to Natty and I'm still having the same problems.

Symptoms:
Other PC's (including: a couple windows systems (xp and vista), a couple old xboxes (with xbmc), one other ubuntu machine running Maverick) are having problems connecting to my server shares.  It seems that after my server is running for a period of time (amount of time not determined) others cannot connect to it's shares.  However, after reboots or restarting samba, everything kicks back in and people can read from my shares again.

Work Around:
As already mentioned, if i restart my server or just restart samba with:

> 
sudo service smbd restart
Everything seems to work.  And as long as people are connected and using the shares there isn't a problem (fast speeds, good sharing all around, no disconnects)

Here's my full but censored smb.conf:

> 
[global]
;    netbios name = <censored: it's first initial and last name.  eg. jdoe>
    server string = Samba file and print server
    workgroup = <censored: one word, not a reserved word>
    security = share
    hosts allow = 127. 192.168.0.
    interfaces = 127.0.0.1/8 192.168.0.0/24
    bind interfaces only = yes
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    printcap name = cups
;    load printers = yes
    cups options = raw
;    printing = cups
;    guest account = nobody
    log file = /var/log/samba/samba.log
    max log size = 1000
;    null passwords = no
    username level = 6
    password level = 6
;    encrypt passwords = yes
    unix password sync = yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = no
    domain master = no
;    preferred master = no
;    domain logons = no
    os level = 33
    logon drive = m:
    logon home = \\%L\homes\%u
    logon path = \\%L\profiles\%u
    logon script = %G.bat
;    time server = no
    name resolve order = wins lmhosts bcast
;    wins support = no
;    wins proxy = no
    dns proxy = no
;    preserve case = yes
;    short preserve case = yes
    client use spnego = no
    client signing = no
    client schannel = no
;    server signing = no
    server schannel = no
;    nt pipe support = yes
;    nt status support = yes
    allow trusted domains = no
    obey pam restrictions = yes
;    enable spoolss = yes
;    client plaintext auth = no
;    disable netbios = no
    follow symlinks = no
    update encrypted = yes
;    pam password change = no
    passwd chat timeout = 120
;    hostname lookups = no
;    passdb backend = tdbsam
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete user script = /usr/sbin/userdel '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    machine password timeout = 120
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind use default domain = yes
    winbind separator = @
    winbind cache time = 360
    winbind trusted domains only = yes
    winbind nested groups = no
    winbind nss info = no
;    winbind refresh tickets = no
;    winbind offline logon = no
;    guest ok = no

[homes]
    comment = Home Directories
    path = /home
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = no
;    available = yes
    browseable = no
;    guest ok = no
;    printable = no
    create mode = 0600
    directory mask = 0700
    locking = no
    strict locking = no

[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = No
;    guest ok = no
    printable = yes
    locking = no
    strict locking = no

[pdf-documents]
    path = /home/pdf-documents
    comment = Converted PDF Documents
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    lprm command = 

[video]
    path = /media/data/video
    comment = Videos
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[music]
    path = /media/data/music
    comment = Music
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[software]
    path = /media/data/software
    comment = Software
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[shared]
    path = /media/data/shared
    comment = Public Share
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

It seems to time out.  What could be my problem?

There's one line:

> machine password timeout = 120

That kinda bugs me but that's a password timeout, not a sharing timeout.  Or am I wrong?

---

### Post by atomicben on 2011-05-11
I have a better idea of what's happening now.  It's not timing out as I first thought.  

When I first start or reboot my computer samba shares are not accessable.  

All I have to do to get things going again is:

> sudo service smbd restart 			 		

I am not running wicd.  I'm running the regular old network manager.

I've played around with my smb.conf to see if that made any difference, it doesn't but I'll post it here anyway.

> 
[global]
    netbios name = <censored>
    server string = Samba file and print server
    workgroup = <censored>
    security = share
    hosts allow = 127. 192.168.0.
    interfaces = 127.0.0.1/8 192.168.0.0/24
    bind interfaces only = yes
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    printcap name = cups
;    load printers = yes
    cups options = raw
;    printing = cups
;    guest account = nobody
    log file = /var/log/samba/samba.log
    max log size = 1000
;    null passwords = no
    username level = 6
    password level = 6
;    encrypt passwords = yes
    unix password sync = yes
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    local master = no
    domain master = no
;    preferred master = no
;    domain logons = no
    os level = 33
    logon drive = m:
    logon home = \\%L\homes\%u
    logon path = \\%L\profiles\%u
    logon script = %G.bat
;    time server = no
    name resolve order = wins lmhosts bcast
;    wins support = no
;    wins proxy = no
    dns proxy = no
;    preserve case = yes
;    short preserve case = yes
    client use spnego = no
    client signing = no
    client schannel = no
;    server signing = no
    server schannel = no
;    nt pipe support = yes
;    nt status support = yes
    allow trusted domains = no
    obey pam restrictions = yes
;    enable spoolss = yes
;    client plaintext auth = no
;    disable netbios = no
    follow symlinks = no
    update encrypted = yes
;    pam password change = no
    passwd chat timeout = 120
;    hostname lookups = no
;    passdb backend = tdbsam
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete user script = /usr/sbin/userdel '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    machine password timeout = 120
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind use default domain = yes
    winbind separator = @
    winbind cache time = 360
    winbind trusted domains only = yes
    winbind nested groups = no
    winbind nss info = no
;    winbind refresh tickets = no
;    winbind offline logon = no
;    guest ok = no

[homes]
    comment = Home Directories
    path = /home
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = no
;    available = yes
    browseable = no
;    guest ok = no
;    printable = no
    create mode = 0600
    directory mask = 0700
    locking = no
    strict locking = no

[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = No
;    guest ok = no
    printable = yes
    locking = no
    strict locking = no

[pdf-documents]
    path = /home/pdf-documents
    comment = Converted PDF Documents
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    lprm command = 

[video]
    path = /media/data/video
    comment = Videos
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[music]
    path = /media/data/music
    comment = Music
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[software]
    path = /media/data/software
    comment = Software
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no

[shared]
    path = /media/data/shared
    comment = Public Share
;    available = yes
;    browseable = yes
    writeable = yes
    guest ok = yes
    locking = no
    strict locking = no



Any ideas?

Is there a log file that might help me with this?  How can i filter dmesg to only show samba stuff?

Thanks.

---

### Post by atomicben on 2011-05-18
Sorry for bumping again.  

To summarize the problem: After a boot or reboot I cannot access my samba shares.  

If I run:

```

sudo service smbd restart

```Everything works fine until my next boot/reboot.

I cleared out my samba.log and rebooted.  Here are the full contents of the log file.

```

[2011/05/18 20:15:46.105451,  1] smbd/service.c:1251(close_cnum)
  192.168.0.199 (192.168.0.199) closed connection to service video
[2011/05/18 20:15:46.106203,  1] smbd/service.c:1251(close_cnum)
  192.168.0.101 (192.168.0.101) closed connection to service video
[2011/05/18 20:15:46.109027,  1] smbd/service.c:1251(close_cnum)
  192.168.0.199 (192.168.0.199) closed connection to service video
[2011/05/18 20:16:33.318367,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/05/18 20:16:33.353070,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/05/18 20:16:33.354574,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option
[2011/05/18 20:16:35.090507,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1

```
Why is it saying connection closed and connection refused?  On my xbox it says "Cannot connect to network server".

After:
```

 sudo service smbd restart
 
```The log says:

```

[2011/05/18 20:26:02.100574,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2011/05/18 20:35:52.053530,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option
[2011/05/18 20:36:00.518143,  1] smbd/service.c:1070(make_connection_snum)
  192.168.0.199 (192.168.0.199) connect to service video initially as user nobody (uid=65534, gid=65534) (pid 1849)

```

Then everything works fine again.  So frustrating.

---

### Post by capscrew on 2011-05-18
> **atomicben said:**
> Sorry for bumping again.  

To summarize the problem: After a boot or reboot I cannot access my samba shares.  

If I run:

```

sudo service smbd restart

```Everything works fine until my next boot/reboot.

I cleared out my samba.log and rebooted.  Here are the full contents of the log file.

```

[2011/05/18 20:15:46.105451,  1] smbd/service.c:1251(close_cnum)
  192.168.0.199 (192.168.0.199) closed connection to service video
[2011/05/18 20:15:46.106203,  1] smbd/service.c:1251(close_cnum)
  192.168.0.101 (192.168.0.101) closed connection to service video
[2011/05/18 20:15:46.109027,  1] smbd/service.c:1251(close_cnum)
  192.168.0.199 (192.168.0.199) closed connection to service video
[2011/05/18 20:16:33.318367,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/05/18 20:16:33.353070,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/05/18 20:16:33.354574,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option
[2011/05/18 20:16:35.090507,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1

```
Why is it saying connection closed and connection refused?  On my xbox it says "Cannot connect to network server".

After:
```

 sudo service smbd restart
 
```The log says:

```

[2011/05/18 20:26:02.100574,  0] winbindd/winbindd_cache.c:3076(initialize_winbindd_cache)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2011/05/18 20:35:52.053530,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option
[2011/05/18 20:36:00.518143,  1] smbd/service.c:1070(make_connection_snum)
  192.168.0.199 (192.168.0.199) connect to service video initially as user nobody (uid=65534, gid=65534) (pid 1849)

```

Then everything works fine again.  So frustrating.

I just have to ask.  Are you running this at home using a workgroup with local logins; or is this a domain login setup with AD in the mix?

I see little details in your smb.conf that are incorrect, but the major factors are dependent on the environment the Samba (smbd and nmbd) operates in.

---

### Post by atomicben on 2011-05-19
Not a domain or active directory setup.  Just a local workgroup.

The smb.conf had previously only been edited by the samba GUI (I also tried gadmin samba gui).  It's only now I'm starting to take matters into my own hands with the smb.conf.

Any advice you have is appreciated.

---

### Post by capscrew on 2011-05-19
> **atomicben said:**
> Not a domain or active directory setup.  Just a local workgroup.

The smb.conf had previously only been edited by the samba GUI (I also tried gadmin samba gui).  It's only now I'm starting to take matters into my own hands with the smb.conf.

Any advice you have is appreciated.

There is no need for Winbind in a workgroup situation. >  "Winbind uses a UNIX implementation of Microsoft RPC calls, Pluggable Authentication Modules (PAMs), and the name service switch (NSS) ***to allow Windows NT domain users to appear and operate as UNIX users*** on a UNIX machine." ... "Winbind maintains a database called winbind_idmap.tdb in which it stores mappings between UNIX UIDs, GIDs, and NT SIDs.* **This mapping is used only for users and groups that do not have a local UID/GID.***"

As you are running only local logins and have no need to integrate into a Windows domain situation you should remove winbind altogether as a first step.  ```
sudo apt-get purge winbind
```  Next you need to edit the /etc/nsswitch.conf file back to original if you have molested it in any way.

Do you have LAN side DNS or some method of resolving DNS hostnames locally?  You need to be able to do that.  There is no need to worry about NetBIOS name resolution as the Samba nmbd daemon will convert DNS hostnames to NetBIOS names for Samba.

The next step is to start over with a new smb.conf file.  Did you make a copy the original smb.conf file?  I usually do this before I modify a system file.  That way if I have to revert back to the original file, I have the file in the same directory. ```
cp <conf.file> <conf.file.original
```

If you did not, the original file exists at ```
/usr/share/samba/smb.conf
```

Any user login should from a windows host should also be a local user on the Ubuntu host.  All the workgroup users also need to be in the smbpasswd data base. ```
sudo smbpasswd -a
```

With the original smb.conf file in place and confirmed working local DNS resolution (hosts or DNS), along with Samba users in the smbpasswd database,  you can start to add back the shares.  The only thing other than the shares you need to edit is the WORKGROUP name. All the other default parameters are fine just the way they are.

In short you need to do these steps:
[LIST]
[*]Remove winbind from the system
[*]Provide DNS name resolution for LAN
[*]Create Ubuntu users
[*]Create Samba users (populate the smbpasswd database)
[*]Revert to a clean copy of the /etc/samba/smb.conf file
[*]Add WORKGROUP name and shares to smb.conf
[*]Add your shares
[/LIST]

This is a good [**_[COLOR="Blue"]guide[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1590").  It assumes you have DNS resolution working.

---

### Post by atomicben on 2011-05-19
Wow, thanks for the amazing reply.  

I do not have a LAN side DNS or hosts file.  Never needed one before.  I've always been able to connect to samba through \\servername\sharename 

I'm confused why doing a 'service smbd restart' works but it doesn't on boot.  I'd imagine that if there was a bad setting (or more) it would fail in every situation.  That's why this has been such an annoying problem.  

I will follow your steps and let you know what happens.

---

### Post by capscrew on 2011-05-19
> **atomicben said:**
> Wow, thanks for the amazing reply.  

I do not have a LAN side DNS or hosts file.  Never needed one before.  I've always been able to connect to samba through \\servername\sharename 
Except when you have trouble.  :-)> 

I'm confused why doing a 'service smbd restart' works but it doesn't on boot.  I'd imagine that if there was a bad setting (or more) it would fail in every situation.  That's why this has been such an annoying problem.  

I will follow your steps and let you know what happens.

You should not rely on winbind to provide you with name resolution.  This is what you are doing (e.g name resolution).  It can create bizarre reactions.  I have used the steps I provided you hundreds of times.  They work and are consistent with the Samba  developers intentions.

You MUST provide hosts/DNS for your Ubuntu machine.  This can be as simple as editing the /etc/hosts file and adding all the hosts in the LAN.   Post the output here of the /etc/hosts file you propose to use.

---

### Post by atomicben on 2011-05-20
capscrew,

Everything is back to normal!  I don't know exactly which step(s) fixed it (I hate that) but I'll tell you what I did.

I purged winbind with:

```
sudo apt-get purge winbind
```

I looked at the /etc/nsswitch.conf file but since I had never molested (or even heard of) it I left it be.

Although I always make a copy of a file before I molest it I grabbed ```
/usr/share/samba/smb.conf
``` instead of trusting my backup. BTW, I never even knew that existed so extra thanks for that tip!

Other Notes:

[LIST]
[*]I did not do anything for a DNS solution - didn't touch the hosts file.
[/LIST]

[LIST]
[*]Windoze users/passwords were already existing on my Ubuntu machine/Samba Server.
[/LIST]
Other Happy-endings:
My main ubuntu box could never see this other ubuntu box.  All of a sudden that kicked in!  Weird...

I'm betting that is was the winbind deal that was messing this up because I had purged and re-installed Samba a few times while troubleshooting and that didn't work so, anyway...

Thank you very much for taking the time to reply and for providing such concise instruction.

Happy May two-four!  Have a good weekend.

---

### Post by capscrew on 2011-05-20
> **atomicben said:**
> capscrew,

Everything is back to normal!  I don't know exactly which step(s) fixed it (I hate that) but I'll tell you what I did.

I purged winbind with:

```
sudo apt-get purge winbind
```

I looked at the /etc/nsswitch.conf file but since I had never molested (or even heard of) it I left it be.

Although I always make a copy of a file before I molest it I grabbed ```
/usr/share/samba/smb.conf
``` instead of trusting my backup. BTW, I never even knew that existed so extra thanks for that tip!

Other Notes:

[LIST]
[*]I did not do anything for a DNS solution - didn't touch the hosts file.
[/LIST]

[LIST]
[*]Windoze users/passwords were already existing on my Ubuntu machine/Samba Server.
[/LIST]
Other Happy-endings:
My main ubuntu box could never see this other ubuntu box.  All of a sudden that kicked in!  Weird...

I'm betting that is was the winbind deal that was messing this up because I had purged and re-installed Samba a few times while troubleshooting and that didn't work so, anyway...

Thank you very much for taking the time to reply and for providing such concise instruction.

Happy May two-four!  Have a good weekend.

Great to hear that all is well.  Yes winbind messes up lots of things when it is misapplied.  I'll bet your router provides some type of local nameservices (DNS).  Anyway it all works and that is the main thing

FYI -- Unless you corrupt the actual smbd or nmbd dasmons you only need to copy the spare smb.conf over to start again.  There should be no need to reinstall Samba most of the time.

You have a great weekend too.

---

### Post by atomicben on 2011-05-20
Well, if you think the router may have been involved, this article would not be complete without that information.

Linksys / Cisco WRT54G2 FW Ver 1.0.03

---

### Post by Using Debian on 2011-09-06
Just wanted to say thanks.  I will apply these steps as well.  If all goes well, this post will be my only on the subject ):P

---

### Post by inforvez on 2011-09-29
hello,

i have the same kind of problem, but with my printer:

When I first start or reboot my shared printer is not accessable by a windows user - note that my shared folder is accessible.  

All I have to do to get things going again is:


> sudo service smbd restart                      my smb.conf look like this:

> 

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = lmhosts host wins bcast
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    hosts allow = 192.168.
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    read only = No
    create mask = 0755
    guest ok = Yes
[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    hosts allow = 192.168.
    printable = Yes
    browseable = No
    browsable = NoAny ideas?

thanks

---

### Post by Ryanm2890 on 2012-07-04
My printer also becomes invisible on my shared network whenever a boot or reboot occurs and it becomes visible again when samba is restarted. If anyone can provide any insight as to why it works after samba restart but not after boot, I would greatly appreciate it. Thanks in advance.

---

### Post by bab1 on 2012-07-04
> **Ryanm2890 said:**
> My printer also becomes invisible on my shared network whenever a boot or reboot occurs and it becomes visible again when samba is restarted. If anyone can provide any insight as to why it works after samba restart but not after boot, I would greatly appreciate it. Thanks in advance.

Sounds like the nmbd process is not starting a boot time,  When things become invisible again, post back here the output of ```
ps -e|grep mbd
```

---

### Post by Ryanm2890 on 2012-07-04
> **bab1 said:**
> Sounds like the nmbd process is not starting a boot time,  When things become invisible again, post back here the output of ```
ps -e|grep mbd
```

When I type that in i get:```

683?       00:00:00 smbd
711?       00:00:00 smbd
1285?     00:00:00 smbd
```Also, the "mbd" is highlighted in red. I should have put in the above post that my printer becomes invisible to the other computer on the network, not the computer its plugged into. Forgive me if anything looks suspicious, I'm both a new to Linux and these forums. Thanks.

---

### Post by bab1 on 2012-07-04
> **Ryanm2890 said:**
> When I type that in i get:```

683?       00:00:00 smbd
711?       00:00:00 smbd
1285?     00:00:00 smbd
```Also, the "mbd" is highlighted in red.
...because that's the search term we used.> 
I should have put in the above post that my printer becomes invisible to the other computer on the network, not the computer its plugged into. Forgive me if anything looks suspicious, I'm both a new to Linux and these forums. Thanks.
It seems like nmbd (the Samba name service daemon) is not starting or quitting for no apparent reason.  I'll bet it's not starting.

What version of Ubuntu are you running?

Without changing anything, lets try and restart it *nmbd* with ```
sudo service nmbd restart
```

if it gripes then we will have to try these two commands```
sudo service nmbd stop
```...and then ```
sudo service nmbd start
```

---

### Post by Ryanm2890 on 2012-07-04
I'm using Ubuntu 12.04. When I try to restart it doesn't give me any problems. Thank you for your quick responses, this has been driving me crazy.

---

### Post by bab1 on 2012-07-04
> **Ryanm2890 said:**
> I'm using Ubuntu 12.04. When I try to restart it doesn't give me any problems. Thank you for your quick responses, this has been driving me crazy.
Post the output of this```
cat /etc/init/nmbd.conf 
```

---

### Post by Ryanm2890 on 2012-07-04
> **bab1 said:**
> Post the output of this```
cat /etc/init/nmbd.conf 
```

```

description "NetBIOS name server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]

expect fork
respawn

pre-start script
    [ -f /etc/samba/smb.conf ] || { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
    NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null || true`

    [ "x$NMBD_DISABLED" = xYes ] && { stop; exit 0; }

    exit 0
end script

exec nmbd -D

```So is this saying that NMBD is disabled upon startup?

---

### Post by bab1 on 2012-07-04
> **Ryanm2890 said:**
> ```

description "NetBIOS name server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]

expect fork
respawn

pre-start script
    **[COLOR="Red"]mkdir -p /var/run/samba[/COLOR]**
    [ -f /etc/samba/smb.conf ] || { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
    NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null || true`

    [ "x$NMBD_DISABLED" = xYes ] && { stop; exit 0; }

    exit 0
end script

exec nmbd -D

```So is this saying that NMBD is disabled upon startup?
No, this is the script to start nmbd but it has a bug.  Add the line I have added in red (above) to the file and it will work fine.

You can use this command to open an editor ```
gksudo gedit /etc/init/nmbd.conf
```... add the line and save the file.  It should start nmbd every time after that.

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=11515129&postcount=10") for the listing of the bugs and the fix.

---

### Post by Ryanm2890 on 2012-07-04
[LEFT]I updated that file to reflect the added line so it now reads:

```
 description "NetBIOS name server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo)
stop on runlevel [!2345]

expect fork
respawn

pre-start script
    mkdir -p /var/run/samba
    [ -f /etc/samba/smb.conf ] || { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
    NMBD_DISABLED=`testparm -s --parameter-name='disable netbios' 2>/dev/null || true`

    [ "x$NMBD_DISABLED" = xYes ] && { stop; exit 0; }

    exit 0
end script

exec nmbd -D

```

but my printer is still not visible on my network at startup. Any other ideas? Thanks.
[/LEFT]

---

