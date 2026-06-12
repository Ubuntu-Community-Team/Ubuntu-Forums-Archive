---
title: "filesharing strange problems!!!"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by kwstas on 2010-02-26
hi guys,

here is a strange problem...

after the installation of karmic from the livecd i used the synaptic to install "samba".
i made a file "downloads" shared with all options ticked and i also installed my printer also shared.
so i went on my other pc wich has xp installed and eventhough it detects the "ubuntu machine", it can't connect to it!
i made a lot of changes to solve this but nothing happened so i uninstalled anything that had to do with the "samba" name from synaptic.
i thought i better try to make the network as most instructions note on google so i firstly installed the "nautilus-share" and then right-clicked on a file that i wanted to share. after the prompt that i needed the samba i just accepted to install it.
i made the file "downloads" shared again with all options ticked and worked! my "xp" pc found immediatelly the file "downloads" and i could use it.
after this i noticed that the "ubuntu machine" was in a different group(workgroup) that my "xp" pc (mshome) so i had to change it.
i run the gedit for smb.conf and i just changed from workgroup to mshome.
my problems started from this point!
from ubuntu i was still watching the "workgroup"!
i finally corrected this but then i had to check if the printer was also sharable from "xp".
"xp" detected the "ubuntu" and the shared file "downloads" but when i tried to double click on "ubuntu machine" to see my shared files, it gave me the message that i have no permissions!
that was strange! i tried to see if i still have access to the "downloads" file and i had!
i tried to make a second shared file in "ubuntu machine" which i did again with all sharing options ticked. this time the "xp" couldn't detect this file!
i though i should take a look at the smb.conf for my shared files......none there!!!
i am so confused with this!

PLEASE any help would be really appreciated

---

### Post by kwstas on 2010-02-27
good news!

from xp i searched the for the linux ip from network places and found every single shared file! i even made the printer shared successfully. but that wasn't all...
next day that i switched them on, i couldn't have access in linux again!
the ip's were changed!
so i manually set the ip's on both systems from network manager and now it seems there is no more problem!

i just can't still have access in my "ubuntu-kwstas" which is found under "mshome" group!!!
and now i can't even find it under "network" of ubuntu!

---

### Post by cariboo on 2010-03-01
Could you run in a terminal:

```
smbclient -L<ip_address -%H
```

on the computer that **ubuntu-kwstas** is located and paste the output in your next post. It might also be a good idea to run:

```
testparm
```

on the same computer. The first command prints out a share list on the computer it is run on, and the second command checks /etc/samba/smb.conf for errors.

---

### Post by Morbius1 on 2010-03-01
Since you used Nautilus-share you also might want to post the output of this command:

**net usershare info**

---

### Post by kwstas on 2010-03-08
hi,

here is the "testparm"

> Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[linuxsharing]"
Processing section "[faxin]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = MSHOME
    server string = %h
    interfaces = 127.0.0.0/8, eth0, 192.168.1.5, 192.168.1.6
    security = SHARE
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
    read only = No
    guest ok = Yes

[linuxsharing]
    path = /home/kwstas/linuxsharing
    read only = No
    guest ok = Yes

[faxin]
    path = /home/kwstas/faxin
    valid users = kwstas, nobody
    read only = No



..and this the "net usershare info"

> [faxin]
path=/home/kwstas/faxin
comment=
usershare_acl=Everyone:F,
guest_ok=y

[ergostasia]
path=/home/kwstas/linuxsharing/ERGOSTASIA
comment=
usershare_acl=Everyone:F,
guest_ok=y

[public]
path=/home/kwstas/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

