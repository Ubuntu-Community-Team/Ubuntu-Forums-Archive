---
title: "Network/Wireless Folder Share Connectivity Issues on Jaunty"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by edvar on 2009-05-21
Since I upgraded to Jaunty a couple of weeks ago I've experienced this problem and it's driving me nuts!

Basically I have an Ubuntu box with all my media files and configured a samba share so I can access the files from my macbook running Mac OS X 10.5 using a wireless connection. It worked fine before on Intrepid. No connection drops.

Now several times a day the samba share just disconnects out of nowhere. Sometimes it reconnects (not automatically... I have to manually try to reconnect) in a couple of seconds after the drop and sometimes it doesn't. When it doesn't I cannot ping my Ubuntu box (destination unreachable or no route to host) and I either have to restart my wireless router or restart networking on Ubuntu to get the connection to the samba share back. Sometimes when it doesn't reconnect I just have to ping to the Mac from Ubuntu and go back to the Mac and try to reconnect. It's almost like the route between the both computers is lost but... no route is needed since they are on the same subnet!! That's the message on the Mac's log:

> May 20 23:10:15 ed-mac KernelEventAgent[39]: tid 00000000 type 'smbfs', mounted on '/Volumes/MediaCenter', from '//ed@ed-linux/MediaCenter', not responding
May 20 23:10:15 ed-mac KernelEventAgent[39]: tid 00000000 found 1 filesystem(s) with problem(s)
May 20 23:10:15 ed-mac loginwindow[38]: 1 server now unresponsive


And this is how the samba share is configured:

> [MediaCenter]
        path = /MediaCenter
        writeable = yes
        browseable = yes
        valid users = ed


I thought it was a problem with the wireless card on the Ubuntu box so I bought a new one with the Atheros chipset and ath9k driver. I replaced the card, Jaunty recognized it straight away and my wireless connection was back. I must say it wasn't the only reason to replace the card. I wanted to upgrade my home network wireless setup to Wireless N. So I bought a new wireless card and a new wireless N router. Anyway, with a brand new wireless card and a brand new wireless router I was still having the samba share connection drop issue I was having with the previous Wireless G router and card. It pretty much excluded the wireless card on Ubuntu and the wireless router as causes. Other then that, when I check the wireless manager software on the wireless N router it shows the wireless connection doesn't drop at all either on the Mac or on the Ubuntu box. It's available at all times and steady at 300Mbps for both wireless clients!

So no problem with the wireless connection lead me to the next usual suspect: samba. I checked the configuration and it was all good. To test if samba was the cause, I setup a NFS share between Ubuntu and the Mac and disconnected the samba share. After a while, same problem: NFS share disconnected and ping unreachable.

Ruled out samba and the wireless network as causes, I thought it might be something wrong with TCP/IP. However everything seems to be fine on both boxes in regards to TCP/IP connectivity. I still can connect to the Internet either from Ubuntu or the Mac but cannot make the boxes talk between themselves. I also disabled the firewall on Ubuntu to test. No success. Firewall disabled and I still got connection drops. Other than that I have a firewall rule enabling all traffic on the local network so all my computers can talk to my Ubuntu box on any port.

My last resort was to blame the Mac OS. So I installed Windows 7 RC on a separate partition on my Mac and tested the connection from Windows. Exact same problem. Connection drops, cannot ping the Ubuntu box, samba share unavailable. To get the connection back I had to restart the network using the Gnome Network Manager on Ubuntu. After that I managed to connect to the share. Tried to stream a movie from the samba share and 5 minutes later I lose the connection again.

Any ideas? Is anyone experiencing the same issues? Again, it worked fine on Intrepid and just started to behave like this after I upgraded to Jaunty. Also I run 'apt-get upgrade' every day and I have the latest updates installed.

---

