---
title: "scanning local samba network issues"
date: 2013-06-26
forum: Networking &amp; Wireless
---

### Post by hiflyer on 2013-06-26
I have had increasing lack or reliability of scanning the local lan for the computers on the network. I have had NO problems connecting to any of the machines on the lan. I have diagnosed the issue down to the appearent samba setup configurations. As I have added Ubuntu machines, the problem has gotten worse. 

The problem seems to be that each and every computer on the local lan in the same workgroup deems itself to be the local browser. This means that I have 2 ubuntu machines (ubuntu os is 12.10 for one machine and 64 bit 13.04 for the other ubuntu machine) (each on wireless fios router) each thinking it is a local browser, 1 windows 7 machine (which actually does not think it is the local browser) and 1 windows 8 machine which does think it is the local browser. 

the master brower for this network is supposed to be a 3rd ubuntu machine (Ubuntu os is 64 bit 12.10) with the master browser = yes, local brower = yes, preferred browser = yes, os level = 255. 

It has taken a long time to figure out but the solution I have implemented is to turn off the 2 ubuntu machines browsing capability (master browser = no, local brower = no, preferred browser = no). Also turned off the windows 8 machine browsing capability in the services.  things now work much better ie reliably.

So why is Samba/Ubuntu having so much trouble with this master browsing function. If I set the master browser on the 3rd machine with a high os level, it seems there should be little issue with the system so long as none of the other ubuntu machines are set to master browser. 

Is this a bug in either Samba or Ubuntu?

tia for any insight into this problem

---

### Post by redmk2 on 2013-06-27
> **hiflyer said:**
> I have had increasing lack or reliability of scanning the local lan for the computers on the network. I have had NO problems connecting to any of the machines on the lan. I have diagnosed the issue down to the appearent samba setup configurations. As I have added Ubuntu machines, the problem has gotten worse. 

The problem seems to be that each and every computer on the local lan in the same workgroup deems itself to be the local browser. This means that I have 2 ubuntu machines (ubuntu os is 12.10 for one machine and 64 bit 13.04 for the other ubuntu machine) (each on wireless fios router) each thinking it is a local browser, 1 windows 7 machine (which actually does not think it is the local browser) and 1 windows 8 machine which does think it is the local browser. 

the master brower for this network is supposed to be a 3rd ubuntu machine (Ubuntu os is 64 bit 12.10) with the master browser = yes, local brower = yes, preferred browser = yes, os level = 255. 

It has taken a long time to figure out but the solution I have implemented is to turn off the 2 ubuntu machines browsing capability (master browser = no, local brower = no, preferred browser = no). Also turned off the windows 8 machine browsing capability in the services.  things now work much better ie reliably.

So why is Samba/Ubuntu having so much trouble with this master browsing function. If I set the master browser on the 3rd machine with a high os level, it seems there should be little issue with the system so long as none of the other ubuntu machines are set to master browser. 

Is this a bug in either Samba or Ubuntu?

tia for any insight into this problem

I would say this is not a bug in either Samba or Ubuntu.  Attempting to force a specific host to assume the Local Master (on a LAN) or Domain Master is bad practice.  it certainly does not stop a specific host from browsing the LAN at all.  It only defines what happens when in the absence of a Master Browse List (MBL) and how the elections for a new Master Browser will be held.  

It is best to allow the machine that has the most chance of being on all the time become the Browse Master (BM).  The (MBL) can function perfectly on the most lowly workstation as long as it is up and connected to the LAN.  What you are doing is forcing elections om MB and delaying the rapid response to NETBIOS NAME request as the hosts are constantly going through the MB election process and then rebuilding the MBL.  You don't "*turn off*" browsing capability in an individual host with *"master browser = no, local brower = no, preferred browser = no*".   There is no  "*local browser*" or "*preferred browser*" settings anyway (or did you misspeak?)?

On my network I have 3 hosts that serve as Samba servers.  At any time one or the other can be off and as a result the Local Master Browser (LMB) can be any of these 3 hosts.  There is no degradation in performance with this setup.  in fact 1 of those hosts is a Pentium P3 with 1GB of RAM.

