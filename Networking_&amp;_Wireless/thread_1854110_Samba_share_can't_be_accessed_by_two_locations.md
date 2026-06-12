---
title: "Samba share can't be accessed by two locations"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by Weidbrewer on 2011-10-03
I have a shared folder set up on one of my machines (10.04) using Samba that contains an ebook library.  For a while, I was using Samba to connect and edit from my laptop (Win7).  Eventually, my wife wanted to use it as well, so I set it to auto-mount on her computer (10.04).

Since then, I have noticed that, when her computer is on, I cannot access the folder from my laptop.  Although it is set to "anyone can use," when I enter my name and password, it gives me an access denied message.

Here is my config for it:

```

        [global]
	workgroup = mshome
	server string = %h server (Samba, Mythbuntu)
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	dns proxy = no
	security = share
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

        [library]
	path = /media/raid/library
	writeable = yes
;	browseable = yes
	guest ok = yes
```

Anyone have any suggestions?

---

### Post by capscrew on 2011-10-03
> **Weidbrewer said:**
> I have a shared folder set up on one of my machines (10.04) using Samba that contains an ebook library.  For a while, I was using Samba to connect and edit from my laptop (Win7).  Eventually, my wife wanted to use it as well, so I set it to auto-mount on her computer (10.04).

Since then, I have noticed that, when her computer is on, I cannot access the folder from my laptop.  Although it is set to "anyone can use," when I enter my name and password, it gives me an access denied message.

Here is my config for it:

```

        [global]
	workgroup = mshome
	server string = %h server (Samba, Mythbuntu)
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	dns proxy = no
	security = share
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

        [library]
	path = /media/raid/library
	writeable = yes
;	browseable = yes
	guest ok = yes
```

Anyone have any suggestions?
How did you *"set it to auto-mount on her computer (10.04)"*?  Think of why you did that?  

Since you have set the share access to the permissions of the share, I'll bet that the share permissions become that of your wifes machine since it is now mounted on her file system.  I would either (or both) change the share security to user```
security = user
``` and set the directory and file permissions that both of you can use.

---

### Post by Weidbrewer on 2011-10-04
I can't find the exact instructions that I used (it was a while ago) but [these are very close]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite").  As for thinking about why I did it...Um, I'm not sure what you're getting at there.  I did it so that the file folder would automatically mount at boot...

Please explain more about the security=user setting.  I don't know how to do what you're saying.

---

### Post by capscrew on 2011-10-04
> **Weidbrewer said:**
> I can't find the exact instructions that I used (it was a while ago) but [these are very close]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite").  As for thinking about why I did it...Um, I'm not sure what you're getting at there.  I did it so that the file folder would automatically mount at boot...
I just wanted to see if there was some application specific reason you had to do that. The instructions are for an older unsupported version.  A lot has changed since Feisty.> 

Please explain more about the security=user setting.  I don't know how to do what you're saying.

When you set the share security to *security = user * you allow no security (e.g Samba doesn't check at all).  The only restrictions are the underlaying file system permissions on Ubuntu.  

Can you provide the output from the terminal (Ubuntu) of this command```
testparm -v
```

If you have trouble capturing all of the info you can feed it to a file temporarily so you can cut and paste it.  You can do this with this command ```
testparm -v > testparm
```

This will create a file called *testparm *in the home directory of the user you are logged in as on Ubuntu.

I would also like to see the permissions of the folder you have shared.  Post the output of  ```
ls -ahl /media/raid/library

