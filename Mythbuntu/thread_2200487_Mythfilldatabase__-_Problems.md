---
title: "Mythfilldatabase  - Problems"
date: 2014-01-19
forum: Mythbuntu
---

### Post by ylafont on 2014-01-19
[COLOR=#000000]A few days ago I began having problems manually updating the MythTv database. Ususually, i run the following [/COLOR]

[COLOR=#000000]mythfilldatabase --refresh 14 --file --sourceid 1 --xmlfile ./xmltv.xml[/COLOR]

[COLOR=#000000]A few days, ago, i began receving the following error:[/COLOR]


[COLOR=#000000]2014-01-03 06:01:48.891761 I Marking repeats.[/COLOR]
[COLOR=#000000]2014-01-03 06:01:48.909281 I Found 0[/COLOR]
[COLOR=#000000]2014-01-03 06:01:48.909297 I Unmarking new episode rebroadcast repeats.[/COLOR]
[COLOR=#000000]2014-01-03 06:01:48.909835 I Found 0[/COLOR]
[COLOR=#000000]2014-01-03 06:01:48.997834 I Marking episode first showings.[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.332394 I Found 3041[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.332402 I Marking episode last showings.[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.663863 I Found 3027[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.667263 I[/COLOR]
[COLOR=#000000]================================================== =============[/COLOR]
[COLOR=#000000]| Attempting to contact the master backend for rescheduling. |[/COLOR]
[COLOR=#000000]| If the master is not running, rescheduling will happen when |[/COLOR]
[COLOR=#000000]| the master backend is restarted. |[/COLOR]
[COLOR=#000000]================================================== =============[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.674889 I MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.675132 E Connection to master server timed out.[/COLOR]
[COLOR=#000000]Either the server is down or the master server settings[/COLOR]
[COLOR=#000000]in mythtv-settings does not contain the proper IP address[/COLOR]


[COLOR=#000000]2014-01-03 06:01:49.675146 E Error rescheduling MATCH 0 0 0 - MythFillDatabase in ScheduledRecording::SendReschedule[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.675196 I MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.675254 E Connection to master server timed out.[/COLOR]
[COLOR=#000000]Either the server is down or the master server settings[/COLOR]
[COLOR=#000000]in mythtv-settings does not contain the proper IP address[/COLOR]


[COLOR=#000000]2014-01-03 06:01:49.675303 I MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)[/COLOR]
[COLOR=#000000]2014-01-03 06:01:49.675344 E Connection to master server timed out.[/COLOR]
[COLOR=#000000]Either the server is down or the master server settings[/COLOR]
[COLOR=#000000]in mythtv-settings does not contain the proper IP address[/COLOR]


[COLOR=#000000]2014-01-03 06:01:49.675352 N mythfilldatabase run complete.[/COLOR]

[COLOR=#000000]I know the backend is up. [/COLOR]
[COLOR=#000000]I have also verfied the mythtv config file[/COLOR]
[EMAIL="xbmc@PlexOne:~/.mythtv"]xbmc@PlexOne:~/.mythtv[/EMAIL][COLOR=#000000]$ cat config.xml[/COLOR]
[COLOR=#000000]<Configuration>[/COLOR]
[COLOR=#000000]<LocalHostName>my-unique-identifier-goes-here</LocalHostName>[/COLOR]
[COLOR=#000000]<Database>[/COLOR]
[COLOR=#000000]<PingHost>1</PingHost>[/COLOR]
[COLOR=#000000]<Host>127.0.0.1</Host>[/COLOR]
[COLOR=#000000]<UserName>mythtv</UserName>[/COLOR]
[COLOR=#000000]<Password>password</Password>[/COLOR]
[COLOR=#000000]<DatabaseName>mythconverg</DatabaseName>[/COLOR]
[COLOR=#000000]<Port>3306</Port>[/COLOR]
[COLOR=#000000]</Database>[/COLOR]
[COLOR=#000000]<WakeOnLAN>[/COLOR]
[COLOR=#000000]<Enabled>0</Enabled>[/COLOR]
[COLOR=#000000]<SQLReconnectWaitTime>0</SQLReconnectWaitTime>[/COLOR]
[COLOR=#000000]<SQLConnectRetry>5</SQLConnectRetry>[/COLOR]
[COLOR=#000000]<Command>echo 'WOLsqlServerCommand not set'</Command>[/COLOR]
[COLOR=#000000]</WakeOnLAN>[/COLOR]

[COLOR=#000000]Checked /etc/mysql./my.cnf[/COLOR]
[COLOR=#000000][client][/COLOR]
[COLOR=#000000]port	 = 3306[/COLOR]
[COLOR=#000000]socket	 = /var/run/mysqld/mysqld.sock[/COLOR]

[COLOR=#000000]# Here is entries for some specific programs[/COLOR]
[COLOR=#000000]# The following values assume you have at least 32M ram[/COLOR]

[COLOR=#000000]# This was formally known as [safe_mysqld]. Both versions are currently parsed.[/COLOR]
[COLOR=#000000][mysqld_safe][/COLOR]
[COLOR=#000000]socket	 = /var/run/mysqld/mysqld.sock[/COLOR]
[COLOR=#000000]nice	 = 0[/COLOR]

[COLOR=#000000][mysqld][/COLOR]
[COLOR=#000000]user	 = mysql[/COLOR]
[COLOR=#000000]pid-file	= /var/run/mysqld/mysqld.pid[/COLOR]
[COLOR=#000000]socket	 = /var/run/mysqld/mysqld.sock[/COLOR]
[COLOR=#000000]port	 = 3306[/COLOR]
[COLOR=#000000]basedir	 = /usr[/COLOR]
[COLOR=#000000]datadir	 = /var/lib/mysql[/COLOR]
[COLOR=#000000]tmpdir	 = /tmp[/COLOR]
[COLOR=#000000]lc-messages-dir	= /usr/share/mysql[/COLOR]
[COLOR=#000000]skip-external-locking[/COLOR]

[COLOR=#000000]bind-address	 = 127.0.0.1 <- this was commented out[/COLOR]
[COLOR=#000000]bind-address	 = 192.168.1.2 <- added this.[/COLOR]


[COLOR=#000000]verified MySQl Config[/COLOR]
[COLOR=#000000]/etc/mysql/my/cnf[/COLOR]
[COLOR=#000000][client][/COLOR]
[COLOR=#000000]port	 = 3306[/COLOR]
[COLOR=#000000]socket	= /var/run/mysqld/mysqld.sock[/COLOR]

[COLOR=#000000]and connected sql via the cli wiht [/COLOR]
[COLOR=#000000]mysql -u your_magic_username_for_mysql --password=your_magic_password mythconverg -h 127.0.0.1[/COLOR]

[COLOR=#000000]Does anyone have a clue?[/COLOR]

---

### Post by drink1297 on 2014-05-05
My.cnf is the global file for mysql, go a little deeper and check mythtv.cnf  (/etc/mysql/conf.d/mythtv.cnf) that takes precedent over my.cnf

---

### Post by blm-ubunet on 2014-05-05
The OP is 4 months old...

Mythfilldatabase is normally auto-run by BE user "mythtv".

Running mythfilldatabase manually (in the OP) runs as frontend user account, this can be a different user.
Therefore a different /home/"user"/.mythtv/config.xml file is searched for dB permissions.

If OP had tried to run mythfilldatabase as root then the tmp file permissions can prevent (success of) any later run.
Might have to clear out cached results in some tmp location.

Can run cmd as user "mythtv" with
```
sudo -H -u mythtv mythfilldatabase --refresh etc...etc
```

---

### Post by itlarson2 on 2014-05-05
Thanks for the replies.  I can't look at it tonight, since things are dissembled, and I am out of time, but I will research what you have told me at lunch tomorrow, and try to put it into action tomorrow night.

---