My opinion is that you should revert all of these hosts back to there defaults and diagnose what the real problem is.  As a start you might post the output of this```
smbclient -L <ip_address>
# where <ip_address> is one of your Samba servers
``` ... and this from the same <ip_address>```
testparm -s
```

Here is what I get if I purposely miss configure the smb.conf with "local browser =no```

**[COLOR="#FF0000"]Ignoring unknown parameter "local browser"[/COLOR]**
Processing section "[printers]"
Processing section "[print$]"
Processing section "[public]"
Loaded services file OK.
Server role: ROLE_STANDALONE
...

```

As you can see (in red) the Samba server ignores the setting.

Show us what you have and then we can start to get things right for you.

---

### Post by hiflyer on 2013-06-27
OK, I have remove all browser definitions an gone to defaults in samba.
I restarted both smbd and nmbd before doing the suggested commands. I also waited awhile first.
I have included the commands from multiple machines - all smbclient commands were run from ZEUS
the testparm were run on each of the 3 ubuntu machines.
I also included the 3 samba configuration files just in case. (I cleaned out the comment lines ie all lines starting with # or ;)

here are the results
smbclient -L LINUX-SERVER
Anonymous login successful

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (linux-server server (Samba, Ubuntu))
	Stylus-Photo-R300 Printer   EPSON Stylus Photo R300
	HP-Officejet-Pro-L7600 Printer   HP Officejet Pro L7600
	bee_dsk7        Disk      
	bee_dsk8        Disk      
	HP_OfficeJet_Faxes Disk      
	bee_dsk6        Disk      
	quicken2010B    Disk      
	Server_xxx Disk      
	HP_PAVILION     Disk      
	quicken2010A    Disk      
	bee_dsk2        Disk      
	Share_Disk      Disk      
	HP_OfficeJet_Faxes_2 Disk      
	bee_dsk4        Disk      
	bee_dsk5        Disk      
Anonymous login successful

	Server               Comment
	---------            -------
	LINUX-SERVER         linux-server server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	ROAD_RUNNER          LINUX-SERVER

---------------------------------------------------------------------
smbclient -L NEXCOM
Anonymous login successful

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	xxx       Disk      
	IPC$            IPC       IPC Service (NEXCOM server (Samba, Ubuntu))
	HP-Officejet-Pro-L7600-2 Printer   HP Officejet Pro L7600
	Epson-Stylus-Photo-R300 Printer   Epson Stylus Photo R300
	documents       Disk      
Anonymous login successful

	Server               Comment
	---------            -------
	NEXCOM               NEXCOM server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	ROAD_RUNNER          NEXCOM

---------------------------------------------------------------------
smbclient -L ZEUS

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	xxx       Disk      
	IPC$            IPC       IPC Service (ZEUS server (Samba, Ubuntu))
	HP-Officejet-Pro-l7600 Printer   HP Officejet Pro l7600

	Server               Comment
	---------            -------
	ZEUS                 ZEUS server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	ROAD_RUNNER          ZEUS

---------------------------------------------------------------------
smbclient -L VENUS
note this is a windows 8 machine

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	xxx       Disk      
	C$              Disk      Default share
	D$              Disk      Default share
	dblake          Disk      
	IPC$            IPC       Remote IPC
	Users           Disk      

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------

---------------------------------------------------------------------
smbclient -L DWB-GREENOSPREY
note this is a windows 7 machine

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	D$              Disk      Default share
	E$              Disk      Default share
	F               Disk      
	HP Officejet Pro L7600 Series Printer   HP Officejet Pro L7600 Series
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	Users           Disk      

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	
---------------------------------------------------------------------
root@linux-server:/media/bee_dsk7/programs# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = ROAD_RUNNER
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
	name resolve order = bcast lmhosts host wins
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---------------------------------------------------------------------
xxx@ZEUS:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[xxx]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = ROAD_RUNNER
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
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[xxx]
	path = /home/xxx
	read only = No
	guest ok = Yes

---------------------------------------------------------------------
xxx@NEXCOM:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[xxx]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = ROAD_RUNNER
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
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[xxx]
	path = /home/xxx
	read only = No
	guest ok = Yes

---------------------------------------------------------------
smb.conf on both ZEUS
also I removed all commented and lines starting with a ;
[global]
   workgroup = ROAD_RUNNER
   netbios name = ZEUS
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
   wins support = no
[printers]
   comment = All Printers

------------------------------------------------------
smb.conf on both NEXCOM
also I removed all commented and lines starting with a ;


[global]
   workgroup = ROAD_RUNNER
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[xxx]
path = /home/xxx
available = yes
browsable = yes
public = yes
writable = yes

------------------------------------------------------
smb.conf on LINUX-SERVER
also I removed all commented and lines starting with a ;

[global]
   workgroup = ROAD_RUNNER
   server string = %h server (Samba, Ubuntu)
   usershare owner only = false
   dns proxy = no
   name resolve order = bcast lmhosts host wins 
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[xxx]
path = /home/[user directory]
available = yes
browsable = yes
public = yes
writable = yes

also I can no longer display any samba network information in nautilus on any of the Ubuntu machines.
ps thanks for any insights or help on this.

---

### Post by redmk2 on 2013-06-27
> **hiflyer said:**
> OK, I have remove all browser definitions an gone to defaults in samba.
I restarted both smbd and nmbd before doing the suggested commands. I also waited awhile first.
I have included the commands from multiple machines - all smbclient commands were run from ZEUS
the testparm were run on each of the 3 ubuntu machines.
I also included the 3 samba configuration files just in case. (I cleaned out the comment lines ie all lines starting with # or ;)

Let's start with what I asked for first.  Please format the output data in the future by using the **[SIZE=4]#[/SIZE]** icon to wrap the data in code blocks as seen below> 


here are the results
```
smbclient -L LINUX-SERVER
Anonymous login successful

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (linux-server server (Samba, Ubuntu))
	Stylus-Photo-R300 Printer   EPSON Stylus Photo R300
	HP-Officejet-Pro-L7600 Printer   HP Officejet Pro L7600
	bee_dsk7        Disk      
	bee_dsk8        Disk      
	HP_OfficeJet_Faxes Disk      
	bee_dsk6        Disk      
	quicken2010B    Disk      
	Server_xxx Disk      
	HP_PAVILION     Disk      
	quicken2010A    Disk      
	bee_dsk2        Disk      
	Share_Disk      Disk      
	HP_OfficeJet_Faxes_2 Disk      
	bee_dsk4        Disk      
	bee_dsk5        Disk      
