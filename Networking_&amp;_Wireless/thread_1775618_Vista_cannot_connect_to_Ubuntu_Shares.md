---
title: "Vista cannot connect to Ubuntu Shares"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by wwtorres on 2011-06-05
I have spent the last two weekends trying to get Vista and Ubuntu(natty) to work together.

From Ubuntu:
- I have disabled ufw
- setup a shared directory at /mnt/public (Permissions on public are 777)
- Ubuntu can access Vista shares.
- From the GUI, the "Network Servers" directory contains a "Windows Network" directory, but the Windows Network is empty.
- I can ping the Vista machine

From Vista:
- Nothing is visible.  The ubuntu PC itself is not listed in the "Network" folder or map.
- I have disabled all firewalls (including the router)
-  I can ping the ubuntu machine by IP address but cannot access it by IP address through
      - "Run" - I enter \\192.168.1.50, then get the logon pop-up.  I enter the ubuntu creds, then receive a "Windows cannot connect to \\192.168.1.50..." error message.
      - "Command Prompt" ftp (or sftp) - I get connection refused.
      - via "Web Browser" - I get the following message: "It works! This is the default web page for this server. The web server software is running but no content has been added, yet."  The problem is that it doesn't work.

Everything I have googled up so far has been problems connecting in the opposite direction.  I am trying to get to the Ubuntu machine.  Although I checked all the smb.conf, inetd.conf and a few other files that I've seen mentioned, I cannot get the Vista machine to connect to the ubuntu machine.

---

### Post by capscrew on 2011-06-05
> **wwtorres said:**
> I have spent the last two weekends trying to get Vista and Ubuntu(natty) to work together.

From Ubuntu:
- I have disabled ufw
- setup a shared directory at /mnt/public (Permissions on public are 777)
- Ubuntu can access Vista shares.
- From the GUI, the "Network Servers" directory contains a "Windows Network" directory, but the Windows Network is empty.
- I can ping the Vista machine

From Vista:
- Nothing is visible.  The ubuntu PC itself is not listed in the "Network" folder or map.
- I have disabled all firewalls (including the router)
-  I can ping the ubuntu machine by IP address but cannot access it by IP address through
      - "Run" - I enter \\192.168.1.50, then get the logon pop-up.  I enter the ubuntu creds, then receive a "Windows cannot connect to \\192.168.1.50..." error message.
      - "Command Prompt" ftp (or sftp) - I get connection refused.
      - via "Web Browser" - I get the following message: "It works! This is the default web page for this server. The web server software is running but no content has been added, yet."  The problem is that it doesn't work.

Everything I have googled up so far has been problems connecting in the opposite direction.  I am trying to get to the Ubuntu machine.  Although I checked all the smb.conf, inetd.conf and a few other files that I've seen mentioned, I cannot get the Vista machine to connect to the ubuntu machine.

How did you setup sharing?  Did you install Samba server?  Are you sure Samba is running?

---

