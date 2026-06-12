---
title: "samba24 problem"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by ewientje on 2010-05-02
I have 2 computer 1 with a ubuntu 10, one with windows 7.
I can access the windows 7 computer from Ubuntu, and see all the documents.
However I can't access \\SAMBA24 which I assume is the Ubuntu.
What do i have to do ?
I'm a complete beginner at this.
Windows 7 can't find networkpath, and Ubuntu says fail to retrieve sharelist from server.

---

### Post by Scunizi on 2010-05-02
I'm assuming samba24 is what you named your computer when you installed Ubuntu.  Install smbfs and avahi. you'll either find it in synaptic or in a terminal you can type sudo apt-get install smbfs avahi <then hit enter>.  By default Ubuntu doesn't allow sharing.. so to see the ubuntu machine, right click a folder and choose "share".. if you do this first the system will typically install what is needed so you don't have to do the first couple of things I mentioned.

---

### Post by d00derino on 2010-05-02
[http://ubuntuforums.org/showthread.php?t=1468498](http://ubuntuforums.org/showthread.php?t=1468498)

I'm REALLY trying to push this guy's tutorial because it works and is very simple. You don't need the other package ewientje suggested (although I will commend him for helping out). All you need is Samba, and follow the instructions, and leave the guy some nice feedback lol.

---

### Post by Morbius1 on 2010-05-02
You seem to imply that you've created shares on the Ubuntu machine. What method of samba sharing did you use to create the share - there are two: Nautilus-share ( Nautilus > Right Click > Sharing Options ) and Classic-share.

If you post the output of the following commands maybe we can see what's up:

Open **Terminal**
Type **net usershare info**  
Type** testparm -s**

Also in Win7, are you using "Windows Live assistant":
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

---

### Post by ewientje on 2010-05-02
First of all, both of you, thanks for your help. Since it is getting late for me here, and being allready sleep deprived because I installed Ubuntu on 2 computers till 2 oclock in the morning, I'll call it a night now. 
Samba24 is what Ubuntu did, I didn't do that, I made another share, called corrie-desktop, following some instructions.

---

### Post by d00derino on 2010-05-02
> **Morbius1 said:**
> You seem to imply that you've created shares on the Ubuntu machine. What method of samba sharing did you use to create the share - there are two: Nautilus-share ( Nautilus > Right Click > Sharing Options ) and Classic-share.

If you post the output of the following commands maybe we can see what's up:

Open **Terminal**
Type **net usershare info**  
Type** testparm -s**

Also in Win7, are you using "Windows Live assistant":
[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

Windows 7 should detect it from your network, in Explorer (Winkey + E) > Network. For some reason I always thought it needed to be threw a LAN, because on campus where I go to school it needs to be LAN'd to work, but at my house it shows up when it just uses the wireless connection. 

I have to say, I love Windows 7 and Ubuntu is really growing on me. They make a good team -- it's super easy to make shares between the two, especially if you use the tutorial I found (and posted here). It's a very enlightening feeling knowing it's this simple to set up. I used an old thread here that worked, but was about 3 times the work, and was version specific so the paths didn't match up post 9.04.

---

### Post by Morbius1 on 2010-05-02
Nautilus-share:

Open Nautilus ( your home folder )
Right click say .... /home/your_username/Public
Select "Sharing Options"
Select all three boxes
Select Create Share

You've just created a public share that will allow guest access.

The point of my post was that there are two different samba methods. I would recommend using only one at a time. To be sure, I suggested posting the output of the two commands so we can see what method he's using and how he's using it.

As for the Win7 link, I believe it's self explanatory - it's a procedure to uninstall the Live Assistant.

---

### Post by Scunizi on 2010-05-02
If you're going to do samba and not nautilus share.. then I though I'd share my samba conf file for examination.  It may give you more ideas of how it can be implemented.  Lines with a " # " or an apostrophe are considered "comment lines" or are lines that are commented out so samba will not use them.

> 
# Server Section #

[global]
  netbios name = <my computer name>
  workgroup = WORKGROUP
  server string = %h server (Samba, Ubuntu)

  interfaces = lo eth0 wlan0
  hosts allow = 192.168.0. 127.0.0.1
  hosts deny = 0.0.0.0/0
  bind interfaces only = yes
  socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	unix extensions = No

  log file = /var/log/samba/log.%m
  max log size = 50

  security = user
  local master = Yes
  os level = 33
  domain master = Yes
  preferred master = Yes
  wins support = Yes
  dns proxy = No

## Security Section ###
  panic action = /usr/share/samba/panic-action %d
  encrypt passwords = true
  passdb backend = tdbsam
  obey pam restrictions = yes
  unix password sync = yes
  passwd program = /usr/bin/passwd %u
  passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
  pam password change = yes
  map to guest = bad user
  create mask = 0644
  directory mask = 755

  guest account = nobody
  
#  hide files = /.*/
#  create mask = 0644
#  Debug logging information
#  log level = 0 vfs:2
#  debug timestamp = yes
#  vfs objects = extd_audit
#  syslog = 0
      

#[homes]
  #guest ok = no
  #read only = no
  #valid users = %S
  
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no


############ Global Shares ###############3
[Approv_BPO]
	comment = Approved BPOz
	path = /media/Data/BPO/Approv_BPO
	read only = No
	writeable = yes
#	valid users = user1 user2
	public = Yes
	printable = Yes
	browseable = Yes
	guest ok = Yes
#	inherit permissions = yes
	create mask = 0666
	directory mask = 0777

[BPO]
	comment = BPO_Files
	path = /media/Data/BPO/
	read only = No
	guest ok = Yes
	public = Yes
	browseable = Yes
	create mask = 0666
	directory mask = 0777
	writeable = Yes
#	inherit permissions = yes

[Music]
	comment = Dadz_Music
	path = /media/Data/Music
	read only = Yes
	guest ok = Yes	
	public = Yes
	browseable = Yes
	create mask = 644
	directory mask = 755


---

### Post by Morbius1 on 2010-05-02
Too many cooks spoiling this broth............... I'm outa here :-D

Good luck.

---

### Post by ewientje on 2010-05-03
this was the output of :

corrie@corrie-desktop:~$ net usershare info
[corrie1]
path=/home/corrie
comment=
usershare_acl=Everyone:R,
guest_ok=n

[pictures]
path=/home/corrie/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=n

corrie@corrie-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: netbiosname corrie-desktop
Processing section "[homes]"
Processing section "[printers]"
WARNING: The "share modes" option is deprecated
Processing section "[corrie-desktop]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_DOMAIN_MEMBER
[global]
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	security = ADS
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = corrie
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	browsable = No
	locking = No
	share modes = No

[corrie-desktop]
	path = /home/corrie
	read only = No
corrie@corrie-desktop:~$ 




At the moment I can connect from Ubuntu to Windows 7.
I can access w7 through connect to server: 
or Network, Workgroup

And my windows7 computer can see corrie-desktop, a share I tried to create on the ubuntu one. He want to access it now, but won't accept the username or password.

I don't have Windows Livein installed, never had. And I don't have a small homenetwork installed on w7, because they all have to be w7, and that is not the case here. W7 has avg firewall, but if I can get in, I should also be able to get out. Ubuntu has no firewall.

At Ubuntupc I can still see the samba24 share, which I did not create, and I thought by installing gadmin-samba that share also popped up.
The Ubuntu was upgraded from 9.04 to 9.10 via internet, and then with alternate cd to 10.4, because the 9.10 version makes a mess with my internet connection. After the upgrade I had the samba24 share.

---

### Post by Morbius1 on 2010-05-03
OK, I'm back - but I won't stay long I promise.

When I saw these lines in your testparm output I realized that this is above my paygrade:
>  Server role: ROLE_DOMAIN_MEMBER
    security = ADSYou've set yourself up as being part of a domain. That means things like kerberos, and realms, and password servers somewhere on the network. If this is just a simple home network and this smb.conf is the result of using gadmin-samba, I would never use it again.

However, I would like to comment on the Nautilus-share part of this problem.

You have two nautilus-shares:
> [corrie1]
path=/home/corrie
comment=
usershare_acl=Everyone:R,
[COLOR=Blue] guest_ok=n[/COLOR]

[pictures]
path=/home/corrie/Pictures
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=n[/COLOR]Both of them do not allow guest access. Yet in the [global] section of smb.conf you have this line:
>  [COLOR=Blue]    guest ok = Yes[/COLOR]Whatever is in the [global] section overrules everything else. Go back into nautilus and "unshare" /home/corrie and /home/corrie/Pictures. You'll still have the Classic-share in smb.conf:
> [corrie-desktop]
	path = /home/corrie
	read only = No

You won't need to restart samba since nautilus-share doesn't require samba to be restarted.

The other odd thing is this line in the [global] section of smb.conf:
>      guest account = corrieThat's a little different. Unfortuanately you don't have a mechanism to ever get to the guest account because you're missing a line:
```
map to guest = Bad User
```Then again you're part of a domain and all passwords are being controlled by another mechanism. Like I said, this is out of my area of expertise. Member CAPSCREW might be able to maneuver through these waters but not I.

---

### Post by Scunizi on 2010-05-03
All good comments by Morbius1.  I take exception to one thing he mentioned. Global settings do not universally override other settings in the shares.  Some settings do apply universally and some don't.  This is how you maintain fine grained control over your shares.  

Quote from Samba docs
>  Each section of the smb.conf file that specifies a share, or a meta-service, is called a stanza. The global stanza specifies settings that affect all the other stanzas in the smb.conf file. Configuration parameters are documented in the smb.conf man page. Some parameters can be used only in the global stanza, some only in share or meta-service stanzas, and some can be used globally or just within a share or meta-service stanza. 

One thing mentioned briefly is "testparm".. it's part of Samba and checks your smb.conf file for errors.. very handy tool.

---

### Post by dannyboy79 on 2010-05-03
> **Scunizi said:**
> All good comments by Morbius1.  I take exception to one thing he mentioned. Global settings do not universally override other settings in the shares.  
correct. each share can have fine grained control, if he didn't have the guest_ok set for the share, it would read the global setting of allowing guest access.

The thing to is ask the OP if he even wants active setup? OP, is this a simple home network or do you have tons of users to manage and want to use a domain versus a WORKGROUP?

---

### Post by ewientje on 2010-05-03
I did comply with the suggestions of Morbius1, sort of, I uninstalled Samba, and I unshared my folders, and replaced smb.conf with a backup. Restarted my computer, tried to share with Nautilus one of my folders, got a message that some service was not installed, I installed the service restarted again,(he installed samba again) and now I have on both pc's access to my files, corrie-desktop on Ubuntu and corrie-pc on windows7.
So I think this problem is solved.
Thank you all very much for your help.

---

### Post by Morbius1 on 2010-05-03
I'm awfully talkative for someone you vowed to never return:D

ewientje, I'm glad you found a way out of this mess. For future reference there is a copy ( sort of ) of the factory fresh smb.conf available for people like us that mess with things too much at:

**/usr/share/samba/smb.conf**

It only has one mistake:
> encrypt passwords = noIt should be set to Yes. It would have saved you a reinstall of samba.

Scunizi and dannyboy79,

You are quite right about global vs share. What I was thinking of was a parameter that controlls whether or not nautilus-share will [COLOR=Blue]allow guest access to be set[/COLOR]: **usershare allow guests = yes**. It is in fact a global parameter that contols how one can set a nautilus-share. Got myself discombobulated there. 

There is enough bad information on the web and in this forum concerning Samba without me contributing to it. My sincere apologies.

---

