---
title: "Restoring database"
date: 2009-05-10
forum: Mythbuntu
---

### Post by codymyth on 2009-05-10
First the Story: I have/had a mythbuntu fully set up with about 250gb of recordings on it and then the sound stopped working. To fix the sound i tried upgrading to 9.4 (from 8.10)but it froze during installation and i was forced to restart it manually and the os completely stopped working. so i reinstalled the os and didn't touch the partion with all the recordings.

Now the question: How would i go about getting all of the recordings back on the new os. Everything on the xfs partion is totally untouched(which i think is all the /var/lib stuff) so i believe i can still get all the recordings back, but i have no idea how to do that and cannot find any help searching google.

Can anybody help me?

---

### Post by 4dognight on 2009-05-11
You might want to try myth.rebuilddatabase.pl
It should be located at /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz

---

### Post by codymyth on 2009-05-11
I'll try that, thanks

---

### Post by codymyth on 2009-05-11
Ok i found the file, now how would a go about using it?

---

### Post by 4dognight on 2009-05-11
I think if you run it without any options, it will give you the usage on how to run it.

---

### Post by codymyth on 2009-05-11
if i do this: ```
sudo /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz
``` I get a command not found error and if i go to the file location and double click it asks me what application to run it with

---

### Post by nickrout on 2009-05-11
> **codymyth said:**
> if i do this: ```
sudo /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz
``` I get a command not found error and if i go to the file location and double click it asks me what application to run it with

The file is zipped to save space. Do this:

```
sudo gunzip /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz
sudo cp /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl /usr/local/bin
sudo chmod +x /usr/local/bin/myth.rebuilddatabase.pl
```

you should then be able to run it. The three commands unzip the file, move it into the path and make it executable :)

---

### Post by codymyth on 2009-05-11
OK i did that and now when i try to excute it the terminal says this: ```
 cody@cody-myth:~$ /usr/local/bin/myth.rebuilddatabase.pl
Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/bin/myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at /usr/local/bin/myth.rebuilddatabase.pl line 55.
```

---

### Post by nickrout on 2009-05-12
> **codymyth said:**
> OK i did that and now when i try to excute it the terminal says this: ```
 cody@cody-myth:~$ /usr/local/bin/myth.rebuilddatabase.pl
Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/bin/myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at /usr/local/bin/myth.rebuilddatabase.pl line 55.
```

sudo aptitude install libtimedate-perl

---

### Post by codymyth on 2009-05-12
i tried that and got the same error. i'll try restarting the computer

---

### Post by codymyth on 2009-05-12
i tried sudo aptitude install libtimedate-perl and a restart and neither helped, i still get the same error. I opened up the file in gedit and it is the line with the time and date things

---

### Post by nickrout on 2009-05-12
Are you sure its the same error? Or caused by another dependency?

---

### Post by klc5555 on 2009-05-12
> **nickrout said:**
> Are you sure its the same error? Or caused by another dependency?

Just to make things more confusing than they ever needed to be, Canonical thoughtfully supplies not only libtimedate-perl, but also libdatetime-perl (and its derivatives).

It's likely this other one (or one of its derivatives) that myth.rebuilddatabase.pl is looking for.

---

### Post by codymyth on 2009-05-12
Thanks for the help so far guys.
ok i installed both libdatetime-perl and libtimedate-perl

i still get this error: ```
 cody@cody-myth:~$ sudo /usr/local/bin/myth.rebuilddatabase.pl
Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/bin/myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at /usr/local/bin/myth.rebuilddatabase.pl line 55.

```

This is what line 55 says: ```
 use Time::Format qw(time_format); 
```

---

### Post by klc5555 on 2009-05-12
> **codymyth said:**
> Thanks for the help so far guys.
ok i installed both libdatetime-perl and libtimedate-perl

i still get this error: ```
 cody@cody-myth:~$ sudo /usr/local/bin/myth.rebuilddatabase.pl
Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/local/bin/myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at /usr/local/bin/myth.rebuilddatabase.pl line 55.

```

This is what line 55 says: ```
 use Time::Format qw(time_format); 
```

