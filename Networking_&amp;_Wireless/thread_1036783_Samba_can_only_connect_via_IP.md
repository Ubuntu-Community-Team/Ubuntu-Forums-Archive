---
title: "Samba can only connect via IP"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by flintflake on 2009-01-11
I'm having issues connecting to my other devices via Samba.  I can connect by putting in the IP address of the device, but I can't go to Places|Network|Windows Network.   It never shows anything.  From that screen, I can put in the IP address of any device and it shows up.

I also want a drive to map on boot but it won't do that either.  Here is my fstab ( i changed my username/password after i posted the fstab)...

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=533f3fcd-e30e-4621-a14f-a0921a89e3e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=f09f6b58-8abe-46a3-88e5-704e2e8dacc0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


#smbmount //192.168.1.6/DISk1 /media/disk1 -o username=password,password=password,uid=1000,mask=000

//slug/disk1    /media/disk1        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Any ideas?

---

### Post by albinootje on 2009-01-11
> **flintflake said:**
>  #smbmount //192.168.1.6/DISk1 /media/disk1 -o username=password,password=password,uid=1000,mask=000

//slug/disk1    /media/disk1        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0[/CODE]


Did you put the ip address for "slug" in /etc/hosts ?

And in general you should realise the big difference between using hostnames from DNS or /etc/hosts versus the NetBIOS names that Samba and MS-Windows uses.