### Post by superprash2003 on 2009-05-22
problem with jaunty
[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

### Post by edvar on 2009-05-22
Thankyou but this not the problem. My wireless connection stays up all the time. It's just the share that becomes unavailable. Even when the share is unavailable I can connect to the internet from my Ubuntu box.

---

### Post by edvar on 2009-05-22
I think I found the problem. For some reason something is deleting the Ubuntu box entry on the arp cache from the Mac from time to time. It's not caused by the mac or else the Windows 7 wouldn't have the same problem.

When I lose connection and ping my macbook from ubuntu, the arp entry is recreated temporarily and then, after a while, it's deleted again.

Has someone ever seen anything like this?

---

### Post by superprash2003 on 2009-05-22
but what about

> . When it doesn't I cannot ping my Ubuntu box

---

### Post by edvar on 2009-05-23
I meant I cannot ping the ubuntu box from my macbook but if I go to the Ubuntu box everything is working fine and I can even ping back from ubuntu to the mac.

Basically computers on the same subnet talk between them selves based on the arp table since they don't have to route packages. Routing just comes into play between different subnets. So if the arp table is messed up, the computers won't be able to communicate.

Anyway, I solved the problem by creating a permanent entry on the arp table for my ubuntu box on the mac. Now it's all good!

---

### Post by edvar on 2009-05-26
Sorry, the problem is not solved. It's better after the arp fix since it's automatically reconnecting everytime now  but I still lose connectivity to my samba share several times a day.

Since I tested with Mac and Windows, I think samba on ubuntu is the one to blame. Does anyone know if there's anything I need to put on /etc/samba/smb.conf in order to fix this?

---

### Post by Iowan on 2009-05-26
Might be unrelated, but > May 20 23:10:15 ed-mac KernelEventAgent[39]: tid 00000000 [COLOR="Red"]type 'smbfs'[/COLOR], mounted on '/Volumes/MediaCenter', from '//ed@ed-linux/MediaCenter', not responding
May 20 23:10:15 ed-mac KernelEventAgent[39]: tid 00000000 found 1 filesystem(s) with problem(s)
May 20 23:10:15 ed-mac loginwindow[38]: 1 server now unresponsive SMBFS has been deprecated in favor of CIFS. Perhaps [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To will be helpful.

---

### Post by urkurk on 2009-05-27
I have the exact same problem with an Ubuntu Jaunty samba server on wireless and a Windows XP client. 

The Ubuntu box becomes unpingable from the XP box after a while and the samba shares become unreachable, but outgoing connections from Ubuntu still works fine.

arp on XP did not show an entry for Ubuntu, so I added it and now it's all fine and dandy. I guess I'll see how long it lasts.

Problem started appearing after upgrade from Intrepid.

---

### Post by dmizer on 2009-05-27
Also, try this: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by edvar on 2009-05-27
I tried mounting with CIFS and also tried the suggestion from [http://ubuntuforums.org/showthread.php?t=938902](http://ubuntuforums.org/showthread.php?t=938902) . Things got a bit better after I created a static entry on the arp table as mentioned but the problem still happens.

Samba Share Browsing is not actually a problem since I mount the samba share automatically at startup. I don't need to browse for shares.

I'm not sure if it's a problem with Samba or Wireless or both.

---

### Post by dmizer on 2009-05-27
In your first post, you posted your share configuration. Can you post your entire smb.conf file please?

---

### Post by edvar on 2009-05-27
Thanks, my SSH connection to my Ubuntu box just dropped so I'll send it as soon as I get home.

This is the error message on my mac system logs from yesterday:

> 27/05/09 6:16:28 PM KernelEventAgent198 tid 00000000 type 'smbfs', mounted on '/Volumes/MediaCenter', from '//ed@ed-linux/MediaCenter', not responding 
27/05/09 6:16:28 PM KernelEventAgent198 tid 00000000 found 1 filesystem(s) with problem(s) 
27/05/09 6:16:28 PM loginwindow197 1 server now unresponsive 
27/05/09 6:16:28 PM loginwindow197 1 server now unresponsive 
27/05/09 6:16:58 PM loginwindow197 1 server now unresponsive 
27/05/09 6:17:39 PM kernel smb_iod_reconnect: Retrying connection to ed-linux 
27/05/09 6:17:39 PM kernel smb_iod_reconnect: Retrying connection to ed-linux 
27/05/09 6:18:13 PM kernel smb_iod_reconnect: Reconnected to ed-linux 
27/05/09 6:18:13 PM KernelEventAgent198 tid 00000000 received VQ_NOTRESP event (1) 
27/05/09 6:18:13 PM loginwindow197 No servers unresponsive 
27/05/09 6:18:13 PM loginwindow197 No servers unresponsive 

As you can see, the share disconnects for almost 2 minutes and then reconnects back automatically (before the arp table change I had to try and reconnect manually)

---

### Post by edvar on 2009-05-28
Here it is:

```
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = mediacenter

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
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
	log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
	max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
	passdb backend = tdbsam

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
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

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
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;	printing = cups
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
socket options = TCP_NODELAY SO_KEEPALIVE IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = no
	username map = /etc/samba/smbusers
	security = user
	guest ok = no
;	guest account = nobody

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

;[printers]
;	comment = All Printers
;	browseable = no
;	path = /var/spool/samba
;	printable = yes
;	guest ok = no
;	read only = yes
;	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[MediaCenter]
	path = /MediaCenter
	writeable = yes
	browseable = yes
	valid users = ed
```

---

### Post by dmizer on 2009-05-28
Everything looks fine. Overly complex, but fine. The only thing I can really suggest is adding this:
netbios name = Jaunty-name

It should be added right below the "workgroup =" option. Reboot, or restart samba for the change to take effect. That should remove the need for the arp entry.

---

### Post by edvar on 2009-05-28
Thanks for the tip. I'll try that and let you know if it helped.

Just for the sake of testing, I completely removed samba (apt-get remove --purge and deleted /etc/samba) from my Ubuntu box and reinstalled with a vanilla config. After that I reconfigured everything as it was before. Just tested and the share is up and running again. You never know if my upgrade from Intrepid to Jaunty broke something...

Other than that I'm kinda tempted to install Samba 4.0. There's a package on the repositories but it's still on Alpha...

---

### Post by dmizer on 2009-05-28
> **edvar said:**
> Other than that I'm kinda tempted to install Samba 4.0. There's a package on the repositories but it's still on Alpha...

I wouldn't suggest risking it for your problem. If my above suggestion doesn't fix the problem, then I suspect we'll be looking into possible networking issues which a newer version of Samba wouldn't fix anyway.

Edit:
I meant to ask, is there a particular reason for this option?
```
	dns proxy = no
```

---

### Post by edvar on 2009-05-28
About the "dns proxy = 0", it's the default option on smb.conf and I haven't changed it.

Anyway, great news! I just streamed a 30 minutes video from my samba share and I haven't had any disconnection. It hasn't happened since I upgraded to Jaunty.

After reinstalling and reconfiguring my samba share from scratch I did a couple things:

- Added "netbios name" on smb.conf as suggested
- Added "socket options = TCP_NODELAY SO_KEEPALIVE IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192" on smb.conf
- Changed "wins support" to yes on smb.conf
- Installed winbind
- Restarted samba
- Configured my Ubuntu box as a WINS Server on my macbook (SYSTEM PREFERENCES -> NETWORK -> ADVANCED)

I'll keep testing with longer videos on the next couple of days and keep you guys posted. Hopefully it'll sove the problem once and for all!

Thanks for the help!

---

### Post by dmizer on 2009-05-28
Only thing further I have to add is that you should not use the "wins support = yes" option for the following reasons:
```
          wins support (G)
             This boolean controls if the nmbd(8) process in Samba will act as
             a  WINS  server. [COLOR="Red"]You should not set this to yes unless you have a
             multi-subnetted network and you wish a particular nmbd to be your
             WINS  server[/COLOR].  Note that you should NEVER set this to yes on more
             than one machine in your network.

             Default: wins support = no
```
Taken from man smb.conf

Glad it's working for you! I think the "netbios name =" option is what really did it.

---

### Post by SpiderTex on 2009-07-31
Hi y'all,
all new to Ubuntu
I was wrecking my brain with exactly the same symptoms, I&#8217;m going to try the &#8220;netbios name=&#8221; thing.
 
Will let you know if that solved it.
 
Edvar, please note that my connection stays sometimes alife for over 60 minutes before my shares dissapear!! 
 
 
>>> my set-up
Ubuntu 9.04 with 1.12TB RAID 1 multi media shared wirelessly connected to a Vista box that serves as a HTPC and an XP box
 
Experience: exactly the same thing as Edvar describes.
Sometimes pinging from XP to Ubuntu solved it, but most of the time it required a switch off of the Wireless network, and restart it again&#8230;
 
I did notice yesterday a &#8220;Master Browser election&#8221; error in my XP&#8217;s eventlog&#8230; not sure if that has anything to do with this&#8230;

---

### Post by dmizer on 2009-07-31
> **SpiderTex said:**
> Hi y'all,
all new to Ubuntu
I was wrecking my brain with exactly the same symptoms, I’m going to try the “netbios name=” thing.
 
Will let you know if that solved it.
 
Edvar, please note that my connection stays sometimes alife for over 60 minutes before my shares dissapear!! 
 
 
>>> my set-up
Ubuntu 9.04 with 1.12TB RAID 1 multi media shared wirelessly connected to a Vista box that serves as a HTPC and an XP box
 
Experience: exactly the same thing as Edvar describes.
Sometimes pinging from XP to Ubuntu solved it, but most of the time it required a switch off of the Wireless network, and restart it again…
 
I did notice yesterday a “Master Browser election” error in my XP’s eventlog… not sure if that has anything to do with this…

For more information on how to set things up, see the 6th link in my sig.

---

### Post by SpiderTex on 2009-08-01
Ok update: adapted my smb.conf as per dmizer's excellent 6th link!
 
Behaviour has changed, Ubuntu seems to see all the machines on my network, thing is that my XP client disconnected after 20 minutes. After that I can ping, but when in explorer my XP gets an "no access" msg.
 
Checked the eventlog, bar the Master Browser error -which has nothing to do (I think) with it- it is as clean as a whistle.
 
I need to check my HTPC (Vista) later to see if it disconnects also...
 
Odd thing was, when on Ubuntu I disconnected from the wireless connection, and reconnected it, XP could see my Ubuntu shares again...
 
I'll give an update later with results from my Vista box...

---

### Post by dmizer on 2009-08-01
> **SpiderTex said:**
> Ok update: adapted my smb.conf as per dmizer's excellent 6th link!
 
Behaviour has changed, Ubuntu seems to see all the machines on my network, thing is that my XP client disconnected after 20 minutes. After that I can ping, but when in explorer my XP gets an "no access" msg.
 
Checked the eventlog, bar the Master Browser error -which has nothing to do (I think) with it- it is as clean as a whistle.
 
I need to check my HTPC (Vista) later to see if it disconnects also...
 
Odd thing was, when on Ubuntu I disconnected from the wireless connection, and reconnected it, XP could see my Ubuntu shares again...
 
I'll give an update later with results from my Vista box...

Please post the contents of /etc/samba/smb.conf

---

### Post by SpiderTex on 2009-08-01
Here you go attached.txt  (don't know how to that nice scrollie thing) :

---

### Post by dmizer on 2009-08-01
Under the Misc section, add this option:
```
domain master = no
```
After making the change, be sure to restart samba, or reboot.

To make the scrolling code box, use the ```
 tag like so:
[COLOR="Red"][noparse][code][/noparse][/COLOR]your smb.conf file here[COLOR="Red"][noparse]
```[/noparse][/COLOR]

---

### Post by SpiderTex on 2009-08-01
Alright, the Ubuntui machine was on for 5 hours, the Ubuntu box was not visible anymore from XP.

Added the suggestion...  restarted Samba.  No changes.
Disconnected the wireless network, reactivated, no changes.

Restarted the whole machine, and everything is visible again...

:confused::confused::confused: triple confused (and thx for helping me dmizer)

---

### Post by dmizer on 2009-08-01
On the off chance ...

Try rebooting the router.

---

### Post by SpiderTex on 2009-08-02
> **dmizer said:**
> On the off chance ...
 
Try rebooting the router.
 
Router is fine.. the rest of the network stands.. and connectivity inter windoz is fine...
 
So I left my Ubuntu box running overnight, and Vista has no trouble to gain access...  XP is still having a [\\Ubuntu\share]("file://\\Ubuntu\share") not accessible"
Checking access from Ubuntu to the Share on XP fails also....
 
But since the Vista box is my HTPC that will do for now...
 
thanks for the support dmizer...

---

### Post by dmizer on 2009-08-02
> **SpiderTex said:**
> Router is fine.. the rest of the network stands.. and connectivity inter windoz is fine...

This does not mean that the router isn't the problem. And rebooting the router takes little to no effort. It's, at the very least, worth a shot.

---

### Post by SpiderTex on 2009-08-02
> **dmizer said:**
> This does not mean that the router isn't the problem. And rebooting the router takes little to no effort. It's, at the very least, worth a shot.
 
I know, but restarting the router will also mean that the lan connections will be recycled, and that solved the problem in the past...  
 
But ok, I recycled now the router, all clients on the network reconnected...
And my XP client sees the Ubuntu shares again.
 
Now we will have to wait...

---

### Post by SpiderTex on 2009-08-02
Odd things happen to the way to the forum...     my XP box saw the ubuntu shares, but vista didn't anymore....

I did notice that Ubuntu weahter screenlet lost connection to the internet before...   hmmm

---

### Post by SpiderTex on 2009-08-03
Again, recycling the network on the Ubuntu resolved the issues, both boxes PC and Vista can see the Ubuntu shares....
 
// side note: the Master Browser error in my XP's eventlog has disapeared, thx to the domain master = no

---

### Post by dmizer on 2009-08-03
Perhaps you just have a flaky wireless connection. What wireless card do you have?

---

### Post by SpiderTex on 2009-08-03
> **dmizer said:**
> Perhaps you just have a flaky wireless connection. What wireless card do you have?
 
It is a D-Link G510.
 
I have one of the XP boxes with another G510, and another with USR 54xx series card
 
The vista is connected via cable to the access point.
 
If I have time I'll try to swap the D-link with the USR tonight...

---

### Post by dmizer on 2009-08-03
Actually, I was going to suggest that you try connecting your Ubuntu box via ethernet cable for a while ... just for testing. If you experience the same problem with a hard line connection, then you'll know that the problem is not with wireless and you'll save yourself the trouble of trying to swap out wireless cards.

---

### Post by SpiderTex on 2009-08-04
> **dmizer said:**
> Actually, I was going to suggest that you try connecting your Ubuntu box via ethernet cable for a while ... just for testing. If you experience the same problem with a hard line connection, then you'll know that the problem is not with wireless and you'll save yourself the trouble of trying to swap out wireless cards.
Well I didn't had the time to swap NIC's...  good idea...  I'll try that....

---

### Post by edvar on 2009-09-14
Guys,

The problem is still happening. It worked fine for a while and then the choppy video streaming came back again.

Take a look at this: [http://ubuntuforums.org/showthread.php?t=1168950](http://ubuntuforums.org/showthread.php?t=1168950)

Apparently it is a problem with the wireless connection as it works fine when Jaunty is connected via ethernet. Samba is not the issue.

Does anyone know if there's a bug report created about this?

---

### Post by edvar on 2009-09-15
Answering my own question:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/348204)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190144](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190144)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/384924](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/384924)

Apparently it's fixed on kernel 2.6.30... It seems we have to wait for Karmic...

Also I just installed linux-backports-modules-jaunty and the performance seems to be much better

---