```

**[COLOR="Blue"]I would also like to see the output of this[/COLOR]**```
cat /etc/fstab
```

---

### Post by Weidbrewer on 2011-10-04
I'll check those things out when I get home later tonight.  Thanks.

---

### Post by Weidbrewer on 2011-10-04
Okay...set it to "user," and it was *accessible* from my wife's computer, but no longer auto-mounted.  Also, now the whole server machine is inaccessible from my laptop, not just the folder in question...so I changed it back.  Here is the testparm output (edited to remove the other folders that are cluttering it up.)

```
*******@*******:~$ testparm -v
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[library]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	dos charset = CP850
	unix charset = UTF-8
	display charset = LOCALE
	workgroup = MSHOME
	realm = 
	netbios name = *******
	netbios aliases = 
	netbios scope = 
	server string = %h server (Samba, Mythbuntu)
	interfaces = 
	bind interfaces only = No
	security = SHARE
	auth methods = 
	encrypt passwords = Yes
	update encrypted = No
	client schannel = Auto
	server schannel = Auto
	allow trusted domains = Yes
	map to guest = Never
	null passwords = No
	obey pam restrictions = No
	password server = *
	smb passwd file = /etc/samba/smbpasswd
	private dir = /etc/samba
	passdb backend = tdbsam
	algorithmic rid base = 1000
	root directory = 
	guest account = nobody
	enable privileges = Yes
	pam password change = No
	passwd program = 
	passwd chat = *new*password* %n\n *new*password* %n\n *changed*
	passwd chat debug = No
	passwd chat timeout = 2
	check password script = 
	username map = 
	password level = 0
	username level = 0
	unix password sync = No
	restrict anonymous = 0
	lanman auth = No
	ntlm auth = Yes
	client NTLMv2 auth = No
	client lanman auth = No
	client plaintext auth = No
	preload modules = 
	dedicated keytab file = 
	kerberos method = default
	map untrusted to domain = No
	log level = 0
	syslog = 0
	syslog only = No
	log file = /var/log/samba/log.%m
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
	name resolve order = lmhosts wins host bcast
	max ttl = 259200
	max wins ttl = 518400
	min wins ttl = 21600
	time server = No
	unix extensions = Yes
	use spnego = Yes
	client signing = auto
	server signing = No
	client use spnego = Yes
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
	max open files = 16384
	socket options = TCP_NODELAY
	use mmap = Yes
	hostname lookups = No
	name cache timeout = 660
	ctdbd socket = 
	cluster addresses = 
	clustering = No
	load printers = Yes
	printcap cache time = 750
	printcap name = 
	cups server = 
	cups connection timeout = 30
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
	machine password timeout = 604800
	add user script = 
	rename user script = 
	delete user script = 
	add group script = 
	delete group script = 
	add user to group script = 
	delete user from group script = 
	set primary group script = 
	add machine script = 
	shutdown script = 
	abort shutdown script = 
	username map script = 
	logon script = 
	logon path = \\%N\%U\profile
	logon drive = 
	logon home = \\%N\%U
	domain logons = No
	init logon delayed hosts = 
	init logon delay = 100
	os level = 20
	lm announce = Auto
	lm interval = 60
	preferred master = No
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
	ldap ssl = start tls
	ldap ssl ads = No
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
	preload = 
	lock directory = /var/run/samba
	state directory = /var/lib/samba
	cache directory = /var/cache/samba
	pid directory = /var/run/samba
	utmp directory = 
	wtmp directory = 
	utmp = No
	default service = 
	message command = 
	get quota command = 
	set quota command = 
	remote announce = 
	remote browse sync = 
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
	panic action = /usr/share/samba/panic-action %d
	perfcount module = 
	host msdfs = Yes
	passdb expand explicit = No
	idmap backend = tdb
	idmap alloc backend = 
	idmap cache time = 604800
	idmap negative cache time = 120
	idmap uid = 
	idmap gid = 
	template homedir = /home/%D/%U
	template shell = /bin/false
	winbind separator = \
	winbind cache time = 300
	winbind reconnect delay = 30
	winbind enum users = No
	winbind enum groups = No
	winbind use default domain = No
	winbind trusted domains only = No
	winbind nested groups = Yes
	winbind expand groups = 1
	winbind nss info = template
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
	guest ok = No
	only user = No
	hosts allow = 
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
	cups options = 
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
	access based share enum = No
	browsable = Yes
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
	wide links = No
	follow symlinks = Yes
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



[Libraryrar]
	path = /media/raid/Libraryrar
	read only = No
	guest ok = Yes


