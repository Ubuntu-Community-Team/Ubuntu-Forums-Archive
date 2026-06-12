---
title: "Gammu Version Compatibilities"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by arturo322 on 2011-02-07
Hi im Art and I'm currently taking my thesis, and would require me to use Gammu SMS Daemon. I downloaded Wammu,and Gammu SMS Daemon using the ubuntu software manager, and downloaded gammu again using apt-get


i configured my gammu properly and i am currently able to send sms using gammu command

arturo322@arturo322-K42F:~$ gammu --identify
Device               : /dev/ttyUSB0
Manufacturer         : huawei
Model                : unknown (E1552)
Firmware             : 11.608.10.00.00
IMEI                 : 353143034056318
SIM IMSI             : 515020303139038

arturo322@arturo322-K42F:~$ gammu --version
[Gammu version 1.27.92 built 06:14:48 on May 10 2010 using GCC 4.4]

Copyright (C) 2003 - 2010 Michal Cihar <michal@cihar.com> and other authors.

License GPLv2: GNU GPL version 2 <http://creativecommons.org/licenses/GPL/2.0/>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Check <http://wammu.eu/gammu/> for updates.


arturo322@arturo322-K42F:~$ gammu-smsd -v
Gammu-smsd version 1.27.92
Built 06:14:38 on May 10 2010 using GCC 4.4
Compiled in features:
OS support:
  - SHM
  - DAEMON
  - PID
  - ALARM
  - GETOPT
  - GETOPT_LONG
  - SYSLOG
Backend services:
  - NULL
  - FILES
  - MYSQL
  - POSTGRESQL
  - DBI

Copyright (C) 2003 - 2010 Michal Cihar <michal@cihar.com> and other authors.

License GPLv2: GNU GPL version 2 <http://creativecommons.org/licenses/GPL/2.0/>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Check <http://wammu.eu/gammu/> for updates.

arturo322@arturo322-K42F:~$ gammu-smsd
gammu-smsd[7425]: Database structure is from newer Gammu version
gammu-smsd[7425]: Initialisation failed, stopping Gammu smsd: Unknown error. (UNKNOWN[27])
Failed to run SMSD: Unknown error.

this was my error...


[smsd]
Service = mysql
PIN = 1234
LogFile = syslog
User = root
Password = ""
PC = localhost
Database = smsd


this was my gammu-smsd file...

BTW i used xampp/lampp and its MySQL for database...


can someone help me here please... im a little new to gammu sms daemon. I had read the manual. But still a little confusing.. did i miss something or have i configured something wrong?

---

### Post by alexfish on 2011-02-07
hi

not sure 
but can try looking at the versions of installed parts in synaptic
filter with gammu
had a problem some time ago of similar , but this was caused by downloading (for upgrade) from separate site , ended up un-installing , then reinstall so all parts of gammu (version matched) , all via synaptic

could also run updates from the terminal , see if anything shows

```
sudo apt-get update
```

---

### Post by arturo322 on 2011-02-07
arturo322@arturo322-K42F:~$ sudo apt-get update
[sudo] password for arturo322: 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en              
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_PH       
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_PH
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_PH       
Ign [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner Translation-en_PH           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_PH 
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_PH 
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_PH   
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_PH           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_PH
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_PH
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_PH
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_PH
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,061B]                  
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates Release                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick/universe Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Fetched 2,677B in 3s (690B/s)
Reading package lists... Done
arturo322@arturo322-K42F:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
arturo322@arturo322-K42F:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
arturo322@arturo322-K42F:~$ gammu-smsd
gammu-smsd[7685]: Database structure is from newer Gammu version
gammu-smsd[7685]: Initialisation failed, stopping Gammu smsd: Unknown error. (UNKNOWN[27])
Failed to run SMSD: Unknown error.
Heres what I got no updates for gammu no upgrades also. and still have the same error

---

### Post by alexfish on 2011-02-07
The first part of error from SMSD
> ammu-smsd[7425]: Database structure [COLOR=Blue]is from newer Gammu version[/COLOR]had asked if all parts of the gammu installation the same
see screen shot , note , this screen shot does not have wammu installed

if every thing checks out , other possible cause could be libusb , but check all versions first
if libusb checks out need question if SMDS is as says it is, as regards the installed files, sql , etc can have a look at this thread
[http://ubuntuforums.org/showthread.php?t=1364499](http://ubuntuforums.org/showthread.php?t=1364499)
see what happens

---

### Post by arturo322 on 2011-02-07
i have no idea of the latest version but what im currently using is 
Gammu-smsd version 1.27.92

---

### Post by alexfish on 2011-02-07
> **arturo322 said:**
> i have no idea of the latest version but what im currently using is 
Gammu-smsd version 1.27.92

Note from the screen shot 1.27.92-3 all parts should be the same , IE the -3
your -3 may differ from mine, view these in synaptic package manager

have updated previous post , t also check SQL , there is a link there
Think SQL more likely to be the problem, check the debug file as per the link

---

### Post by arturo322 on 2011-02-07
Okay i checked the synaptic package manager and I got the same with the screen shot literally the same.
PS. I used MySQL of lampp/xampp could this be possibly an issue?

---

### Post by alexfish on 2011-02-08
need to check your log file as requested RE:link:
for a line highlighted in blue
> Configuring Gammu SMSD...
SHM token: 0xffffffffce025713 (-838707437)
PIN code is "1234"
commtimeout=30, sendtimeout=30, receivefrequency=0, resetfrequency=0, checksecurity=1
deliveryreport = sms
phoneid = 
[COLOR=Blue]Database structures version:[COLOR=Red] 11[/COLOR], SMSD current version: [COLOR=Red]10[/COLOR][/COLOR]
DataBase structures are from higher Gammu version
Please update this client application
Initialisation failed, stopping Gammu smsd (Unknown error.:27)
the version numbers are in red :can confirmif version numbers different then smsd/sql is the problem : Can confirm

---

### Post by arturo322 on 2011-02-10
Where can i find the log file please im a total noob of this...
my log name is syslog
so i typed

#whereis syslog

this is what I got
syslog: /usr/include/syslog.h /usr/share/man/man2/syslog.2.gz /usr/share/man/man3/syslog.3.gz

---

### Post by arturo322 on 2011-02-12
Uhm Bump?
or maybe i have wrong procedures of installing and setting up gammu and gammu-smsd because some of my apps were downloaded on ubuntu software manager and some were apt-get? you think this would be a case?

---

### Post by arturo322 on 2011-02-12
ok gammu is now working and running but it gives me error

gammu-smsd[3111]: Error code: 1054, Error: Unknown column 'Signal' in 'field list'

how should i fix this issue :D thanks for the previous help really appreciated it, i just modified the gammu table in mysql changed version to 11

---

