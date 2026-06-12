---
title: "Drive shares"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by 9000cse on 2011-07-20
Hi all. Question.
I have a few shares over a network. All work fine. XP and 7 can attach to them, copy, delete, read, write.  Happy.
But shut down Ubuntu, reboot the following day. And nothing. All the shares have gone. So have to redo them.
Is this a common problem with UBUNTU, Linex?

Any help in solving this would be great. OH, I'm using SAMBA.

---

### Post by Morbius1 on 2011-07-20
Are you by any chance creating these shares in Nautilus?

There's a bug that I'm almost certain will never get fixed where the emblem used to indicate a "shared" folder disappears after a reboot. The only reliable way to determine what you are sharing via the nautilus method is to run the following command:
```
net usershare info --long
```If you're not using nautilus to share the folders then please post the output of the following command:
```
testparm -s
```

---

### Post by 9000cse on 2011-07-20
I do not think I'm using Nautilus?  But just in case...
```


asjmm@asjmm-saviour:~$ net usershare info --long
[james1]
path=/media/KIDS/james
comment=
usershare_acl=Everyone:F,
guest_ok=y

[t&amusic]
path=/media/KIDS/Toni and Alice's Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[antonia1]
path=/media/KIDS/Antonia
comment=
usershare_acl=Everyone:F,
guest_ok=y

[ebay]
path=/media/DATA/ebay
comment=
usershare_acl=Everyone:F,
guest_ok=y

[scalextric]
path=/media/stuff/scalextric
comment=
usershare_acl=Everyone:F,
guest_ok=y

```
And the other code
```
asjmm@asjmm-saviour:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[scalextric]"
Processing section "[ebay]"
Processing section "[james]"
Processing section "[Antonia]"
Processing section "[Toni and Alice's Music]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = SAVIOUR
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = asjmm
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
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	valid users = asjmm
	read only = No

[scalextric]
	path = /media/stuff/scalextric
	read only = No

[ebay]
	path = /media/DATA/ebay
	read only = No

[james]
	path = /media/KIDS
	read only = No

[Antonia]
	path = /media/KIDS/Antonia
	read only = No

[Toni and Alice's Music]
	comment = Alice Toni Music
	path = /media/KIDS/Toni and Alice's Music
	read only = No
asjmm@asjmm-saviour:~$ 


```

A bug that may never get fixed??
That sounds good?

Thanks for your help.
Andy

---

### Post by Morbius1 on 2011-07-20
There are 2 ways to create samba shares - Classic and Usershares ( Nautilus ). As it turns out you are using both at the same time on the same target folders. This is generally a very bad idea but you are one lucky duck as it appears they are both set up as guest shares without any complicated parameters. I would suggest however that you choose one method over the other.

Other than that each set of shares seems to be in order so why do say that you have to reshare them. And which method do you use to reshare them.

BTW, all these shares seem to point to /media/KIDS, /media/stuff, /media/DATA. Are these partition mount points? You have to have these partitions mounted for them to be shared.

---

### Post by 9000cse on 2011-07-21
Yes, I know, they have to be mounted. 
Data, Stuff and Kids are HDD, Data, Kids, one drive partitioned. On boot, all drive are automaticly mounted, it seems.
Opening SAMBA, and all shares are there. Opening Home Folder. They hare not. So right clicking and share options to re-share. Which to me does not seem the right way of going about it?

Cheers
Andy

---

### Post by Morbius1 on 2011-07-21
> Opening SAMBA, and all shares are there. Opening Home Folder. They hare  not. So right clicking and share options to re-share. Which to me does  not seem the right way of going about it?I repeat, there are 2 methods of creating Samba shares:

**Classic Samba**: Using in your case what you call "Opening SAMBA" will place share definitions in /etc/samba/smb.conf. When you create a Classic Share the emblem within Nautilus does not change to indicate that the folder is shared.

