---
title: "Setting up LAN"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by elkade on 2010-01-10
I would like to know if there is a fairly easy "How To" for setting up my home network.

I have 2 XP SP3 computers and 2 Linux with ver. 9.10.

The XP boxes can see each other and share files and folders.

I can see from an XP box one of the Ubuntu machines, but can't access any of the files or folders.

I get the following when I try:  \\Lstorage\music is not accessible. You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions.

The network path was not found.

Any and all help would be appreciated

Larry

---

### Post by Lars Noodén on 2010-01-11
Tell more about your set up.  I presume you are using Samba on the Linux box to serve up files, right?

---

### Post by Iowan on 2010-01-11
Lars Noodén: You need to feed your fish ;)

Have you set up shares on the Ubuntu machines? 
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a good How-To for troubleshooting the Windows shares.

---

### Post by Morbius1 on 2010-01-11
> I get the following when I try: \\Lstorage\music is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.
This doesn't sound like a samba problem. It sounds like a permissions problem. If I'm reading this correctly, Lstorage is an ubuntu machine, correct?

Please post the output of the following commands from Lstorage:

Open **Terminal**
Type **net usershare info**
Type [B]testparm -s
[/B]Type[B] smbtree
[/B]

---

### Post by Iowan on 2010-01-11
Another thought comes to mind (happens so seldom anymore...)
Have you set up usernames/passwords on Ubuntu and Samba for the Windows user (or is Samba set up with security=share)?

---

### Post by lisati on 2010-01-11
> **Iowan said:**
> Lars Noodén: You need to feed your fish ;)

Have you set up shares on the Ubuntu machines? 
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is a good How-To for troubleshooting the Windows shares.

Here's another "how to" which I've used on my laptop (dual boot Vista & 9.04), my main desktop (9.04 server) & my backup desktop (a cli install of 6.06), should work with 9.10 as well:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by elkade on 2010-01-23
> **Morbius1 said:**
> This doesn't sound like a samba problem. It sounds like a permissions problem. If I'm reading this correctly, Lstorage is an ubuntu machine, correct?

Please post the output of the following commands from Lstorage:

Open **Terminal**
Type **net usershare info**
Type [B]testparm -s
[/B]Type[B] smbtree
[/B]

As requested:

larry@lstorage:~$ net usershare info
info_fn: file /var/lib/samba/usershares/software & apps is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/kids movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/vuze movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/vuze tv is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/ tv is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/music is not a well formed usershare file.
info_fn: Error was Path is not a directory.
larry@lstorage:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Media]"
Processing section "[FreeAgent Drive]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = HIVE
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

[Media]
	comment = Movies, TV Shows
	path = /media/Media
	guest ok = Yes

[FreeAgent Drive]
	comment = Movies, TV Shows, Backups
	path = /media/FreeAgent Drive
	guest ok = Yes
larry@lstorage:~$ smbtree
The program 'smbtree' is currently not installed.  You can install it by typing:
sudo apt-get install smbclient
smbtree: command not found
larry@lstorage:~$ sudo apt-get install smbclient
[sudo] password for larry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libproc-simple-perl libgnome2-wnck-perl libsort-naturally-perl libnet-ssleay-perl libxml-namespacesupport-perl
  libhttp-response-encoding-perl libgoocanvas-common libextutils-pkgconfig-perl libfile-copy-recursive-perl
  libxml-sax-expat-perl libfile-basedir-perl libgoo-canvas-perl libfile-mimeinfo-perl libgtkimageview0 libfile-which-perl
  libxml-sax-perl libhttp-server-simple-perl libfile-desktopentry-perl libwww-mechanize-perl libxml-simple-perl
  libx11-protocol-perl libextutils-depends-perl libgnome2-gconf-perl libio-socket-ssl-perl libgtk2-imageview-perl perlmagick
  libfile-homedir-perl libgoocanvas3 libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
Suggested packages:
  smbfs
