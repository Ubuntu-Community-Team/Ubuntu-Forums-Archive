---
title: "Two part SAMBA Q"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by OldManRiver on 2011-08-18
All,

I was up on IRC on the Ubuntu channel #ubuntu and was having 2 problems.
[LIST=1]
[*]I can not get SAMBA to work right
[*]I can not get WebMin to install
[/LIST]
I use WebMin to control remote boxes, mostly not Ubuntu, install/config SAMBA.  I also use the WebMin install as it does SAMBA seamlessly, first time, everytime, always works and works right; where GADMIN-Samba, and SWAT are total jokes and never make it work or work right.  SWAT doesn't even have a "restart" option and no way to view the logs.

So I get to the IRC channel, start asking about my WebMin install and get this message, "No longer supported on Ubuntu".  Anyway my WebMin install is not calling the part of the install config that gets the pop-up to configure MySQL and since no DB gets generated, which is where all login info goes, I can not login; even though I get the login screen and all the PHP code wants to run.  Gotta figure out how to break out the SQL part and be able to run it seperate to get WebMin working.  Even using apt-get purge webmin, is not clearing something out so not getting it to run right.

The real problem though is the SAMBA, because it has to run, because all the network machines share the printer that is installed on this box.  That said here is my current smb.conf file:
```
[global]
#-------[ Net Hood Settings ]
        workgroup = DAVISOFT
        netbios name = tc-noc-server
        server string = %h Samba Server
        socket options = TCP_NODELAY SO_SNDBUF=8192 SO_RCVBUF=8192 IPTOS_LOWDELAY
	wins support = yes
	hostname lookups = yes
	name resolve order = wins lmhosts host bcast

#-------[ Log Level ]
        log level = 2
	log file = /var/log/samba/log.%m
	max log size = 1000
	syslog = 0
	null passwords = no

#-------[ Server Role Settings ]
        guest ok = Yes
        security = user
#        password server = YOUR PDC
        encrypt passwords = true
	guest account = nobody
	invalid users = root

#-------[NT ACL Compatability]
        nt acl support = true
        create mode = 0644
        directory mode = 0755

#-------[ Printserver information ]
	load printers = yes
	printing = cups
        printcap name = cups
        cups options = "raw"
        disable spoolss = no
        show add printer wizard = yes
        security mask = 0777

#-------[ All Printer information ]
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
	browseable = yes
	read only = no
	guest ok = yes
;	write list = root, @ntadmin

[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = Yes
	browseable = yes
	public = yes
	writable = no
	guest ok = yes
	locking = no
	strict locking = no
        create mode = 0700

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	printable = yes
	guest ok = yes
	use client driver = yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command =
	lprm command =

#-------[ Shares ]
# A sample share for sharing your CD-ROM with others.
[cdrom]
	comment = Samba server's CD-ROM
	writable = no
	locking = no
	path = /cdrom
	public = yes
	preexec = /bin/mount /cdrom
	postexec = /bin/umount /cdrom

[homes]
	comment = Home Directories
	path = /home
	read only = no
	available = yes
	browseable = yes
	writable = yes
	guest ok = no
	public = no
	printable = yes
	locking = no
	strict locking = no

[Data]
	comment = Data Share
	path = /data
	read only = no
	available = yes
	browseable = yes
	writable = yes
	guest ok = no
	public = yes
	printable = yes
	locking = no
	strict locking = no

[Backups]
	comment = Backup Directory
	path = /backups
	read only = no
	available = yes
	browseable = yes
	writable = no
	guest ok = no
	public = no
	printable = yes
	locking = no
	strict locking = no

[Shared Files]
	comment = Shared Files Directory
	path = /home/files
	read only = no
	available = yes
	browseable = yes
	writable = yes
	guest ok = yes
	public = yes
	printable = yes
	locking = no
	strict locking = no

[MyFiles]
	comment = MyFiles Directory
	path = /home/myuser/myfiles
	read only = no
	available = yes
	browseable = yes
	writable = yes
	guest ok = no
	public = no
	printable = yes
	locking = no
	strict locking = no

[L_Scripts]
	comment = Shared Linux Scripts Directory
	path = /home/Linux Scripts
	read only = no
	available = yes
	browseable = yes
	writable = yes
	guest ok = yes
	public = yes
	printable = yes
	locking = no
	strict locking = no

;[pdf-documents]
;	comment = Converted PDF Documents
;	path = /home/pdf-documents
;	available = yes
;	browseable = yes
;	writeable = yes
;	guest ok = yes
;	locking = no
;	strict locking = no

;[install_cds]
;	comment = CDs on Server
;	path = smbclient -I 192.168.7.105\Install_CDs
;	#path = /var/shared-files/install_cds
;	browseable = yes
;	writable = yes
;	valid users = administrator nyle root
;	public = no
;	printable = no
;	inherit permissions = Yes
;	inherit acls = yes
;	create mask = 0644
;	guest ok = no
;	security mask = 0777

;[bids_plans]
;	comment = Bid Plans
;	path = smbclient -I 192.168.7.105\bid_plans
;	#path = /var/shared-files/bids_plans
;	browseable = yes
;	writable = yes
;	valid users = administrator nyle root
;	public = no
;	printable = no
;	inherit permissions = Yes
;	inherit acls = yes
;	create mask = 0644
;	guest ok = no
;	security mask = 0777

;[print_howto]
;	comment = Printing Setup Howto Files
;	path = smbclient -I 192.168.7.105\print_howto
;	#path = /var/shared-files/print_howto
;	browseable = yes
;	writable = yes
;	valid users = administrator nyle root
;	public = no
;	printable = no
;	inherit permissions = Yes
;	inherit acls = yes
;	create mask = 0644
;	guest ok = no
;	security mask = 0777

;[school]
;	comment = Folder for North Lake College Unix Classes
;	path = smbclient -I 192.168.7.105\school
;	#path = /var/shared-files/school
;	browseable = yes
;	writable = yes
;	valid users = administrator nyle root
;	public = no
;	printable = no
;	inherit permissions = Yes
;	inherit acls = yes
;	create mask = 0644
;	guest ok = no
;	security mask = 0777

;[linux_howto]
;	comment = Linux Howto
;	path = smbclient -I 192.168.7.105\linux_howto
;	#path = /usr/shared_files/linux_howto

[wireless_LF]
;	comment = Local Files on Laptop
;	path = smbclient -I 192.168.7.105\linux_howto
;	#path = /usr/shared_files/linux_howto

;[wireless_DB]
;	comment =  Databases on Laptop
;	path = smbclient -I 192.168.7.105\linux_howto
;	#path = /usr/shared_files/linux_howto

;[wireless_ZP]
;	comment =  Z&D on Laptop
;	path = smbclient -I 192.168.7.105\linux_howto
;	#path = /usr/shared_files/linux_howto


```
I had this working before, thought I backed it up, had to re-format the box, with fresh 10.04 install and somehow lost it.

