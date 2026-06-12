---
title: "SAMBA after 9.04 doesnt work"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by evilbuntu on 2009-07-21
well by the title youc an see after the upgrade from 8.04 to 9.04 my samba no longer works but......

the ubuntu can see the xp machine it just cant mount the shared drives saying "can not contact server to find the share list"

my xp machine can still see and access the linux shared drive but not vice versa.

i have gone in to my samba setting in webmin and tried to make adjustments but no luck.

my next step is to remove samba and start all over. any help appreciated before this though thanks.

---

### Post by superprash2003 on 2009-07-21
have you tried accessing via ip? like smb://x.x.x.x ?

---

### Post by evilbuntu on 2009-07-21
yes that didnt work, but i can ping the other machine fine

update:

i must have tried that before i made changes in my xp and smaba machine cause now i can apparently ip in only

---

### Post by swerdna on 2009-07-21
I suggest three diagnostics:

[LIST=1]
[*]Can you post here the contents of your file smb.conf but in abbreviated form, generated this way: Open a terminal and run the command:```
testparm -s
``` post back here the results.
[*]Also check that the line in smb.conf that names the workgroup is the same as the name for the workgroup on xp (see My Computer --> Right click --> Computer Name --> workgroup).
[*]probably not a problem, but just to be sure, check the new firewall ufw status with this command: ```
sudo ufw status
```
[/LIST]

---

### Post by evilbuntu on 2009-07-22
this is the file. the only thing i did was change my work group and username here. thanks guys

Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[stuff]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = "work group is correct"
    map to guest = Bad User
    obey pam restrictions = Yes
    passdb backend = tdbsam
    guest account = "me"
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    wins support = Yes
    default service = global
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    path = /media/SimpleDrive/ProFTP
    valid users = media
    write list = media
    read only = No
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    read only = Yes
    create mask = 0700
    guest ok = No
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
    read only = Yes
    guest ok = No

[stuff]

---

### Post by doas777 on 2009-07-22
I usually expect to see a line in the global config like:
```
security=share
OR
security=user
```if you want unauthenticated, then I think you map bad user to guest and allow guest on the shares. but you still need the "security =" setting.

also most of the time, before a user can login, i need to run:
```
sudo smbpasswd -a <username>
``` on the server and set the samba password for the user there.

---

### Post by evilbuntu on 2009-07-22
> **doas777 said:**
> I usually expect to see a line in the global config like:
```
security=share
OR
security=user
```if you want unauthenticated, then I think you map bad user to guest and allow guest on the shares. but you still need the "security =" setting.

also most of the time, before a user can login, i need to run:
```
sudo smbpasswd -a <username>
``` on the server and set the samba password for the user there.

it seems you alter the files manually where i use webmin.

I am not that in depth that i really know these files yet and how to manually change them.
I do like to have it so there is no login needed and everyone just goes in and out precariously lol.
It has worked fine until the update though. Though i may have found out that on my xp machine i am running avg anti spyware and background watcher and that may be stopping my linux machine from entering. i had a similar problem on this same machine before i switched to AVG and was running spyware terminator.

to change the file though do i basically just change my name in guest to "bad user"?

thanks

---

### Post by doas777 on 2009-07-22
> **evilbuntu said:**
> it seems you alter the files manually where i use webmin.

I am not that in depth that i really know these files yet and how to manually change them.
I do like to have it so there is no login needed and everyone just goes in and out precariously lol.
It has worked fine until the update though. Though i may have found out that on my xp machine i am running avg anti spyware and background watcher and that may be stopping my linux machine from entering. i had a similar problem on this same machine before i switched to AVG and was running spyware terminator.

to change the file though do i basically just change my name in guest to "bad user"?

thanks

well first, I've never done a sucessful distro upgrade, so a good starting point you may want to confirm that samba is installed
```
sudo apt-get install samba --reinstall
``` if you get an error, remove the '--reinstall'.

failing that, try to add "security = user" and restart samba with
```
sudo /etc/init.d/samba restart
``` to see if that helps. I'm prolly not qualified to assist you with unauthenticated access (I know the theory but have never tried), but hopefully someone will. I am led to believe that it is important to have the security mode defined, but it may default if the value is not present.

if you look in \etc\samba are there any backups of smb.conf? the solution may be as simple as restoring an older config.

---

### Post by martinbaselier on 2009-07-22
to edit the file manually open a terminal and type:
**sudo gedit /etc/samba/smb.conf**

There are a lot of comments in the file, starting with #. 
All lines starting with # or ; are regarded comments and are ignored. 

