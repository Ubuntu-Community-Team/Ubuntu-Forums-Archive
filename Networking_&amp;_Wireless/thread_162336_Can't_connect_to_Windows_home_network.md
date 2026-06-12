---
title: "Can't connect to Windows home network"
date: 2006-04-18
forum: Networking &amp; Wireless
---

### Post by jflash on 2006-04-18
I'm not sure if this is in the right forum, but here goes.

First of all, I am very new to Ubuntu and Linux in general. 

I had a home network through Windows XP Home before I installed Ubuntu on my computer. We use a Linksys WRT54G router with both wired and wireless access. We have two desktops connected by wired, and a laptop with wireless. The laptop and the family desktop can communicate with each other, and I can communicate from my computer when I boot into XP. However, I cannot connect to the network for filesharing or network printing when I am in Ubuntu. I can connect to the internet, however, which uses the same connection, thus telling me that my connection is not to blame. I am assuming that I have gotten my configuration wrong somewhere, but I don't know where I've gone wrong. As I said, I am very new to Linux, so if someone could walk me through the setup process, I'd appreciate it. I have installed samba, but that's about it. If you need any more information, let me know. Thanks!

---

### Post by jflash on 2006-04-22
*bump*

---

### Post by bryan4134 on 2006-04-22
Not answer I am afraid but I am in exactly the same position.  I can see the internet but not my XP network.  Still trying - will let you know if I succeed!

Bryan

---

### Post by jflash on 2006-04-22
Thanks. I'll keep trying as well. If anyone has any solutions, please let me know!

---

### Post by souki on 2006-04-22
can you ping each others ?
is it xp pro or home edition ?
what kind of windows network, workgroup, domain ?

try this is a terminal, and post the output (leave the password empty if you are asked to, hit [Enter]) :
```
smbtree
```

---

### Post by Jason_25 on 2006-04-22
Can you ping all other PCs on the network?  Do all PCs have a unique ip address?  Once you have confirmed that, what happens when you go to places > network servers?

---

### Post by jflash on 2006-04-22
1. I can NOT ping the other computers on my network.
2. It works fine when I boot into XP (home) on ym computer. Aside from that, the family computer runs XP Home, and the laptop runs Windows 2000.
3. I don't quite get what you mean, what kind of network. I may have said it earlier, but if this helps, I have a Linksys WRT54G router/gateway with both wired and wireless connections. My computer and the family computer are connected to the wired ports, and the laptop connects via wifi. Our cable modem also hooks up directly to the router. When I initially set up the network, I used XP's Network Setup Wizard, from there I used the disks I made with it.
4. When I tried smbtree, it did prompt me for a password. WHen I pressed [enter], it simply returned to the initial prompt, as seen below:

```
me@mycomputer:~$ smbtree
Password:
me@mycomputer:~$
```

5. The router serves as a DHCP server for our network. 
6. When I go to Places > Network Servers, I get the FTP connections I have set up as well as an icon that says 'Windows Network'. When I click on that, however, it appears the same way an empty folder would appear.

---

### Post by Jason_25 on 2006-04-22
My guess would be an ip address conflict with your ubuntu pc and a windows pc.  DHCP makes it so tough to troubleshoot things.  Make sure you were pinging the right IP addresses.

---

### Post by jflash on 2006-04-22
OK, I tried disabling the DHCP part of my router. After I did that, my XP machine couldn't acquire an IP address, so I re-enabled it. After that, I renewed the XP machne's IP address and pinged it from my computer successfully. However, I still get no results from running the smbtree command or by going to places > network servers > windows network. Any other suggestions? For what it's worth, I have no real need for dynamic IP addresses. If there is some easy way to make them static, I have no objections as long as somone tells me how.

---

### Post by LoclynGrey on 2006-04-22
can you try pinging with all machines firewalls turned off or set each firewall up to accept local connections.
Also you can set static ips, but you should always let you dhcp router do it for you. (i set a static ip on a networked machine only if it was like a fileserver or webserver etc)

---

### Post by jflash on 2006-04-22
I can ping the other computers (at least the XP one) with no problems. However, I can't browse the shared resources on the computer.

---

