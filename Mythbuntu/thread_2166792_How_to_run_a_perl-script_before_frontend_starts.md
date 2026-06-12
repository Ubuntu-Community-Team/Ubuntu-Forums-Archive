---
title: "How to run a perl-script before frontend starts?"
date: 2013-08-11
forum: Mythbuntu
---

### Post by Erik-NA on 2013-08-11
I have a MythBuntu install with a sepatate backend and a a few mythtv frontends. I am watchning DVB-S Live TV and have a startup problem when starting live TV in frontend.
There is a setting in the database called DefaultChanid which are storing the last viewed channel id. When a front end starts Live TV it starts on that particular channel.
If there is no transmission on that particular channel when Live TV starts, Live Tv will bail out with an error message. I cannot change channel and I have to set another starting channel id in the database. 

I have made a simple perl script to run either when:
[LIST]
[*]Front end application starts
[*]Front end OS (Mythbuntu) is booting
[/LIST]

Preferably the script should be run at boot. The trick is to wait for networking is up in order to remotely connect to mysql database on the backend.

Questions:
[LIST=1]
[*]Is it possible to run a script before/when Live TV starts?
[*]How do I ensure to run the script after networking is up?
[/LIST]

Perl-script (the first test version!)
```
#!/usr/bin/perl

use DBI;
use Sys::Hostname;
$hostname = hostname;

# CONFIG VARIABLES
$host = "backend";
$database = "mythconverg";
$tablename = "settings";
$user = "mythtv";
$pass = "password";

# Array of forbidden channels ids
@forbiddenChanIds = (2027,2544,2025,4211,1227);

# Default channel Id if channel is forbidden
$defaultChanid = 4801;

# Connect to dabase
$dbh = DBI->connect("DBI:mysql:$database:$host", $user, $pass) or die "Connection Error: $DBI::errstr\n";

my $sth = $dbh->prepare("SELECT data FROM settings WHERE value = 'DefaultChanid' AND hostname = ? LIMIT 1");
$sth->execute($hostname);
my $currentChanid = $sth->fetchrow_array();

print "DefaultChanid is set to $currentChanid for $hostname\n";

foreach (@forbiddenChanIds) {
	if ($currentChanid == $_) {
		$sth = $dbh->prepare("UPDATE settings SET data = ? WHERE value = 'DefaultChanid' AND hostname = ? LIMIT 1");
		$sth->execute($defaultChanid, $hostname);
		print "Defaultchanid was set to $currentChanid\n for hostname $hostname. Resetting it to $defaultChanid\n";
	}
} 

```

---

### Post by Erik-NA on 2013-08-18
Here is one solution.

First create script dir and script file
```
mkdir /home/mythtv/scripts
touch /home/mythtv/scripts/checkMythTvChannel.pl
chown -R mythtv:mythtv /home/mythtv/scripts
chown mythtv:mythtv /home/mythtv/checkMythTvChannel.pl
chmod 0755 /home/mythtv/scripts
chmod 0755 /home/mythtv/scripts/checkMythTvChannel.pl
```

Edit checkMythTvChannel.pl
```
edit /home/mythtv/scripts/checkMythTvChannel.pl
```

Paste the following content in checkMythTvChannel.pl. 
Replace <hostname> and <password> with your own.
Update @forbiddenChanIds with your forbidden channels ids.

```
#!/usr/bin/perl
use DBI;
use Sys::Hostname;
$hostname = hostname;
use Net::Ping;

use Sys::Syslog;    
use Sys::Syslog qw(:DEFAULT setlogsock);  

# CONFIG VARIABLES
$host = "<hostname>";
$database = "mythconverg";
$tablename = "settings";
$user = "mythtv";
$pass = "<password>";

# Array of forbidden channels ids
@forbiddenChanIds = (2027,2544,2025,4211,1227);

# Default channel Id if channel is forbidden
$defaultChanid = 4801;

sub writeToSysLog
{
	($class, $text) = @_;
	syslog($class, $text);
	print "$text\n";
}

openlog("checkMythTvChannel.pl", 'pid', 'user');

$ping = Net::Ping->new("icmp");
my $count=10;
do {
	$count--;
	$retval = $ping->ping($host);
	writeToSysLog("info", "Pinging host $host. Result $retval");
} while ((!$retval) && ($count >0));

if ($count == 0) {
	writeToSysLog('warning', "No connection to host $host");
	closelog();
	die;
}

# Connect to dabase
if (($dbh = DBI->connect("DBI:mysql:$database:$host", $user, $pass)) == 0) {
	writeToSysLog('warning', "Mysql connection Error: $DBI::errstr");
	closelog();
	die;
}

my $sth = $dbh->prepare("SELECT data FROM settings WHERE value = 'DefaultChanid' AND hostname = ? LIMIT 1");
$sth->execute($hostname);
my $currentChanid = $sth->fetchrow_array();
syslog('info', "DefaultChanid is set to $currentChanid for $hostname");

foreach (@forbiddenChanIds) {
	if ($currentChanid == $_) {
		$sth = $dbh->prepare("UPDATE settings SET data = ? WHERE value = 'DefaultChanid' AND hostname = ? LIMIT 1");
		$sth->execute($defaultChanid, $hostname);
		writeToSysLog("info", "Resetting defaultchanid from $currentChanid to $defaultChanid");
	}
} 
closelog();
```

Create a startup script
```
edit /etc/init.d/checkMythTvChannels
```

Paste the following content in checkMythTvChannels
```
#!/bin/bash
### BEGIN INIT INFO
# Provides:		sshd
# Required-Start:	$syslog
# Required-Stop:	
# Default-Start:	2 3 4 5
# Default-Stop:		
# Short-Description:	Check MythTV starting channels
### END INIT INFO

RETVAL=0
case "$1" in
start)
/home/mythtv/scripts/checkMythTvChannel.pl
;;
stop)
## pkill very dangerous, ensure the perl script name is unique
pkill checkMythTvChannel.pl
;;
status|restart|reload)
;;
*)
echo "Usage: sysstat {start|stop|status|restart|reload}"
exit 1
esac
exit $RETVAL
```

Make it executable and update rc.d
```
chmod 0755 /etc/init.d/checkMythTvChannels
update-rc.d checkMythTvChannels start 20 2 3 4 5 .
```

---