Sorry --my mistake. I just did a keyword search at packages.ubuntu.com, and apparently the module Time/Format.pm is to be found in the package libtime-format-perl

Cheers!

---

### Post by codymyth on 2009-05-12
now i get this ```
cody@cody-myth:~$ sudo /usr/local/bin/myth.rebuilddatabase.pl --try_default
DBI connect('database=mythconverg:host=cody-myth','mythtv',...) 
failed: Can't connect to MySQL server on 'cody-myth' (111) at 
/usr/local/bin/myth.rebuilddatabase.pl line 191
Cannot connect to database ()

```

---

### Post by klc5555 on 2009-05-12
> **codymyth said:**
> now i get this ```
cody@cody-myth:~$ sudo /usr/local/bin/myth.rebuilddatabase.pl --try_default
DBI connect('database=mythconverg:host=cody-myth','mythtv',...) 
failed: Can't connect to MySQL server on 'cody-myth' (111) at 
/usr/local/bin/myth.rebuilddatabase.pl line 191
Cannot connect to database ()

```

1) Doesn't require sudo.
2) Requires --pass  (with MySQL password)  and --dir arguments.

---

### Post by codymyth on 2009-05-12
I can't get that to work, could you show me an example of what i should put in the terminal. All my passwords are the defaults by the way

---

### Post by klc5555 on 2009-05-13
> **codymyth said:**
> I can't get that to work, could you show me an example of what i should put in the terminal. All my passwords are the defaults by the way

The MySQL password is a random alphanumeric sequence generated by Mythbuntu at install. It is found either from the frontend ( "Utilities/Setup" > "Setup" > "General" > the first page) or in the /home/mythtv/.mythtv/ directory where it is in the simlink text file "mysql.txt"

The "dir" variable is the path to a storage directory (the script needs to be run again for each different directory in your storage group, if there are more than one).

So, from the directory where the nuvexport script is located (and has been made executable) the command should look something like this (from your user prompt '$'):

$ ./nuvexport --pass Yjn7TVr --dir /var/lib/mythtv/recordings


Sometimes versions of this script (which has been around for several years) have been a bit fussy about accepting the password from the command-line argument, and I've found it easier in those cases to edit the password into the script itself, where it specifies the 'mypass' option, instead of the default "mythtv".

When this script is working, it will find every recording that is not in your mythconverg. It will offer to add them to the database one after the other. It will check each recording against its stored SchedulesDirect listings, back as far as 10 days if they exist on the machine.

When nothing is found, it will begin offering defaults, which can be accepted or changed. _Accept_ what it says about the channel number (changing this means that the recording will become invisible to mythtranscode or mytharchive, because the filename will get changed). You will be given a chance to type in the title, subtitle, and synopsis of each recording. If you don't know them, the title and subtitle (but not synopsis) can always be added later in the "Recording Options" for the individual recording in the frontend "View Recordings".

