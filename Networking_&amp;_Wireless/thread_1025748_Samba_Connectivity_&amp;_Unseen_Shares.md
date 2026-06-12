---
title: "Samba Connectivity &amp; Unseen Shares"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by wallyweb on 2008-12-30
**OBJECTIVE:**Share files between two PCs
=============================================================================
**SETUP:**	Wired home network
		192.168.0.103 98box running Windows98SE OEM Fully patched
		192.168.0.0 DLINK Router
		192.168.0.100 2kbox running Ubuntu 8.10 Intrpid Ibex (Samba Host SAMBA24) [2kbox name retained for convenience after uninstalling Windows 2000 Pro - Ubuntu 8.04 installed then upgraded to 8.10]
		Workgroup WALNET
		Each box is able to access the internet via the router.
=============================================================================
**ISSUE:**		98box Network Neighbourhood sees the workgroup and 98box and it's shares. It also sees SAMBA24, but does not see the shares.
		2kbox Windows Network only shows Location: smb:///

		I have done troubleshooting for several days and I have searched in vain wide and far for a resolution. Hopefully someone here can help me work this one out.
=============================================================================
**PING:**		98box can ping itself by IP and by name
		98box can ping 2kbox by IP but not by name (unknown host)
		98box can't ping SAMBA24 (Destination specified is invalid)
		2kbox (via terminal) can ping itself by IP and by name
		2kbox (via terminal) can ping 98box by IP but not by name. By name returns an IP address (8.15.7.107) from outside the network*.
		2kbox (via terminal) can ping samba24 by name which returns an IP address (8.15.7.107) from outside the network*.
		2kbox (via terminal) can't ping SAMBA24 by name (unknown host)
		* - traceroute verified the ping passed through the router and onto the internet.
=============================================================================
**smb.conf:**
# Samba config file created using SWAT
# from UNKNOWN (&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;y&#1279;W&#6519;&#65533;&#65533;&#65533;&#65533;g&#65533;&#65533;&#65533;y&#1279;)
# Date: 2008/12/30 13:39:40

