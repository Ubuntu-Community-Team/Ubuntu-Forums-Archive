---
title: "Trying to print with Ubuntu on Window XP network printer"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by jukingeo on 2009-09-17
Hello all,

I tried to look up some information in regards to my situation in setting up a Windows printer to print on my computer and I can't get any results.

Here is my scenario.  I have two machines on a network, one is mine which is a dual boot box that I normally run Ubuntu Studio Hardy (8.04) on.  The other machine is my wife's which has Windows XP on it. 

The printer I have is an HP Photosmart C5580.  Her computer also has Norton Internet Security on it (version 16.2.7.11)

On her end I have set up the printer for sharing and I have set up her Nortion to allow communication to my machine (Or at least I think so).

I have Samba on my machine and when I go to the printer set up I go to the "Device URI" setting and I can navigate to the location of the printer on my wife's machine and select it.  I also set "print  via Samba". However, if I try to verify the connection or attempt to print a test page, nothing happens.

EDIT:  Sorry with "Verify" I do get an error message:

Inaccessable:  The print share is not accessible.

So I decided to run a test for sharing on my wife's machine.  I first selected my temporary downloads folder in Ubuntu and I set it up for sharing.  I went to my wife's machine and accessed the network.  Low and behold my shared folder IS showing up on her machine.  So it would seem that her machine is talking to my Linux box, but I can't get to her printer.

Incidentally I do have a "shared folder" on her Windows machine.  I would like to know where to look for it in Ubuntu.  I can't seem to find it.  I would like to see if I can access it from my Ubuntu machine.

Edit:  I think I have found where to get into the network.  I click on a button on the left drop down for PLACES ====> COMPUTER.  I think click on Windows Network and then MSHome.   A small window comes up for about 1 minute or so saying "Opening MSHOME".  After which an error message comes up saying "Unable to Mount Location: Failed to Retrieve Share List From Server".   I also found a way to turn off the Nortion firewall and computer protection OFF for these tests. 

Thus it appears my wife's Windows XP machine CAN see my shared files on Ubuntu, but I can't get into her machine.

There are a few more settings in regards to Network communication, however, I don't know what Network communication protocols Ubuntu uses.

Anyone have any idea what is going on and how I can fix the problem?    

Thank You,

Geo

---

### Post by dustingold09 on 2009-09-17
You have got Ubuntu Linux server to share it's printer with Windows XP.After installing samba  and getting it to a state where the server PC appeared in the workgroup . 
Make sure workgroup has same name on all computers and  Ubuntu knows about the printer. 


Steps to Share Printer On Windows :
------------------------------------------

1. Make sure the Windows computer that you will share the printer from has a printer installed and is functioning properly.

2.Now, share the printer on your XP Computer by clicking on Start \ Settings \ Printers and Faxes.

After that  right click on the printer and select Properties & click on the Sharing tab.


Steps to setup printer in ubuntu :
---------------------------------------

1.  Log on to your Ubuntu computer and click on System \ Administration \ Printing
     from the menu on the Panel.

2.  In the Printers window, double click on New Printer.

3. Then in Step 1 of 3, select Network Printer for Printer Type and select 
    Windows Printer SMB (circled).  If an Authentication windows pop-up, click
    Cancel until it's disappears.




[Laser Printers]("http://www.brother.ca")

---

### Post by jukingeo on 2009-09-17
> **dustingold09 said:**
> You have got Ubuntu Linux server to share it's printer with Windows XP.After installing samba  and getting it to a state where the server PC appeared in the workgroup . 
Make sure workgroup has same name on all computers and  Ubuntu knows about the printer. 

The printer is on the WINDOWS computer, I am trying to get the Ubuntu machine to talk to it.  Now I CAN see the printer in the setup box, but the problem is I can't communicate with it.

> 
Steps to Share Printer On Windows :
------------------------------------------

