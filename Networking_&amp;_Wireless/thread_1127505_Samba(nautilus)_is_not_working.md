---
title: "Samba(nautilus) is not working"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by ongun.kanat on 2009-04-16
I've installed smbclient samba gadmin-samba and it's requirements...
and I tried to connect my windows computer on my network.
I runned nautilus and opened network:// in this folder there is one Link to "Windows Network" I clicked it and waited some time...
and then an error showed 
> Failed to retrieve share list from server

so what can i do??

---

### Post by uncle-c on 2009-04-16
Have you tried [COLOR="black"][COLOR="RoyalBlue"]**--->>PLACES--->> CONNECT TO SERVER...**[/COLOR][/COLOR] and then choosing settings to access your windows share ? I have been told that there is a bug wrt nautilus and network browsing.

---

### Post by Funkydonut5000 on 2009-04-16
Sounds like you're setting up a simple file share with samba, yes?

Have you setup all the required user accounts in ubuntu?

---

### Post by ongun.kanat on 2009-04-16
@uncle-c:
I've tried this but it is not working shows the error again

@Funkydonut5000:
yes i'm setting a share i edited my shared folders workgroup etc. and my guest user is smbguest

---

### Post by Funkydonut5000 on 2009-04-16
Can you post your samba.config file.

So under Users and Accounts you have a desktop user named smbguest?

In User Settings ---> Manage Groups, smbguest is registered under User and smbshare?

---

### Post by ongun.kanat on 2009-04-17
my setttings are normal
but my desktop(ubuntu) cannot connect my laptop(win) and my laptop also can't connect ubuntu...

this is my smb.conf
> 
[global]
server string = ongun-ubuntu Samba Sunucusu
workgroup = ev
security = user
hosts allow = 127. 192.168.0. 192.168.1
interfaces = 127.0.0.1/8 192.168.0.0/24
	bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
cups options = raw
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 998
username level = 6
password level = 8
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
client use spnego = no
client signing = no
client schannel = no
server schannel = no
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = yes
follow symlinks = no
update encrypted = yes
passwd chat timeout = 120
hostname lookups = yes
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
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
	guest ok = yes

[homes]
	comment = Home Directories
	path = /home
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = no
;	available = yes
	browseable = no
;	guest ok = no
;	printable = no
	locking = no
	create mode = 0600
	directory mask = 0700

[printers]
	comment = All Printers
	path = /var/spool/samba
;	browseable = yes
;	writable = no
;	guest ok = no
	printable = yes
	share modes = no
	locking = no

[pdf-documents]
	path = /home/pdf-documents
	comment = Converted PDF Documents
;	available = yes
;	browseable = yes
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

[Ongun Ev]
	path = /home/ongun
	comment = Ongun Ev
	read only = no
;	available = yes
;	browseable = yes
;	guest ok = no
;	printable = no
	share modes = no
	locking = no



---

### Post by Iowan on 2009-04-17
Is Windows firewall active?
Are Windows boxes in "ev" workgroup?

---

### Post by ongun.kanat on 2009-04-18
my firewall is active but windows vista shows other windows computers... ubuntu server can't connect the workgroup "ev".

when i try enter the smb:// or places->connect server->server name=my_win_pc  it shows error:
 > Failed to retrieve share list from server

and the windows computers cannot find my computer

my computers are connected via switch of adsl modem

---

### Post by nanohead on 2009-04-19
This is been a problem for a while with several releases of Ubuntu and associated Samba configs.   

The one thing I've learned (from some great folks here), is that this is the Samba CLIENT side config that is broken, not the server side.   I can get my server processes running just fine now, and consistently.   I can mount my Ubuntu shares from my Windows network just fine now.

But I still cannot for the life of me get any Windows shares mounted from Ubuntu.  

I have 12 windows machines all sharing nicely with each other, and with some Ubuntu machines.   However, I the Ubuntu machines refuse to see any Windows shares, and am still hacking at it.   There are some subtleties that are specific to Windows Vista, as well as Windows Server 2003 and newer that are handled differently than XP and earlier.   

Will let you know if I make any progress

---

### Post by MrWES on 2009-04-19
> **ongun.kanat said:**
> my firewall is active but windows vista shows other windows computers... ubuntu server can't connect the workgroup "ev".

when i try enter the smb:// or places->connect server->server name=my_win_pc  it shows error:
 

and the windows computers cannot find my computer

my computers are connected via switch of adsl modem

Try using the actual IP number vs. the computer name.

Bill

---

### Post by nanohead on 2009-04-19
> **MrWES said:**
> Try using the actual IP number vs. the computer name.

Bill

Doesn't fix it.   The problem is with this Error that is buried under the covers "NT_STATUS_CONNECTION_REFUSED".   You can see the error if you do a command line mount, but in Nautilus, you may see other errors.

Whether you do it via IP address or hostname, it yields the same results with Vista or Windows Server 2003 and newer.   This is a known issue, and there are some workarounds.  I've tried several, but so far, still no consistent fix.   There are several issues at play here to, in order to further confuse matters.    There is a Nautilus issue, that makes browsing not work properly, and then there is a Vista permission issue, and a slightly different WS2003 and newer permission issue.

---

### Post by jonandrews on 2009-04-19
I recently came across the following info on the forum which solved a very similar problem for the originator of that post. (I have not tried it myself, as I have never been able to duplicate the probelm)



Re: Cannot mount XP network shares 
________________________________________
Step 1:
Edit /etc/nsswitch.conf. To do this, open a terminal (programs > accessories > terminal) and copy/paste this command:
Code:
gksudo gedit /etc/nsswitch.conf
Find the line that looks like this:
Code:
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
And just in front of "dns" add "wins" so it looks like this:
Code:
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
Save the file, and close gedit.

Step 2:
Install winbind by copying and pasting the following command:
Code:
sudo aptitude install winbind
See if that fixes your problem.

If that still doesn't work, try this: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)


### >> The writer of the solution later explained what it did as follows:

Quote:
Originally Posted by inobe  
"i would like to know how winbind came up short if you followed the steps correctly " 

Are you sure that wins is placed before dns? Order DOES matter in this file. If you place wins at the end of the line, then dns requests get queried before wins. Some hosts dns servers respond with a search page if dns queries are not successful. This counts as a resolution, so wins is never queried.



I hope this stuff gives you a solution...

---

### Post by nanohead on 2009-04-19
OK, so I fixed mine, and now I have it running.  I can browse all my Windows machines, including Server 2003 (peer networked, WFWG style).   *I think I know what I did* ;)

I read about a zillion posts and did 2 things.  1) I added smbnetfs from the standard repository.  I also ran across a post where a guy put his Windows workgroup name into his router as a domain name.   Well, I did that, and lo and behold, after I rebooted the router and the Ubuntu box, IT WORKED!!!

I am stunned!!!!!  :o:o

I did not change smb.conf or anything fancy.   I didn't even set up smbnetfs.   I should have done one change at a time (I always kick myself for that!)    But it worked anyway!

Whats interesting, is that this solved the 1 major gripe about Ubuntu-windows network sharing with the latest releases.  I may take another disk, and do a fresh build with it to see if I can reproduce this, but not till tomorrow or the next day.

Anyway, hope this works for you!!!

---