### Post by wwtorres on 2011-06-05
How did I set up sharing?
 - [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

Did I install Samba?
 - Yes

Am I sure it's running?
 - Yes

---

### Post by capscrew on 2011-06-05
> **wwtorres said:**
> How did I set up sharing?
 - [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

In my opinion that howto is part of your problem.  It is outdated and in many cases it is inaccurate.
> 

Did I install Samba?
 - Yes

Are you also running Apache (maybe a LAMP server?> 

Am I sure it's running?
 - Yes
Please provide the following output (from the terminal)
```

pgrep -l mbd

smbtree -d3

testparm -s


```
> \\192.168.1.50..." error message.
What was the error message?

---

### Post by wwtorres on 2011-06-17
> **capscrew said:**
> In my opinion that howto is part of your  problem.  It is outdated and in many cases it is inaccurate.

I  found that one after trying and failing with many others.  This is the  one that worked the most, albeit not entirely.  After following that  guide I was at least able to connect from Ubuntu to Windows Vista.

> Are you also running Apache (maybe a LAMP server?I have barely installed any packages and definitely haven't installed Tomcat

> Please provide the following output (from the terminal)
```

pgrep -l mbd
smbtree -d3
testparm -s

``````

$pgrep -l mbd
678 smbd
720 smbd
1219 nmbd

$smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added  interface eth0 ip=2002:63fd:d429:0:20e:a6ff:feb8:d246  bcast=2002:63fd:d429:0:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added  interface wlan0 ip=2002:63fd:d429:0:224:1ff:fe60:c889  bcast=2002:63fd:d429:0:ffff:ffff:ffff:ffff netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::20e:a6ff:feb8:d246%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::224:1ff:fe60:c889%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.50 bcast=192.168.1.255 netmask=255.255.255.0
added interface wlan0 ip=192.168.1.51 bcast=192.168.1.255 netmask=255.255.255.0
Enter wwtorres's password:
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.1 ( 192.168.1.1 )
Connecting to host=192.168.1.1
Connecting to 192.168.1.1 at port 445
Connecting to 192.168.1.1 at port 139
Error connecting to 192.168.1.1 (Connection refused)
cli_start_connection: failed to connect to 192.168.1.1<20> (192.168.1.1). Error NT_STATUS_CONNECTION_REFUSED
Connecting to host=LCARSHOME
Connecting to 192.168.1.1 at port 445
Connecting to 192.168.1.1 at port 139
Error connecting to 192.168.1.1 (Connection refused)
cli_start_connection: failed to connect to LCARSHOME<20> (192.168.1.1). Error NT_STATUS_CONNECTION_REFUSED

$testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
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
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* n\n 
*password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
[homes]
    comment = Home Directories
    valid users = %S
    browseable = No
[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
```> What was the error message?```
Windows cannot access \\192.168.1.50
Check  the spelling of the name.  Otherwise, there might be a problem with  your network.  To try to identify and resolve network problems, click  Diagnose.
Error code: 0x80070035
The network path was not found.

Clicking Diagnose results in:
Windows cannot connect to the server "192.168.1.50"
Windows  found a problem that cannot be repaired automatically.  Contact your  Internet service provider or network administrator for help or click  here for information about things you can try to help resolve the  problem.

This opens the not-very-helpful Windows Help and Support window.
```

---

### Post by jonandrews on 2011-06-17
I have written step-by-step illustrated guides, aimed at users more familiar with Windows, for networking between Windows & Ubuntu... have a look at
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by wwtorres on 2011-06-18
> **jonandrews said:**
> I have written step-by-step illustrated guides, aimed at users more familiar with Windows, for networking between Windows & Ubuntu... have a look at
[www.europe.eclipse.co.uk/Ubuntu/]("http://www.europe.eclipse.co.uk/Ubuntu/")

Jon, your guide is directing me to perform actions I cannot do (e.g. Step 1, Line 4 - the Windows Network folder).  Please read the original post before trying to provide any more help.

---

### Post by SteveHillier on 2011-07-04
I don't know how much of this will be useful to you but I recently set up a test server.
OK, When I installed I had two disks.  I partitioned the second disk, using the whole disk, as a single partition and gave it a moint point of /data.

I then edited the Samba config file.  I did two things here.  I changed the workgroup ID to match our windows network.
I then added a new share (look towards the bottom of the config file.
The share was relatively simple
the share name,
the destination directory
browseable = yes
I think I set some permissions so all users could get access.
I will check this and patch this post later.

Then on my Win7 machine (which should apply to Vista) I mapped a shared drive in Windows Explorer

I selected a drive letter then entered the path as \\servername\sharename 
Job done (much to the amazement of my colleagues who thought it wouldn't happen).

Good luck

---

### Post by nm_geo on 2011-07-08
> **wwtorres said:**
> I have spent the last two weekends trying to get Vista and Ubuntu(natty) to work together.

From Ubuntu:
- I have disabled ufw
- setup a shared directory at /mnt/public (Permissions on public are 777)
- Ubuntu can access Vista shares.
- From the GUI, the "Network Servers" directory contains a "Windows Network" directory, but the Windows Network is empty.
- I can ping the Vista machine

From Vista:
- Nothing is visible.  The ubuntu PC itself is not listed in the "Network" folder or map.
- I have disabled all firewalls (including the router)
-  I can ping the ubuntu machine by IP address but cannot access it by IP address through
      - "Run" - I enter \\192.168.1.50, then get the logon pop-up.  I enter the ubuntu creds, then receive a "Windows cannot connect to \\192.168.1.50..." error message.
      - "Command Prompt" ftp (or sftp) - I get connection refused.
      - via "Web Browser" - I get the following message: "It works! This is the default web page for this server. The web server software is running but no content has been added, yet."  The problem is that it doesn't work.

Everything I have googled up so far has been problems connecting in the opposite direction.  I am trying to get to the Ubuntu machine.  Although I checked all the smb.conf, inetd.conf and a few other files that I've seen mentioned, I cannot get the Vista machine to connect to the ubuntu machine.

This may or may not help.  I recently, like in the last couple of days, decided I wanted to setup a Samba home network mainly to print from my Linux Box to the printer connected to my wife's desktop.  The desktop runs only XP Home at the moment while she is Europe i might change that LOL..  Anyway, i could get the windoz shares visible and usable and printing went pretty well too, but I could not see my Linux laptop shared files on the Windoz Box.  

I yanked samba conf around un-mercifully then it occurred to me that even though I have setup the MSHOME workgroup that maybe something in XP was not setup correctly.. Guess what I went to the local network icon right click properties and BINGO the windoz network client was not enabled.. 

Man I felt dumb but relieved .. But hey I learned a lot about Samba in the process..:)

---

### Post by hmandmpsaunders on 2011-07-10
I had the same problem and found that if I restarted Samba

sudo service smbd restart

then my Natty box became visible.  Perhaps the gurus have an explanation.

Malcolm

---