1. Make sure the Windows computer that you will share the printer from has a printer installed and is functioning properly.

2.Now, share the printer on your XP Computer by clicking on Start \ Settings \ Printers and Faxes.

After that  right click on the printer and select Properties & click on the Sharing tab.

That has already been done.

> 

Steps to setup printer in ubuntu :
---------------------------------------

1.  Log on to your Ubuntu computer and click on System \ Administration \ Printing
     from the menu on the Panel.

2.  In the Printers window, double click on New Printer.

3. Then in Step 1 of 3, select Network Printer for Printer Type and select 
    Windows Printer SMB (circled).  If an Authentication windows pop-up, click
    Cancel until it's disappears.




[Laser Printers]("http://www.brother.ca")

I have done this as well.  In the boxes on the right side when it comes to making a selection, you can browse for the printer.  I can see my wife's computer and browse to the printer and select it.  However, clicking verify will yield an error message.  If I don't click verify and just select the printer, if I try to print a test page, nothing happens.  If I just print something, nothing happens.

As I mentioned above, I tried to do some further testing in terms of file sharing to see if the machines can talk to each other and my discovery was that my wife's machine CAN see and access shared files on my Ubuntu machine.  However, I cannot view the shared folders on my wife's machine to mine.  Thus if I can't see her shared files on my Ubuntu machine, then it is safe to say that the printer is likely blocked.

I turned my attention to her Norton Internet Security program, but even after shutting it down (or at least shutting off the firewall), I STILL cannot communicate with her machine.

So judging by your post, I DID do everything correctly in setting up the printer via Samba, but for some reason my machine cannot communicate with the Windows machine, BUT the Windows machine CAN communicate with Ubuntu.

Now before you (or anyone else) mention(s) it...moving the printer to my machine isn't an option.

Thanx,

Geo

---

### Post by Cuba71 on 2009-09-17
> 
1. Log on to your Ubuntu computer and click on System \ Administration \ Printing
from the menu on the Panel.

2. In the Printers window, double click on New Printer.

3. Then in Step 1 of 3, select Network Printer for Printer Type and select
Windows Printer SMB (circled). If an Authentication windows pop-up, click
Cancel until it's disappears.

Verify that the URI: looks like "smb://home_network_name/windows_pc_name/printer_name"

---

### Post by jukingeo on 2009-09-17
> **Cuba71 said:**
> Verify that the URI: looks like "smb://home_network_name/windows_pc_name/printer_name"

Yes, I can see that on the URI line. That is what I don't get, it seems that Ubuntu CAN see the printer, but it can't do anything about it.  Hitting the verify button produces that error message I mentioned earlier.

Likewise, I cannot view the shared files on the Windows computer either. 

However, if I go to the Windows computer I CAN see AND access the files on the Ubuntu computer.

Putting it in simpler terms, it seems the communication is one way.  That is why I labeled Norton as the culprit, but even turning the firewall protection (and other potential blockers) off on Norton, I still have the same problem.

I even tested the connections last night by assigning a NEW folder to be shared on both the Windows and Ubuntu machine.  I CAN see the newly shared Ubuntu folder on the Windows machine, but I can't view the folder I created in Windows on the Ubuntu machine.  Communication is clearly one way.

Thus if there is something in the Windows machine that is blocking me from viewing files there, it would make sense that is why I can't see the printer either.

Any other suggestions?

Thanx,
Geo

---

### Post by Cuba71 on 2009-09-17
One more thing to check:

Go to one of your shared folders in Windows and right click on it
Click on Properties > Sharing > View Windows Firewall settings
Make sure that File and Printer Sharing is checked.

This is what opens the Windows Firewall

I hope this does it

---

### Post by Victorino Tom on 2009-09-18
Hi,
    The firewall on the router shouldn't be causing the problem. Firewalls protect the systems on your internal network from the outside world. 
    
     The firewall sits between the inbound data and the NAT part, in theory. The packets are examined for bad stuff or corruption, or attempts to access unauthorized ports, and rejected before they arrive.

 [Discount printer copier]("http://www.tonerpirate.com")

