---
title: "Mythfilldatabase  - Problems"
date: 2014-01-04
forum: Mythbuntu
---

### Post by ylafont on 2014-01-04
A few days ago I began having problems manually updating the MythTv database.   Ususually, i run  the following 

mythfilldatabase --refresh 14 --file --sourceid 1 --xmlfile ./xmltv.xml

A few days, ago, i began receving the following error:


2014-01-03 06:01:48.891761 I  Marking repeats.
2014-01-03 06:01:48.909281 I      Found 0
2014-01-03 06:01:48.909297 I  Unmarking new episode rebroadcast repeats.
2014-01-03 06:01:48.909835 I      Found 0
2014-01-03 06:01:48.997834 I  Marking episode first showings.
2014-01-03 06:01:49.332394 I      Found 3041
2014-01-03 06:01:49.332402 I  Marking episode last showings.
2014-01-03 06:01:49.663863 I      Found 3027
2014-01-03 06:01:49.667263 I
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2014-01-03 06:01:49.674889 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-01-03 06:01:49.675132 E  Connection to master server timed out.
                        Either the server is down or the master server settings
                        in mythtv-settings does not contain the proper IP address


2014-01-03 06:01:49.675146 E  Error rescheduling MATCH 0 0 0 - MythFillDatabase in ScheduledRecording::SendReschedule
2014-01-03 06:01:49.675196 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-01-03 06:01:49.675254 E  Connection to master server timed out.
                        Either the server is down or the master server settings
                        in mythtv-settings does not contain the proper IP address


2014-01-03 06:01:49.675303 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-01-03 06:01:49.675344 E  Connection to master server timed out.
                        Either the server is down or the master server settings
                        in mythtv-settings does not contain the proper IP address


2014-01-03 06:01:49.675352 N  mythfilldatabase run complete.

I know the backend is up. 
I have also verfied the mythtv config file
[EMAIL="xbmc@PlexOne:~/.mythtv"]xbmc@PlexOne:~/.mythtv[/EMAIL]$ cat config.xml
<Configuration>
<LocalHostName>my-unique-identifier-goes-here</LocalHostName>
<Database>
<PingHost>1</PingHost>
<Host>127.0.0.1</Host>
<UserName>mythtv</UserName>
<Password>password</Password>
<DatabaseName>mythconverg</DatabaseName>
<Port>3306</Port>
</Database>
<WakeOnLAN>
<Enabled>0</Enabled>
<SQLReconnectWaitTime>0</SQLReconnectWaitTime>
<SQLConnectRetry>5</SQLConnectRetry>
<Command>echo 'WOLsqlServerCommand not set'</Command>
</WakeOnLAN>

Checked /etc/mysql./my.cnf
[client]
port	 = 3306
socket	 = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket	 = /var/run/mysqld/mysqld.sock
nice	 = 0

[mysqld]
user	 = mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket	 = /var/run/mysqld/mysqld.sock
port	 = 3306
basedir	 = /usr
datadir	 = /var/lib/mysql
tmpdir	 = /tmp
lc-messages-dir	= /usr/share/mysql
skip-external-locking

bind-address	 = 127.0.0.1 <- this was commented out
bind-address	 = 192.168.1.2 <- added this.


verified MySQl Config
/etc/mysql/my/cnf
[client]
port	 = 3306
socket	= /var/run/mysqld/mysqld.sock

and connected sql via the cli wiht 
mysql -u your_magic_username_for_mysql --password=your_magic_password mythconverg -h 127.0.0.1

Does anyone have a clue?

---