**Usershares**: Using Nautilus ( your Home Folder ) will place share definitions in /var/lib/samba/usershares. When you create a Usershare the emblem does change to indicate that the folder is shared but there is a bug in that the emblem change may not survive a reboot. But this is a cosmetic bug in that the folder is still shared it just doesn't indicate that it is shared in the emblem. That's the bug that is likely not to get fixed.

You don't have to keep re-sharing your folders. 

Again I would suggest using one method or the other but not both on the same target folder. If you want to know what folders are shared run the following command which will list them:
```
smbtree
```

---

### Post by 9000cse on 2011-07-21
Running  'subtree'
it asks for PW and the return to prompt.
```
asjmm@asjmm-saviour:~$ smbtree
Enter asjmm's password: 
asjmm@asjmm-saviour:~$ smbtree
Enter asjmm's password: 
asjmm@asjmm-saviour:~$ smbtree
Enter asjmm's password: 
asjmm@asjmm-saviour:~$ 

```
I understand what you are saying, If I'm using two, How do I stop Usershares ? 
Cheers,

---

### Post by Morbius1 on 2011-07-21
If you run smbtree and it doesn't show your shares then you have a completely different problem.

Make sure the following services are running:
```
sudo service smbd start
``````
sudo service nmbd start
```Then run smbtree again to show your shares.
> How do I stop Usershares ? Go back into Nautilus and "un-share" them.

---

### Post by 9000cse on 2011-07-21
I think there's a problem?
```


asjmm@asjmm-saviour:~$ sudo service smbd start
[sudo] password for asjmm: 
start: Job is already running: smbd
asjmm@asjmm-saviour:~$ sudo service nmbd start
start: Job is already running: nmbd
asjmm@asjmm-saviour:~$ smbtree
Enter asjmm's password: 
asjmm@asjmm-saviour:~$ 

```

---

### Post by bab1 on 2011-07-21
> **9000cse said:**
> I think there's a problem?
```


asjmm@asjmm-saviour:~$ sudo service smbd start
[sudo] password for asjmm: 
start: Job is already running: smbd
asjmm@asjmm-saviour:~$ sudo service nmbd start
start: Job is already running: nmbd
asjmm@asjmm-saviour:~$ smbtree
Enter asjmm's password: 
asjmm@asjmm-saviour:~$ 

```

See if you really have smbtree.

```
whereis smbtree
```

You should get something like this
```
smbtree: /usr/bin/smbtree /usr/share/man/man1/smbtree.1.gz
```

---

### Post by Morbius1 on 2011-07-21
Turn off or disable the firewall on your machine and try smbtree again. 

To make sure the firewall isn't getting in the way install the following package:
```
sudo apt-get install nmap
```Then run the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of your machine.*[/COLOR]

And post the output.

---

### Post by 9000cse on 2011-07-21
Yes, I do.
```
asjmm@asjmm-saviour:~$ whereis smbtree
smbtree: /usr/bin/smbtree /usr/share/man/man1/smbtree.1.gz
asjmm@asjmm-saviour:~$ 

```

```
asjmm@asjmm-saviour:~$ sudo apt-get install nmap
[sudo] password for asjmm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nmap is already the newest version.
nmap set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
asjmm@asjmm-saviour:~$ sudo nmap -sS -sU -T4 192.168.1.69

Starting Nmap 5.21 ( http://nmap.org ) at 2011-07-21 16:39 BST
Nmap scan report for asjmm-saviour (192.168.1.69)
Host is up (0.0019s latency).
Not shown: 1992 closed ports
PORT     STATE         SERVICE
80/tcp   open          http
139/tcp  open          netbios-ssn
443/tcp  open          https
445/tcp  open          microsoft-ds
123/udp  open          ntp
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.29 seconds

```

---

### Post by Morbius1 on 2011-07-21
I'll be honest with you - I have no idea.

Given all the possibilities I can probably explain all the shares connected to /media if you did not have them automounted in fstab. Then you would have to mount them first in Nautilus before they become shared. But even if those were not mounted when you run smbtree you should still see the print$ share.

---

### Post by 9000cse on 2011-07-21
Thanks Morbius1. I'll figure it out sometime.  Cheers
Andy

---