---

### Post by pricetech on 2009-09-18
Just a wild and crazy idea.  Is there any chance the printer has an ethernet port ???

If not, it could be a "windows printer".  I haven't seen one in a while, but then I try to stay out of wally world.  I've had my share of issues in the past with cheap printers being windows only and simply not working with Linux.

---

### Post by Cuba71 on 2009-09-18
> **Victorino Tom said:**
> Hi,
    The firewall on the router shouldn't be causing the problem. Firewalls protect the systems on your internal network from the outside world. 
    
  

Well, I meant the Windows firewall in your XP computer

---

### Post by petermg on 2009-09-18
Why not just do this:

From your Ubuntu PC, go to SYSTEM > ADMINISTRATION > PRINTERS.

Right-click on your printer and select SHARED.



Then from your Windows PC, START > CONTROL PANEL > PRINTERS AND FAXES > then click on ADD A PRINTER, then NEXT.

Select "A Network printer, or a printer attached to another computer".  Then click NEXT>
then select "Connect to a printer on the Internet or on a home or office network:" then type the URL of the shared printer.  It will be this:
```
http://yourcomputersIPaddressorwinshostname:631/printers/yourprinters-exact-name
```

For example this one was mine:

```
http://kids-ubuntu:631/printers/Photosmart-d7100-series
```

if your Ubuntu isn't setup to broadcast it's hostname you can just put the ip address of it instead.

Make sure you put the ":631" at the end since that's the port CUPS shares the printer on.  This was the easiest way for me.  Samba kept giving me authorization and permission headaches.  I don't want to have to authenticate every time I want to print or every time my computer reboots before I try to print.

Once you type the correct URL of your printer, just click NEXT and windows will eventually ask you to install the drivers for it.  VIOLA! SUCCESS!!!:guitar:

---

### Post by oldgeekster on 2009-09-18
Peter I think you have it backwards - his printer is connected to his wife's Windows XP machine and he needs it to remain there.

~~~

Here is a "WAG" that you might check "just in case":

Windows XP has a default Workgroup name of "WORKGROUP"..  So does SAMBA...

If somewhere along the line you changed the name of your windows Workgroup to something other than "WORKGROUP", you will probably need to either edit the file /etc/samba/smb.conf  (see line that says workgroup = WORKGROUP) to match that name - or change Windows XP back to the default.

Hope this helps,
-=dave=-

---

### Post by falconindy on 2009-09-18
I'd bet that he can connect by IP, but not by name. OP, if you pop open a terminal and do this...
```
smbclient -L 192.168.1.1
```
and obviously replace the IP there with the IP of the windows machine. You should get a prompt to enter a password. Hit enter (anonymous logon) and you should get **something** to return. Anything but an 'access denied', 'host not found' or anything else to that effect would be golden.

If that **is** the case, there's a quick fix so that you can identify the windows machine by name. Open up /etc/samba/smb.conf with your favorite text editor (with gksu or sudo, of course), and find the line that starts with "name resolve order". You'll want the parameters after that in the following order:
```
   name resolve order = lmhosts wins bcast host
```
And that should hopefully sort things out.

---

### Post by jukingeo on 2009-09-19
Hello All

> **Cuba71 said:**
> One more thing to check:

Go to one of your shared folders in Windows and right click on it
Click on Properties > Sharing > View Windows Firewall settings
Make sure that File and Printer Sharing is checked.

This is what opens the Windows Firewall

I hope this does it

The Windows Firewall is off and generally when I set up on a Windows network, the "Shared Files" folder will be seen across the network.  I can't even see that folder. However, I DO have a Linksys Firewall router.  That router is usually meant for Windows networks...could it be interfering with Ubuntu?