[http://en.wikipedia.org/wiki/NetBIOS](http://en.wikipedia.org/wiki/NetBIOS)
See this section -> Host name

---

### Post by capscrew on 2009-01-11
Samba will work with DNS (hostnames) only, if tha is your wish.  You ***do*** have to have DNS configured.  MS Windows has not required WINS (netBIOS) since W2K.  

I do not run any form of netBIOS on my system and can call Samba shares by \\hostname\share.

So, the question to the OP is:  What naming service are you using.  NetBios (WINS) or hostname (DNS)?

---

### Post by sschnee on 2009-01-11
How can I tell (and change) if I'm using WINS or DNS?

---

### Post by flintflake on 2009-01-11
> **capscrew said:**
> Samba will work with DNS (hostnames) only, if tha is your wish.  You ***do*** have to have DNS configured.  MS Windows has not required WINS (netBIOS) since W2K.  

I do not run any form of netBIOS on my system and can call Samba shares by \\hostname\share.

So, the question to the OP is:  What naming service are you using.  NetBios (WINS) or hostname (DNS)?

I had WINS added to my nsswitch.conf file but it still wouldn't allow me to find the machines by name.  I removed it yesterday because aMSN wouldn't start with it.

How would I configure DNS?  

Why won't my drive map using the IP on bootup, yet i can connect once its booted?

I really need to access my Vista machine so I can print from Ubuntu.  That's my main concern.

---

### Post by albinootje on 2009-01-11
> **flintflake said:**
> 
How would I configure DNS?  

You can run a local DNS-server, and force your machines to use that as the first nameserver in the DNS settings of those clients.

Easier and faster is to edit /etc/hosts on your Linux machine(s), and the equivalent hosts file in MS-Windows.
> 
Why won't my drive map using the IP on bootup, yet i can connect once its booted?

I really need to access my Vista machine so I can print from Ubuntu.  That's my main concern.

I don't have any experience with MS-Windows machines as server at all, but setting up printing via another machine you would normally configure via the printer admin interface.
I think it's quite likely that you don't need any local samba settings for that.

---

### Post by capscrew on 2009-01-11
flintflake,

Once Samba is installed, you have the ability to use it to run a WINS nameserver.  It is a matter of configuring WINS via the /etc/samba/smb.conf file.  See: [http://ubuntuforums.org/showthread.php?t=65385&highlight=wins]("http://ubuntuforums.org/showthread.php?t=65385&highlight=wins")

Setting the order of preference in the nsswitch.conf file is only part of the equation.  Setting the same nsswitch.conf file for DNS requests and adding the hostnames to the DNS servers conf file does the same for DNS.

As albinootje has suggested, adding the name to IP mappings in the /etc/hosts file (linux) and the C:\windows\system32\etc\hosts (XP) file and adding the proper requests in the nsswitch.conf file is probably the easiest way as it does not require configuring a DNS server.  

In short -- look in the smb.conf file to see it the wins server is requested.  Check the nsswitch.conf for order of requests (wins = WINS server) (dns = DNS server) (files = hosts files)

if you want to see if the Samba server is running try this from the command line:```
>ps -ef|grep mbd
```

Something like following is what it will return:```
root      4426     1  0 19:20 ?        00:00:00 /usr/sbin/nmbd -D
root      4428     1  0 19:20 ?        00:00:00 /usr/sbin/smbd -D
root      4525  4428  0 19:20 ?        00:00:00 /usr/sbin/smbd -D

```

The entry: 
/usr/sbin/nmbd -D is the wins server naming daemon 
and the entry: 
/usr/sbin/smbd -D is the samba server daemon.

---

### Post by flintflake on 2009-01-14
That command doesn't work.  It says that the '-ef' command not found.  

I can't use WINS because i need to be able to use aMSN.   I'd like to configure DNS if possible.  I have those address in the /etc/hosts on my Ubuntu machine and it still doesn't work.

---

### Post by capscrew on 2009-01-14
> **flintflake said:**
> That command doesn't work.  It says that the '-ef' command not found. 
The command is ```
ps -ef
``` 
> 

I can't use WINS because i need to be able to use aMSN.


Sure you can.  The internal naming service does not have to be the same as the external.

> 

I'd like to configure DNS if possible.  I have those address in the /etc/hosts on my Ubuntu machine and it still doesn't work.

How many hosts are there in your network? Are you using DHCP? Describe your LAN topology.  

Post the contents of your /etc/hosts file here.

---

### Post by flintflake on 2009-01-15
```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 13:47 ?        00:00:01 /sbin/init
root         2     0  0 13:47 ?        00:00:00 [kthreadd]
root         3     2  0 13:47 ?        00:00:00 [migration/0]
root         4     2  0 13:47 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 13:47 ?        00:00:00 [watchdog/0]
root         6     2  0 13:47 ?        00:00:00 [events/0]
root         7     2  0 13:47 ?        00:00:00 [khelper]
root        41     2  0 13:47 ?        00:00:00 [kblockd/0]
root        44     2  0 13:47 ?        00:00:00 [kacpid]
root        45     2  0 13:47 ?        00:00:00 [kacpi_notify]
root       115     2  0 13:47 ?        00:00:00 [kseriod]
root       149     2  0 13:47 ?        00:00:00 [pdflush]
root       150     2  0 13:47 ?        00:00:00 [pdflush]
root       151     2  0 13:47 ?        00:00:00 [kswapd0]
root       192     2  0 13:47 ?        00:00:00 [aio/0]
root      1449     2  0 13:47 ?        00:00:00 [ksuspend_usbd]
root      1453     2  0 13:47 ?        00:00:00 [khubd]
root      1481     2  0 13:47 ?        00:00:00 [ata/0]
root      1488     2  0 13:47 ?        00:00:00 [ata_aux]
root      1492     2  0 13:47 ?        00:00:00 [khpsbpkt]
root      1774     2  0 13:47 ?        00:00:00 [scsi_eh_0]
root      1776     2  0 13:47 ?        00:00:00 [scsi_eh_1]
root      2222     2  0 13:47 ?        00:00:00 [knodemgrd_0]
root      2427     2  0 13:47 ?        00:00:00 [kjournald]
root      2630     1  0 13:47 ?        00:00:00 /sbin/udevd --daemon
root      2923     2  0 13:47 ?        00:00:00 [kpsmoused]
root      2938     2  0 13:47 ?        00:00:00 [pccardd]
root      2944     2  0 13:47 ?        00:00:00 [ipw2200/0]
root      4221     2  0 13:47 ?        00:00:00 [cifsoplockd]
root      4224     2  0 13:47 ?        00:00:00 [cifsdnotifyd]
root      4278     1  0 13:47 tty4     00:00:00 /sbin/getty 38400 tty4
root      4279     1  0 13:47 tty5     00:00:00 /sbin/getty 38400 tty5
root      4283     1  0 13:47 tty2     00:00:00 /sbin/getty 38400 tty2
root      4284     1  0 13:47 tty3     00:00:00 /sbin/getty 38400 tty3
root      4286     1  0 13:47 tty6     00:00:00 /sbin/getty 38400 tty6
root      4461     1  0 13:47 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      4498     2  0 13:47 ?        00:00:00 [kondemand/0]
syslog    4566     1  0 13:47 ?        00:00:00 /sbin/syslogd -u syslog
root      4616     1  0 13:47 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      4618     1  0 13:47 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
108       4640     1  0 13:48 ?        00:00:00 /usr/bin/dbus-daemon --system
root      4656     1  0 13:48 ?        00:00:00 /usr/bin/system-tools-backends
avahi     4676     1  0 13:48 ?        00:00:00 avahi-daemon: running [ubuntu-la
avahi     4677  4676  0 13:48 ?        00:00:00 avahi-daemon: chroot helper
root      4716     1  0 13:48 ?        00:00:00 /usr/sbin/cupsd
root      4758     1  0 13:48 ?        00:00:00 /usr/sbin/inetd
root      4796     1  0 13:48 ?        00:00:00 /usr/sbin/nmbd -D
root      4816     1  0 13:48 ?        00:00:00 /usr/sbin/winbindd
root      4860  4816  0 13:48 ?        00:00:00 /usr/sbin/winbindd
root      4861     1  0 13:48 ?        00:00:00 /usr/sbin/dhcdbd --system
111       4880     1  0 13:48 ?        00:00:00 /usr/sbin/hald
root      4883     1  0 13:48 ?        00:00:00 /usr/sbin/console-kit-daemon
root      4945  4880  0 13:48 ?        00:00:00 hald-runner
root      4958  4945  0 13:48 ?        00:00:00 hald-addon-input: Listening on /
111       4971  4945  0 13:48 ?        00:00:00 hald-addon-acpi: listening on ac
root      4992  4945  0 13:48 ?        00:00:00 hald-addon-storage: polling /dev
root      5012     1  0 13:48 ?        00:00:00 /usr/sbin/hcid -x -s
root      5018     2  0 13:48 ?        00:00:00 [btaddconn]
root      5019     2  0 13:48 ?        00:00:00 [btdelconn]
root      5028  5012  0 13:48 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-se
root      5029  5012  0 13:48 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-se
root      5037     2  0 13:48 ?        00:00:00 [krfcommd]
root      5074     1  0 13:48 ?        00:00:00 /usr/sbin/gdm
root      5077  5074  0 13:48 ?        00:00:00 /usr/sbin/gdm
root      5081  5077  2 13:48 tty7     00:00:26 /usr/bin/X :0 -br -audit 0 -auth
daemon    5119     1  0 13:48 ?        00:00:00 /usr/sbin/atd
root      5133     1  0 13:48 ?        00:00:00 /usr/sbin/cron
root      5211     1  0 13:48 ?        00:00:00 wpa_supplicant -B -Dwext -ieth1
root      5243     1  0 13:48 tty1     00:00:00 /sbin/getty 38400 tty1
root      5338     1  0 14:00 ?        00:00:00 /usr/sbin/anacron -s
jeremy    5355     1  0 14:00 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 4
jeremy    5357     1  0 14:00 ?        00:00:00 /usr/bin/gnome-keyring-daemon -d
jeremy    5358  5077  0 14:00 ?        00:00:00 x-session-manager
jeremy    5411  5358  0 14:00 ?        00:00:00 /usr/bin/seahorse-agent --execut
jeremy    5415     1  0 14:00 ?        00:00:00 dbus-daemon --fork --print-addre
jeremy    5416  5358  0 14:00 ?        00:00:01 gnome-settings-daemon
jeremy    5431  5416  0 14:01 ?        00:00:00 /usr/bin/pulseaudio --log-target
jeremy    5434  5431  0 14:01 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-
jeremy    5443     1  0 14:01 ?        00:00:00 gnome-screensaver
jeremy    5444  5358  0 14:01 ?        00:00:00 /bin/sh /usr/bin/compiz --sm-cli
jeremy    5450  5358  0 14:01 ?        00:00:02 gnome-panel --sm-client-id defau
jeremy    5451  5358  0 14:01 ?        00:00:01 nautilus --no-default-window --s
jeremy    5458     1  0 14:01 ?        00:00:00 /usr/lib/bonobo-activation/bonob
jeremy    5485     1  0 14:01 ?        00:00:00 /usr/lib/gvfs/gvfsd
jeremy    5517  5444  1 14:01 ?        00:00:03 /usr/bin/compiz.real --ignore-de
jeremy    5521     1  0 14:01 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon
jeremy    5524  5358  0 14:01 ?        00:00:00 bluetooth-applet --singleton
jeremy    5528  5358  0 14:01 ?        00:00:00 update-notifier
jeremy    5532  5358  0 14:01 ?        00:00:00 /usr/lib/evolution/2.22/evolutio
jeremy    5535  5358  0 14:01 ?        00:00:00 tracker-applet
jeremy    5537     1  1 14:01 ?        00:00:04 conky
jeremy    5546  5358  0 14:01 ?        00:00:00 trackerd
jeremy    5550  5358  0 14:01 ?        00:00:00 python /usr/share/system-config-
jeremy    5551     1  0 14:01 ?        00:00:00 /usr/lib/gnome-volume-manager/gn
jeremy    5553     1  0 14:01 ?        00:00:00 gnome-power-manager
jeremy    5609     1  0 14:01 ?        00:00:00 /usr/lib/evolution/evolution-dat
jeremy    5612     1  0 14:01 ?        00:00:00 /usr/lib/gnome-applets/trashappl
jeremy    5615     1  0 14:01 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spaw
jeremy    5624     1  0 14:01 ?        00:00:00 /usr/lib/evolution/2.22/evolutio
jeremy    5637     1  0 14:01 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawn
jeremy    5649     1  0 14:01 ?        00:00:00 /usr/lib/gnome-applets/mixer_app
jeremy    5652     1  0 14:01 ?        00:00:00 /usr/lib/fast-user-switch-applet
jeremy    5656  5517  0 14:01 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decor
jeremy    5657  5656  0 14:01 ?        00:00:00 /bin/sh /usr/bin/compiz-decorato
jeremy    5659  5657  0 14:01 ?        00:00:00 /usr/bin/gtk-window-decorator
jeremy    5670     1 12 14:01 ?        00:00:42 /usr/lib/firefox-3.0.5/firefox
jeremy    5674     1  1 14:01 ?        00:00:06 wish /home/jeremynew/.local/bin/
root      5745  5338  0 14:05 ?        00:00:00 /bin/sh -c nice run-parts --repo
root      5746  5745  0 14:05 ?        00:00:00 run-parts --report /etc/cron.dai
root      5757  5746  0 14:05 ?        00:00:00 /bin/sh /etc/cron.daily/apt
root      5781  5757  0 14:05 ?        00:00:00 sleep 887
jeremy    5787     1  5 14:07 ?        00:00:00 gnome-terminal
jeremy    5789  5787  0 14:07 ?        00:00:00 gnome-pty-helper
jeremy    5790  5787  4 14:07 pts/0    00:00:00 bash
jeremy    5807  5790  0 14:07 pts/0    00:00:00 ps -ef

```

> 
Sure you can. The internal naming service does not have to be the same as the external.
How do I set it to be internal?

> 
How many hosts are there in your network? Are you using DHCP? Describe your LAN topology.

Post the contents of your /etc/hosts file here. 

There are currently 4 machines on my network.  I'm using static IP's on the ubuntu machine,Vista desktop that has the printer shared, and my NSLU2 (media server) has a static IP.  The other machine, which is powered off most of the time and never connects to anything, is using DHCP.

Here is my hosts file:

```
127.0.0.1 localhost
127.0.1.1 ubuntu-laptop
192.168.1.11 Gway
192.168.1.6 Slug

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I think i covered all of your questions.  :)

---

### Post by capscrew on 2009-01-15
Are you able to ping by name the hosts listed in your etc/hosts file?  Do you have the same listings all of the machines /etc/hosts files?

Can you post the relevant parts of the /etc/samba/smb.conf file?

---

### Post by flintflake on 2009-01-16
Yes, I can ping using the name in Terminal.  

here is my smb.conf:

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
   workgroup = "My network name-removed to post here"

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts bcast wins host 

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth1

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

```

---

### Post by albinootje on 2009-01-16
> **flintflake said:**
> Yes, I can ping using the name in Terminal.  

here is my smb.conf:


I've reread your OP, can you explain the structure of your network please ?
Sorry in case I've missed something in all those comments.
You're trying to use a share from a MS-Windows machine or an Ubuntu machine ?

Your smb.conf doesn't have any shares defined.
And I don't see any reason why you would not want to publish the name of your workgroup from your home LAN here.

---

### Post by flintflake on 2009-01-16
> **albinootje said:**
> I've reread your OP, can you explain the structure of your network please ?
Sorry in case I've missed something in all those comments.
You're trying to use a share from a MS-Windows machine or an Ubuntu machine ?


There are currently 4 machines on my network. I'm using static IP's on the ubuntu machine,Vista desktop that has the printer shared, and my NSLU2 (media server). The other machine, which is powered off most of the time and never connects to anything, is using DHCP.

I have 2 issues here.

1)  The attached fstab doesn't mount the network drive on boot up.  Once booted, I can manually access the drive by IP.

2)  I can't print to my Vista shared printer.