### Post by LoclynGrey on 2006-04-22
Lets back track here.

is Samba installed on your Ubuntu machine. (Which I assume from your posts you are dual booting with xp home - correct?)

typing smbtree in the terminal (ubuntu) will list the network shares.

---

### Post by jflash on 2006-04-22
Correct, I am dual booting with XP Home. I do have samba installed, and when I try smbtree, it pauses for a moment, then gives me no output, just prints the initial prompt, as I put a few posts back. I have tried this both entering and not entering my password at the prompt.

---

### Post by LoclynGrey on 2006-04-22
Edit:
have a read through this post:

[http://ubuntuforums.org/showthread.php?t=155654&highlight=set+samba+share+network+windows](http://ubuntuforums.org/showthread.php?t=155654&highlight=set+samba+share+network+windows)

---

### Post by jflash on 2006-04-22
Other than the links to FTP servers I have set up, there is an icon that reads "Windows Network". However, when I open that, nothing shows up.

---

### Post by jflash on 2006-04-22
OK, I have it partially working. I can now access the files on the fmaily computer. However, my computer and the fmaily computer are now in seperate domains/workgroups. My computer shows up in the default MSHOME workgroup, whereas our family computer shows up in the workgroup whose name I will not mention because it is our last name. I know I correctly edited the smb.conf file to match the workgroup. 
Also, I can't seem to find the printer set up and shared on our family computer. I'll try installing the Linux driver and see if that works.

Aside from that, it works great. Thanks!

In case you're wondering, I got it to work by disabling Firestarter (which I had forgotten I had installed. #-o)

---

### Post by dcarter on 2006-04-22
I have the same problem myself. I am a windows network administrator with a lot of experience in LAN and WAN networks. I am in my first week of Linux. I am running a W2K Advanced server in Domain mode. I provide my own DHCP, DNS, WINS, and Active Directory. My Windows domain works Flawlessly. I recently installed UBUNTU to dual boot on two desktops on my network.

Both Linux boxes have full internet connectivity and email. Neither Linux box will recogonize the other thru the LAN. I can not access any resource from either machine. I can log into the Windows Domain, but I get an empty window with no content. I cannot print to any of my network servers. So far I have found no documentation on what the problem might be. I am thinking that it may be the difference in the file systems and networking componants. Are there any patches of modules available to correct this, or is it manual configurations. If so, where can you get a guide to set the correct configurations?

Any help wuold be appreciated. I fear that I am loosing what little hair I have left...

---

### Post by jflash on 2006-04-22
Read through this topic, and check some of the other discussions referenced. I have read through most of them, and they have helped me a lot.

---

### Post by jflash on 2006-04-22
New problem. Now, the samba service won't start. I tried reinstalling it with synaptic, but no luck. Someone please help me!

---

### Post by Jason_25 on 2006-04-23
Generally that means something is wrong in your smb.conf.  Samba keeps it's logs in the usual place at /var/log.  You don't need samba to connect to smb shares though.  You only need it to host samba shares.

---

### Post by bryan4134 on 2006-04-23
I now have almost everything working.  Once I disabled the "block all SMB" rule in Norton Internet Security package, suddenly my Windows network became visible.  Thanks to the tip re "smbtree" I now have been able to locate and set up my printers - and they are working.

The only thing that I cannot do is access my Linux machine from any of my Windows machine (I cannot access all Windows shares from the Linux machine). I can 'see' the Linux machine in My Network Places but when I try to access it Windows keeps prompting for a user name and password.  I cannot find any combination that works - is there a way to check this on the linux machine itself?

Still very impressed with Ubuntu!

Bryan

---

### Post by bryan4134 on 2006-04-23
Ahh Jason_25 may have hit on my problem.  After I installed SAMBA I have not done anything with it to set up the local shares.  Am I supposed to 'run' SAMBA somehow? How do I do that?  Thanks, Bryan

---

### Post by Jason_25 on 2006-04-23
Samba is an in-depth subject.  Generally you want to edit the /etc/samba/smb.conf file,  set up samba user accounts, and then verify permissions.

This is the wiki page.  The relevant part is the 'configuring your computer as a server' part.
[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)

Post 3 of this thread further covers setting up a server, notably a public read/write server akin to the windows simple file sharing.

[http://ubuntuforums.org/showthread.php?t=2389](http://ubuntuforums.org/showthread.php?t=2389)

---

### Post by jflash on 2006-04-23
OK, well, here's my smb.conf file below. Let me know anything else you need, cause it's probably just something I'm missing. Thanks!

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
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = [My Last Name]

# server string is the equivalent of the NT Description field
   server string = %h

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


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = user user map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

wins support = no
[homes]
   path = /home
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no
   create mode = 0700

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
   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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

[JRFDocuments]
path = /home/jflash/Documents
available = yes
browseable = yes
public = yes
writable = no
valid users = jflash fleischauer
create mask = 0700
directory mask = 0700

```

---

### Post by Jason_25 on 2006-04-23
So maybe you could read those links I posted, change your file as appropriate, and come back when you encounter any problems.  Rather than letting us do all the work for you.

---

### Post by jflash on 2006-04-23
Oh, I had missed those links. Sorry about that!

---

### Post by jflash on 2006-04-23
OK, I have everything set up (seemingly) correctly, but I have one problem: My Ubuntu box can see and control files on both itself and the XP Box. However, the XP box can see both itself and the Ubuntu box, but it can't access the Ubuntu box. Any ideas?

---

### Post by bryan4134 on 2006-04-24
Again we seem to be at exactly the same point!!  I also can access everything except my Ubuntu box from any windows machine.  When I click on the Ubuntu icon I am prompted for login and password - I enter the only login / password I have set on my Ubuntu machine but it does not work.  So back to the drawing board.  Let me know if you solve this.   Bryan

---

### Post by bryan4134 on 2006-04-24
FINALLY!!!  Done it.....  You need to set a user up via smbpasswd.  Here's how I did it..

Open terminal window (following is my transcript...)

bryan4134@Sony_Ubuntu:~$ sudo -s -H
Password:

root@Sony_Ubuntu:/home/bryan4134# sudo smbpasswd -a bryan4134
New SMB password:
Retype new SMB password:

root@Sony_Ubuntu:/home/bryan4134# sudo /etc/init.d/samba reload
 * Reloading /etc/samba/smb.conf (smbd only)...                          [ ok ]
root@Sony_Ubuntu:/home/bryan4134#

The go to windows machine, click on Ubuntu machine icon and login - it worked for me.

BTW you also have to make changes to smb.conf as detailed in the Wiki setting up SAMBA document relating to File Shares - here's the link..

[https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29](https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29)

Hope this helps...  Bryan

---

### Post by Zhukov on 2006-04-24
Define the workgroup and add this to your samba conf:

############################# ADICIONADO A UNHA
interfaces = 192.168.0.0/255.255.255.0 127.0.0.1
bind interfaces only = Yes
netbios name = FANTASMAS
socket options = TCP_NODELAY IPTOS_LOWDELAY
local master = yes
os level = 65
domain master = yes


Note:
Set the ip range to suit yours, as well as the NETBIOS (use the same as the workgroup name)
The os level defines this machine as the "boss" because Windows machines can only go as high as 32.

This solves the "connection problem" with the Windows machines.

---

### Post by jflash on 2006-04-24
I'll try what you suggested, but I'm getting a different error:

```
\\Johnsroom is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.
```

UPDATE: I tried both what bryan and what zhukov suggested, and neither worked. Any other ideas?

BTW, the error above is what I get when I try to connect to the Ubunut box from the XP box.

---

### Post by Iowan on 2006-04-25
Username is the same on the XP and Ubuntu box?

---

### Post by jflash on 2006-04-25
Uh, no. Besides, in XP, don't remote users connect to file sharing through the guest account?

---

### Post by Iowan on 2006-04-25
Dunno about XP (not THAT sure about Samba), but > # "security = user" is always a good idea. [COLOR="Red"]This will require a Unix account
# in this server for every user accessing the server[/COLOR]. See
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.I also wonder if these shouldn't be on separate lines:
 >   security = user user map = /etc/samba/smbusers and >    passdb backend = tdbsam guest
**testparm** had no issues?  
Having already plead ignorance, I suspect the guest account would work only if a guest account were set and **guest ok = yes** is used.

---

### Post by daWabbit on 2006-04-25
I'm in somewhat of the same predicament. My warty box is fine, but the two Breezy boxes are not. They cannot see shared files and folders, nor will the other computers let me log on. 

Here's my output from smbtree;

jack@dancingotter:~$ smbtree
Password:
OTTERSHOUSE
        \\SERENITY
                \\SERENITY\BJC-250              Canon Bubble-Jet BJC-250
                \\SERENITY\CD Drive (D)
                \\SERENITY\print$               Printer Drivers
                \\SERENITY\Documents
                \\SERENITY\IPC$                 Remote IPC
                \\SERENITY\My Documents
        \\LUCY                          lucy server (Samba 3.0.7-Ubuntu)
                \\LUCY\ADMIN$           IPC Service (lucy server (Samba 3.0.7-Ub untu))
                \\LUCY\IPC$             IPC Service (lucy server (Samba 3.0.7-Ub untu))
                \\LUCY\print$           Printer Drivers
        \\HAIRBALL                      hairball server (Samba, Ubuntu)
                \\HAIRBALL\ADMIN$               IPC Service (hairball server (Sa mba, Ubuntu))
                \\HAIRBALL\IPC$                 IPC Service (hairball server (Sa mba, Ubuntu))
                \\HAIRBALL\jack
                \\HAIRBALL\print$               Printer Drivers
        \\DANCINGOTTER                  dancingotter server (Samba, Ubuntu)
                \\DANCINGOTTER\ADMIN$           IPC Service (dancingotter server  (Samba, Ubuntu))
                \\DANCINGOTTER\IPC$             IPC Service (dancingotter server  (Samba, Ubuntu))
                \\DANCINGOTTER\/home/jack
                \\DANCINGOTTER\print$           Printer Drivers

We can print from anywhere. Just not share files. When I go to config networking the asssignment to the Windows workgroup will not take.  There is no domain. Just the workgroup. 

This is probably trivial for some of you, but even though I've dabbled in Linux since RH 5.2, and always had at least one Linux machine running since then. it has me flummoxed. 

I'll follow this thread as it seems you folks are headed toward a solution that might help me, as well. 

Thanks to all.

Jack

---

### Post by Ruler on 2006-05-11
Hey,

Dont know if any of you guys are still having problems, but if you cant access your windows share with samba; getting "smb:/// is not a valid location" or something tho that effect then what you need to do is install the libgnomevfs2-extra package.

```

sudo apt-get install libgnomevfs2-extra 

```
and like magic it works, (well it did for me anyway)

Hope this is helpful to someone.

Cheers

---

### Post by jaxson on 2006-05-17
Ahh thx Ruler.. I was having that problem. Had to mount it from console each time I wanted to use a windows share in dapper. Not sure why I lost the vfs2 extras.. since it was working before the dapper dist-upgrade. *shrug* Fixed samba for me anyway. :)

---

### Post by mad_dog369 on 2006-05-18
hello, 
i am only new to linux (ubunu) and i love it but i am having trouble useing the network, i can brouse the internet and ping my windows pc but cannot share files. when i try to view shared file with either pc it always comes up asking for a username and password, i have tried all the usernames and passwords that i know of on my systems but still i can't access the files. please help.

---

### Post by Iowan on 2006-05-18
mad_dog369:
You might want to start your own thread if you don't find the answer after searching the forum (start with **share files**).

---

### Post by Doghouse on 2006-05-18
Just a side note.  For those of you using wireless routers running dhcp you might want to mac filter and static map the addresses.  Also, if you can.. enable wep encryp.  Unless of course you don't mind your teen age hack next door getting free internet from you..... or checking out those pics you really don't want him to see on your xp box.

I'ts easy to set up so no reason not to.  Also I wouldn't disable firestarter unless your running at least the basic rules on your router and you've enabled the above mentioned.  If you do have a breach your buntu box will be totally exposed to a multitude of attacks.  Just set a rule to allow all in and outbound to a specific ip... prefferable one you have mac filtered and set static.  This should let your network shares / printing remain intact.


$02.


-K

---

