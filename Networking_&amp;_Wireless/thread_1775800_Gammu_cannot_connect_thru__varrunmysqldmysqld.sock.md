---
title: "Gammu cannot connect thru  /var/run/mysqld/mysqld.sock"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by arturo322 on 2011-06-05
Help! I've been trying to configure my gammu-smsd to be able to connect to mysql


my gammu-smsdrc contains the following data

# Configuration file for Gammu SMS Daemon

# Gammu library configuration, see gammurc(5)
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
LogFile = syslog
User = root
Password = ""
PC = localhost
Database = smsd


Here is the commands and errors that were shown

Username@PcName:/opt/lampp$ gammu-smsd
gammu-smsd[3090]: Error connecting to database!
gammu-smsd[3090]: Error code: 2002, Error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
gammu-smsd[3090]: Initialisation failed, stopping Gammu smsd: Unknown error. (UNKNOWN[27])
Failed to run SMSD: Unknown error.

---

### Post by arturo322 on 2011-06-05
I would like to add that im using lampp as my local server thank you. would making a symbolic link to sockets of lampp help here? im not quite sure of the codes involved and the directores involved can you help me please T_T

---

### Post by oskandaria on 2012-07-08
Hi Artur you may try this one, it's work for me ..

sudo mkdir /var/run/mysqld
sudo ln -s /opt/lampp/var/mysql/mysql.sock /var/run/mysqld/mysqld.sock

source:  [http://www.arejae.com/blogv2/](http://www.arejae.com/blogv2/)

---