3)  I can't access any of my network devices by name... only by IP.

---

### Post by albinootje on 2009-01-16
> **flintflake said:**
> There are currently 4 machines on my network. I'm using static IP's on the ubuntu machine,Vista desktop that has the printer shared, and my NSLU2 (media server). 

Thanks.
It could make sense to set up a local DNS-server on a machine which is on all the time, and then enforce all the machines to use that as the first nameserver (DNS). Does that make sense for your situation ?

Does your NSLU2 listen to the name "slug" somewhere in your setup ?
Or is that the name you would like to give it ?
Did you put the hostnames in the appropriate hostname file on the Vista machine ? 
I think the filename you would need for that is called lmhosts.

---

### Post by capscrew on 2009-01-16
@ albinootje,

I believe flintflake has described the network adequately in post #10.  If he does not want to revel his workgroup name that's okay too. The answers he gave in respnse to my questions help me understand his situation.

@ flintflake,

The point that albinootje make about your workgroup setting has some need for clarification. Workgroups are a mechanism to allow the user to browse a group of associated computers.  This has nothing to do with authentication.  It is only local to your LAN.  In your situation you ned to remember that all of the hosts (computers) on your LAN   use the same workgroup setting.

> Yes, I can ping using the name in Terminal.

If you have not setup DNS in your DSL modem/router then you are using the /etc/hosts file for name resolution.

