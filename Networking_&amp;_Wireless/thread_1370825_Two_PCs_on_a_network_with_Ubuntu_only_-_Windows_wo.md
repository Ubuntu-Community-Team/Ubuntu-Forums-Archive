---
title: "Two PCs on a network with Ubuntu only - Windows word ?"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by Mongao on 2010-01-02
Hi all,

I have two computers connected through a Linksys router, I have started from scratch again, formatted HD`s and installed 9.10 on both.

When I try to share folders, Ubuntu tells me that it needs to install Windows (!!!!!) drivers, it asks me to install samba :confused::(

Question: Why does the word "Windows" appear in my screen ?? I can`t understand, as I am in a (supposedly...) Windows free environment :confused:

OK, I installed Samba through apt-get, tried sharing, but got stuck in a screen with three fields; username, domain (appears filled in WORKGROUP),and password. Of course I know all these as I have installed everything, I fill in and nothing happens, this screen keeps reloading as if either the username or password were wrong - they are not.

After that, I tried editing the smb.conf file accordingly, adding the line 

usershare owner only = false

under the global section, nothing changed.

When I click on "Network", I see three options:

-PC1 (the PC I wanna reach)
-PC2 (the own PC)
-Windows Network (PLEASE WHY DOES THIS APPEAR ?? WHY IS WINDOWS INVOLVED IN THAT ???) :confused::(

When I click on PC2, occasionally I can see the shared folder, but when I click on it either of two things happen:

1) The screen I mentioned above appears and I can`t get rid of it
2) Ubuntu says "Failed to mount windows share" - again, why does Ubuntu mention Windows ?? can`t understand it at all ! :confused::confused:

Please help me,

Thanks,

Mongao

---

### Post by Morbius1 on 2010-01-02
Samba is the reversed engineered, Microsoft **SMB** networking protocol. That's why there are all those references to Windows.

It's very late in the day for me so I really couldn't follow the rest of your post. What would be of great help is for you to post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the Ubuntu machine*[/COLOR]

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do.

---

### Post by Mongao on 2010-01-02
> **Morbius1 said:**
> Samba is the reversed engineered, Microsoft **SMB** networking protocol. That's why there are all those references to Windows.

It's very late in the day for me so I really couldn't follow the rest of your post. What would be of great help is for you to post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the Ubuntu machine*[/COLOR]

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do.

Thanks, here it is the copy/paste of the commands:

-----------------------------------

andre@andre-ubuntu:~$ net usershare info
[geral_andre]
path=/media/Dados_1/Geral_Andre
comment=
usershare_acl=Everyone:F,
guest_ok=y

[videos]
path=/media/Dados_1/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=n

[videos_tv]
path=/media/Dados_2/Videos_TV
comment=
usershare_acl=Everyone:F,
guest_ok=n

andre@andre-ubuntu:~$ sudo net usershare info
[sudo] password for andre: 
andre@andre-ubuntu:~$ sudo net usershare info
andre@andre-ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
andre@andre-ubuntu:~$ smbtree
Enter andre's password: 
WORKGROUP
	\\ANDREA-UBUNTU  		andrea-ubuntu server (Samba, Ubuntu)
		\\ANDREA-UBUNTU\geral_andrea   	
		\\ANDREA-UBUNTU\IPC$           	IPC Service (andrea-ubuntu server (Samba, Ubuntu))
		\\ANDREA-UBUNTU\print$         	Printer Drivers
	\\ANDRE-UBUNTU   		andre-ubuntu server (Samba, Ubuntu)
		\\ANDRE-UBUNTU\geral_andre    	
		\\ANDRE-UBUNTU\videos         	
		\\ANDRE-UBUNTU\videos_tv      	
		\\ANDRE-UBUNTU\IPC$           	IPC Service (andre-ubuntu server (Samba, Ubuntu))
		\\ANDRE-UBUNTU\print$         	Printer Drivers