[&#949;&#960;&#953;&#963;&#951;&#956;&#945;]
path=/home/kwstas/linuxsharing/&#917;&#928;&#921;&#931;&#919;&#924;&#913;
comment=
usershare_acl=Everyone:F,
guest_ok=y

[documents]
path=/home/kwstas/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y


about the command "smbclient -L<ip_address -%H"
> bash: ip_address: No such file or directory
i bet i haven't given the command right so i tried to put the ip of my ubuntu-kwstas like "smbclient -L<192.168.1.5 -%H" but gave me the same.

---

### Post by Morbius1 on 2010-03-08
First, there are two completely different ways to use samba to share folders: Nautilus-share and Classic-share. They define the share in two completely different places: /var/lib/samba/usershare vs. smb.conf. You're using both methods. That can be done if you're careful but in this case both methods are overlapping on the same target folders and in one case you're defining it with opposite permissions.

What I would suggest , just to clean this up a bit, is to remove the following shares from smb.conf:
> [linuxsharing]
    path = /home/kwstas/linuxsharing
    read only = No
    guest ok = Yes> [faxin]
    path = /home/kwstas/faxin
    valid users = kwstas, nobody
    read only = No                      The only other oddity is the following line in smb.conf:
>      security = SHAREShare level security in Samba hasn't been used since Ronald Reagan was president so unless there is a complelling reason why you did that I would set it back to the default by commenting it out:

From this:
>      security = SHARETo this:
> #     security = SHAREThen I would restart samba: **sudo service samba restart**

Originally you had this working when you had different workgroups names and the only thing you had shared was /home/kwstas/Documents, right? Maybe the rest of these shares are being hampered by linux permissions and not samba. Please post the output of the following command so we can determine the permissions on the target directories:

[B]ls -al /home/kwstas/linuxsharing

[/B]It could be that samba is allowing guests but linux is not.

---

### Post by kwstas on 2010-03-08
hi morbius1,

well i've tried a lot to make this work so the "security=share" could be surely one of them...

> Originally you had this working when you had different workgroups names and the only thing you had shared was /home/kwstas/Documents, right? - **correct!**

here is the "[B]ls -al /home/kwstas/linuxsharing"
[/B]
> total 20
drwxrwxrwx  5 kwstas kwstas 4096 2010-03-08 10:56 .
drwxr-xr-x 54 kwstas kwstas 4096 2010-03-08 18:10 ..
drwxrwxrwx 21 kwstas kwstas 4096 2009-07-02 21:18 ERGOSTASIA
drwx------  5 kwstas kwstas 4096 2010-03-02 21:09 Windows XP Crack    :))
drwxrwxrwx  3 kwstas kwstas 4096 2010-03-08 10:59 &#917;&#928;&#921;&#931;&#919;&#924;&#913;


---

### Post by Morbius1 on 2010-03-08
Well, the permissions on **/home/kwstas/linuxsharing **look OK**, **although I'm not exactly sure what samba will do with: /home/kwstas/linuxsharing/[COLOR=Blue]&#917;&#928;&#921;&#931;&#919;&#924;&#913;

[COLOR=Black]Did the changes I suggested make any difference at all?[/COLOR]
[/COLOR]

---

### Post by kwstas on 2010-03-08
i'm afraid there is no change...

still the same. xp detects the "ubuntu" but cannot access it.

---

### Post by Morbius1 on 2010-03-08
Let's see if we can generate some error messages. Post the output from the following:

From Ubuntu:

Open **Terminal **
Type **smbtree**

From WinXP

Open **Command Prompt** ( not run - command prompt )
Type **net view**
Type **net view \\ubuntu_machine_name**

net view should show you all the machines on the network from WinXP's perspective. One of those machine should be your ubuntu_machine_name.

---

### Post by kwstas on 2010-03-08
ok!

from smbtree(after i installed it)

> MSHOME
    \\KWSTAS-DESKTOP-L        kwstas-desktop-linux
        \\KWSTAS-DESKTOP-L\faxin              
        \\KWSTAS-DESKTOP-L\ergostasia         
        \\KWSTAS-DESKTOP-L\public             
        \\KWSTAS-DESKTOP-L\&#949;&#960;&#953;&#963;&#951;&#956;&#945;     
        \\KWSTAS-DESKTOP-L\documents          
        \\KWSTAS-DESKTOP-L\FaxPrinter         FaxPrinter
        \\KWSTAS-DESKTOP-L\XEROX_Phaser_3100MFP    XEROX Phaser 3100MFP
        \\KWSTAS-DESKTOP-L\IPC$               IPC Service (kwstas-desktop-linux)
        \\KWSTAS-DESKTOP-L\print$             Printer Drivers
    \\ANDYTSOB               ANDY
        \\ANDYTSOB\&#919; &#956;&#959;&#965;&#963;&#953;&#954;&#942; &#956;&#959;&#965;    
        \\ANDYTSOB\Address Book       
        \\ANDYTSOB\sd                 
        \\ANDYTSOB\&#917;&#954;&#964;&#965;&#960;&#969;&#964;&#942;&#962;2    Microsoft XPS Document Writer
        \\ANDYTSOB\&#917;&#954;&#964;&#965;&#960;&#969;&#964;&#942;&#962;    &#913;&#960;&#959;&#963;&#964;&#959;&#955;&#942; &#963;&#964;&#959; OneNote 2007
        \\ANDYTSOB\&#914;&#913;&#931;&#919;           
        \\ANDYTSOB\koina mousikh      
        \\ANDYTSOB\print$             &#928;&#961;&#959;&#947;&#961;&#940;&#956;&#956;&#945;&#964;&#945; &#959;&#948;&#942;&#947;&#951;&#963;&#951;&#962; &#949;&#954;&#964;&#965;&#960;&#969;&#964;&#974;&#957;
        \\ANDYTSOB\&#932;&#945; &#941;&#947;&#947;&#961;&#945;&#966;&#940; &#956;&#959;&#965;    
        \\ANDYTSOB\SharedDocs         
        \\ANDYTSOB\IPC$               &#913;&#960;&#959;&#956;&#945;&#954;&#961;&#965;&#963;&#956;&#941;&#957;&#959; IPC
        \\ANDYTSOB\Outlook Express    