Anonymous login successful

	Server               Comment
	---------            -------
	LINUX-SERVER         linux-server server (Samba, Ubuntu)

	Workgroup            Master
	---------            -------
	ROAD_RUNNER          LINUX-SERVER
```

```
root@linux-server:/media/bee_dsk7/programs# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = ROAD_RUNNER
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
	name resolve order = bcast lmhosts host wins
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


```

also I can no longer display any samba network information in nautilus on any of the Ubuntu machines.
ps thanks for any insights or help on this.

I see a one thing I didn't expect to find on a server; this host uses only only Samba usershares.  I guess I expected a server to have root administrated shares.  Since there are only user created Samba shares to get an accurate idea of the share construction we should look at the output from this host of```
sudo net usershare --long
```

From the output of *smbclient* I see that this host is the master browser for this LAN```

	Workgroup            Master
	---------            -------
	ROAD_RUNNER          LINUX-SERVER

```

What I don't see in the output is this ```

Domain=[MYDOMAIN] OS=[Unix] Server=[Samba 3.4.7]


```...so I don't know what version of Samba you are running.

I did notice that, as you say, the Master Browser is different on each machine.  I also looked at your past post history.  I wonder if some of the misconfiguration from the past are still being used, thus causing you continued grief.  Are you running winbind on this host?  Have you altered the nsswitch.conf file?  Are you still using Firestarter?

---

### Post by hiflyer on 2013-06-27
Sorry I did not know how to do that. Hopefully I have the code rapping correct in this.

from the request to I got

sudo net usershare --long

Code:
[SIZE=4]
net usershare --long
Invalid command: net usershare 
Usage:
net usershare add             Add/modify user defined share
net usershare delete          Delete user defined share
net usershare info            Display information about a user defined share
net usershare list            List user defined shares
[/SIZE]

so I tried

[SIZE=4]
$ net usershare info
[Share_Disk]
path=/media/bee_dsk2/Share_Disk
comment=
usershare_acl=Everyone:F,
guest_ok=n

[quicken2010A]
path=/media/bee_dsk2/Share_Disk/Quicken/quicken2010A
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Server_beckstein]
path=/home/beckstein
comment=
usershare_acl=Everyone:F,
guest_ok=y

[quicken2010B]
path=/media/bee_dsk2/Share_Disk/Quicken/quicken2010B
comment=
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/dwb_1 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[/SIZE]

and

[SIZE=4]
net usershare list
Share_Disk
quicken2010A
Server_beckstein
quicken2010B
info_fn: file /var/lib/samba/usershares/dwb_1 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[/SIZE]
Code: [SIZE=4]$ net usershare list
Share_Disk
quicken2010A
Server_beckstein
quicken2010B
info_fn: file /var/lib/samba/usershares/dwb_1 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[/SIZE]

for the previous info I sent you I did a pipe but I guess that bit did not go in the pipe
here if for the linux-server
[SIZE=4]
Domain=[ROAD_RUNNER] OS=[Unix] Server=[Samba 3.6.6]
[/SIZE]

hopefully one of these is what you were looking for.

---

### Post by hiflyer on 2013-06-27
```
[SIZE=2]
I think I got the code block thing now
[/SIZE]
```

---

### Post by redmk2 on 2013-06-27
> **hiflyer said:**
> Sorry I did not know how to do that. Hopefully I have the code rapping correct in this.

Nope!  you need to use the icon with the **#** hash symbol, not the size =4 > 

from the request to I got

sudo net usershare --long

This is my mistake.  It should have been```
net usershare info --long
```...but I can see some problems already.  I will highlight them in red. > 

so I tried

```