[global]
	dos charset = CP850
	unix charset = UTF-8
	display charset = LOCALE
	workgroup = WALNET
	realm = 
	netbios name = SAMBA24
	netbios aliases = 
	netbios scope = 
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/200
	bind interfaces only = Yes
	config backend = file
	security = USER
	auth methods = 
	encrypt passwords = Yes
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	map to guest = Never
	null passwords = No
	obey pam restrictions = Yes
	password server = *
	smb passwd file = /etc/samba/smbpasswd
	private dir = /var/lib/samba
	passdb backend = smbpasswd
	algorithmic rid base = 1000
	root directory = 
	guest account = web
	enable privileges = Yes
	pam password change = No
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat debug = No
	passwd chat timeout = 120
	check password script = 
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	restrict anonymous = 0
	lanman auth = No
	ntlm auth = Yes
	client NTLMv2 auth = No
	client lanman auth = No
	client plaintext auth = No
	preload modules = 
	use kerberos keytab = No
	log level = 0
	syslog = 1
	syslog only = No
	log file = /var/log/samba/samba.log
	max log size = 1000
	debug timestamp = Yes
	debug prefix timestamp = No
	debug hires timestamp = No
	debug pid = No
	debug uid = No
	debug class = No
	enable core files = Yes
	smb ports = 445 139
	large readwrite = Yes
	max protocol = NT1
	min protocol = CORE
	min receivefile size = 0
	read raw = Yes
	write raw = Yes
	disable netbios = No
	reset on zero vc = No
	acl compatibility = auto
	defer sharing violations = Yes
	nt pipe support = Yes
	nt status support = Yes
	announce version = 4.9
	announce as = NT
	max mux = 50
	max xmit = 16644
	name resolve order = wins lmhosts bcast
	max ttl = 259200
	max wins ttl = 518400
	min wins ttl = 21600
	time server = No
	unix extensions = Yes
	use spnego = Yes
	client signing = No
	server signing = No
	client use spnego = No
	client ldap sasl wrapping = plain
	enable asu support = No
	svcctl list = 
	deadtime = 0
	getwd cache = Yes
	keepalive = 300
	lpq cache time = 30
	max smbd processes = 0
	paranoid server security = Yes
	max disk size = 0
	max open files = 10000
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	use mmap = Yes
	hostname lookups = No
	name cache timeout = 660
	ctdbd socket = 
	cluster addresses = 
	clustering = No
	load printers = No
	printcap cache time = 750
	printcap name = cups
	cups server = 
	iprint server = 
	disable spoolss = No
	addport command = 
	enumports command = 
	addprinter command = 
	deleteprinter command = 
	show add printer wizard = Yes
	os2 driver map = 
	mangling method = hash2
	mangle prefix = 1
	max stat cache size = 256
	stat cache = Yes
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	rename user script = 
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	set primary group script = 
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	shutdown script = 
	abort shutdown script = 
	username map script = 
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	domain logons = No
	os level = 33
	lm announce = Auto
	lm interval = 60
	preferred master = Yes
	local master = Yes
	domain master = Auto
	browse list = Yes
	enhanced browsing = Yes
	dns proxy = No
	wins proxy = No
	wins server = 
	wins support = No
	wins hook = 
	kernel oplocks = Yes
	lock spin time = 200
	oplock break wait time = 0
	ldap admin dn = 
	ldap delete dn = No
	ldap group suffix = 
	ldap idmap suffix = 
	ldap machine suffix = 
	ldap passwd sync = no
	ldap replication sleep = 1000
	ldap suffix = 
	ldap ssl = no
	ldap timeout = 15
	ldap connection timeout = 2
	ldap page size = 1024
	ldap user suffix = 
	ldap debug level = 0
	ldap debug threshold = 10
	eventlog list = 
	add share command = 
	change share command = 
	delete share command = 
	config file = 
	preload = 
	lock directory = 
	pid directory = /var/run/samba
	utmp directory = 
	wtmp directory = 
	utmp = No
	default service = 
	message command = 
	get quota command = 
	set quota command = 
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	socket address = 0.0.0.0
	homedir map = auto.home
	afs username map = 
	afs token lifetime = 604800
	log nt token command = 
	time offset = 0
	NIS homedir = No
	registry shares = No
	usershare allow guests = No
	usershare max shares = 100
	usershare owner only = Yes
	usershare path = /var/lib/samba/usershares
	usershare prefix allow list = 
	usershare prefix deny list = 
	usershare template share = 
	panic action = 
	host msdfs = Yes
	passdb expand explicit = No
	idmap domains = 
	idmap backend = 
	idmap alloc backend = 
	idmap cache time = 900
	idmap negative cache time = 120
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template homedir = /home/%D/%U
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind enum users = No
	winbind enum groups = No
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind expand groups = 1
	winbind nss info = no
	winbind refresh tickets = No
	winbind offline logon = No
	winbind normalize names = No
	winbind rpc only = No
	comment = 
	path = 
	username = 
	invalid users = 
	valid users = 
	admin users = 
	read list = 
	write list = 
	printer admin = 
	force user = 
	force group = 
	read only = Yes
	acl check permissions = Yes
	acl group control = No
	acl map full control = Yes
	create mask = 0744
	force create mode = 00
	security mask = 0777
	force security mode = 00
	directory mask = 0755
	force directory mode = 00
	directory security mask = 0777
	force directory security mode = 00
	force unknown acl user = No
	inherit permissions = No
	inherit acls = No
	inherit owner = No
	guest only = No
	administrative share = No
	guest ok = Yes
	only user = No
	hosts allow = 127., 192.168.0.
	hosts deny = 
	allocation roundup size = 1048576
	aio read size = 0
	aio write size = 0
	aio write behind = 
	ea support = No
	nt acl support = Yes
	profile acls = No
	map acl inherit = No
	afs share = No
	smb encrypt = auto
	block size = 1024
	change notify = Yes
	directory name cache size = 100
	kernel change notify = Yes
	max connections = 0
	min print space = 0
	strict allocate = No
	strict sync = No
	sync always = No
	use sendfile = No
	write cache size = 0
	max reported print jobs = 0
	max print jobs = 1000
	printable = No
	printing = cups
	cups options = raw
	print command = 
	lpq command = %p
	lprm command = 
	lppause command = 
	lpresume command = 
	queuepause command = 
	queueresume command = 
	printer name = 
	use client driver = No
	default devmode = Yes
	force printername = No
	printjob username = %U
	default case = lower
	case sensitive = Auto
	preserve case = Yes
	short preserve case = Yes
	mangling char = ~
	hide dot files = Yes
	hide special files = No
	hide unreadable = No
	hide unwriteable files = No
	delete veto files = No
	veto files = 
	hide files = 
	veto oplock files = 
	map archive = Yes
	map hidden = No
	map system = No
	map readonly = yes
	mangled names = Yes
	store dos attributes = No
	dmapi support = No
	browseable = Yes
	blocking locks = Yes
	csc policy = manual
	fake oplocks = No
	locking = Yes
	oplocks = Yes
	level2 oplocks = Yes
	oplock contention limit = 2
	posix locking = Yes
	strict locking = Auto
	share modes = Yes
	dfree cache time = 0
	dfree command = 
	copy = 
	include = 
	preexec = 
	preexec close = No
	postexec = 
	root preexec = 
	root preexec close = No
	root postexec = 
	available = Yes
	volume = 
	fstype = NTFS
	set directory = No
	wide links = Yes
	follow symlinks = No
	dont descend = 
	magic script = 
	magic output = 
	delete readonly = No
	dos filemode = No
	dos filetimes = Yes
	dos filetime resolution = No
	fake directory create times = No
	vfs objects = 
	msdfs root = No
	msdfs proxy = 

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	share modes = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	valid users = 98box$, Debian-exim, smbguest, web
	locking = No
	share modes = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	valid users = 98box$, Debian-exim, smbguest, web
	create mask = 0600
	directory mask = 0700
	browseable = No
	locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	locking = No
	share modes = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	valid users = 98box$, Debian-exim, smbguest, web

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	valid users = 98box$, Debian-exim, smbguest, web
	printable = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	lprm command = lprm -P'%p' %j
	use client driver = Yes