I was not using the IP connect with smbclient, since all machines connect via dhcp, but this was the only example I could find, so included those 3 file links to the laptop, and the ones to the other main file server, but got to work those off.

Some of the errors I'm getting are:
```
tail -n 40 /var/log/samba/log.smbd
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[print$]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[printers]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[pdf-printer]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[cdrom]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[homes]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[Data]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[Backups]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[Shared Files]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[MyFiles]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[L_Scripts]"
[2011/08/18 09:48:25,  2] param/loadparm.c:7743(do_section)
  Processing section "[wireless_LF]"
[2011/08/18 09:48:25,  0] param/loadparm.c:6767(service_ok)
  WARNING: No path in service wireless_LF - making it unavailable!
[2011/08/18 09:48:25,  1] param/loadparm.c:6774(service_ok)
  NOTE: Service wireless_LF is flagged unavailable.
[2011/08/18 09:48:25,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/08/18 09:48:25,  2] printing/print_cups.c:545(cups_async_callback)
  cups_async_callback: failed to read a new printer list
[2011/08/18 09:48:25,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/08/18 09:48:25,  2] printing/print_cups.c:545(cups_async_callback)
  cups_async_callback: failed to read a new printer list
[2011/08/18 09:48:25,  2] lib/interface.c:340(add_interface)
  added interface eth0 ip=192.168.3.2 bcast=192.168.3.255 netmask=255.255.255.0
[2011/08/18 09:48:26,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2011/08/18 09:48:31,  2] smbd/server.c:676(smbd_parent_loop)
  waiting for connections

```
Looks like to me that something in the CUPS section is what is blowing it all up.