andre@andre-ubuntu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.104   ANDREA-UBUNTU  [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.105   ANDRE-UBUNTU  +[WORKGROUP] [Unix] [Samba 3.4.0]
andre@andre-ubuntu:~$ nmap -sT 192.168.0.105/22
The program 'nmap' is currently not installed.  You can install it by typing:
sudo apt-get install nmap
nmap: command not found
andre@andre-ubuntu:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liblua5.1-0
The following NEW packages will be installed:
  liblua5.1-0 nmap
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,681kB of archives.
After this operation, 6,570kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main liblua5.1-0 5.1.4-3 [90.5kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main nmap 5.00-2 [1,590kB]
Fetched 1,681kB in 3s (436kB/s) 
Selecting previously deselected package liblua5.1-0.
(Reading database ... 141105 files and directories currently installed.)
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-3_i386.deb) ...
Selecting previously deselected package nmap.
Unpacking nmap (from .../archives/nmap_5.00-2_i386.deb) ...
Processing triggers for man-db ...
Setting up liblua5.1-0 (5.1.4-3) ...

Setting up nmap (5.00-2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
andre@andre-ubuntu:~$ 

---------------------------------------------

Installed nmap, but still have the same message:

FAILED TO MOUNT WINDOWS SHARE

any guess ?

Thanks,

Mongao

---

### Post by garryknight on 2010-01-02
If you're only running Linux on your network, you don't have to use Samba at all. You could mount partitions on each machine onto the other by using NFS (Network File System) or sshfs (Secure Shell File System). There are tutorials on how to do both of these on the web.

It's very late in the day for me, too (or early, depending how you look at it) so I don't have time to go into details but I'll keep an eye on the thread in case you decide to use one of these and get into problems.

---

### Post by Mongao on 2010-01-02
> **garryknight said:**
> If you're only running Linux on your network, you don't have to use Samba at all. You could mount partitions on each machine onto the other by using NFS (Network File System) or sshfs (Secure Shell File System). There are tutorials on how to do both of these on the web.

It's very late in the day for me, too (or early, depending how you look at it) so I don't have time to go into details but I'll keep an eye on the thread in case you decide to use one of these and get into problems.

Thanks gary, but I wanna the "less difficult" way....if it`s samba, that`s the way. I had followed another guide to have Windows access an Ubuntu PC, it worked one way but not the other, so I tried an "Ubuntu only" configuration expecting it to be straight forward - but it`s not :(

I`ll keep reading, but I don`t have the time to be a computer-geek, typing in some lines on the terminal is OK for me, but i am not a systems analyst and I am figuring out that Linux may still be far from common users like me.

Thanks,
Mongao

---

### Post by Mongao on 2010-01-02
Please, if I edit the smb file like here

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

will it work ? 

I assume this link is only for Ubuntu and Windows computers on the LAN, I a "how to" for two computers running Ubuntu only, NOT Windows.


EDIT:
I have tried these fixes:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

still, I receive the message back: "failed to mount windows share" when I click on the folder on the remote computer. Annoying.

Thanks,
Mongao

---

### Post by Mongao on 2010-01-03
OK, although Windows is not involved, I have done this

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

on both computers. Now, the screen "failed to mount windows bla-bla-bla" hasn`t appeared, but I get stuck to the screen that asks me to enter username, domain (appears filled as WORKGROUP, as expected) and password; can`t get rid of that.

[B][I][U]I CAN SEE THE SHARED FOLDERS, BUT WHEN I DOUBLE CLICK ON THEM I CAN`T PASS THE 3 FIELDS SCREEN.
[/U][/I][/B]
Sometimes NOTHING appears when I click in "network".

I am absolutely sure that username and password I am using are correct.

Any guess ?

Thanks,

Mongao

---

### Post by Morbius1 on 2010-01-03
Lordy, lordy. If you followed this post: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) you're now using two completely different methods to share folders. We need to go back to the beginning to find out exactly where you are. Sorry

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the Ubuntu machine*[/COLOR]

---

### Post by dmizer on 2010-01-03
Ditch samba and Windows style sharing. Try NFS instead. It's dead easy by comparison. There's a good howto in the 4th link in my sig.

---

### Post by garryknight on 2010-01-03
I would second this. NFS is much easier to set up than Samba. In fact, if you're not running KDE, I'd say that NFS is the easiest option.

---

### Post by Mongao on 2010-01-03
Thanks friends, I have some questions please

On this part:

-------------------------------------------------

"Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files

Note you may need to restart above services:
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

Mounting at boot using /etc/fstab
Invoke the text editor using your favorite editor, or
gksudo gedit /etc/fstab

In this example my /etc/fstab was like this:

    * server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr

You could copy and paste my line, and change &#8220;servername.mydomain.com:/files&#8221;, and &#8220;/files&#8221; to match your server name:share name, and the name of the mount point you created.
It is a good idea to test this before a reboot in case a mistake was made.
type
mount /files
in a terminal, and the mount point /files will be mounted from the server."

-------------------------------------

I am now sitting on the "andrea" computer, and I wanna access a folder called "videos" in the "andre" computer.
"andre" and "andrea" are the login names on both computers.
I remember that, when installing ubuntu, I filled in "andre-ubuntu" and "andrea-ubuntu" as computer names. So, "andre" is my login name, while "andre-ubuntu" is the computer name.

Please, can anyone please give an example on how my line on the fstab should be at the "andrea" computer ?

Also, after this "sudo /etc/init.d/nfs-kernel-server restart" I received this error

exportfs warning /file does not exist

What is this "file" please ? Is it the name of the folder I wanna share ?

------------------------------------

another question, I am planning on buying a NAS device like the D-Link DNS-343, it will be hooked to my router of course.

Considering this, SHOULD I GO THE SAMBA OR THE NFS WAY ?

smb.conf has been completely rebuilt following the other guide "samba-peer-to-peer..."

-----------------------------------------

Samba: the problem is that one computer access the server properly, but the vice-versa is not true, the computer that access the other can`t be accessed by that one (I get stucked with the username,domain,password screen). Is there an easy way to fix that ?

Thanks,

Mongao

---

### Post by Mongao on 2010-01-03
Thanks friends, I have some questions please

On this part:

-------------------------------------------------

"Mounting manually
Example to mount server.mydomain.com:/files to /files. In this example server.mydomain.com is the name of the server containing the nfs share, and files is the name of the share on the nfs server

The mount point /files must first exist on the client machine.
cd /
sudo mkdir files

to mount the share from a terminal type

sudo mount server.mydomain.com:/files /files

Note you may need to restart above services:
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-common restart

Mounting at boot using /etc/fstab
Invoke the text editor using your favorite editor, or
gksudo gedit /etc/fstab

In this example my /etc/fstab was like this:

    * server.mydomain.com:/files /files nfs rsize=8192,wsize=8192,timeo=14,intr

You could copy and paste my line, and change “servername.mydomain.com:/files”, and “/files” to match your server name:share name, and the name of the mount point you created.
It is a good idea to test this before a reboot in case a mistake was made.
type
mount /files
in a terminal, and the mount point /files will be mounted from the server."

-------------------------------------

I am now sitting on the "andrea" computer, and I wanna access a folder called "videos" in the "andre" computer. 
"andre" and "andrea" are the login names on both computers. 
I remember that, when installing ubuntu, I filled in "andre-ubuntu" and "andrea-ubuntu" as computer names. So, "andre" is my login name, while "andre-ubuntu" is the computer name.

Please, can anyone please give an example on how my line on the fstab should be at the "andrea" computer ?

Also, after this "sudo /etc/init.d/nfs-kernel-server restart" I received this error

exportfs warning /file does not exist

What is this "file" please ? Is it the name of the folder I wanna share ?

------------------------------------

another question, I am planning on buying a NAS device like the D-Link DNS-343, it will be hooked to my router of course.

Considering this, SHOULD I GO THE SAMBA OR THE NFS WAY ?

smb.conf has been completely rebuilt following the other guide "samba-peer-to-peer..."

-----------------------------------------

Samba: the problem is that one computer access the server properly, but the vice-versa is not true, the computer that access the other can`t be accessed by that one (I get stucked with the username,domain,password screen). Is there an easy way to fix that ?

Thanks,

Mongao

---

### Post by Mongao on 2010-01-03
-

---

### Post by Mongao on 2010-01-03
Considering I`ll incorporate other devices to this network (media player, NAS and a Windows based laptop), I think that the Samba way should be the choice, what do you think please ? Would NFS allow sharing with other devices ? I don`t think so....:confused:

As I said, I have done this on BOTH Computers:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

but only PC1 access the shared folders on PC2, PC2 "sees" the shared folders on PC1, but can`t open it. Does anyone have an idea on that ? I am sure that something is missing in one of the computers....seems like I am almost there...

Thanks,

Mongao

---

### Post by Mongao on 2010-01-03
> **Morbius1 said:**
> Samba is the reversed engineered, Microsoft **SMB** networking protocol. That's why there are all those references to Windows.

It's very late in the day for me so I really couldn't follow the rest of your post. What would be of great help is for you to post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type **testparm -s**
Type **smbtree**
Type **findsmb**
Type **nmap -sT 192.168.0.100/22**
[COLOR=Blue]*Change 192.168.0.100 to the ip address of the Ubuntu machine*[/COLOR]

You may not have nmap installed but when you issue the nmap command it will ask you if you want to install it - you do.

Here it is:

-------------------------

andre@andre-ubuntu:~$ net usershare info
[para_andrea]
path=/media/Dados_2/Para_Andrea
comment=
usershare_acl=Everyone:F,
guest_ok=n

[geral_andre]
path=/media/Dados_1/Geral_Andre
comment=
usershare_acl=Everyone:F,
guest_ok=n

[videos]
path=/media/Dados_1/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=n

[videos_tv]
path=/media/Dados_2/Videos_TV
comment=
usershare_acl=Everyone:F,
guest_ok=n

andre@andre-ubuntu:~$ sudo net usershare info
andre@andre-ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	netbios name = ANDRE
	server string = 
	null passwords = Yes
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS
	wins support = Yes
	usershare owner only = No

[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No

[MyFiles]
	path = /media/
	force user = andre
	force group = andre
	read only = No
	create mask = 0644
andre@andre-ubuntu:~$ smbtree
Enter andre's password: 
WORKGROUP
	\\ANDREA-PC      		
		\\ANDREA-PC\Users          	
		\\ANDREA-PC\Torrents       	
		\\ANDREA-PC\Samsung SCX-4300 Series	Samsung SCX-4300 Series
		\\ANDREA-PC\print$         	Printer Drivers
		\\ANDREA-PC\IPC$           	Remote IPC
		\\ANDREA-PC\Geral_Andrea   	
		\\ANDREA-PC\D$             	Default share
		\\ANDREA-PC\C$             	Default share
		\\ANDREA-PC\ADMIN$         	Remote Admin
	\\ANDRE          		
		\\ANDRE\para_andrea    	
		\\ANDRE\geral_andre    	
		\\ANDRE\videos         	
		\\ANDRE\videos_tv      	
		\\ANDRE\IPC$           	IPC Service ()
		\\ANDRE\MyFiles        	
		\\ANDRE\print$         	
andre@andre-ubuntu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.105   ANDRE          [	WORKGROUP     ]
andre@andre-ubuntu:~$ nmap -sT 192.168.1.105/22

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-01-03 17:16 PST

------------------------------

Nothing happened after the last command :confused:

Any guess please ?

Thanks,
Mongao

---

### Post by Mongao on 2010-01-04
I have noticed that, on PC2 where files CAN BE ACCESSED from PC1, the third box on the sharing options "guest access" is marked and grey, can`tbe edited.

On PC1, where the shared folder can`t be accessed, it`s also grey (unwritable), but it`s unmarked.

I have made so many changes that I don`t remember how I have done that, can someone please tell me how to make this option accessible again ?

Thanks,

Mongao

---

### Post by Morbius1 on 2010-01-04
If you could start calling PC1 and PC2 as ANDRE and ANDREA-PC              it would be helpful since I don't know what PC1 and PC2 are.

All of your nautilus-share shares have this form:
> [para_andrea]
path=/media/Dados_2/Para_Andrea
comment=
usershare_acl=Everyone:F,
guest_ok=nYou've given full read /write access, but require authentication. Unless you've created another login user and created a corresponding samba user, or at least created a samba user for your own login user name, no one will get access.

Your classic samba share will not work:
> [MyFiles]
    path = /media/
    force user = andre
    force group = andre
    read only = No
    create mask = 0644/media is owned by user:group = root:root with permissions set to read/write by user=root and read only by group=root.

You've set force user and force group to andre but andre does not have permissions to do much in /media

You've set read only = no but andre has no permissions to write to /media. andrea may have permissions to write to subdirectories of /media but not to /media itself.

You've also set this one to require authentication ( force user = has nothing to do with authentication, it only applies after authentication )

> Starting Nmap 5.00 ( [http://nmap.org]("http://nmap.org/") ) at 2010-01-03 17:16 PST
Nothing happened after the last commandNo errors, no output at all? I'd disable any firewalls on those machines. If this is a clean install of Ubuntu and you haven't done anything with the firewall just leave it as it is.

What I would do is this:

(1) I would, for the time being anyway, remove the "MyFiles" share from smb.conf and restart the samba server: **sudo service samba restart**

(2) I would take one of your nautilus-shares, say this one:
> [para_andrea]
path=/media/Dados_2/Para_Andrea
comment=
usershare_acl=Everyone:F,
guest_ok=nAnd go back into nautilus and change it to allow guests to have access. Now see if you can access that share.

Access may still not be possible though because I don't know what file permissions you have on /media/Dados_2/Para_Andrea.

To find out post the output of these after you make the change ( above ) to allow guests on /media/Dados_2/Para_Andrea

[B]ls -dl /media/Dados_2/Para_Andrea
ls -l /media/Dados_2/Para_Andrea[/B]

---

### Post by Mongao on 2010-01-04
Morbius,

Thank you for your attention, I must admitt I haven`t understood much of what you said, I don`t know what authentication is, for example, and it`s hard for me to understand the meaning of the "forces", etc; also, I have noticed that the third box in my "sharing options" dialogue is greyed out, unmarked, and can`t be edited in the andre computer. In the andrea computer, it`s also greyed out and can`t be edited, but it`s marked.

I don`t remember how I did that, what happens now is that the andre computer can access andrea, but not the vice-versa.

This is my situation:

Computer 1:

netbios name: andre-ubuntu
login: andre


Computer 2:

netbios name: andrea-ubuntu
login: andrea

below is a copy of the andre computer smb.conf file, I have basically copied the template from the other thread and edited accordingly, the "andrea" smb file is the same. Could you please point me what to change specifically ? Thanks so much.

[global]
    ; General server settings
; of course, on the line below use proper user name
    netbios name = andre-ubuntu
    server string =
; workgroup = WORKGROUP is the Windows default
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]


[B][U]; I don`t understand this line below, all stuff that I want to share is on media (actually it`s a separate HD NTFS formatted), so I think that my path should be only path = /media/
but if I do this it doesn`t work.[/U][/B]

    ;path =/media/ (SHOULD BE THIS ??)
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755

;of course, change andre in the 2 lines below by your desired username
    force user = andre
    force group = andre

---

### Post by Morbius1 on 2010-01-04
All of this has to be deleted:

> [MyFiles]
;path =/media/ (SHOULD BE THIS ??)
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
;of course, change andre in the 2 lines below by your desired username
    force user = andre
    force group = andreDo that first and then restart samba: [B]sudo service samba restart

This latest posting of your smb.conf does not match your previous posting of your smb.conf. It's kind of hard for anyone to help you if you keep moving the target.
[/B]

---

### Post by Morbius1 on 2010-01-04
In an unusual moment of clarity for me I think I've discovered the source of your problem. Your getting advice from two different people. He's sending you down one path, and I'm sending you down another.

This isn't going to work because it looks like I'm having you undo everything he's making you do. I believe this is what we call in programming an infinite loop.

It won't hurt my feelings in the slightest if you go his way since it appears he understands the nature of the permissions problem you're having with the NTFS partition. ( Didn't you start this thread complaining about all this Windows stuff ? )

EDIT: You might want to tell him you're trying to share /home/samba - whatever that is.

---

### Post by Mongao on 2010-01-04
> **Morbius1 said:**
> In an unusual moment of clarity for me I think I've discovered the source of your problem. Your getting advice from two different people. He's sending you down one path, and I'm sending you down another.

This isn't going to work because it looks like I'm having you undo everything he's making you do. I believe this is what we call in programming an infinite loop.

It won't hurt my feelings in the slightest if you go his way since it appears he understands the nature of the permissions problem you're having with the NTFS partition. ( Didn't you start this thread complaining about all this Windows stuff ? )

EDIT: You might want to tell him you're trying to share /home/samba - whatever that is.

Well, not really; another  friend offered me the NFS way, I started shuffling around, but I quit that as soon as I noticed that I wouldn`t be able to add others windows based devices to my network, so I concentrated only in this thread that you have been kindly helping me - I need the samba way anyway.

I have done the changes you suggested on both computers, deleting everything after My Files.

Situation:

- One computers not only sees but access the shared folders on the others, good ! Please, can you explain what the changes meant ? Was it an issue with the "invisible" root user, that lives somewhere near here my two computers, messes both around and I never had the chance to ask him how to fix problems ? :(
Whenever I meet him i`ll invite him for a beer....

- my media player (actually it`s a samsung Blu-ray player with network capability) only sees the andre computer, not andrea, and says that "username and/or password" are wrong. Does it have anything to do with the root/andre users problem ? I have never understood this well....

- Please, how do I "ungrey" (make changeable) the third option on the "sharing options" dialogue box ? Rather than making only things 'work", I`d like to understand a bit more (I know some java programming, but I don`t know networks at all). I thought that changing the set to "y" in the smb file should work, but it didn`t.

You`re right when you say that I have changed things,last night I had some time and was shuffling around.

Thanks so much,
Mongao

---

### Post by shairozan on 2010-01-04
Make it a third for NFS. Using samba to connect two linux machines is kind of like paying a middle man to be the middle man for your middle men. You'll also get better transfer speeds out of NFS since it's a UDP protocol.

---

### Post by Mongao on 2010-01-04
> **shairozan said:**
> Make it a third for NFS. Using samba to connect two linux machines is kind of like paying a middle man to be the middle man for your middle men. You'll also get better transfer speeds out of NFS since it's a UDP protocol.

Thanks, but as I said I`ll need to add other Windows based computers to this network.

Actually, I didn`t know that Microsoft had set THE network standard, I thought it was just the Windows manufacturer....

Thanks,
Mongao

---

### Post by Morbius1 on 2010-01-04
> One computers not only sees but access the shared folders on the others, good ! Please, can you explain what the changes meant ?Can't answer that because I don't know which computer is which in your description.

> - my media player (actually it`s a samsung Blu-ray player with network capability) only sees the andre computer, not andrea, and says that "username and/or password" are wrong. Does it have anything to do with the root/andre users problem ? I have never understood this well....
I don't even know what that means.

