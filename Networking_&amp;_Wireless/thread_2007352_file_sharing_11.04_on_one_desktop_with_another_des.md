---
title: "file sharing 11.04 on one desktop with another desktop running 12.04"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by mikey on 2012-06-20
both machines are amd 64 and neither machine has a bit of trouble seeing a third machine if its a windoz one. would very much like to get these 2 ubuntu pc's file sharing as easily as with a windoz one. 
so far using the nautilus file sharing option doesn't work. samba doesn't either.have looked at giver and something like nfs without result. don't want to resort to using ubuntu one to do what should be very quick and easy but isn't.
is there a simple and clear tutorial or menu to follow out there?
thank
mikey

---

### Post by bab1 on 2012-06-20
> **mikey said:**
> both machines are amd 64 and neither machine has a bit of trouble seeing a third machine if its a windoz one. would very much like to get these 2 ubuntu pc's file sharing as easily as with a windoz one. 
so far using the nautilus file sharing option doesn't work. samba doesn't either.have looked at giver and something like nfs without result. don't want to resort to using ubuntu one to do what should be very quick and easy but isn't.
is there a simple and clear tutorial or menu to follow out there?
thank
mikey
[**_[COLOR="Blue"]This[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1168")  is an excellent howto that works!

You will need to do one more thing. Find this line in the ***/etc/samba/smb.conf*** file
```
;   name resolve order = lmhosts host wins bcast

```
Edit it to look like this
```
 name resolve order =  bcast
```

---

### Post by Morbius1 on 2012-06-20
Nothing is simpler that "Sharing Options" in nautilus. It even installs samba for you if you haven't installed it yourself so the problem may be something else about your setup.
> so far using the nautilus file sharing option doesn't work.Please post the output of the following command:
```
net usershare info --long
```> samba doesn't either"Sharing Options" is Samba but just in case you did something in there please post the output of this command:
```
testparm -s
```And one last thing, please post the output of this command as well:
```
hostname
```There's a rule about hostname length. Greater than 15 characters and your machine is invisible on the network.

[COLOR=Blue]**EDIT**[/COLOR]: oops, stepped on another one of your posts again, bab1.

---

### Post by mikey on 2012-06-24
output of  net usershare info --long

info_fn: file /var/lib/samba/usershares/ushare is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[roza 2011 pl dvdrip xvid pbwt]
path=/home/mikey/Downloads/Roza 2011 PL DVDRip XviD PBWT
comment=/home/mikey
usershare_acl=Everyone:F,
guest_ok=n

[sherlock 2x03 the reichenbach fall 720p hdtv x264 fov]
path=/home/mikey/Downloads/Sherlock 2x03 The Reichenbach Fall 720p HDTV x264 FoV
comment=/home/mikey/downloads
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/win win 2011  is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[public]
path=/home/mikey/Public
comment=
usershare_acl=Everyone:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/video_ts is not a well formed usershare file.
info_fn: Error was Path is not a directory.

output of testparm -s

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Processing section "[movies]"
Processing section "[Pictures]"
Processing section "[Downloads]"
Processing section "[Downloads]"
Processing section "[ushare]"
Processing section "[Public]"
Processing section "[mikey]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = KLEINMANS
	netbios name = SAMBA24
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = mikey
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	guest ok = Yes
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	strict locking = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = No
	locking = No
	strict locking = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	locking = No
	strict locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	locking = No
	strict locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No
	locking = No
	strict locking = No

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	printable = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes

[movies]
	comment = No comment
	path = /home/mikey/movies
	read only = No
	locking = No
	strict locking = No

[Pictures]
	path = /home/mikey/Pictures
	valid users = mikey
	read only = No

[Downloads]
	path = /home/mikey/Downloads
	read only = No

[ushare]
	path = /home/mikey/Desktop/ushare
	read only = No

[Public]
	path = /home/mikey/Public
	read only = No

[mikey]
	path = /home/mikey
	valid users = mikey, mikeyvostros$, smbguest
	read only = No
output of hostname is
mikey-desktop

hope all this helps

---

### Post by Morbius1 on 2012-06-24
Well I don't know about bab1 but I think I've gotten to the point that if someone uses gadmin-samba then they are on their own.

My personal preference is to start over again with a fresh copy of smb.conf. There's one here:  /usr/share/samba/smb.conf
[COLOR=Blue]**EDIT**[/COLOR]: If you want a procedure for that follow steps 1 - 5 here and then change the name resolve order as indicated below: [http://ubuntuforums.org/showpost.php?p=9505697&postcount=13](http://ubuntuforums.org/showpost.php?p=9505697&postcount=13)

If you want to use the monstrosity that you have now I would suggest making one adjustment. Change this:
```
     name resolve order = wins lmhosts bcast
```To this:
```
     name resolve order = bcast host lmhosts wins
```Then restart samba:
```
sudo service smbd restart
```My other suggestion would be to go to /var/lib/samba/usershares and delete the files you have there. I'm a big advocate of Usershares but in this case it's just getting in the way.

---

### Post by bab1 on 2012-06-24
> **Morbius1 said:**
> Well I don't know about bab1 but I think I've gotten to the point that if someone uses gadmin-samba then they are on their own.

My personal preference is to start over again with a fresh copy of smb.conf. There's one here:  /usr/share/samba/smb.conf

I completely agree with Morbius1.  I won't deal with gadmin-samba either.  Follow Morbius1's advice and start over with a fresh smb.conf file.

---