> **pricetech said:**
> Just a wild and crazy idea.  Is there any chance the printer has an ethernet port ???

If not, it could be a "windows printer".  I haven't seen one in a while, but then I try to stay out of wally world.  I've had my share of issues in the past with cheap printers being windows only and simply not working with Linux.

I see where you are going...Yeah, I DID check it that out and it is only a USB printer.  I can see the printer in the Ubuntu printer setup box, but I can't verify the connection.  But because I also can't see the shared files on my wife's machine I am thinking there is something else going on here.

> **oldgeekster said:**
> Peter I think you have it backwards - his printer is connected to his wife's Windows XP machine and he needs it to remain there.

Yes, this is correct.  The printer isn't physically connected to my Ubuntu machine, it is connected to my wife's Windows machine.  I am trying to 'network connect' to that printer.

> 
~~~

Here is a "WAG" that you might check "just in case":

Windows XP has a default Workgroup name of "WORKGROUP"

Yes, it's MSHOME which is the default.

> 
..  So does SAMBA...

If somewhere along the line you changed the name of your windows Workgroup to something other than "WORKGROUP", you will probably need to either edit the file /etc/samba/smb.conf  (see line that says workgroup = WORKGROUP) to match that name - or change Windows XP back to the default.

Hope this helps,
-=dave=-

This is my smb.conf file:

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


Under Global Settings it says:

workgroup = WORKGROUP

Should I change this to MSHOME?

Anyway I have the whole file up.  Let me know if something is amiss 

Thanx,

Geo

---

### Post by jnorene on 2009-09-19
I am a newcomer to Linux, but I have a bit of experience in the Windows world.  I suspect your problem lies with Norton's.  I have had many issues sharing printers and files with Norton installed.  I am currently running 9.04 64bit on a test machine and am able to print to two other printers attached to Windows machines with no problems, and I am able to access Windows shares with no problem.  My problem is I cannot get to the Linux shares on my Ubuntu machine - login failure.
 
If you uninstall Norton's your problems will likely clear, but that may not be the most desirable solution.

---

### Post by jukingeo on 2009-09-19
> **jnorene said:**
> I am a newcomer to Linux, but I have a bit of experience in the Windows world.  I suspect your problem lies with Norton's.  I have had many issues sharing printers and files with Norton installed.  I am currently running 9.04 64bit on a test machine and am able to print to two other printers attached to Windows machines with no problems, and I am able to access Windows shares with no problem.  My problem is I cannot get to the Linux shares on my Ubuntu machine - login failure.
 
If you uninstall Norton's your problems will likely clear, but that may not be the most desirable solution.

I believe I have turned Norton and it's firewall OFF for testing.  I don't think it would still interfere.  I have set up Windows connections before with Norton, but the firewall usually has to be set as per computer you have that is trying to access the machine.   This usually can be done easily if you have Norton on 3 machines or less.  But after that it starts getting hairy and generally I use different virus protection.

I don't have a 64 bit machine so generally the rules for 32 bit machines usually don't apply.  I do get an access error message.

The message I get is:

Unable to mount location: Failed to retrieve share list from server.

However, one thing I am concerned about is that I do have a hardware firewall in the form of a Linksys router.   Normally for Windows connections I never have an issue with the hardware firewall...however, that was for WINDOWS, the firewall could be thinking the Linux connection could be a threat and prevent access to the Windows computer.  Yet the Windows computer CAN get out of the system.

Hard to say though.  Any thoughts?

Geo

---

### Post by falconindy on 2009-09-19
It's unlikely that the router is imposing any rules on the internal network with its firewall. Have you tried connecting to the Windows box with smbclient as I suggested above?

---

### Post by Cuba71 on 2009-09-20
After all that's been said in this thread, I decided to conduct an experiment to backtrack what I did to get my XP printer with Ubuntu Jaunty 9.04, and this is exactly what I did:

The printer is an HP Deskjet 5900.