> - Please, how do I "ungrey" (make changeable) the third option on the "sharing options" dialogue box ? Rather than making only things 'work", I`d like to understand a bit more (I know some java programming, but I don`t know networks at all). I thought that changing the set to "y" in the smb file should work, but it didn`t.This is the disturbing question because at this point there should be nothing in smb.conf to set to "y" so let's go back to the beginning:

On whatever machine has the greyed out guest option , post the output of the following commands:

**net usershare info ( [COLOR=Blue]EDIT: that was originally misspelled[/COLOR] )**
**testparm -s**
**ls -l /var/lib/samba/usershares**


[I]Not to start an NFS / Samba war but someone else suggested he use NFS and when he posted back asking for assistance with that it was like turing on the kitchen light and seeing all the cockroaches scatter. - just kidding - just kidding :)
[/I]

---

### Post by Mongao on 2010-01-04
> **Morbius1 said:**
> Can't answer that because I don't know which computer is which in your description.

I don't even know what that means.

This is the disturbing question because at this point there should be nothing in smb.conf to set to "y" so let's go back to the beginning:

On whatever machine has the greyed out guest option , post the output of the following commands:

**net usershare info ( [COLOR=Blue]EDIT: that was originally misspelled[/COLOR] )**
**testparm -s**
**ls -l /var/lib/samba/usershares**


