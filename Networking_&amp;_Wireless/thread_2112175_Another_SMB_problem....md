---
title: "Another SMB problem..."
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by sandsjh on 2013-02-04
there are hundreds of threads out there and I have come back to restoring my original smb.conf files and then enabled sharing on directories plus changed the workgroup name. I cannot get ay Linux machines to connect to each other or get either XP machine to connect to Linux. Your assistance is appreciated. not that I may not be back until 48 hours from now.

I've made a spreadsheet to make a little more sense of the situation:
[https://docs.google.com/spreadsheet/ccc?key=0AltvzKlogviOdDZOVEFaaGlBbWxsLWM4UGZGa21reFE&usp=sharing](https://docs.google.com/spreadsheet/ccc?key=0AltvzKlogviOdDZOVEFaaGlBbWxsLWM4UGZGa21reFE&usp=sharing)

```

ownerx64 - Linux Mint Mate 13 x64 (latest updates)
ownerx32 - Linux Mint Mate 13 x32 (latest updates)
dm0 - Linux Mint Mate 13 x64 (latest updates)

```
```

-ownerx64 13 MATE -> DM0
 Failed to retrieve share list from server.
-ownerx64 -> ownerx32
 password required for ownerx32
 enter username and password and get error
-ownerx64 -> winXPlaptop
shows shares
-ownerx64 -> winXPdesktop
 show shares

```
```

-ownerx32 13 XFCE4-> DM0
 Could not display "smb://192.168.22.2/".
 Error: Failed to retrieve share list from server
 Please select another viewer and try again.
-ownerx32 -> ownerx64
 password required for ownerx64
 enter username and password and get error
-ownerx32 -> winXPlaptop
 shows shares
-ownerx32 -> winXPdesktop
 show shares
-ownerx32 -> router
 shows shares

```
```

-dm0 -> ownerx32
 password required for ownerx32
 enter username and password and get error
-dm0 -> ownerx64
 password required for ownerx32
 enter username and password and get error
-ownerx32 -> winXPlaptop
 shows shares
-dm0 -> winXPdesktop
 show shares
-dm0 -> -> router
 shows shares

```
```

-xp desktop to all three Mint machines
 The account is not authorized to login from this station.

```
```

ownerx32 ~ $ sudo testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[d]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = SLM
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
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

[d]
	comment = Downloads
	path = /home/owner/Downloads
	read only = No
	guest ok = Yes
======
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

```


```

ownerx64
ownerx64 ~ $ sudo testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = SLM
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
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
[d]
	comment = Downloads
	path = /home/owner/Downloads
	read only = No
	guest ok = Yes
=======
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

```


```

dm0 /etc/samba $ sudo testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[d]"
Processing section "[mint]"
Processing section "[ddown]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = SLM
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
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

[d]
	comment = Downloads
	path = /home/owner/Downloads
	read only = No
	guest ok = Yes

[mint]
	comment = Mint Updates
	path = /downloads/downloads-saved/os_reinstall_mint
	read only = No
	guest ok = Yes

[ddown]
	comment = RAID1 Downloads
	path = /downloads/downloads
	read only = No
	guest ok = Yes
======
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination 

```

```

smbclient //192.168.22.2/d
Enter owner's password: 
Server requested LM password but 'client plaintext auth = no' or 'client ntlmv2 auth = yes'
session setup failed: SUCCESS - 0

```

---