$ net usershare info
[Share_Disk]
path=/media/bee_dsk2/Share_Disk
comment=
usershare_acl=Everyone:F,
guest_ok=n

[quicken2010A]
path=/media/bee_dsk2/Share_Disk/Quicken/quicken2010A
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Server_beckstein]
path=/home/beckstein
comment=
usershare_acl=Everyone:F,
guest_ok=y

[COLOR="#FF0000"][quicken2010B]
path=/media/bee_dsk2/Share_Disk/Quicken/quicken2010B
comment=
usershare_acl=Everyone:F,
guest_ok=n

[B]info_fn: file /var/lib/samba/usershares/dwb_1 is not a well formed usershare file.
info_fn: Error was Path is not a directory.[/B][/COLOR]

```

and

```

net usershare list
Share_Disk
quicken2010A
Server_beckstein
quicken2010B
info_fn: file /var/lib/samba/usershares/dwb_1 is not a well formed usershare file.
info_fn: Error was Path is not a directory.

```

```
$ net usershare list
Share_Disk
quicken2010A
Server_beckstein
quicken2010B
[COLOR="#FF0000"]info_fn: file /var/lib/samba/usershares/dwb_1 is not a well formed usershare file.
info_fn: Error was Path is not a directory[/COLOR]
```


for the previous info I sent you I did a pipe but I guess that bit did not go in the pipe
here if for the linux-server
[SIZE=4]
Domain=[ROAD_RUNNER] OS=[Unix] Server=[Samba 3.6.6]
[/SIZE]

hopefully one of these is what you were looking for.

Remove the share that is not formed correctly and see what you have.

Answer the questions from the last post:  . Are you running winbind on this host? Have you altered the nsswitch.conf file? Are you using Firestarter?

---

### Post by hiflyer on 2013-06-27
I missed answering the last questions

I dont think I am running winbind anywhere
I have not modified nsswitch.conf
I am still using firestarter.

---

### Post by hiflyer on 2013-06-27
I guess I am running winbind (why 4 instances though?)
```

