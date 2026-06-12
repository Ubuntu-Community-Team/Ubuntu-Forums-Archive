---
title: "Can Ping IP and hostname, but can't browse to share in Nautilus"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by ignisuti on 2012-04-22
I'm setting up a new server using Ubuntu 11.10. I've configured Samba to share my "Data" folder, but I can not view this Share on other devices: Ubuntu PC, Boxee, Smartphone, etc... 

I've done this successfully before with older versions of Ubuntu.

From another Ubuntu PC, I can successfully ping the server's IP address and hostname. 
I've reinstalled Nautilus, Samba, and gvfs-backends on both server and other Ubuntu PC.
What's the next step in the troubleshooting process?

Please help. I've been Googling this for days now without finding a solution.

---

### Post by papibe on 2012-04-22
Hi ignisuti.

Could you post your Samba configuration on the server by ruining this command?
```
sudo testparm
```
Regards.

---

### Post by ignisuti on 2012-04-22
> **papibe said:**
> Hi ignisuti.

Could you post your Samba configuration on the server by ruining this command?
```
sudo testparm
```
Regards.

Here you go:
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[Data]"
Processing section "[kist]"
Processing section "[printers-1]"
Processing section "[Untitled Folder]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
[global]
	server string = SERVER-NAS
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = wins lmhosts bcast host
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[Data]
	comment = SERVER-NAS
	path = /media/Data
	force group = users
	read only = No
	guest ok = Yes

[kist]
	path = /home/kist
	read only = No
	guest ok = Yes

[printers-1]
	path = /var/lib/samba/printers
	read only = No
	guest ok = Yes

[Untitled Folder]
	path = /home/kissell/Untitled Folder
	read only = No
	guest ok = Yes

```

---

### Post by ignisuti on 2012-04-23
Bump...
I'm really pulling my hair out over this one. Please help.

---

### Post by Morbius1 on 2012-04-23
I have a question. You have the following lines in your smb.conf:
> wins support = Yes
name resolve order = wins lmhosts bcast hostThe first line set you up as a WINS server and there's nothing wrong with that but that means you have to modify every client on your network to point to this machine for name resolution. Is that what you intended?

If not, you can leave it alone but change the second line to this:
```
name resolve order = bcast host lmhosts wins
```There's one more thing and that's your hostname for this server. Run the following command and count the number of characters:
```
hostname
```If it's 16 characters or more it's invisible to Samba/SMB. You can change it ( for samba purposes ) in smb.conf itself with the following line in the [global] section:
```
netbios name = something
```Just make sure "something" is 15 characters or less in length.

---

### Post by ignisuti on 2012-04-24
I've changed the name resolve order as you suggested, but that didn't seem to change anything. So, I've changed it back. 

The hostname is SERVER-NAS which is under the 16 character limit.

Any other suggestions?

---

### Post by Morbius1 on 2012-04-24
Change the name resolve order back to the way I suggested and restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by ignisuti on 2012-04-24
> **Morbius1 said:**
> Change the name resolve order back to the way I suggested and restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```

Thanks for the suggestion Morbius1. I tried that, but didn't see an improvement.

---

### Post by Morbius1 on 2012-04-24
Are your machines in the same subnet? In other words are they all connected to the same router and have ip addresses in the same range like:
192.168.0.100 - 150

---

### Post by ignisuti on 2012-04-24
> **Morbius1 said:**
> Are your machines in the same subnet? In other words are they all connected to the same router and have ip addresses in the same range like:
192.168.0.100 - 150

Same router.

My IP range for my PCs is from 192.168.1.0 to 192.168.1.100. I assume this is just fine..?

---

### Post by Morbius1 on 2012-04-24
From your Ubuntu machine run the following command and post it's output:
```
smbtree
```

---