In Windows XP, I defined the printer as shared and enabled the File and Printer Sharing in Windows firewall.

[LIST]
[*]Booted Ubuntu Jaunty 9.04 from the Live CD
[*]Established the wireless network connection
[*]Went to System > Administration > Printing
[*]In the printer config. screen, clicked New
[*]After the search completed, expanded the tab Network Printers
[*]Clicked on Windows Printers via SAMBA
[*]Clicked on Browse
[*]The printer showed up on the SMB Brose screen (see attachment)
[*]Clicked OK
[*]And proceeded on the next screen to find and install the proper driver
[/LIST]

The printer was installed and printed a test page.

As an interesting side note, my Windows network is called HOMENET, and I didn't have to change anything in UBUNTU

And I also noticed a driver for HP Photosmart 5500
 
I hope this helps

---

### Post by tripler on 2009-09-26
Edit: not relevant

---

### Post by jukingeo on 2009-10-01
> **falconindy said:**
> I'd bet that he can connect by IP, but not by name. OP, if you pop open a terminal and do this...
```
smbclient -L 192.168.1.1
```
and obviously replace the IP there with the IP of the windows machine. You should get a prompt to enter a password. Hit enter (anonymous logon) and you should get **something** to return. Anything but an 'access denied', 'host not found' or anything else to that effect would be golden.

If that **is** the case, there's a quick fix so that you can identify the windows machine by name. Open up /etc/samba/smb.conf with your favorite text editor (with gksu or sudo, of course), and find the line that starts with "name resolve order". You'll want the parameters after that in the following order:
```
   name resolve order = lmhosts wins bcast host
```
And that should hopefully sort things out.

Hello FalconIndy,

Sorry for my slow response but I was on vacation the week before last and really didn't get much on my computer.  Anyway, I did as you ask above.   I edited the IP address with xxx for security reasons but I indeed DID use the actual address from my wife's machine.

The good news is that I DID get something but all is not roses.  Take a look see:

geo@home:~$ smbclient -L 192.168.x.xxx
Password: 
Domain=[ANGELA] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       Remote IPC
	print$          Disk      Printer Drivers
	SharedDocs      Disk      
	E Drive         Disk      
	HP C5580        Printer   HP Photosmart C5500 series
session request to 192.168.x.xxx failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[ANGELA] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
geo@home:~$ 

Now here is the kicker.  My machine CAN see my wife's machine and it CAN see the shared folder and also the printer.  I DO indeed have an HP 5500 series printer connected to that machine.

After that it says the session request failed because of no called name.

Now what does that mean?

I tried the access with both the Norton Security Firewall on and off.  I get the same results.  With the firewall on, I have assigned Norton permissions to allow communication across my IP Address on to my wife's machine.   From her machine I CAN access the shared files on Ubuntu, but I can't access anything on her machine from my Ubuntu machine.

What is my next course of action.  And please don't say remove Norton because that is out of the question.

Thanx,

Geo

---

### Post by barlaventoexpert on 2009-10-02
Let me add to this debate as a similar situation is driving me nuts!

Here at home we have:

1) My partner's Windows XP Laptop to which is attached a brother Laser Printer and connected by ethernet cable to the router.

2) Buffalo Wifi router with 4 ethernet ports.

3) My old desktop machine with Ubuntu Hardy aboard connected by ethernet cable to the router.

4) My Acer 4310 laptop running Ubuntu 9.04. This can connect this to the network either by ethernet cabel at two locations and by wireless.

HOWEVER, while I can print to the Brother and access file shares on the XP machine from the ACER with no problem at all when connected to the router via an ethernet cable, I cannot print nor access file shares on the Windows XP machine while using wifi. A futher point is that while the wifi signal is showing Strength Five on the NM-applet, page loading time is sloooooowwwwwww. I have tried other machines, Windows XP and An Acer EEEpc with its version of Linux onboard and there does not seem to be a problem.