Please read the beginning of the file before starting to make any changes. Also create a comment when you make changes, so you know what you have done later. 
# june 16th 2009 17:10, turned of option ....

when **security = user** is on, you will need a linux user account to get access. 
**guest ok=yes** will allow guest (unauthorised) access.
It would be best to define this per share.
You can find your shares on the bottom of the file.

---

### Post by evilbuntu on 2009-07-22
> **martinbaselier said:**
> to edit the file manually open a terminal and type:
**sudo gedit /etc/samba/smb.conf**

There are a lot of comments in the file, starting with #. 
All lines starting with # or ; are regarded comments and are ignored. 

Please read the beginning of the file before starting to make any changes. Also create a comment when you make changes, so you know what you have done later. 
# june 16th 2009 17:10, turned of option ....

when **security = user** is on, you will need a linux user account to get access. 
**guest ok=yes** will allow guest (unauthorised) access.
It would be best to define this per share.
You can find your shares on the bottom of the file.

well i looked at the file and it appears that security does = yes and in teh shares everything that doesnt have to do with printing is set guest ok = yes.

as for share, should this file have the acceptable user list anywhere? mine just basically has the info for my linux box only.
thanks, learning alot

---

### Post by martinbaselier on 2009-07-22
I'm not an expert on samba. I got it working in the past by following some online explanations. 

Here's my output of testparm -s. 
```

Server role: ROLE_STANDALONE
[global]
	workgroup = ADMIN
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
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

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[tin]
	path = /home/tin
	read only = No
	guest ok = Yes

```

allowguests seems the important differenece 

When I check the authentication part, I only have the stuff below in it.
```

####### Authentication #######
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   pam password change = yes
   map to guest = bad user

```

Please keep in mind that opening your network like this is of course quite insecure.

---

### Post by swerdna on 2009-07-22
> my xp machine can still see and access the linux shared drive but not vice versa

You have the Linux machine configured as a wins server. If you haven't configured the xp machine to interact with a wins server, communications will be flaky. I suggest that you back up your existing smb.conf with this command:```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```and then open the original for editing with this command:```
gksu gedit /etc/samba/smb.conf
```and then copy/paste this alternative into it, over the top of the existing code, except leave the stanza for [stuff] in ther if it is real. Here the correct version of smb.conf:
```
[global]
workgroup = WORKGROUP_NAME [COLOR="Red"]<----- adjust this[/COLOR]
netbios name = NETBIOS_NAME [COLOR="Red"]<----- adjust this[/COLOR]
name resolve order = bcast host lmhosts wins
map to guest = Bad User
local master = yes
preferred master = yes
os level = 65
printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
load printers = yes
use client driver = yes
server string =
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

[printers]
comment = All Printers
path = /var/spool/samba
printable = Yes
create mask = 0700
guest ok = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
read only = Yes
guest ok = No

[stuff]
```
If you have two Linux boxes, leave out the line "preferred master = yes".
As it stands, the share [stuff] is broken. I assume you know that and have left the detail out of these forums for security purposes.

Then you would save and reboot and then reboot the winbox and finally, reboot them both again, sequentially.

I must assume you know about ufw and that it's OK for Samba (or switched off).

Some other comments:

Since you didn't have the [global] stanza configured for "usershares" I assume you do not use the sharing facility if Nautilus to make shares? Is that correct?

If you have no line for security (like security = user) in the [global] stanza, it will use the default which is "security = user", so forget about that line because it's correct to simply leave it out.

You only need to run smbpasswd if there is a secure share on the Ubuntu machine. If it's configured "so there is no login needed and everyone just goes in and out precariously lol" then you don't need it. Depends what's in [stuff].

"sudo gedit": sometimes creates problems, the preferred method is "gksu gedit".

You asked: "should this file have the acceptable user list anywhere". If you have "guest ok = yes" then "valid users" is kind of a contradiction in terms, so don't use it in a guest share. So this combination is very dicey:
> valid users = media
write list = media
The "guest ok" line should be done on a share-by-share basis. I assume it's in the full stanza for [stuff] which you left out of your post.

Finally, AVG will not interfere with Samba, and the windows xp firewall allows Samba by default, but I don't know about "background watcher" so it wouldn't hurt temporarily disable that as a diagnostic precaution until it's all working.

FFI reference: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by evilbuntu on 2009-07-23
well update:


i removed all teh existing networking ID's, mapped drives ETC form my XP machine and re ran it. Now both sides seem to be working fine.

Thanks everyone

---