[I]Not to start an NFS / Samba war but someone else suggested he use NFS and when he posted back asking for assistance with that it was like turing on the kitchen light and seeing all the cockroaches scatter. - just kidding - just kidding :)
[/I]

Hi,

A media player is device (like a separate computer) that plays only media and shows on the TV screen. It has a network port and a audio/video output, so it reads the video files on a shared folder and plays it on the TV. It has the capability of "seeing" computers in a network, access their shared folders and play video/audio content. My media player now sees ONLY the andre computer (it should see both computers), asks for the username/pass and says either one is wrong; all I can do is that it`s an 'authorization" issue (root user only accepted ? how can I set the andre computer to accept the connection from a third computer, not only the andrea computer ?).

What did I achieve by deleting everything after the "My Files" section of the smb file ? 

As far as I understood, saying only "path = /media/" wouldn`t work cause only root can access media, right ? So, I should have written "path = /media/dados_1/", cause andrea can access dados but not media, right ?

By deleting this line (like I did and things worked), I have basically authorized "anyone" to access "everything", does it make sense ?

Here it is the output of the commands you have asked,on the andre computer (things should look the same on the andrea computer)

 [B][U]THANKS AGAIN !!
[/U][/B]

andre@andre-ubuntu:~$ net usershare info
[para_andrea]
path=/media/Dados_2/Para_Andrea
comment=
usershare_acl=Everyone:F,
guest_ok=n

