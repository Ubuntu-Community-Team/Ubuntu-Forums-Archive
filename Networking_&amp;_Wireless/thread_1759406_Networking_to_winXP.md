---
title: "Networking to winXP"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by Bruv on 2011-05-15
I have a Desktop upstairs running Ubuntu and one downstairs running winXP, both are connected to a cabled connection to the internet via a wired router, an ethernet cable runs to the downstairs winXP PC.

I want to network them.

How do I go about it ?

---

### Post by Morbius1 on 2011-05-15
[] Create a share on WinXP

[] Access the share from Ubuntu:
Nautilus > Network > ......
Or if you know the WinXP's ip address ( let's say it's 192.168.0.100 ):
```
nautilus smb://192.168.0.100
```[] Create a share on Ubuntu:

Open Nautilus
Right click a folder you own say ... Documents
Select "Sharing Options"
At this point if you don't have Samba installed it will ask you if you want to install it ( I think it calls it "Windows Networking" just to confuse people ) - you do.
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

[] Access the share from WinXP.

If you run into problems post the output of the following commands so people have a starting place to help you debug things:
```
net usershare info --long
testparm -s
smbtree
```

---

### Post by jonandrews on 2011-05-16
I have written a step-by-step guide for networking between Windows & Ubuntu...  have a look at
[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Bruv on 2011-05-16
Many thanks for the replies, I shall have to set aside some time and work through the process step by step.
Probably need to move PC's closer temporarily, so I am not up and down the stairs.

I shall report back when successful.....(always the optimist.)

---

### Post by Bruv on 2011-05-17
It has not gone as planned.
I can access Ubuntu from the XP machine but not visa versa.
This is the output from the command as requested.> bruv@upstairs:~$ net usershare info --long
[shared]
path=/home/bruv/Desktop/shared
comment=
usershare_acl=Everyone:F,
guest_ok=y

bruv@upstairs:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
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
bruv@upstairs:~$ smbtree


---

### Post by Morbius1 on 2011-05-18
Everything on the Ubuntu machine related to Samba seems to be in order with one exception and that's the output of "smbtree". 

What it should have done is list every workgroup and within every workgroup every host and within every host every share. Did it come back blank or did you just forget to post it?

One thing you should try next is to temporarily disable the WinXP firewall and see if it's getting in the way. On way to verify that the requisite ports are open on WinXP is to use the following procedure from Ubuntu:

Install nmap:
```
sudo apt-get install nmap
```Run the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of the WinXP machine.*[/COLOR]
The following ports need to be open for samba to do it's thing:
> PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
You might want to run the same command against your own Ubuntu ip address for good measure.

---

### Post by lizzycaplon on 2011-05-18
Every one nice sharing.  i like it. but i have no idea about it.

---

