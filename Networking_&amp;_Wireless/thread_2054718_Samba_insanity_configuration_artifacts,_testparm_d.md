---
title: "Samba insanity: configuration artifacts, testparm disagreeing with net usershare, etc"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by koanhead on 2012-09-07
For the last 3 years or so I've been struggling with a particular Samba share. It *should* be simple- just a read-only guest share- but it is not.

It started when I decided I'd like to share my ~/Music directory over the local network. I right-clicked the icon in Nautilus, selected "sharing options", and set up a share with read-only access, accessible to everyone. Easy peasy, except that it didn't work. Other machines on the network could see the share, but weren't permitted to access it.
After perusing the forums and checking out lots of confusing documentation (I'm not exactly new to Samba, by the way- it's a lot more complicated than it was in 1999) I discovered that making the share accessible only to a particular user make it work. Big deal, if I wanted that kind of access I'd just use sshfs. It's a lot simpler and easier. So much for setting it up through Nautilus.
I tried several other methods at that time, including editing smb.conf by hand. Nothing worked. Eventually I figured out that I could create and edit shares on other paths, just not for that specific directory. I moved all the files to another path and it worked... for a while.
Later I moved house and the computer joined an existing network with a different workgroup name. Changing the workgroup name caused the share to stop working (separately from the fact that you actually *can't* change the workgroup name in system-config-samba unless you explicitly restart nmbd).
I've spent four hours today messing about with it. The machine is currently headless, so I logged in via ssh to effect configuration changes. I somehow managed to get the share working (I'm not sure how, but I think it was by adding some undocumented directives I found in forum posts to the share definition) for a while. When I tried to log out, the xterm froze. When I tried to close it via GNOME (using the 'X' button on the window) it complained that there was still a process running and that closing the window would kill it. After I closed the window, the share stopped working. WTF?!

testparm output:
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[Music]"
Processing section "[Video]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
  
[global]
	server string = %h server (Samba, Ubuntu)
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
	name resolve order = bcast lmhosts host wins
	os level = 33
	dns proxy = No
	wins support = Yes
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[Music]
	comment = music, videos, etc
	path = /home/andyman/shared-stuff/shared/music
	force user = andyman
	force group = andyman
	locking = No

[Video]
	path = /home/andyman/Videos
	locking = No

```

output of net usershare info --long:
```

[shared-stuff]
path=/home/andyman/shared-stuff
comment=music and video and stuff
usershare_acl=Everyone:R,MISTERBOCHS\andyman:F,
guest_ok=n

```

'shared-stuff' was a share that existed before, but has been deleted from smb.conf as the tesparm output shows. Why does it still show up in net usershare?

EDIT: Apparently this was because the folder in question was still marked as shared via the Nautilus method. Turning it off made the entry disappear from net usershare info. Groovy.

here's smb.conf:

```

# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
	name resolve order = bcast lmhosts host wins
	os level = 33
#### Networking ####




#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

	syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
	panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

	obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
	unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
	pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
	map to guest = bad user


############ Misc ############


# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes

#======================= Share Definitions =======================


	wins support = yes
	security = user
	guest ok = yes
;	guest account = nobody
	username map = /etc/samba/smbusers
;	guest account = nobody
;	guest account = nobody


[Music]
	path = /home/andyman/shared-stuff/shared-music
	# writeable = no
	read only = yes
	browseable = yes
	comment = music, videos, etc
	# valid users = guest
	guest ok = yes
	locking = no
	force user = andyman
	force group = andyman
[Video]
	path = /home/andyman/Videos
	guest ok = Yes
	locking = No

```

I've omitted some parts of the file which are unchanged from the default.
Right now the configuration is identical to the last working version, but it still does not work.
EDIT: It works if I log in via ssh and restart smbd. When I attempt to log out the process hangs as mentioned above.

---

### Post by koanhead on 2012-09-17
I filed this bug on the issue:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1048119](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1048119)

It's marked "invalid", since I erroneously thought that the config was stored in gconf instead of /var/lib/samba/usershares. My bad for not reading the right docs (my google-fu was weak that day :^/)

Anyway the problem still exists. A split config is still split, and still wrong. This is *probably* separate from the problem such that the shares only work when I'm logged in via ssh (not just on the ssh client- the shares are *globally* available when I'm logged in, and error out when I'm not.)

---

### Post by critin on 2012-09-17
> Load smb config files from /etc/samba/smb.confTo avoid having to mess with the configs, I prefer to 
install Samba from SC and work from there.  Adding the music 
  folder and setting the preferences make it very easy to share.

As a test, I just now shared my music folder simply from the folder 
permissions. It didn't show on the network.

 I then opened Samba and added music folder and set the permission/sharing in samba user/server  preferences, It immediately showed on the network and I was able to open and read it from other machines.
In server preferences, I set Auth Mode as Share;  no password;  guest acct: nobody.  Any machine can open, but no one uses my machines except me, so I don't need the security to be tight.  I can get to it from wherever I am with no password.

I don't know which samba files you're using, and SC has several.  I simply choose the single SAMBA. It does the job for me.

---