beckstein@linux-server:~$ ps ax | grep winbind
 3182 ?        Ss     0:00 /usr/sbin/winbindd -F
 3197 ?        S      0:00 /usr/sbin/winbindd -F
 3820 ?        S      0:00 /usr/sbin/winbindd -F
 4230 ?        S      0:00 /usr/sbin/winbindd -F
 5548 pts/0    S+     0:00 grep --color=auto winbind

```

---

### Post by redmk2 on 2013-06-27
> **hiflyer said:**
> I guess I am running winbind (why 4 instances though?)
```

beckstein@linux-server:~$ ps ax | grep winbind
 3182 ?        Ss     0:00 /usr/sbin/winbindd -F
 3197 ?        S      0:00 /usr/sbin/winbindd -F
 3820 ?        S      0:00 /usr/sbin/winbindd -F
 4230 ?        S      0:00 /usr/sbin/winbindd -F
 5548 pts/0    S+     0:00 grep --color=auto winbind

```

Why are you running winbind at all.  It is not needed and will cause problems.  You should remove both Firestarter and winbindd.  Post the output of ```
cat /etc/nsswitch.conf
```

---

### Post by hiflyer on 2013-06-27
have found the share directory and remove 2 offending files
dwb_1, quicken and virus

currently the command says
```

root@linux-server:/var/lib/samba/usershares# net usershare info --long
[bee_dsk5]
path=/media/bee_dsk5
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bee_dsk4]
path=/media/bee_dsk4
comment=
usershare_acl=Everyone:F,
guest_ok=y

[HP_OfficeJet_Faxes_2]
path=/media/bee_dsk2/Share_Disk/HP_OfficeJet_Faxes
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Share_Disk]
path=/media/bee_dsk2/Share_Disk
comment=
usershare_acl=Everyone:F,
guest_ok=n

[bee_dsk2]
path=/media/bee_dsk2
comment=
usershare_acl=Everyone:F,
guest_ok=y

[quicken2010A]
path=/media/bee_dsk2/Share_Disk/Quicken/quicken2010A
comment=
usershare_acl=Everyone:F,
guest_ok=n

[HP_PAVILION]
path=/media/HP_PAVILION
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Server_beckstein]
path=/home/beckstein
comment=
usershare_acl=Everyone:F,
guest_ok=y

[quicken2010B]
path=/media/bee_dsk2/Share_Disk/Quicken/quicken2010B
comment=
usershare_acl=Everyone:F,
guest_ok=n

[bee_dsk6]
path=/media/bee_dsk6
comment=
usershare_acl=Everyone:F,
guest_ok=y

[HP_OfficeJet_Faxes]
path=/media/bee_dsk2/Share_Disk/HP_OfficeJet_Faxes
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bee_dsk8]
path=/media/bee_dsk8
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bee_dsk7]
path=/media/bee_dsk7
comment=
usershare_acl=Everyone:F,
guest_ok=n

root@linux-server:/var/lib/samba/usershares# 

```

nautilus on linux server can display the workgroup but nothing below.

---

### Post by hiflyer on 2013-06-27
/etc/nsswitch.conf below
```
beckstein@linux-server:~$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
beckstein@linux-server:~$ 

```

I have shut down firestarter (not removed yet)
Is there a difference at this point in time on it being shut down vs removed?

why am I running winbind?
 I really did not think I was. I do not find it being enabled in the smb.conf. I did not specifically install/start it as far as I know. Where would it be that I need to stop it from running/being started in the first place?

---

### Post by redmk2 on 2013-06-28
> **hiflyer said:**
> /etc/nsswitch.conf below
```
beckstein@linux-server:~$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
beckstein@linux-server:~$ 

