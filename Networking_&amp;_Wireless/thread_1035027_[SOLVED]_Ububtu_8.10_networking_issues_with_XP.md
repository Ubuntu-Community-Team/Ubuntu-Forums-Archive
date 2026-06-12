---
title: "[SOLVED] Ububtu 8.10 networking issues with XP"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by ARGMan on 2009-01-09
Hi, I am relatively new to Linux and would appreciate any help with this problem please.
I have installed Ubuntu 8.10 (Intrepid) onto an old desktop box that is connected to my local network that has 2 XP NTFS professional boxes running on it.
I have installed SAMBA onto Intrepid and I am able to connect to either of the XP machines from Intrepid using the IP addresses of those machines.
I am not able to see the XP boxes from the network menu link within Intrepid for some strange reason?
From either of the XP boxes I do not see Intrepid as a machine on the workgroup which is called EUROPE?
I don't seem able to see any share that I create on Intrepid from the XP box via the network places link?

This is my Samba conf file:

[global]
	netbios name = tony-ubuntu
	server string = Samba file and print server
	workgroup = EUROPE
	security = user
	hosts allow = 127. 192.168.0. 192.168.1.
	interfaces = 127.0.0.1/8 192.168.0.0/24 192.168.1.1/24
	bind interfaces only = yes
	remote announce = 192.168.0.255 192.168.1.0.255
	remote browse sync = 192.168.0.255 192.168.1.0.255
	printcap name = cups
	cups options = raw
	guest account = tony
	log file = /var/log/samba/samba.log
	max log size = 1000
	username level = 6
	password level = 6
	unix password sync = yes
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	local master = no
	domain master = no
	os level = 33
	logon drive = m:
	logon home = \\%L\homes\%u
	logon path = \\%L\profiles\%u
	logon script = %G.bat
	name resolve order = wins lmhosts bcast
	dns proxy = no
	client use spnego = no
	client signing = no
	client schannel = no
	server schannel = no
	allow trusted domains = yes
	obey pam restrictions = yes
;	enable spools = yes
	follow symlinks = no
	update encrypted = yes
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
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
	winbind trusted domains only = no
	winbind nested groups = yes
	winbind nss info = yes
	encrypt passwords = no
	guest ok = yes

[homes]
	comment = Home Directories
	path = /home
	read only = no
	share modes = no
	locking = no

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = no
	share modes = no
	locking = no

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = no
	browseable = yes
	locking = no
	create mode = 0600
	directory mask = 0700

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = yes
	share modes = no
	locking = no

[pdf-documents]
	path = /home/pdf-documents
	comment = Converted PDF Documents
	writeable = yes
	guest ok = yes

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

[ubuntushare]
	path = /home/tony/ubuntushare
	comment = No comment
	writeable = yes
	available = yes
	browseable = yes
	guest ok = yes
;	printable = no
	share modes = yes
	locking = no

I have set the Samba password to be the same as my login password.

Do you need any other info to help point me in the right direction with this as I have read and tried everything I can to get this far but now I am stuck!

Thanks again for any help with this,
Tony

---

### Post by wjp.reg on 2009-01-09
You've got a lot going on in your smb.conf that I am unfamiliar with.  The following thread worked for me and may help out if you haven't already stumbled upon it.

good luck

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

---

### Post by ARGMan on 2009-01-09
Thanks for your reply - I have followed your link and replaced my samba config file with the one in the link and then tweaked it accordingly.
This has helped a lot as my XP box now sees the linux box which I called Intrepid.
When I double click that link in windows it now prompts me for a username and password combination - I have tried every permutation I can think of and none seem to work - any ideas to help get me past that?

---

### Post by wjp.reg on 2009-01-09
In ubuntu, you need to set up SAMBA users with passwords as directed in the thread.  I have copied the applicable section below.


> 

Time to add yourself as an samba user.

NOTE: You will be asked for a password - make sure you use the same as you use for login!

Code:

sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

In case you need other users to be able to access the share you need to add them to your system AND samba as well. Make sure you use the very same Windows usernames and passwords!

NOTE: Windows XP doesn't set passwords for its useraccount per default. If you haven't set a password on your XP box just press enter when prompted to enter a password for the user account you're about to create!


---

### Post by ARGMan on 2009-01-09
Ok I think I have now resolved this by adding another user, as in the instructions in the linked document contained in the original reply to my post - I had not done this step before as I incorrectly thought that I had a user setup properly already - rule 1 never assume!!

So I just added a new user name like this:

First stop Samba:
tony@tony-ubuntu:~$ sudo /etc/init.d/samba stop
 * Stopping Samba daemons                                        [ OK ] 

Next add the new user and a password for this user which is my linux password:
tony@tony-ubuntu:~$ sudo useradd -s /bin/true tonyubuntu
tony@tony-ubuntu:~$ sudo smbpasswd -L -a tonyubuntu
New SMB password:
Retype new SMB password:
Added user tonyubuntu

Then start Samba again:
tony@tony-ubuntu:~$ sudo /etc/init.d/samba start
 * Starting Samba daemons                                        [ OK ] 

Then when I went back to my XP Box and double clicked the Intrepid icon in the windows network dialog it prompted me for a user and password to which I entered the new user just created and bingo it now works!!

---

### Post by wjp.reg on 2009-01-09
So am I deserving a Thank You, :D??

cheers!

---

### Post by ARGMan on 2009-01-09
Sorry I didn't thank you immediately but I was trying to figure out how to do that in this forum!
I have clicked a button which mentioned thankyou in the bottom of your last post and I am hoping that is the correct way of doing it if not then thank you very much for your help and advice

I was also trying in vain to alter the initial topic subject to indicate that this is resolved to try and help other readers realise that a solution to the problem was contained within the thread but can't figure out how you do that?

Tony.

---

### Post by wjp.reg on 2009-01-09
Tony,

Thanks for the Thanks, :-)

So how did you mark the thread Solved?  I'm curious 'cause I haven't been able to stumble upon it.

---

### Post by ARGMan on 2009-01-09
At the top of the thread are some menu text links, the first one labelled thread tools has an option to mark the thread as solved - simple as that!!

Maybe I could get a thank you :-) - not had one yet!

Tony.

---

### Post by wjp.reg on 2009-01-09
> **ARGMan said:**
> At the top of the thread are some menu text links, the first one labelled thread tools has an option to mark the thread as solved - simple as that!!

Maybe I could get a thank you :-) - not had one yet!

Tony.

Here you go Bud ;-)

---