```

---

### Post by capscrew on 2011-10-05
It sure looks like there have been problems in the past.  Are you capable of browsing the network shares?  Probably not.  Is that why you attempted to mount the share at boot time for your wifes computer?  I'm going to guess so.  You should always be able to browse and bookmark a Samba share, just as you can a Windows share.

You have part of the puzzle figured out```
netbios name = *******
```I assume that you have provided the same name as the hostname of this machine.  The only limitation is that number of characters is limited to 15.  Mine looks like this```
netbios name = MALIBU
```

This means you do not have to rely on the hostname to resolve into the netbios name (via the nmbd daemon).  But you  have no way to look for it.  The default is *name resolve order = lmhosts wins host **[COLOR="Red"]bcast[/COLOR]***.  This is to cumbersome for Samba on a small LAN.  The [COLOR="Red"]bcast parameter [/COLOR] is really the best (and is how Windows itself handles it).  I have this order on my system```
name resolve order = **bcast** host
```Putting **bcast** first forces Samba to broadcast for the listing of the shares available on the LAN.  The next value would look in the /etc/hosts file, but since you have set the netbios name earlier this won't ever happen.  The last two are not needed at all.  Only a few  use *lmhosts* and you should not run a WINS server (*wins*) on a single segment LAN. 

So if we set the following in you smb.conf file, you should be able to at least browse to the share.```

        netbios name = <your_choice>
	name resolve order = bcast host
```
I would not automount the share to your wifes Ubuntu host.  You can have locking problems and permissions problems.

If this works out for you, we can correct whatever problems you have with the specific share. 

Let me know how this goes.  At this point I'm just looking to be able to browse the shares.

---

### Post by Weidbrewer on 2011-10-05
When I have it set to "share" rather than "user," I can browse with no problems at all - I just can't access a folder from two locations at once.

To be honest, nothing after > I assume that you have provided the same name as the hostname of this machine.  makes any sense to me.  Could you please break it down a bit farther?

As for why it is automounted, this is for a matter of ease.  I can tell my wife until I'm blue in the face how to navigate to a network share manually, but in a few months she'll make a comment about not being able to get at the e-books and I'll find out that she forgot how and didn't want to bother me.  With it mounted, they're right there on her desktop when she turns on her computer.

---

### Post by capscrew on 2011-10-05
> **Weidbrewer said:**
> When I have it set to "share" rather than "user," I can browse with no problems at all - I just can't access a folder from two locations at once.

To be honest, nothing after  > I assume that you have provided the same name as the hostname of this machine. 
makes any sense to me.  Could you please break it down a bit farther?

In simple terms, browsing network shares requires that the computer  doing the browsing (functioning as a *Samba [COLOR="Green"]**Client**[/COLOR]*) must be able to find the list of shares listed by: //netbios_name/share_name.  To do this it must be able to communicate (using *netbios* names) with the computer that has a master list of all the shares.

The computer that holds the shares (functioning as a *Samba [COLOR="Blue"]**Server**[/COLOR]*) usually functions also as the holder of the list of shares (Browse List).  The holder of the list  needs to be announced too and this also done via *netbios* names.

Samba provides a method for hostnames conversion to *netbios* names if needed via a process called *[COLOR="Purple"]nmbd[/COLOR]*.  If you manually configure the *netbios* name then Samba does not have to rely on DNS (hosts) naming. 

The steps I listed show the method to manually configure *netbios* naming.  In a nutshell: You can provide the *netbios* name directly in the smb.conf file (as you have done), but you also need to tell Samba to look for the name via broadcast (bcast) first.> 

As for why it is automounted, this is for a matter of ease.  I can tell my wife until I'm blue in the face how to navigate to a network share manually, but in a few months she'll make a comment about not being able to get at the e-books and I'll find out that she forgot how and didn't want to bother me.  With it mounted, they're right there on her desktop when she turns on her computer.

It appears that you do have browsing capabilities.  Is this so?  Is it consistent?  Can you at least see the share when you wife is reading something in that share?

In the end you can provide a sym-link to the share on the desktop without auto mounting it.  But it opens another can of worms.

Please post the contents of your /etc/fstab file.

---

### Post by Weidbrewer on 2011-10-05
Okay...well, thanks anyway for the help.  I think this is going in a direction that's way more complicated than I intend it to be.  I've accomplished this a number of times in the past without issues like these, and I think this is just a matter of me (as usual) not being able to ask the question properly.  

I'll either try to remember what I've done in the past, or just deal with the fact that I can't access the folder from my laptop if she's on her computer. (unless you have a link to a step-by-step walk-through that will accomplish what I'm trying...)

Again, thank you for taking the time.

---