```

This is good.  It has the default settings.  Yeah!!!!> 

I have shut down firestarter (not removed yet)
Is there a difference at this point in time on it being shut down vs removed?

For what we are doing right now you can just leave it off.  BUT, you have to make sure it is truly off when we are testing.
> 

why am I running winbind?
 I really did not think I was. I do not find it being enabled in the smb.conf. I did not specifically install/start it as far as I know. Where would it be that I need to stop it from running/being started in the first place?

Well here's the deal, you were advised to do this way back in '08 and you have been using it ever since.  It was wrong then and it still is wrong.  Some misguided soul confused Winbind with WINS and the bad advice has been with us ever since.  Winbind is for mapping Linux users to Windows users in an NT Domain situation (we're talking before Active Directory domains).  WINS is a server that provides NetBIOS name resolution across multiple subnets in a LAN situation.  Neither of these solutions are needed in a simple home LAN where the user is just trying to share data between all of the computers in the house.

As far as FIreStarter is concerned; I think you can do better.  Use [**[COLOR="#FF8C00"]GUFW[/COLOR]**]("http://gufw.org/").  FireStarter is not actively maintained by the developers.  So any changes in the Linux OS are not accounted for.  In short, FireStarter is outdated and can cause you trouble.  I do not use "host based" Firewalls in my LAN at all.  My firewall is at the edge of the network.  This is the division between the LAN and the WAN (your router/gateway).  Since all traffic to the public Internet can be inspected at that point, that is the most encompassing place to configure a firewall.  If you are running a larger LAN that has anonymous and/or possibly untrustworthy users then using an internal router/firewall makes sense to protect servers and the data on them.

How are you using FireStarter in your network?

It is unfortunate, but I think it is going to take reconfiguring a lot of what you have in you network infrastructure.  Ultimately you will be the winner as you will have a deeper understanding and and a much more stable network.  My original configuration for Samba still works on all Ubuntu versions including 13.04.

I would start with the network topology.  At least to verify what your IP addressing scheme is and what your LAN name services are.  You can start by removing winbind.  To test what is really going to be removed you can do this```

sudo apt-get **[COLOR="#FF0000"]-s[/COLOR]** purge winbind

``` ...note the red switch.  This says: Simulate the command -- Do not  really do anything.  Please post the results back here.

---

### Post by hiflyer on 2013-06-28
Problem seems to be solved.
ZEUS and LINUX-SERVER now reliably scan the network (at least since last night for each time I have tried) even though winbind and firestarter were still installed.

I have since removed winbind from all 3 machines. (I still dont know how it got there on ZEUS as I recently did a fresh install from CD). Winbind was also on nexcom which nautilus on that machine is scanning correctly now.

nautilus is still scanning the network on both LINUX-SERVER and ZEUS.

I removed some more unwanted shares from LINUX-SERVER.

this is the current output of net usershare

```

beckstein@192.168.1.151's password: 
beckstein@linux-server:~$ net usershare info --long
[bee_dsk2]
path=/media/bee_dsk2
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bee_dsk6]
path=/media/bee_dsk6
comment=
usershare_acl=Everyone:F,
guest_ok=y

[HP_OfficeJet_Faxes]
path=/media/bee_dsk2/Share_Disk/HP_OfficeJet_Faxes
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bee_dsk8]
path=/media/bee_dsk8
comment=
usershare_acl=Everyone:F,
guest_ok=y

[bee_dsk7]
path=/media/bee_dsk7
comment=
usershare_acl=Everyone:F,
guest_ok=n

```

as a note I do not get any output from ZEUS when I run the net usershare command presumably as I am not sharing any directories from that machine.

I thank you very much for solving my problems with samba. I really was off base on this one. There are many people having problems with this and many different answers. I think you have given me one of the cleanest ones I have seen.\\:D/

---

### Post by redmk2 on 2013-06-28
> **hiflyer said:**
> Problem seems to be solved.
ZEUS and LINUX-SERVER now reliably scan the network ...

as a note I do not get any output from ZEUS when I run the net usershare command presumably as I am not sharing any directories from that machine.
As it should be.  If there are no user shares, non will be listed.> 

I thank you very much for solving my problems with samba. I really was off base on this one. There are many people having problems with this and many different answers. I think you have given me one of the cleanest ones I have seen.\\:D/

Thank you for the compliment.  I know there are lots of folks with problems that make guesses as to what to do.  I never guess guess at an answer.  I would prefer to diagnose the real problem first and fix it rather correctly rather than patch the system or create workarounds.  But that's just me.  ;-)

---