The following NEW packages will be installed:
  smbclient
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/11.4MB of archives.
After this operation, 33.8MB of additional disk space will be used.
Selecting previously deselected package smbclient.
(Reading database ... 237065 files and directories currently installed.)
Unpacking smbclient (from .../smbclient_2%3a3.4.0-3ubuntu5.3_i386.deb) ...
Processing triggers for man-db ...
Setting up smbclient (2:3.4.0-3ubuntu5.3) ...
larry@lstorage:~$ smbtree
Enter larry's password: 
HIVE
	\\PVR            		TV PC
cli_start_connection: failed to connect to PVR<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\LSTORAGE       		lstorage server (Samba, Ubuntu)
		\\LSTORAGE\IPC$           	IPC Service (lstorage server (Samba, Ubuntu))
		\\LSTORAGE\FreeAgent Drive	Movies, TV Shows, Backups
		\\LSTORAGE\Media          	Movies, TV Shows
		\\LSTORAGE\print$         	Printer Drivers
	\\CUBE2          		winxp
cli_start_connection: failed to connect to CUBE2<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
larry@lstorage:~$ 

Hope this is what you were looking for

Larry

---

### Post by Morbius1 on 2010-01-24
> The program 'smbtree' is currently not installed.  You can install it by typing:
sudo apt-get install smbclientThat's kind of scary. smbclinet should have been in your base install and makes me wonder what else is missing.
> net usershare info
info_fn: file /var/lib/samba/usershares/music is not a well formed usershare file.
info_fn: Error was Path is not a directoryAll of these errors indicate that all of your Nauilus-share shares are messed up. Since your original post talked about  \\Lstorage\music, let's see if we can fix that one to start.

Post the output of the following command:

Open **Terminal**
Type [B]cat  /var/lib/samba/usershares/music


[/B]

---

### Post by elkade on 2010-01-24
> **Morbius1 said:**
> That's kind of scary. smbclinet should have been in your base install and makes me wonder what else is missing.
All of these errors indicate that all of your Nauilus-share shares are messed up. Since your original post talked about  \\Lstorage\music, let's see if we can fix that one to start.

Post the output of the following command:

Open **Terminal**
Type [B]cat  /var/lib/samba/usershares/music


[/B]

larry@lstorage:~$ cat /var/lib/samba/usershares/music
#VERSION 2
path=/media/FreeAgent Drive/Music
comment=
usershare_acl=S-1-1-0:F
guest_ok=y
larry@lstorage:~$

---

### Post by elkade on 2010-01-24
> **Morbius1 said:**
> That's kind of scary. smbclinet should have been in your base install and makes me wonder what else is missing.
All of these errors indicate that all of your Nauilus-share shares are messed up. Since your original post talked about  \\Lstorage\music, let's see if we can fix that one to start.

Post the output of the following command:

Open **Terminal**
Type [B]cat  /var/lib/samba/usershares/music


[/B]

I ran the smbclient, is this what I should have seen??

larry@lstorage:~$ sudo apt-get install smbclient
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbclient is already the newest version.
The following packages were automatically installed and are no longer required:
  libproc-simple-perl libgnome2-wnck-perl libsort-naturally-perl
  libnet-ssleay-perl libxml-namespacesupport-perl
  libhttp-response-encoding-perl libgoocanvas-common
  libextutils-pkgconfig-perl libfile-copy-recursive-perl libxml-sax-expat-perl
  libfile-basedir-perl libgoo-canvas-perl libfile-mimeinfo-perl
  libgtkimageview0 libfile-which-perl libxml-sax-perl
  libhttp-server-simple-perl libfile-desktopentry-perl libwww-mechanize-perl
  libxml-simple-perl libx11-protocol-perl libextutils-depends-perl
  libgnome2-gconf-perl libio-socket-ssl-perl libgtk2-imageview-perl perlmagick
  libfile-homedir-perl libgoocanvas3 libnet-libidn-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
larry@lstorage:~$

---

### Post by Morbius1 on 2010-01-24
Open **Terminal**
Type **net usershare delete music**
Type **gksu gedit /etc/samba/smb.conf**

 Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = larry
```Save the file, exit gedit, and back in the Terminal type:
[B]sudo service samba restart

[/B]Wait a few minutes, then from one of the other machines on your network see if you can access the** FreeAgent Drive **share

---

