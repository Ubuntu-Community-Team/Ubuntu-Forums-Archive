---
title: "Gammu sms daemon SMS message not stored on database"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by arturo322 on 2011-09-29
Hi, I just did a reformat on my pc,

previously i had installed gammu, wammu and gammu-smsd on my laptop and have it fully working along mysql running on Xampp(Lampp) as my database backend

I did all my coding and testing on my laptop but then i migrated my source codes on my pc which is running on mysql-server mysql-client apache2

Gammu is successfully installed without errors i can retrive all my message on my inbox via the command

$gammu --getallsms

but the message is not stored in the database when i use

$gammu-smsd -d
$gammu-smsd

the thing is I left my gammu-smsd running and texted multiple messages on the sim card on the gsm modem but the message remained stored in the simcard and not on the database


this is my gammu-smsdrc file 

# Configuration file for Gammu SMS Daemon

# Gammu Library configuration , see gammurc(5)
[gammu]
# Please configure this!
port = /dev/null
connection = at
# Debugging
#logformat = textall

# SMSD configuration, see gammu-smsdrc(5)
[smsd]
Service = mysql
PIN = 1234
Logfile = syslog
User = root
Password = ""
PC = localhost
Database = smsd

I also configured my gammu well 

$gammu --identify

Device : /dev/ttyUSB0
Manufacturer : huawei
Model : unknown (E1552)
Firmware : 11.608.10.00.00
IMEI : 353143034056318
SIM IMSI : 515022205755645


and when i run gammu-smsd and texted message on the simcard on the gsm modem

what i see is

rmbv@rmbv-BAD-INDEX:~$ gammu-smsd
| <<<< Blinking cursor


Have i done some mistakes on configuring my gammu or perhaps it has compatibility problems with mysql-server mysql-client apache2

and unlike my laptop
i did not make a symbolic link on my mysql.sock because im not using xampp on my pc


Hope you can help me with my concern thank you 

Just reposted from installation and upgrade category thank you

---