**net view gave me an error "53"!**

---

### Post by Morbius1 on 2010-03-08
Change the name of of the Ubuntu machine name in smb.conf to something less than or equal to 15 characters long.

You can do that by adding the following line to smb.conf:

```
netbios name = KWSTAS-DESKTOP
```or better yet:

```
netbios name = KWSTAS-DTOP
```Save the file and restart samba: **sudo service samba restart.**

---

### Post by kwstas on 2010-03-08
:popcorn:

WORKED!
thank you so much! what a small thing to make so much trouble!

have a nice week my friend!

---

### Post by kwstas on 2010-03-09
it seems i can't print from xp to my printer in ubuntu.
i have configured my printer in CUPS which is under
[http://localhost:631/printers/XEROX](http://localhost:631/printers/XEROX)........
from the "printing" i ticked the right permissions.

i did these but no good:

> **WindowsXP Client Machine**

 
[LIST=1]
[*]Open the Control Panel
[*]Click **Printers and Faxes**
[*]Click **Add a Printer**
[*]On the first page of the Add Printer Wizard, click **Next**
[*]Choose **Add a network Printer**
[*]Choose **Connect to a printer on the internet** and type **[http://server_name:631/printers/PRINTER_NAME](http://server_name:631/printers/PRINTER_NAME)** in the text box and then click **next**
[*]On the next screen, Choose the correct driver for your printer
[*]Click **ok** to finish
[*]Right click the printer, choose **properties**, and then try to **print a test page**
[/LIST]
i put "**[http://localhost:631/printers/XEROX_name"]("http://server_name:631/printers/PRINTER_NAME")**

i changed my smb.conf:

> [printers]
    comment = All Printers
    browseable = no
    path = /var/spool/samba
    printable = yes
;    guest ok = no
;    read only = yes
    create mask = 0700
to:

> [printers]
    comment = All Printers
    browseable = yes
    path = /var/spool/samba
    printable = yes
;    guest ok = yes
;    read only = no
    create mask = 0700

so xp now finds the printer under MSHOME/KWSTAS-LDESK
but again can't find it on **"****[B][http://localhost:631/printers/XEROX_name]("http://server_name:631/printers/PRINTER_NAME")"**

[/B]if after step 5 "**Add a network Printer" **i choose the 2nd choise and put:
\\192.168.1.5\
i find the printer and add it but again i cannot print to it!

**"edit"  i don't have access in [http://localhost:631/](http://localhost:631/) from xp!**

---

### Post by kwstas on 2010-03-09
ok!

i tried to put:

[http://192.168.1.5:631/printers/xerox_name](http://192.168.1.5:631/printers/xerox_name)
instead of:
[http://server_name:631/printers/xerox_name](http://server_name:631/printers/xerox_name)

and it worked!
in "server_name" i had tried to put everything i could with no success.

i guess i'll have to set it with the specific ip address now...

---

### Post by Morbius1 on 2010-03-09
Actually, there are two ways to connect to the linux printer from Windows.
You're using http - as if the printer was on the internet. But the printer isn't on the internet it's on your intranet. It will work but there is another way. For example, one of these should work:

URL: \\WORKGROUP_NAME\MACHINE_NAME\Xerox_Printer_Name
URL: \\MACHINE_NAME\Xerox_Printer_Name
URL: \\192.168.0.100\Xerox_Printer_Name

---

### Post by kwstas on 2010-03-09
so if one of these works, i could set my machine to "auto ip address"?

> URL: \\WORKGROUP_NAME\MACHINE_NAME\Xerox_Printer_Name
URL: \\MACHINE_NAME\Xerox_Printer_Name

---

### Post by Morbius1 on 2010-03-09
If you can currently access your printer from the remote machine I wouldn't mess with anything. I was simply stating that there is an alternate way.

> "auto ip address"
I'm not familiar with that - is that on the WinXP box?

---

### Post by dannyboy79 on 2010-03-09
> **kwstas said:**
> 
**"edit"  i don't have access in [http://localhost:631/](http://localhost:631/) from xp!**

if you're trying to access the cups print server on your ubuntu machine FROM xp web browser why would you put [http://localhost:631/](http://localhost:631/) when you're on the win xp machine? do you know what localhost means? i see below you got it all squared away so that's good. sometimes just reading what you're doing and thinking first before just acting is the best way to go.

---

### Post by kwstas on 2010-03-09
>  	Quote:
 	 	 		 			 				"auto ip address" 			 		 	 	 
I'm not familiar with that - is that on the WinXP box?

from the network manager of ubuntu!
i have set a specific ip address in ipv4 settings tab.


> if you're trying to access the cups print server on your ubuntu machine FROM xp web browser why would you put [http://localhost:631/](http://localhost:631/) when you're on the win xp machine? do you know what localhost means? i see below you got it all squared away so that's good. sometimes just reading what you're doing and thinking first before just acting is the best way to go.

:) true but since this network is at work i try to find solutions as fast as i can.


> URL: \\WORKGROUP_NAME\MACHINE_NAME\Xerox_Printer_Name
URL: \\MACHINE_NAME\Xerox_Printer_Name 			 		

i tried these but don't work.
workgroup name is "mshome"
machine name is "kwstas-dtop" as we made it earlier. 

> **Re: filesharing strange problems!!!**
 		Change the name of of the Ubuntu machine name in smb.conf to something less than or equal to 15 characters long.

You can do that by adding the following line to smb.conf:

 	Code:
 	netbios name = KWSTAS-DESKTOP 
or better yet:

 	Code:
 	netbios name = KWSTAS-DTOP 


well.. it's not a big bother since xp can print now.

---

### Post by dannyboy79 on 2010-03-09
> **kwstas said:**
> i tried these but don't work.
workgroup name is "mshome"
machine name is "kwstas-dtop" as we made it earlier. 



well.. it's not a big bother since xp can print now.

most likely because your windows machine can't resolve the netbios name of your ubuntu server. do you have an internal dns server running or are you just using your LMHOSTS or HOSTS file on your win xp machine? or are you hoping your router will resolve internal machine names cause i doubt it will. your at work and your workgroup name is mshome?

---

### Post by kwstas on 2010-03-09
> do you have an internal dns server running or are you just using your LMHOSTS or HOSTS file on your win xp machine?

i'ts all greek to me i'm afraid...
i have 2 pcs both connected on a router.


>  your at work and your workgroup name is mshome?

yes! mshome is the default workgroup name in windows xp so...

---

### Post by Morbius1 on 2010-03-09
kwstas, 

After re-reading through these posts there may be another of those obscure naming rules at work here.

First, when you access the shared folder from WinXP, I assume you're doing it by Ubuntu machine name not ip address. Correct ?

Second, from your original smbtree output:
>          \\KWSTAS-DESKTOP-L\XEROX_Phaser_3100MFP    XEROX Phaser 3100MFPWhich I guess now looks like this:
>  [COLOR=Blue]        \\KWSTAS-DTOP\XEROX_Phaser_3100MFP[/COLOR]    XEROX Phaser 3100MFPRename the printer in Ubuntu to X3100MFP. Or create another instance of the printer and name it X3100MFP. There are rules on fully qualified printer names as well - I just don't remember the exact number off hand. I think it's 31 characters but I could be wrong. Yours in in excess of that:

[http://[COLOR=Black]KWSTAS-DTOP[/COLOR]]("http://%3Cfont%20color=%22Black%22%3EKWSTAS-DTOP%3C/font%3E"):631/printers/XEROX_Phaser_3100MFP = 43 characters

[http://[COLOR=Black]KWSTAS-DTOP[/COLOR]]("http://%3Cfont%20color=%22Black%22%3EKWSTAS-DTOP%3C/font%3E"):631/printers/X3100MFP = 30 characters

It's worth a shot ;)

---

### Post by kwstas on 2010-03-09
> First, when you access the shared folder from WinXP, I assume you're doing it by Ubuntu machine name not ip address. Correct ?

correct!


> Rename the printer in Ubuntu to X3100MFP. Or create another instance of the printer and name it X3100MFP. There are rules on fully qualified printer names as well - I just don't remember the exact number off hand. I think it's 31 characters but I could be wrong

of course i'm going to try this and i'll post(i'm in dual boot with xp now)

about this "[http://KWSTAS-DTOP]("http://%3cfont%20color=%22black%22%3ekwstas-dtop%3c/font%3E"):631/printers/XEROX_Phaser_3100MFP = 43 characters"
shouldn't it show me the contents if i write just "[http://KWSTAS-DTOP]("http://%3cfont%20color=%22black%22%3ekwstas-dtop%3c/font%3E"):631/"  ?
i had tried that way but nothing...
anyway i'll get back soon

---

### Post by kwstas on 2010-03-09
> After re-reading through these posts there may be another of those obscure naming rules at work here.i really appreciate this! thanks

---

### Post by Morbius1 on 2010-03-09
Actually, if everything was working correctly you should be able to open "My Computer" on WinXP and in the "Address" bar type:[COLOR=Black][B] \\KWSTAS-DTOP

[/B]It should show you all your Ubuntu shares and your printer. At that point you could just double click the printer listing to start the install process.

If it's not listed then it's either this printer name length thing ( I'm still not sure if 31 is the right limit ), the printer is not shared on Ubuntu, or the printer is not published on Ubuntu.
[/COLOR]

---

### Post by kwstas on 2010-03-09
my smbtree at the moment is:

> MSHOME
    \\KWSTAS-LDESK           kwstas-desktop-linux
        \\KWSTAS-LDESK\ergostasia         
        \\KWSTAS-LDESK\&#949;&#960;&#953;&#963;&#951;&#956;&#945;     
        \\KWSTAS-LDESK\IPC$               IPC Service (kwstas-desktop-linux)
        \\KWSTAS-LDESK\print$             Printer Drivers
    \\ANDYTSOB               ANDY


since i don't see the printer(!) which i have already made it shared in CUPS i guess i'll have to make shareable in smb.conf somehow?
here is my current smb.conf

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
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = mshome

# server string is the equivalent of the NT Description field
    server string = %h

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

    netbios name = KWSTAS-LDESK
#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
    interfaces = 127.0.0.0/8 eth0, 192.168.1.5, 192.168.1.6

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
;    encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;    passdb backend = tdbsam

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

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

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
;    printing = cups
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
#   socket options = TCP_NODELAY

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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
#    security = share
;    guest ok = no
;    guest account = nobody

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
    browseable = yes
    path = /var/spool/samba
    printable = yes
;    guest ok = yes
;    read only = no
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
    writeable = yes
    guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


```

it shows that it is shared, no? i'm loosing it!

---

### Post by Morbius1 on 2010-03-09
The default configuration for printing in samba is really just a pass-through to CUPS. CUPS not only controls your local printer but is a server as well. You shared the printer but did you publish the printer?

To Publish:

Administration > Printing > Server > Settings > Publish shared printers connected to this system

---

### Post by kwstas on 2010-03-09
> To Publish:

Administration > Printing > Server > Settings > Publish shared printers connected to this system 	  	

yes, i've done that.

i'm now trying to rename the printer but it doesn't let me! :lol:

i tried to rename it by this "printing" menu but it gives me 

> Renaming will lose history - Completed jobs will no longer be available for re-printing.

i don't care so i choose ok but still can't rename!
i tried to disable the printer but still no good...

---

### Post by Morbius1 on 2010-03-09
Can you create a new instance of the printer - this time with a different name?

---

### Post by kwstas on 2010-03-09
since i couldn't change the printer's name, i changed again my netbios name to "dlinux".
xp saw everything and i even heard the printer getting out of "sleep" but it never printed :(

i'll try for a new instance..

---

### Post by kwstas on 2010-03-09
i made a new printer "xerox" and everything went fine as last time but again it didn't print!
i see in xp that under the printer's icon says "no access allowed, can't connect". to me this means that something is wrong with the permissions in ubuntu but what else should i change?
and how comes that by giving the printer's ip address to xp, i have no problem?!

---

### Post by Morbius1 on 2010-03-09
I honestly don't know. 

You're not accessing your shared folders by IP Address and that works.

You can access the printer from XP by ip address but not by netbios name.

And I assume if you do an smbtree from ubuntu, it still doesn't show the printer?

I checked the printer related stuff in my smb.conf and it matched yours so I don't think this is a samba issue. I'm not sure what it is at the moment.

But you can at least print from WinXP . It's not the way you want it but it does work, right?

---

### Post by kwstas on 2010-03-10
good morning morbius1,

you know exactly what my situation is. since i can print is not so bad but i'll try some googling on it and if i fix it i'll post.

thanks

---