[geral_andre]
path=/media/Dados_1/Geral_Andre
comment=
usershare_acl=Everyone:F,
guest_ok=n

[videos]
path=/media/Dados_1/videos
comment=
usershare_acl=Everyone:F,
guest_ok=n

[videos_tv]
path=/media/Dados_2/Videos_TV
comment=
usershare_acl=Everyone:F,
guest_ok=n

andre@andre-ubuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = 
	null passwords = Yes
	username map = /etc/samba/smbusers
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS
	wins support = Yes

[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No
	browsable = No
andre@andre-ubuntu:~$ ls -l /var/lib/samba/usershares
total 16
-rw-r--r-- 1 andre andre 87 2010-01-04 13:13 geral_andre
-rw-r--r-- 1 andre andre 87 2010-01-04 13:14 para_andrea
-rw-r--r-- 1 andre andre 82 2010-01-04 13:14 videos
-rw-r--r-- 1 andre andre 85 2010-01-04 13:14 videos_tv
andre@andre-ubuntu:~$ ^C
andre@andre-ubuntu:~$

---

### Post by Mongao on 2010-01-04
Please,

There`s a printer connected to the andrea computer, the andre one doesn`t see it, here is a copy of my current smb.conf file:

[global]
    ; General server settings
; of course, on the line below use proper user name
    netbios name = andre-ubuntu
    server string =
; workgroup = WORKGROUP is the Windows default
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

---------------------------------

Thanks,
Mongao

---

### Post by Morbius1 on 2010-01-04
](*,)](*,)](*,)