It certainly seems that Ubuntu 9.0.4 still has major bugs in seamlessly connecting to networks via wifi.

---

### Post by jukingeo on 2009-10-02
> **barlaventoexpert said:**
> Let me add to this debate as a similar situation is driving me nuts!

Here at home we have:

1) My partner's Windows XP Laptop to which is attached a brother Laser Printer and connected by ethernet cable to the router.

2) Buffalo Wifi router with 4 ethernet ports.

3) My old desktop machine with Ubuntu Hardy aboard connected by ethernet cable to the router.

4) My Acer 4310 laptop running Ubuntu 9.04. This can connect this to the network either by ethernet cabel at two locations and by wireless.

HOWEVER, while I can print to the Brother and access file shares on the XP machine from the ACER with no problem at all when connected to the router via an ethernet cable, I cannot print nor access file shares on the Windows XP machine while using wifi. A futher point is that while the wifi signal is showing Strength Five on the NM-applet, page loading time is sloooooowwwwwww. I have tried other machines, Windows XP and An Acer EEEpc with its version of Linux onboard and there does not seem to be a problem.

It certainly seems that Ubuntu 9.0.4 still has major bugs in seamlessly connecting to networks via wifi.

As far as I know Linux in general has always had trouble with Wireless.  Some distributions DO handle it better, but Ubuntu does rank pretty low on the list when it comes to wireless.  With that knowledge in mind, I have no intentions of even attempting a wireless connection with Ubuntu.   My connection issue is actually with a wired system.   The Windows computer can talk to the Ubuntu computer, but not vice versa. 

I was hoping the printer had an ethernet port, but it doesn't.  It only has USB.  Since my wife's computer (the Windows XP) one is on more than mine, it doesn't make sense to share through my computer and then my wife has to turn my machine on just to print.   For me, when I want to print something 95% of the time, my wife's machine is already running.

So there has to be something blocking my access because my Ubuntu machine CAN see my wife's machine (as I demonstrated above), but it just will not allow access to it.   And yes, everything that needs to be shared (printers/folders) has been set on my wife's machine.   So I don't get it.  Turning off Norton has no effect.  With the firewall and internet security down, I still have the problem. 

So I would appreciate any assistance in getting this running.

Thanx,
Geo

---

### Post by jukingeo on 2009-10-05
Hello FalconIndy...anyone?

I am still looking to find a solution to my printer problem with the Windows XP /Norton machine.  Hopefully the additional information I provided above will help.

Thanx,

Geo

---

### Post by jukingeo on 2010-04-02
Hello All,

Well, my printer problem was solved by switching to a different router.  I was using a Linksys Firewall Router which apparently didn't 'agree well' with cross platform access across my network.  Could it have been reconfigured...possibly, but what I did was change the router on my system to a new Belkin wireless router to add Wifi capability to my home network.  (no the wifi is NOT going to be for Linux).    But because the Belkin router isn't a firewall router, I no longer have problems accessing my wife's computer using my Linux box.   Add an added bonus, the printer is fully operational now too.

I know this was kind of an unorthodox way of solving my problem, but apparently it was a hardware issue and not an OS issue.

Thanx again to everyone for their assistance in this matter.

Geo

---

### Post by fuegodeth on 2010-05-05
Interesting.  I had the same problem trying to print from ubuntu 9.10, and now 10.04 to my XP machine.  Ubuntu is on Wireless and XP is on cat5 cable to Belkin Wireless N router.  Wireless is working fine.  I had tried everything including the edits to the samba conf file.  Using the direct IP address to the XP machine made it all work right away.  Mine was previously not even able to see the Xp machine, let alone the printer. I typed in 192.168.x.x/canonip4 and it said this is an accessible share when I clicked verify.  I typed in the authentication info and was able to print right away.  I wish I had come across this thread a month ago. that would have saved me a lot of headache. thanks for the excellent help.

---

