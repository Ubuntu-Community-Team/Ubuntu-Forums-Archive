---
title: "Sharing EIT data with another source?"
date: 2008-12-14
forum: Mythbuntu
---

### Post by uMuppet on 2008-12-14
Is there a program or script that will allow me to share EIT data from my satellite card with my analogue card?  

I can see the data in the MySQL database in the "programs" table and I've written a script to share the data with the analogue channels but the script has to run every time new program data is added to the database and I can't find a way to do this.  When does the satellite look for new data?

---

### Post by ian dobson on 2008-12-15
Hi,

I imagine you'll need to use a stored procedure/event thats run whenever data is inserted into the program db. Have a look here:- [http://dev.mysql.com/doc/refman/5.1/en/stored-routines.html](http://dev.mysql.com/doc/refman/5.1/en/stored-routines.html)

Or maybe here [http://www.digitalpropulsion.org/Programming/Triggers_in_MySQL_5_0](http://www.digitalpropulsion.org/Programming/Triggers_in_MySQL_5_0)

Or maybe just try setting the same XMLID for the "same" channels in the channels database, that "should" work.

Regards
Ian Dobson

---

### Post by uMuppet on 2008-12-16
EIT or over air data does not use xmlids (or at least not in New Zealand) but I found that if I just ran the script I wrote once a day it will keep the data up to date.  So I will put this script in my /etc/cron.daiy/ folder

It creates a temporary table in MySQL, copies all the already downloaded program data for satellite channel "Triangle" with a channelid of 3035 to it, changes the channelid to 1001 (the same as the analogue channel "Triangle") and copies it back to the program table in the database. 

 
```

#!/usr/bin/env python

import MySQLdb

#Mysql login info
mysqlHost = 'localhost'
mysqlUsername = 'root'
mysqlPassword = ''
mysqlDatabase = 'mythconverg'


#Analogue channel ids
channelid1 = 1001
channelid2 = 1002
channelid3 = 1003
channelid4 = 1004
channelid8 = 1008

#Satellite Channel Ids
channelida = 3035 
channelidb = 3036 
channelidc = 3920
channelidd = 3921
channelidh = 3925


# Connect to MySQL Database    
db = MySQLdb.connect ( host = mysqlHost, 
			user = mysqlUsername, 
			passwd = mysqlPassword, 
			db = mysqlDatabase )

# create a cursor to pass the MySQL commands to
cursor = db.cursor()

#Create TempTable for changing entries in
cursor.execute("CREATE TABLE   `mythconverg`.`TempTable` (`chanid` int(10) unsigned NOT NULL default '0',  `starttime` datetime NOT NULL default '0000-00-00 00:00:00',  `endtime` datetime NOT NULL default '0000-00-00 00:00:00',  `title` varchar(128) NOT NULL default '',  `subtitle` varchar(128) NOT NULL default '',  `description` text NOT NULL,  `category` varchar(64) NOT NULL default '',  `category_type` varchar(64) NOT NULL default '',  `airdate` year(4) NOT NULL default '0000',  `stars` float NOT NULL default '0',  `previouslyshown` tinyint(4) NOT NULL default '0',  `title_pronounce` varchar(128) NOT NULL default '',  `stereo` tinyint(1) NOT NULL default '0',  `subtitled` tinyint(1) NOT NULL default '0',  `hdtv` tinyint(1) NOT NULL default '0',  `closecaptioned` tinyint(1) NOT NULL default '0',  `partnumber` int(11) NOT NULL default '0',  `parttotal` int(11) NOT NULL default '0',  `seriesid` varchar(40) NOT NULL default '',  `originalairdate` date default NULL,  `showtype` varchar(30) NOT NULL default '',  `colorcode` varchar(20) NOT NULL default '',  `syndicatedepisodenumber` varchar(20) NOT NULL default '',  `programid` varchar(40) NOT NULL default '',  `manualid` int(10) unsigned NOT NULL default '0',  `generic` tinyint(1) default '0',  `listingsource` int(11) NOT NULL default '0',  `first` tinyint(1) NOT NULL default '0',  `last` tinyint(1) NOT NULL default '0',  `audioprop` set('STEREO','MONO','SURROUND','DOLBY','HARDHEAR','VISUALIMPAIR') NOT NULL,  `subtitletypes` set('HARDHEAR','NORMAL','ONSCREEN','SIGNED') NOT NULL,  `videoprop` set('HDTV','WIDESCREEN','AVC') NOT NULL,  PRIMARY KEY  (`chanid`,`starttime`,`manualid`),  KEY `endtime` (`endtime`),  KEY `title` (`title`),  KEY `title_pronounce` (`title_pronounce`),  KEY `seriesid` (`seriesid`),  KEY `id_start_end` (`chanid`,`starttime`,`endtime`),  KEY `program_manualid` (`manualid`),  KEY `previouslyshown` (`previouslyshown`),  KEY `programid` (`programid`,`starttime`),  KEY `starttime` (`starttime`)) ENGINE=MyISAM DEFAULT CHARSET=latin1");



cursor.execute("TRUNCATE TABLE TempTable;")
#ONE
cursor.execute("INSERT INTO TempTable SELECT * FROM program WHERE chanid='%s'" % (channelida))
cursor.execute("DELETE from program WHERE chanid='%s'" % (channelid1))
cursor.execute("UPDATE TempTable SET chanid='%s' WHERE chanid='%s'" % (channelid1, channelida))
#TV2
cursor.execute("INSERT INTO TempTable SELECT * FROM program WHERE chanid='%s'" % (channelidb))
cursor.execute("DELETE from program WHERE chanid='%s'" % (channelid2))
cursor.execute("UPDATE TempTable SET chanid='%s' WHERE chanid='%s'" % (channelid2, channelidb))
#TV3
cursor.execute("INSERT INTO TempTable SELECT * FROM program WHERE chanid='%s'" % (channelidc))
cursor.execute("DELETE from program WHERE chanid='%s'" % (channelid3))
cursor.execute("UPDATE TempTable SET chanid='%s' WHERE chanid='%s'" % (channelid3, channelidc))
#C4
cursor.execute("INSERT INTO TempTable SELECT * FROM program WHERE chanid='%s'" % (channelidd))
cursor.execute("DELETE from program WHERE chanid='%s'" % (channelid4))
cursor.execute("UPDATE TempTable SET chanid='%s' WHERE chanid='%s'" % (channelid4, channelidd))
#Maori
cursor.execute("INSERT INTO TempTable SELECT * FROM program WHERE chanid='%s'" % (channelidh))
cursor.execute("DELETE from program WHERE chanid='%s'" % (channelid8))
cursor.execute("UPDATE TempTable SET chanid='%s' WHERE chanid='%s'" % (channelid8, channelidh))

cursor.execute("INSERT INTO program SELECT * FROM TempTable")


cursor.execute('DROP TABLE IF EXISTS TempTable')

cursor.close()
db.close()








```

---

