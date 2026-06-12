---
title: "Windows 7 not reconnecting to samba shares"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by Audiosears on 2010-07-09
Folks,

Been trying to deal with this one for some time, and still not sure it's more or an issue on the Samba or Win 7 side.

Running Ubuntu 10.04 with Samba 3.4.7, using Windows clients from 2000 on up to access shares.

2000 and XP have no trouble both connecting initially to shares, but upon reboot the shares are disconnected and do not automatically reconnect unless one of them is double-clicked on.  Passwords and mappings are saved such that Windows tries to reconnect upon restart.  When manually reconnected in this way, shares remain open as they should.  This isn't a big issue, but it would be preferable to have these shares reconnect so that links and shortcuts across the LAN work right from bootup.

The bigger issue is with Vista/Windows 7 - When shares are set up with appropriate passwords and such on the clients, they work as expected, until the client is rebooted.  After signing into windows 2 things are observable:

- Black screen for 2-5 minutes before desktop appears
- error message appears when you try to double-click on a mapped share (even with a saved password) that the connection cannot be restored.

If you go into credentials manager and delete the saved password for the share(s) on the samba server, you are prompted for the password when you try to open any of the shares - reenter it and you're then fine until the next reboot.

There must be some issue with the persistence of the saved password, but not sure if this a Windows-side issue or not.  Read some other info on this, and had to make the following changes earlier to even get Win 7 clients to connect to samba at all:

[http://www.builderau.com.au/blogs/viewblogpost.htm?p=339270746]("http://www.builderau.com.au/blogs/viewblogpost.htm?p=339270746")

It appears that when Win 7 starts up, it simply can't connect using the saved password, and the desktop doesn't come up until the reconnecting action(s) time out (if you disconnect your win 7 machine from the network the delay is not present).

anyone have any success solving this issue?  It's not a game-breaker, but really annoying when rebooting having the delay and reentering the network share password(s).

---

### Post by Audiosears on 2010-07-12
Bumpity bump bump?

---

### Post by Audiosears on 2010-07-16
Bueller?  Anyone out there have this issue before?

---

### Post by Crickster on 2010-07-16
Dunno from your description if its the same thing but i remember having a similar problem with Vista a few years ago.
It was resolved with the:
```
security = user
```
directive set. If not check file/folder perms on the samba server (but if it works OK with XP, it won't be that, right?)

---

### Post by Audiosears on 2010-07-21
Crick,

Already have that as part of the config file.  One thing that might be a culprit is the fact that this Ubuntu server has been upgrraded over several versions of Ubuntu / Samba, so doing a clean install of both would be the best option I think, though at present that's not an option :(

You are correct, any version of Windows prior to 7 does not have this issue, and from what I can gather, it's primarily because of Windows 7's insistence on utilizing NTLM by default instead of the old LM handshake - however even changing the registry value via group policy still doesn't solve this aspect of it (though it is what allowed Win 7 as a client to connect to Samba at all).

It seems like the saved password on the Windows side in 7 does not act the same way as previous versions, which stands to reason  since the previous versions don't seem to have this issue, and that hibernating / sleeping your machine does not present the issue.  Could it be that when you restart / shut down the session is seen as broken / terminated on the windows side in a way it did not with previous editions?

Wondering if there might be any Samba changes in the works to address this?  In any case, here's my current Smb.conf file to pick apart.  Our network is a 192.168.1.x /255.255.255.0 run-of-the-mill LAN.  This server is not yet joined to the domain running on a Win2K3 DC (which may be part of the issue), but that is the intent in the future.


```
[global]
	name resolve order = hosts lmhosts wins bcast
	idmap gid = 16777216-33554431
	passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*\n
	preserve case = yes
	remote browse sync = 192.168.1.
	time server = yes
	hosts allow = 127. 192.168.1.
	passwd program = /usr/bin/passwd '%u'
	dns proxy = no
	oplocks = false
	netbios name = server
	cups options = raw
	printing = cups
	logon script = %G.bat
	idmap uid = 16777216-33554431
	local master = yes
	workgroup = ACNET
	os level = 31
	printcap name = /etc/printcap
	security = user
	short preserve case = yes
	max log size = 1000
	lanman auth = yes	
	log file = /var/log/samba/samba.log
	load printers = yes
	guest account = smbguest
	smb passwd file = /etc/samba/smbpasswd
	smb ports = 445
	username level = 8
	socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192
	logon drive = m:
	domain master = no
	interfaces = 127.0.0.1/255.0.0.0 192.168.1.9/255.255.255.0
	username map = /etc/samba/smbusers
	encrypt passwords = true
	winbind use default domain = yes
	keepalive = 600
	wins proxy = yes
	logon home = \\%L\homes\%u
	template shell = /bin/bash
	password level = 8
	server string = Audiosears File / Web Server
	winbind enum users = yes
	logon path = \\%L\profiles\%u
	winbind enum groups = yes
	add user script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M %u
	preferred master = no
	domain logons = no

[homes]
	browseable = yes
	writeable = yes
	locking = no
	printable = no
	admin users = %S
	path = /home/%S
	comment = Home Directories
	valid users = %S
	share modes = no
	allow hosts = 127. 192.168.1.
	available = yes

[netlogon]
	
	locking = no
	printable = no
	path = /home/netlogon
	comment = Network Logon Service
	allow hosts = 127. 192.168.1.
	available = yes
browsable = yes
public = no
writable = no

[profiles]
	
	
	locking = no
	printable = no
	path = /home/profiles
	directory mask = 0700
	comment = User Profiles
	create mode = 0600
	allow hosts = 127. 192.168.1.
	available = yes
browsable = no
public = no
writable = yes

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
guest ok = yes
browsable = yes
public = no
writable = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =

[hr]
path = /media/disk/share/hr
comment = Human Resources Share
valid users = @hr
write list = @hr
admin users = erik edward dan becky maureen
force directory mode = 0770
force create mode = 0770
force group = hr
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[legacy]
path = /media/disk/share/legacy
comment = Legacy Application Share
valid users = @legacy
write list = @legacy
admin users = erik edward dan maureen
force directory mode = 0770
force create mode = 0770
force group = legacy
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[library]
path = /media/disk/share/library
comment = EDO Library Share
valid users = @library
write list = @library
admin users = erik edward dan maureen
force directory mode = 0770
force create mode = 0770
force group = library
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[management]
path = /media/disk/share/management
comment = Management Share
valid users = @management
write list = @management
admin users = erik edward dan shawn maureen
force directory mode = 0770
force create mode = 0770
force group = management
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[oasis]
path = /media/disk/share/oasis
comment = Oasis Share
valid users = @oasis
write list = @oasis
admin users = erik edward dan maureen
force directory mode = 0770
force create mode = 0770
force group = oasis
read only = no
available = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[qnet]
path = /media/disk/share/qnet
comment = Quality Systems Share
valid users = @qnet
write list = joe erik edward dan glenn linda molly pindar maureen kelly jason vinny nancy smorse brian barbie
admin users = erik edward dan glenn maureen
force directory mode = 0770
force create mode = 0770
force group = qnet
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[purchasing]
path = /media/disk/share/purchasing
comment = Purchasing Share
valid users = @purchasing
write list = @purchasing
admin users = erik edward dan nick maureen
force directory mode = 0770
force create mode = 0770
force group = purchasing
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[public]
path = /media/disk/share/public
comment = Public Company Share
valid users = @public
write list = @public
admin users = erik edward dan maureen
force directory mode = 0770
force create mode = 0770
force group = public
read only = no
available = yes
writable = yes
guest ok = no
public = yes
printable = no
locking = no
browsable = yes
share modes = no

[engineering]
path = /media/disk/share/engineering
comment = Engineering Share
valid users = @engineering
write list = @engineering
admin users = erik edward dan sherm maureen
force directory mode = 0770
force create mode = 0770
force group = engineering
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[accounting]
path = /media/disk/share/accounting
comment = Accounting Share
valid users = @accounting
write list = @accounting
admin users = erik edward dan becky maureen
force directory mode = 0770
force create mode = 0770
force group = accounting
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[production]
path = /media/disk/share/production
comment = Production Share
valid users = @production
write list = @production
admin users = erik edward dan sue maureen
force directory mode = 0770
force create mode = 0770
force group = production
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[top]
path = /
comment = Master Share Directory
valid users = erik edward maureen
write list = erik edward maureen
admin users = erik edward maureen
force directory mode = 0770
force create mode = 0770
read only = no
available = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
browsable = no

[software]
path = /media/disk/share/software
comment = Software Archive Share
valid users = @software
write list = @software
admin users = erik edward dan maureen
force directory mode = 0770
force create mode = 0770
force group = software
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[documentation]
path = /media/disk/share/documentation
comment = Audiosears Public Documentation Area
valid users = @public
write list = erik edward dan glenn linda pindar molly
admin users = erik edward dan glenn linda pindar molly
force directory mode = 0770
force create mode = 0770
force group = public
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[engupload]
path = /media/disk/share/upload/engupload
comment = Audiosears Documentation Change Upload Area
valid users = @engupload
write list = @engupload
admin users = erik edward dan glenn linda pindar molly sherm
force directory mode = 0770
force create mode = 0770
force group = engupload
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[hrupload]
path = /media/disk/share/upload/hrupload
comment = Audiosears Documentation Change Upload Area
valid users = @hrupload
write list = @hrupload
admin users = erik edward dan glenn linda pindar molly becky maureen
force directory mode = 0770
force create mode = 0770
force group = hrupload
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[qcupload]
path = /media/disk/share/upload/qcupload
comment = Audiosears Documentation Change Upload Area
valid users = @qcupload
write list = @qcupload
admin users = erik edward dan glenn linda pindar molly joe
force directory mode = 0770
force create mode = 0770
force group = qcupload
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[purchasingupload]
path = /media/disk/share/upload/purchasingupload
comment = Audiosears Documentation Change Upload Area
valid users = @purchasingupload
write list = @purchasingupload
admin users = erik edward dan glenn linda pindar molly nick
force directory mode = 0770
force create mode = 0770
force group = purchasingupload
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[itupload]
path = /media/disk/share/upload/itupload
comment = Audiosears Documentation Change Upload Area
valid users = @itupload
write list = @itupload
admin users = erik edward dan
force directory mode = 0770
force create mode = 0770
force group = itupload
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[salesupload]
path = /media/disk/share/upload/salesupload
comment = Audiosears Documentation Change Upload Area
valid users = @salesupload
write list = @salesupload
admin users = erik edward dan glenn linda pindar molly vinny
force directory mode = 0770
force create mode = 0770
force group = salesupload
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[sales]
path = /media/disk/share/sales
comment = Sales Share
valid users = @sales
write list = @sales
admin users = erik edward dan vinny maureen
force directory mode = 0770
force create mode = 0770
force group = sales
read only = no
available = yes
browseable = no
writable = no
guest ok = no
public = no
printable = no
locking = no

[it]
path = /media/disk/share/it
comment = Information Technology Share
valid users = @it
write list = @it
admin users = erik edward dan maureen
force directory mode = 0770
force create mode = 0770
force group = it
read only = no
available = yes
browseable = no
writable = no
guest ok = no
public = no
printable = no
locking = no

[npteam]
path = /media/disk/share/npteam
comment = Audiosears New Product Team Area
valid users = @npteam
write list = @npteam
admin users = erik edward dan maureen vinny sherm
force directory mode = 0770
force create mode = 0770
force group = npteam
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[engteam]
path = /media/disk/share/engteam
comment = Audiosears Engineering Team Area
valid users = @engteam
write list = @engteam
admin users = erik edward dan maureen sherm
force directory mode = 0770
force create mode = 0770
force group = engteam
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[upload]
path = /media/disk/share/upload
comment = Audiosears Documentation Upload Area
valid users = @public
write list = @public
admin users = erik edward dan maureen linda glenn pindar molly
force directory mode = 1750
force create mode = 0750
force group = upload
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[shipping]
path = /media/disk/share/shipping
comment = Audiosears Shipping/Packaging area
valid users = @shipping
write list = @shipping
admin users = erik edward dan maureen kim
force directory mode = 0770
force create mode = 0770
force group = shipping
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes

[salesteam]
path = /media/disk/share/sales/Sales Team
comment = Audiosears Sales Team Folder
valid users = @salesteam
write list = erik edward dan maureen vinny nancy
admin users = erik edward dan maureen vinny
force directory mode = 0770
force create mode = 0770
force group = salesteam
read only = no
available = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
browsable = yes


[InSpecUpload]
	force create mode = 0770
	writeable = yes
	valid users = @qnet
	path = /media/disk/share/qnet/Upload
	force directory mode = 0770
	force group = qnet
```

---

### Post by Audiosears on 2010-07-21
Looked around again today and found

[http://www.tomshardware.com/forum/75-63-windows-samba-issue]("http://www.tomshardware.com/forum/75-63-windows-samba-issue")

Which did make the suggestion of adding the following lines to my smb.conf:

ntlm auth = yes
client ntlmv2 auth = yes

This seems to have no effect.  Also, the following is already set in group policy on my DC through Active Directory:

Network security: LAN Manager authentication level 
Send LM & NTLM responses 

Minimum session security for NTLM SSP 
Disable Require 128-bit encryption

So, if I delete the saved password from the windows client after a reboot, and put it in again when asked for, we're good til the next reboot as before in Win 7.  Anyone have any idea what the disconnect is between shares in Samba and those on a windows machine?  Typically network drives mapped to a Windows machine share will reconnect as they are supposed to on startup whereas Samba shares do not - in XP you can click on them and they're fine, whereas in 7 you have to reenter the password after every reboot (not reentering the password throws an error that Windows is unable to connect).

---

### Post by Audiosears on 2010-07-26
[Bump]

There has to be SOMEONE out there that has figured this out by now o_O

Any thoughts on the aforementioned?  Any glaring issue(s) with my smb.conf?

---

### Post by Audiosears on 2010-08-03
[Bump]

Interestingly enough, here is some more observed behavior:

On the win 7 clients, if you do not have it save the password permanently, you can still enter it in after a reboot and get to your drives all day (until you log out, reboot, etc).  In this scenario, after a reboot, that long black-screen delay does not occur when there is no saved password.

---

### Post by ynot_mi on 2010-08-21
I'm having the same issue but not just Win 7.  XP is doing the same for me.  Mine started when I installed a new box to replace an old Centos 5 - samba 3.0.27 with Ubuntu 10.04 and samba 3.4.7.  Moved old users and config to the new box and now when Windows reboot or log off and back on, they cannot reconnect to the share that was created with alternate credentials.

---

### Post by dblade on 2010-10-11
Did you ever figure this out?  I have samba share provided by a Solaris 10 server and have this same issue.  Deleting the credentials lets me reconnect to it.

---

### Post by BioHak on 2011-03-30
Anyone figure this out?  Have just installed Win7 on new machine and see same problem.  Credentials are not saved when restarting and connecting to he samba share.  

Thanks,

---

### Post by 0x_ on 2011-11-06
Enter the credentials into the "Credentials Manager" on your Windows 7 client!

---

### Post by radarman on 2011-11-06
I also had a problem where the passwords would be broken after a reboot. After some forum digging I uninstalled the libpam-smbpass module and all was good. I believe that module is responsible for syncing unix accounts and passwords with the smb ones, and it wouldn't stop doing so even when I disabled unix sync in my smb config.

Try this:

```
sudo apt-get remove libpam-smbpass
```

EDIT: My issues were happening when the host machine was reset, not the client

---

### Post by jgarman on 2012-01-20
I fixed this on the Windows 7 client side by using the Credential Manager. Add your credentials under the Windows Credentials section. If your samba share doesn't have a Domain use DOMAIN as the domain. Username must be the DOMAIN\username format to work.

---

### Post by Guinness2702 on 2012-03-02
SOLUTION: prefix your username with your servername.

e.g. if your server is called frog, and your username is kevin, enter the following as your username:-

  [FONT=Courier New]frog\kevin[/FONT]

---