> I have basically authorized "anyone" to access "everything", does it make sense ?No, if that's what's happening then you have moved into a parallel universe. You have no share definitions in smb.conf which means the only shares you have defined are defined by these:
> [para_andrea]
path=/media/Dados_2/Para_Andrea
comment=
usershare_acl=Everyone:F,
[COLOR=Blue] guest_ok=n[/COLOR]

[geral_andre]
path=/media/Dados_1/Geral_Andre
comment=
usershare_acl=Everyone:F,
[COLOR=Blue] guest_ok=n[/COLOR]

[videos]
path=/media/Dados_1/videos
comment=
usershare_acl=Everyone:F,
[COLOR=Blue] guest_ok=n[/COLOR]

[videos_tv]
path=/media/Dados_2/Videos_TV
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=n[/COLOR]As you can see, all of them have "[COLOR=Blue]guest_ok=n[/COLOR]". So each time someone tries to access those shares they should be prompted for a username and password. If they are not it may be related to the greyed out option. And for that I have no answer. But if it works for you the way it is and you're happy with it, then I'm happy with it too.

As for your second question about the printer. That's a completely separate thread you need to start. You don't want samba to handle printing, you want CUPS to handle printing. It has it's own server and works ( for the most part ) much better than samba.

> My media player now sees ONLY the andre computer (it should see both computers), [COLOR=Blue]asks for the username/pass and says either one is wrong[/COLOR]Out of all the pieces of hardware that you have on your network, the media player is the only one that seems to be obeying the laws of physics. It tries to connect to an andre share, the share is defined to not allow guests so it prompts the media player for a username and password. All of this is as it should be.

As for it not seeing the andrea computer, I'd be willing to bet you have not created any shares on nautilus. 

Good luck.

---

### Post by dmizer on 2010-01-04
> **Mongao said:**
> - Please, how do I "ungrey" (make changeable) the third option on the "sharing options" dialogue box ? Rather than making only things 'work", I`d like to understand a bit more (I know some java programming, but I don`t know networks at all). I thought that changing the set to "y" in the smb file should work, but it didn`t.

Please post the output of:
```
ls -la /media
```

Are Dados_2 and Dados_1 separate disks/partitions?

Edit:
In the future, to avoid confusion for yourself and for others, do not create multiple threads on the same problem.

---

### Post by Mongao on 2010-01-04
> **dmizer said:**
> Please post the output of:
```
ls -la /media
```

Are Dados_2 and Dados_1 separate disks/partitions?

Edit:
In the future, to avoid confusion for yourself and for others, do not create multiple threads on the same problem.

Thanks, here it is:

andre@andre-ubuntu:~$ ls -la /media
total 56
drwxr-xr-x  6 root  root   4096 2010-01-04 17:17 .
drwxr-xr-x 22 root  root   4096 2010-01-03 20:19 ..
lrwxrwxrwx  1 root  root      6 2010-01-02 12:46 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2010-01-02 12:46 cdrom0
drwx------  1 andre andre 20480 2010-01-03 21:49 Dados_1
drwx------  1 andre andre 20480 2010-01-04 14:11 Dados_2
drwxr-xr-x  2 root  root   4096 2010-01-03 16:39 samba
andre@andre-ubuntu:~$ 

Dados_1 and Dados_2 are actually two separate physical hard discs.

Thanks,
Mongao

---

### Post by dmizer on 2010-01-04
> **Mongao said:**
> Thanks, here it is:

andre@andre-ubuntu:~$ ls -la /media
total 56
drwxr-xr-x  6 root  root   4096 2010-01-04 17:17 .
drwxr-xr-x 22 root  root   4096 2010-01-03 20:19 ..
lrwxrwxrwx  1 root  root      6 2010-01-02 12:46 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2010-01-02 12:46 cdrom0
drwx------  1 andre andre 20480 2010-01-03 21:49 Dados_1
drwx------  1 andre andre 20480 2010-01-04 14:11 Dados_2
drwxr-xr-x  2 root  root   4096 2010-01-03 16:39 samba
andre@andre-ubuntu:~$ 

Dados_1 and Dados_2 are actually two separate physical hard discs.

Thanks,
Mongao

Are these disks internal or external? Also, are they formatted in NTFS?

Please post the contents of /etc/fstab

---

### Post by Mongao on 2010-01-04
> **dmizer said:**
> Are these disks internal or external? Also, are they formatted in NTFS?

Please post the contents of /etc/fstab

Thanks,

Dados_1 and Dados_2 are internal separate physical HD`s, NTFS formatted (I have dual boot). In Ubuntu, of course they appear as

/media/dados_1
/media/dados_2

All folders that I share are in these two discs.

In the original smb.conf template, there`s a part like this:

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = YOUR_USERNAME
    force group = YOUR_USERGROUP

Following Morbius advice, I deleted all this sector from  my smb files on both computers and things worked, now they see and access each other (in the other computer I also have a /media/Dados_1 HD with shared folders).