It appears that you have tried to configure Samba using the GUI interface in Gnome (Nautilus).  your configuration files are located at /var/lib/samba.  **[SIZE="2"][COLOR="Red"]Dont mess with them.[/COLOR][/SIZE]**  There isn't much you can do with them anyway, it's easier to config your system manually.  Samba looks to smb.conf ***before ***it looks to the /var/lib/samba config's.

Let's get the naming service working before we mess with Samba.

You say you have 3 hosts that you want to refer to by name. I see only 2 in the /etc/host file that you posted.  I would list all 3 in **each **machine's /etc/host file.  Below is what my /etc/hosts file would look like on my desktop machine.  I have annotated the settings in red (not part of the file) ```
127.0.0.1 localhost [COLOR="Red"]<---this machine[/COLOR]
192.168.1.1 bbgw1 [COLOR="Red"]<---router[/COLOR]
192.168.1.145 bbap1  [COLOR="Red"]<---wireless AP[/COLOR]
192.168.1.2 rincon  [COLOR="Red"]<---Samba server[/COLOR]
192.168.1.10 newport [COLOR="Red"]<---XP pro[/COLOR]
192.168.1.12 malibu  [COLOR="Red"]<---Ubuntu Desktop[/COLOR]
192.168.1.200 printer [COLOR="Red"]<---HP 2200DN printer[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Remember you are mapping IP addresses to names.  We need a line for each IP address you wish to resolve at each machine.  This should include the name of the machine you are at.  If you are at Slug and you ping Slug (use only lower case ) you should get a ping that refers to 192.168.1.6.  If you ping localhost you should get 127.0.0.1

Let us know when you can ping all 3 hosts by name from any of the 3 hosts.

---

### Post by albinootje on 2009-01-16
Here's some more information on that lmhosts file editing :
[http://support.microsoft.com/kb/923947](http://support.microsoft.com/kb/923947)
[http://www.howtonetworking.com/Windows/lmhosts.htm](http://www.howtonetworking.com/Windows/lmhosts.htm)
[http://www.technipages.com/vista-access-denied-when-modifying-hosts-or-lmhosts-file.html](http://www.technipages.com/vista-access-denied-when-modifying-hosts-or-lmhosts-file.html)

---

### Post by capscrew on 2009-01-16
@ albinootje.

> I think the filename you would need for that is called lmhosts. lmhosts is for netbios.  The appropriate file is the hosts file in the same .../system32//drivers/etc/ folder on the Vista host.

Edit:  You should read first what you recommend.  See the WINS reference> You experience name resolution issues on your TCP/IP network, especially for a small business with WINS server, you may want to use Lmhosts files to resolve NetBIOS names:

---

### Post by flintflake on 2009-01-16
Thank your capscrew and albinootje for your continued help with my issue.   I had a successful installation of Gutsy on another machine a few years back and I had the network setup correctly.  Whatever this is seems to be something really simple, but it's testing my patience now.

Ok, my network works perfectly without Ubuntu.  My Vista, XP machine, and the slug all work harmoniously in the pc world.   Ubuntu just doesn't want to play along.  I honestly think it's something REALLY simple that we're missing but i just don't know what it is.

I added a reference to every static machine to hosts and have good pings by name:


```

jeremy@ubuntu-laptop:~$ ping slug -c3
PING Slug (192.168.1.6) 56(84) bytes of data.
64 bytes from Slug (192.168.1.6): icmp_seq=1 ttl=64 time=1.86 ms
64 bytes from Slug (192.168.1.6): icmp_seq=2 ttl=64 time=2.00 ms
64 bytes from Slug (192.168.1.6): icmp_seq=3 ttl=64 time=1.80 ms

--- Slug ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 1.806/1.891/2.004/0.090 ms
jeremy@ubuntu-laptop:~$ ping gway -c3
PING Gway (192.168.1.11) 56(84) bytes of data.

--- Gway ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

jeremy@ubuntu-laptop:~$ ping gway -c3
PING Gway (192.168.1.11) 56(84) bytes of data.
64 bytes from Gway (192.168.1.11): icmp_seq=1 ttl=128 time=4.04 ms
64 bytes from Gway (192.168.1.11): icmp_seq=2 ttl=128 time=2.99 ms
64 bytes from Gway (192.168.1.11): icmp_seq=3 ttl=128 time=2.96 ms

--- Gway ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 2.966/3.336/4.048/0.505 ms
jeremy@ubuntu-laptop:~$ ping router -c3
PING Router (192.168.1.1) 56(84) bytes of data.
64 bytes from Router (192.168.1.1): icmp_seq=1 ttl=64 time=1.48 ms
64 bytes from Router (192.168.1.1): icmp_seq=2 ttl=64 time=1.57 ms
64 bytes from Router (192.168.1.1): icmp_seq=3 ttl=64 time=1.55 ms

```

Doing this seemed to have done something because now when i go to the network, I automatically see all of my devices now.  I had to actually drill down through the "Windows Network" before i saw the devices.  Now i just need to address the original issue of mounting the network drive automatically.  I'm going to play with the fstab file a little and report back shortly.

---

### Post by flintflake on 2009-01-16
Ok... printing to Vista is WORKING!!  

I just need to find out why my network drive won't mount on boot.  I get this when i try to mount it in terminal:

```
jeremy@ubuntu-laptop:~$ //192.168.1.6/DISk1 /media/disk1 -o username=jeremy,password=jeremy,uid=1000,mask=000
bash: //192.168.1.6/DISk1: No such file or directory
```

Yet, I can browse my name or IP and access the drive with no problems.  What am I missing?  It has to be something simple.

---

### Post by capscrew on 2009-01-16
you need to use the mount command. :-)

See the man pages on the subject:```
man mount
```

I suggest you should use this option:```
sudo mount -t cifs //server/share /path/to/mountpoint user=user password=password
``` as the basic mounting command.  Remember to use sudo as only root can mount via the command line.

When you have it working correctly you can add it to your /etc/fstab file and it will mount automatically

---

### Post by flintflake on 2009-01-16
Ok, capscrew... LOL!  I forgot about the mount command.  Thanks for the tip.   I'm almost there, but not quite.

This code mounts the drive in terminal:

```

sudo mount -t cifs //slug/disk1 /media/disk1 -o username=jeremy,password=jeremy,uid=1000,mask=00 
```

but this line in fstab doesn't?

```
mount -t cifs //slug/disk1 /media/disk1 -o username=jeremy,password=jeremy,uid=1000,mask=000
```

---

### Post by capscrew on 2009-01-16
flintflake,

The syntax is as follows:

> //server/usersharename /mnt/username cifs user 0 0

See [**[COLOR="Red"]here[/COLOR]**]("http://pserver.samba.org/samba/ftp/cifs-cvs/linux-cifs-client-guide.pdf") for more information

---