Anyway if any of you see what my problem is, I will appreciate the help.

Course if we can figure out the WebMin install, then I do not have to hand edit smb.conf as WebMin does it perfectly.

Thanks!

OMR

---

### Post by OldManRiver on 2011-08-27
All,

OK, been working off the problems in my smb.conf file one at a time now down to just one, the smbclient share "wls_LF" on the windows box.

Here is my current config:
```
[global]
	comment = Global SAMBA Settings
	workgroup = DAVISOFT
;	log file = /var/log/samba/smb.log
	log file = /var/log/samba/log.m%
	map to guest = bad user
	public = yes
	dns proxy = no
	name resolve order = lmhosts host wins bcast
	syslog = 0

#-------[ All Printer information ]
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
	browseable = yes
	read only = no
	guest ok = yes
	load printers = yes
	printcap name = /etc/printcap
	printing = cups
	printcap name = cups

[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = Yes
	browseable = yes
	read only = yes
	public = yes
	writable = no
	guest ok = no
	locking = no
	strict locking = no
        create mask = 0700

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	printable = yes
	guest ok = yes
	use client driver = yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
;	lpq command =
;	lprm command =

#-------[ Shares ]
# A sample share for sharing your CD-ROM with others.
[cdrom]
	comment = Samba server's CD-ROM
	read only = yes
	guest ok = yes
	locking = no
	path = /cdrom
	public = yes
;	/dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
	preexec = /bin/mount /cdrom
	postexec = /bin/umount /cdrom

[data]
	comment = Shared Data Files
	path = /data
	browseable = yes
	writable = yes
	public = yes
	locking = no
	strict locking = no
	create mask = 0770
	directory mask = 0775

[backups]
	comment = Backup Directory
	path = /backups
	browseable = yes
	writable = no
	public = no
	guest ok = no
	locking = no
	strict locking = no
	create mask = 0770
	directory mask = 0775

[home]
	comment = Home Directories
	path = /home
	browseable = yes
	writable = yes
	public = no
	guest ok = yes
	locking = no
	strict locking = no
	create mask = 0770
	directory mask = 0775

[L_Scripts]
	comment = Shared Linux Scripts Directory
	path = /home/Linux Scripts
	browseable = yes
	writable = yes
	public = yes
	guest ok = yes
	locking = no
	strict locking = no
	create mask = 0770
	directory mask = 0775

[s_files]
	comment = Shared Files Directory
	path = /home/files
	browseable = yes
	writable = yes
	public = yes
	guest ok = yes
	locking = no
	strict locking = no
	create mask = 0770
	directory mask = 0775

[MyFiles]
	comment = MyFiles Directory
	path = /home/ndavis/myfiles
	browseable = yes
	writable = yes
	public = no
	guest ok = no
	locking = no
	strict locking = no
	create mask = 0770
	directory mask = 0775

[wls_LF]
	comment = Local Files on Laptop
	path = smbclient "/wireless_LT/Local Files" -W domain -U myuser -P mypass
	browseable = yes
	writable = yes
	public = yes
	guest ok = yes
	locking = no
	strict locking = no
;	create mask = 0770
;	directory mask = 0775

```
Noticing that the smbclient is not addressing the login at the remote box but rather looking back to my current server for the login.  Not sure why but know it is in the correct formatting and syntax of this line.

So not much left to get past this, if you have done this and have the correct smbclient cmd string please pass it along.

Oh one further question:

How does one get the shares to link, mount and yet not be displayed on the Destop?  I hate things written to my DT, unless I specially and manually add them there.

Thanks!

OMR

---

### Post by OldManRiver on 2011-09-28
All,

Still do not have SAMBA working!

Can I get some help?

OMR

---

### Post by OldManRiver on 2011-10-19
All,

The servers on the LAN are seeing each other, but none of the visitors on laptops can see any of the server (Linux) shares.

Think I found out one of my major problems here.  Users on laptops needing to access shares on the Linux servers are connecting to the LAN via a LinkSys WRT54GT, which is assigning new IP to laptops and therefore not seen as part of the primary LAN network.

I need to set a passthru, for these to be seen in the primary LAN.

Anyone done that before?

Thanks!

OMR

---

### Post by OldManRiver on 2012-04-02
All,

Got my WebMin working so in control of the SAMBA now.

Marking this solved!

Cheers!

OMR

---