Of course things sound better now, but I would like to understand it a bit better so I wouldn`t be here eternally asking the same amateur questions forever.

I read that the "media" folder can only be accessed by the root user (?), but its subdirectories (e.g., my shared folders), could be accessed by regular users, once given the proper authorization.

So, for me this line (if not deleted...) should be something like:

[MyFiles]
    path = /media/Dados_1/
    path = /media/Dados_2/

and somewhere I would have to give the access rights to the other user, computer "andrea". Actually, I would like to understanbd each line under this "My Files" sector.

here are the contents of fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=0bc9d330-e774-4674-b216-8d6a4184ca65 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=4f9d310f-ff5b-4f77-9570-abf889ad32cb /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a5550a26-250b-4b65-8731-b12a0ed7e36c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I would like to know why, in both computers, the third option under the "sharing options" dialogue is greyed out, can`t be edited, and in one computer it`s checked and in the other it`s unchecked.

Unfortunately, Linux is far from people that don`t know things like "sudo chmod 0777 /media/samba", this is not easy for regular users.

Thanks,
Mongao

---

### Post by Mongao on 2010-01-04
> **Morbius1 said:**
> ](*,)](*,)](*,)

Good luck.

:confused:

Trust me, rest assured that one is not a moron for not knowing things like "fstab", "smb.conf" and whatever. 

Actually, considering it`s open source software, I don`t undrestand why no one hasn`t written yet a nice GUI that would guide amateur users to  properly configure the smb.conf file - actually it`s strange that samba doesn`t come installed by default.

But it`s OK, I don`t mind your irony, for me it`s important that you have helped.

Mongao

---

### Post by dmizer on 2010-01-04
> **Mongao said:**
> I would like to know why, in both computers, the third option under the "sharing options" dialogue is greyed out, can`t be edited, and in one computer it`s checked and in the other it`s unchecked.
Because your drives are NTFS, which do not support Unix permission levels. That, and you do not have dedicated mount points for your drives listed in /etc/fstab.

Here's a good howto: [http://dollopofdesi.blogspot.com/2009/07/loading-windows-partition-at-bootup-in.html](http://dollopofdesi.blogspot.com/2009/07/loading-windows-partition-at-bootup-in.html)

Fix this and most of your problems will be solved.

> **Mongao said:**
> :confused:

Trust me, rest assured that one is not a moron for not knowing things like "fstab", "smb.conf" and whatever. 

Actually, considering it`s open source software, I don`t undrestand why no one hasn`t written yet a nice GUI that would guide amateur users to  properly configure the smb.conf file - actually it`s strange that samba doesn`t come installed by default.

But it`s OK, I don`t mind your irony, for me it`s important that you have helped.

Mongao

The frustration is understandable. You're following the direction of at least three different threads all with different people leading you towards different targets. There is no frustration about not understanding fstab or smb.conf.

It's really important that once you start a thread asking for help that you try to follow one thread only. That way, everyone who visits your thread will see everything that you've done. If you follow multiple threads trying to solve problems, you're basically making everyone (including yourself) chase their tail.

---

### Post by Mongao on 2010-01-04
> **dmizer said:**
> Because your drives are NTFS, which do not support Unix permission levels. That, and you do not have dedicated mount points for your drives listed in /etc/fstab.

Here's a good howto: [http://dollopofdesi.blogspot.com/2009/07/loading-windows-partition-at-bootup-in.html](http://dollopofdesi.blogspot.com/2009/07/loading-windows-partition-at-bootup-in.html)

Fix this and most of your problems will be solved.



Thanks, will you believe if I tell you,  a week ago when I was running 9.04, the third box was available ?

OK, this is not so important, I `d just like to understand why it`s shaded out now and can`t be edited.

I have added these two lines to my fstab file:

/dev/sdb1 /media/Dados_1 ntfs-3g defaults,locale=en_US.utf8 0 0 
/dev/sdc1 /media/Dados_2 ntfs-3g defaults,locale=en_US.utf8 0 0 

Dados_1 mounted on start up (good, I don`t have to do this manually anymore everytiome I boot), but when I tried sharing my "geral_andre" folder, I was asked to add the line "usershare owner only = false" to the smb file (it didn`t appear before). And the third option is still greyed out.

and dados_2 didn`t mount at all: "only root can mount it". 

I wanna punch the root`s face out !...where is he ? :lolflag:

My problem: my media player file only sees one computer on the network, it doesn`t see the other. Do you have a clue ? maybe it has to do with the authorizations issue ?

Thanks,
Mongao

P.S. I have followed other threads to try to figure out the smb edition issue, but I have started only one thread.

---

### Post by Mongao on 2010-01-04
OK, I have changed the identification to the UUID method and both drives mount on start-up now - OK !

two problems persist:

1) My media player only sees one computer on the network, and even though it says that "username/password wrong" - they are not. Is it expecting a root login or so ?