[chtzlxms]
	comment = Christmas Message
	path = /ubushare

---

### Post by wallyweb on 2008-12-30
I just tried the following:

web@2kbox:~$ smbtree
Password: 
cli_start_connection: failed to connect to 192.168.0.0<20> (192.168.0.0). Error NT_STATUS_NETWORK_UNREACHABLE
Packet send failed to 192.168.0.0(137) ERRNO=Permission denied

192.168.0.0 is my router. This I do not understand as pings get through without problem.

---

### Post by Iowan on 2008-12-31
*Ordinarily*, the router is not set with network address (192.168.0.0). In a *standard* /24 (255.255.255.0) network, both .0 and .255 are used for broadcasting. Dunno if that's what is causing your problems.
I thought Win 95/98 used different password encryption, but my "Unleashed" book suggests they handle encryption just fine.

---

### Post by wallyweb on 2009-01-03
> **Iowan said:**
> *Ordinarily*, the router is not set with network address (192.168.0.0)... You're right and my bad ... It is 192.168.0.1:oops:

And now an **Update:**
The name resolution issue was corrected by editing the respective hosts files and disabling WINS.
I also used gedit to write a simpler smb.conf.
Then I re-established my share on the Intrepid box and all was well ... for a bit.
I am now in "Segmentation Fault" Hell and locked out of my Intrepid install
the details of which have been posted into this bug report that I found:

[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/292791](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/292791)

---