The script will allow you to enter in the duration of the recording (default is 60 min. --a wrong answer doesn't affect the recording itself, just how it gets listed in "View Recordings". The script will offer to build an index for the recording. You'll need one, but the script uses mythcommflag. This means that the resulting index will work perfectly if the recording is from analog, but if it is from dvb, the resulting index will not function satisfactorily, and you'll need to revisit each dvb recording at some later time to build a proper index with mythtranscode:

$ mythtranscode --mpeg2 --buildindex -c -s (or -i)

Good luck!

---

### Post by codymyth on 2009-05-13
Well it still doesn't work. i tried using your exact code line just with my password and it says the file nuvexport doesn't exist

Perhaps i haven't made nuvexport executable(unless its with mythdatabase.pl.gz) or maybe my file isn't in the right place

Error says this:
```
 cody@cody-myth:~$ /usr/local/bin/myth.rebuilddatabase.pl --pass C1RFOKlE --dir /var/lib/mythtv/recordings
DBI connect('database=mythconverg:host=cody-myth','mythtv',...) failed: Can't connect to MySQL server on 'cody-myth' (111) at /usr/local/bin/myth.rebuilddatabase.pl line 191
Cannot connect to database ()
```

mysql.txt says this:
```
DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3
```

Line 191(and 192) says this:
```
my $dbh = DBI->connect("dbi:mysql:database=$database:host=$dbhost",
		"$user","$pass") or die "Cannot connect to database ($!)\n";
```

---

### Post by klc5555 on 2009-05-13
> **codymyth said:**
> Well it still doesn't work. i tried using your exact code line just with my password and it says the file nuvexport doesn't exist

Perhaps i haven't made nuvexport executable(unless its with mythdatabase.pl.gz) or maybe my file isn't in the right place

Error says this:
```
 cody@cody-myth:~$ /usr/local/bin/myth.rebuilddatabase.pl --pass C1RFOKlE --dir /var/lib/mythtv/recordings
DBI connect('database=mythconverg:host=cody-myth','mythtv',...) failed: Can't connect to MySQL server on 'cody-myth' (111) at /usr/local/bin/myth.rebuilddatabase.pl line 191
Cannot connect to database ()
```

mysql.txt says this:
```
DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3
```

Line 191(and 192) says this:
```
my $dbh = DBI->connect("dbi:mysql:database=$database:host=$dbhost",
		"$user","$pass") or die "Cannot connect to database ($!)\n";
```

Your script is definitely executable, but seems breaking down at giving the user/password information to the database.

Some versions of the script have seem to have difficulty accepting the password from the command line argument. In the version of the script I ran on 7.10, I edited in the password into the script into line 69 my $pass, so that the line reads (in your case):

my $pass = "C1RFOKLE";

Try making this edit, and hopefully this will finally get the script moving for you.

---

### Post by codymyth on 2009-05-13
i tried doing what you suggested to no avail. is there anything else i could try? maybe it isn't hanging on the password?

Thanks for all the help by the way

EDIT: While looking in mythbuntu control center i noticed i had mysql server disabled, so i enabled it and now i am getting this error: 
```
cody@cody-myth:~$ /usr/local/bin/myth.rebuilddatabase.pl --pass C1RFOKLE --dir /var/lib/mythtv/recordings
DBI connect('database=mythconverg:host=cody-myth','mythtv',...) failed: Access denied for user 'mythtv'@'cody-myth' (using password: YES) at /usr/local/bin/myth.rebuilddatabase.pl line 191
Cannot connect to database ()

```

---

### Post by klc5555 on 2009-05-14
> **codymyth said:**
> i tried doing what you suggested to no avail. is there anything else i could try? maybe it isn't hanging on the password?

Thanks for all the help by the way

EDIT: While looking in mythbuntu control center i noticed i had mysql server disabled, so i enabled it and now i am getting this error: 
```
cody@cody-myth:~$ /usr/local/bin/myth.rebuilddatabase.pl --pass C1RFOKLE --dir /var/lib/mythtv/recordings
DBI connect('database=mythconverg:host=cody-myth','mythtv',...) failed: Access denied for user 'mythtv'@'cody-myth' (using password: YES) at /usr/local/bin/myth.rebuilddatabase.pl line 191
Cannot connect to database ()

```

Well, it was late at night when I typed my preceding, and I may have typo-ed your MySQL password (the capital "L"). Since it looks like you used my typo-ed reproduction, MySQL won't pass it. The password's case-sensitive, so when you edit the script, check to make sure the caps and lower-case letters match the actual password. Also, check for 0 versus 0, and l versus 1, which are hard for us to pick up reading.

If you have edited the 'my $pass' line in the script with the actual password, then when you run the command, you won't use the --pass option. The command will be run simply:

$ ./nuvexport  --dir /var/lib/mythtv/recordings

And as a final shot, I've always just run the script from my own user directory, and have never installed it in /usr/local/bin. While your location of it shouldn't make any difference, perhaps there is a permissions issue with it in its changed location and perhaps you should try giving it a run with sudo. It won't harm anything.

---

### Post by codymyth on 2009-05-14
for the password i just copied and pasted from mysql.txt. I believe its saying that my password is correct but it won't grant me access for a different reason. don't know why though.

---

### Post by nickrout on 2009-05-14
can you use mysql to connect direct to the database?

---

### Post by 4dognight on 2009-05-14
mysql treats

mythtv@cody-myth , mythtv@localhost, mythtv@127.0.0.1 , etc as all different with different passwords.

How do you have your database server defined as in myth's config?

is it 127.0.0.1 or cody-myth or even as an IP address other than 127.0.0.1?

---

### Post by codymyth on 2009-05-14
Here are a bunch of sql conf files

/etc/mythtv/mysql.txt
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'
```

/home/cody/.mythtv/mysql.txt
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'
```

etc/mysql/my.cnf
```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
#skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 192.168.1
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover		= BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Federated
#
# The FEDERATED storage engine is disabled since 5.0.67 by default in the .cnf files
# shipped with MySQL distributions (my-huge.cnf, my-medium.cnf, and so forth).
#
skip-federated
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

I also tried "/usr/local/bin/myth.rebuilddatabase.pl --dir /var/lib/mythtv/recordings" and got: ```
cody@cody-myth:~$ /usr/local/bin/myth.rebuilddatabase.pl --dir /var/lib/mythtv/recordings

These are the files stored in (/var/lib/mythtv/recordings) and will be checked against
your database to see if the exist.  If they do not, you will be prompted
for a title and subtitle of the entry, and a record will be created.


cody@cody-myth:~$ 

```
nothing happened after that

I connected to the db once from a live cd on another comp but not from another install frontend

---

### Post by klc5555 on 2009-05-14
> **codymyth said:**
> Here are a bunch of sql conf files

/etc/mythtv/mysql.txt
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'
```

/home/cody/.mythtv/mysql.txt
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=C1RFOKlE
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'
```

etc/mysql/my.cnf
```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
#skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 192.168.1
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover		= BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Federated
#
# The FEDERATED storage engine is disabled since 5.0.67 by default in the .cnf files
# shipped with MySQL distributions (my-huge.cnf, my-medium.cnf, and so forth).
#
skip-federated
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

I also tried "/usr/local/bin/myth.rebuilddatabase.pl --dir /var/lib/mythtv/recordings" and got: ```
cody@cody-myth:~$ /usr/local/bin/myth.rebuilddatabase.pl --dir /var/lib/mythtv/recordings

These are the files stored in (/var/lib/mythtv/recordings) and will be checked against
your database to see if the exist.  If they do not, you will be prompted
for a title and subtitle of the entry, and a record will be created.


cody@cody-myth:~$ 

```
nothing happened after that

I connected to the db once from a live cd on another comp but not from another install frontend

Your script is running and has connected. Have you already set up a mythconverg by running mythtv-setup to set up the backend? And after this, have you run mythfilldatabase to set up all the tables with listings information? The script assumes that there's a fully-formed mythconverg with all the tables that the recordings are to be checked against and added to. I don't know whether the script will function if the backend is not already completely set up with tables and listings ready to go.

And, of course, are the recordings (*.mpg and *.nuv) actually in /var/lib/mythtv/recordings ?

We're getting closer, I think... :)

---

### Post by codymyth on 2009-05-14
i had to reinstall the mythbuntu os because it froze on a upgrade. when i reinstalled it i did basicaly the defautlts but i didn't touch my 700gb partion with all the movies on it. so they are in /var/lib/mythtv/recordings but i can't see them because there on the other partition. was a not supposed to reinstall mythbuntu like that?

---

### Post by klc5555 on 2009-05-15
> **codymyth said:**
> i had to reinstall the mythbuntu os because it froze on a upgrade. when i reinstalled it i did basicaly the defautlts but i didn't touch my 700gb partion with all the movies on it. so they are in /var/lib/mythtv/recordings but i can't see them because there on the other partition. was a not supposed to reinstall mythbuntu like that?

Ah! Now this is a problem I understand. The recordings are in the partition formerly mounted as /var/lib/mythtv/recordings. That partition is not mounted that way any longer. You need to mount this partition so it is in the current mythtv filesystem.

First of all, do you have any files/recordings in your *current* /var/lib/mythtv/recordings/ ? If the *current* /var/lib/mythtv/recordings/ is empty, and you wish to continue to use this path for your current myth installation's storage, it's quite easy.

First off, figure out which partition (/dev/sdaX)your recordings are in. 

$ fdisk -l

will *list* the partitions on your first disk (/dev/sda) One of these is the one your mythbuntu install is in; another will be your old storage partition. It could be anything, but let's say it's /dev/sda5

$ sudo mount /dev/sda5 /var/lib/mythtv/recordings

Again assuming that your current /var/lib/mythtv/recordings has been an empty directory.

And now <poof> your recordings files should be visible in /var/lib/mythtv/recordings

If this mounting is correct, your files are visible, and you therefore wish to make this mounting permanent at bootup, you will need to edit and add in one new mount line to your /etc/fstab file. (Be careful about this; fstab is not a file you wish to hose inadvertently.)

This line will look something like the following:

/dev/sda5  /var/lib/mythtv/recordings  ext3  defaults  0 2

Make sure you put in your correct partition listing; make sure you put in the actual filesystem the partition uses --it could be ext3, but it could also be xfs, ext2, reiserfs or whatever. If you feel nervous about editing the fstab, there are a number of available guides, one of which is [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Finally, when the mount has been automatized at bootup, check to make sure the /var/lib/mythtv/recordings directory and all the files in it have the user 'mythtv' as owner and group. Sometimes in all this mounting business, the directory or the files get reassigned to 'root', which causes read/write problems.

$ ls -l /var/lib/mythtv/recordings 

Reassign files as necessary with sudo chown and sudo chgrp.

And now, finally, you should be ready to run myth.rebuilddatabase.pl with reasonable confidence of success! :)

---

### Post by klc5555 on 2009-05-15
It just occurred to me that if your version of mythbuntu is something along the lines of 8.10 or  9.04, your old installation had a little dinky partition mounted /, and a great big partition mounted /var/lib, in which partition was ../mythtv/recordings.

Your current mythbuntu installation may therefore have a dinky partition mounted /, a bigger partition mounted /var/lib, and a very big partition not mounted at all that has the file structure formerly mounted under the old installation's /var/lib/, including ../mythtv/recordings

If so, and if your new installation is the same version of mythbuntu as the old one was, you can rehook things up more simply. If the current /var/lib partition is /dev/sdX, and the old /var/lib partition is /dev/sdY, then simply:

$ sudo umount /dev/sdX

followed by

$ sudo mount /dev/sdY /var/lib

should hook it all up the way it was before. If so, then eventually editing the fstab will consist basically of changing a single character.

---

### Post by codymyth on 2009-05-15
i got the partition mounted and i am adding the recordings back now. is there not a way to use their old names?

Thank you very much for helping me klc5555 and all others who helped

---

### Post by klc5555 on 2009-05-15
> **codymyth said:**
> i got the partition mounted and i am adding the recordings back now. is there not a way to use their old names?

Thank you very much for helping me klc5555 and all others who helped

The only thing the machine currently has is the filename. If you know what the title/subtitle/synopsis of the show was, you can add them in when prompted. If you don't know now, when you find out later (after watching the file and doing your research at tv.com or imdb.com or wherever, you can type in the title/subtitle (but not a synopsis) from the frontend by right-clicking an individual recording in "Watch Recordings" and go into "Recording Options".

But after this weeklong nightmare, I'll bet you'll be willing to set up a daily database backup, so that next time an installation fries, you'll have a complete database ready to drop in. I recommend putting a subdirectory ../databasebackups right in your /var/lib/mythtv/recordings directory, so that if your recordings survive, so will their database. Then implement the strategy and daily backup script found here: 

[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Backup](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Backup)

and substitute your /var/lib/mythtv/recordings/databasebackups/ for the script's /mnt/foo/sqldump/

And you'll be back up and running within 15 minutes of your next new mythbuntu installation being ready. 

Cheers! :)

---

### Post by codymyth on 2009-05-22
when i restart my system it is not mounting /dev/sda6(where my recordings are on) for me. And it says all my old files are corrupted

---