2) the andre computer doesn`t see the printer hooked to the andrea computer

Thanks,
Mongao

---

### Post by Morbius1 on 2010-01-05
> Please, how do I "ungrey" (make changeable) the third option on the "sharing options" dialogue box ? > **dmizer said:**
> Because your drives are NTFS, which do not support Unix permission levels. That, and you do not have dedicated mount points for your drives listed in /etc/fstab.

Although the recommendation is sound the logic in recommending it is in error.
The third option will not be greyed out because it's an ntfs partition. Nautilus-share doesn't know or care that it's an NTFS partition. When you select to change permissions using nautilus-share on an NTFS partition it won't actually do anything because of the reasons dmizer gave but the option will not  be greyed out. I just reverified this  - *I must be the only one in this forum that uses nautilus-share.*

Sorry for the rant.

> 1) My media player only sees one computer on the network, and even though it says that "username/password wrong" - they are not. Is it expecting a root login or so ?We need to see your fstab and share definitions [COLOR=Blue]only on the computer where the media player says you have the wrong username and password please[/COLOR]. You can do that by using these commands:
[B]
cat /etc/fstab[/B]
**net usershare info**

---

### Post by Morbius1 on 2010-01-05
I just realized :oops: there is something missing from both your smb.conf that might explain the missing "guest option" . Neither one of them have this line in them:

```
**usershare allow guests = yes**
``` Add it somewhere in the[COLOR=Blue] [global][/COLOR] section of smb.conf on both machines. Then restart samba: **sudo service samba restart**

Sorry about that - I'm getting sloppy :oops:

Once that's done go back to nautilus and enable guest access. There might be one more addition necessary ( a force user = your_user_name in the global section ) to finally fix this thing depending on how you mounted your ntfs partitions.

[COLOR=Blue]EDIT: The more I think about this the more I think this was the key to your problem - at least since panel #16 .
When you were mounting those ntfs partitions through nautilus instead of fstab they would have by default allowed "others" to read / write, but without a "guest option" in nautilus-share there was no way for a guest to get access from the network. **A thousand appologies**.[/COLOR]

---

### Post by Mongao on 2010-01-05
> **Morbius1 said:**
> Although the recommendation is sound the logic in recommending it is in error.
The third option will not be greyed out because it's an ntfs partition. Nautilus-share doesn't know or care that it's an NTFS partition. When you select to change permissions using nautilus-share on an NTFS partition it won't actually do anything because of the reasons dmizer gave but the option will not  be greyed out. I just reverified this  - *I must be the only one in this forum that uses nautilus-share.*

Sorry for the rant.

We need to see your fstab and share definitions [COLOR=Blue]only on the computer where the media player says you have the wrong username and password please[/COLOR]. You can do that by using these commands:
[B]
cat /etc/fstab[/B]
**net usershare info**

Thanks Morbius, here are the results of the commands on the andre computer, the one that media player sees but says "user/pass wrong":

andre@andre-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=0bc9d330-e774-4674-b216-8d6a4184ca65 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=4f9d310f-ff5b-4f77-9570-abf889ad32cb /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a5550a26-250b-4b65-8731-b12a0ed7e36c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


UUID="F638F21038F1CF9B" /media/Dados_1 ntfs-3g defaults,locale=en_US.utf8 0 0 
UUID="E6048E5E048E321B" /media/Dados_2 ntfs-3g defaults,locale=en_US.utf8 0 0 

andre@andre-ubuntu:~$ net usershare info
[para_andrea]
path=/media/Dados_2/Para_Andrea
comment=
usershare_acl=Everyone:F,
guest_ok=n

[geral_andre]
path=/media/Dados_1/Geral_Andre
comment=
usershare_acl=Everyone:F,
guest_ok=n

[videos]
path=/media/Dados_1/videos
comment=
usershare_acl=Everyone:F,
guest_ok=n

--------------------------------

Thanks,

Mongao

---

### Post by Mongao on 2010-01-05
> **Morbius1 said:**
> I just realized :oops: there is something missing from both your smb.conf that might explain the missing "guest option" . Neither one of them have this line in them:

```
**usershare allow guests = yes**
``` Add it somewhere in the[COLOR=Blue] [global][/COLOR] section of smb.conf on both machines. Then restart samba: **sudo service samba restart**

Sorry about that - I'm getting sloppy :oops:

Once that's done go back to nautilus and enable guest access. There might be one more addition necessary ( a force user = your_user_name in the global section ) to finally fix this thing depending on how you mounted your ntfs partitions.

[COLOR=Blue]EDIT: The more I think about this the more I think this was the key to your problem - at least since panel #16 .
When you were mounting those ntfs partitions through nautilus instead of fstab they would have by default allowed "others" to read / write, but without a "guest option" in nautilus-share there was no way for a guest to get access from the network. **A thousand appologies**.[/COLOR]

Thanks Morbius, the third option is now available and, most important, now I understand a bit more. I didn`t have to do this:

"( a force user = your_user_name in the global section ) to finally fix this thing depending on how you mounted your ntfs partitions."

May I anyway ? Doing so, I would be forcing myself as an user....I don`t understand well.....What is the general idea behind this line ?

You mean that the "proper" way to mount partitions is always through fstab, never by Nautilus, right ?

Thanks again,

Mongao

---

### Post by Morbius1 on 2010-01-05
I do not believe you need the force user at this point. Make sure you can read and write to a remote file and we'll find out.

> You mean that the "proper" way to mount partitions is always through fstab, never by Nautilus, right ?Actually, if I wasn't so stupid and realized you didn't have the 
[B][B]usershare allow guests = yes 
[/B][/B]line in your fstab you could have pulled this off by mounting through Nautilus. But in my opinion it's always better to automount partitions at boot. If for no other reason than you can always go back to fstab and tweak permissions ( on windows filesystems ) and other settings.

---

### Post by Mongao on 2010-01-06
Thanks Morbius,

Well, things are partially working (printer/media player not working yet), but it`s OK for a while, I`ll buy a NAS soon and then I`ll have to rearrange everything, so it`s not of much advantage to go ahead now, the important (and was urgent) is that now both computers can access each other, I needed that desperately so it`s OK so far.

Thank you very much,

Mongao

---

