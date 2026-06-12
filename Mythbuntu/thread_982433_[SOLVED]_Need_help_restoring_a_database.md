---
title: "[SOLVED] Need help restoring a database"
date: 2008-11-14
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-11-14
I'm trying to copy my database from an old mythbuntu box to a new one.  I was able to successfully run the mythconverg_backup.pl script to make a backup.  I copied to my thumbdrive and then went over to my new box and I'm now trying to use the mythconverg_restore.pl script to restore the database to my new mythbuntu box.

All my troubles are on my new mythbuntu box.

First I installed phpmyadmin so that I could drop my current mythconverg database.  That's easy enough.  I then run the command:

```
mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```

I can then verify in phpmyadmin that a new database has been created called mythconverg with no tables in it. I then go to my thumb drive and run the following command.

```
./mythconverg_restore.pl --filename mythconverg-1214-20081114143424.sql.gz --create_database /usr/share/mythtv/sql/mc.sql --username root --verbose
```

I get an error message that says: 
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

Here's the output that I'm getting with the --verbose switch:

```
Configuring environment:
  -    username:  root
  -        HOME:  /home/jbrown
  - MYTHCONFDIR:  /home/jbrown/.mythtv

Parsing configuration files:
  - checking:  /home/jbrown/.mythtv/config.xml
     parsing:  /home/jbrown/.mythtv/config.xml
  - checking:  /home/jbrown/.mythtv/backuprc
     parsing:  /home/jbrown/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

Database Information:
         DBHostName:  localhost
             DBPort:  0
         DBUserName:  root
         DBPassword:  XXX
             DBName:  mythconverg
        DBSchemaVer:  
  DBBackupDirectory:  /media/disk/mythtv
   DBBackupFilename:  mythconverg-1214-20081114143424.sql.gz
    create_database:  /usr/share/mythtv/sql/mc.sql

Executables:
       mysql_client:  mysql
         uncompress:  gzip -d

Miscellaneous:
    partial_restore:  no
   restore_xmltvids:  no
    change_hostname:  no

Checking database.
Unable to connect to database.

Attempting to use supplied password for mysql command-line client.
Any [client] or [mysql] password specified in the MySQL options file will
take precedence.

Attempting to create initial database.

Executing command:
mysql --defaults-extra-file='/tmp/znBimO3q4Y' --host='localhost' --user='root'  2>&1 < /usr/share/mythtv/sql/mc.sql

mysql exited with status:  1
mysql output:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


Unable to create initial database, stopped at ./mythconverg_restore.pl line 924.

```

Can anyone please tell me what I'm doing wrong?  I haven't changed the root password for mysql so, as far as I know, it's still blank.  At least when I go into phpmyadmin, I login with root and a blank password.

---

### Post by anonymousdog on 2008-11-14
I bet a quick browse through the USER_PRIVILEGES table in your information_schema db will yield the answers.

---

### Post by Meph1st0 on 2008-11-14
what should I be looking for in there?

---

### Post by anonymousdog on 2008-11-15
The user with credentials on the db

---

### Post by Meph1st0 on 2008-11-15
Here's the output of my user_privileges table.  The very last record shows 


```
GRANTEE               TABLE_CATALOG    PRIVILEGE_TYPE      IS_GRANTABLE
'mythtv'@'%'               Null             USAGE                NO

```

Does that mean that the Mythtv user doesn't have privileges to create the database?  Besides, I thought I was using root to create and import the database.

---

### Post by Meph1st0 on 2008-11-15
I honestly do not understand why this is so difficult.  I've done everything I can think of and I can not get past line 924 of the script.  Using the verbose switch it says it can't connect to the database.  I'm able to login to mysql with root and with the mythtv username with no problems.  I need some very clear instructions on how to do this.  I can't imagine that I'm the only person who's ever tried doing this.  Please forgive my obvious frustration.

---

### Post by klc5555 on 2008-11-17
> **Meph1st0 said:**
> I honestly do not understand why this is so difficult.  I've done everything I can think of and I can not get past line 924 of the script.  Using the verbose switch it says it can't connect to the database.  I'm able to login to mysql with root and with the mythtv username with no problems.  I need some very clear instructions on how to do this.  I can't imagine that I'm the only person who's ever tried doing this.  Please forgive my obvious frustration.

I think the problem may be simply that, unlike mythtv set up in most distros, by default Mythbuntu is set up so that the root user cannot log into the database. If you restore your database from your own home directory (or wherever), but using the _mythtv_ user (plus the database password) there should be no problem, i.e. (with variations):

$mysql -u mythtv -pwhatever-the-passord-is  mythconverg < the-backup.sql

This drove me crazy the first time I needed to restore a database in Mythbuntu, as the "Backup Your Database" doc in the Mythtv wiki led me astray by specifying the root user, without taking into account Ubuntu's odd setup. 

All the best!

---

### Post by Meph1st0 on 2008-11-17
I get the following output when I use that command:

```
jbrown@BrownDVR:/media/disk/mythtv$ mysql -u mythtv -p C1RFOKlE mythconverg < mythconverg-1214-20081114143424.sql
mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (i486) using readline 5.2
Copyright (C) 2000-2008 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license
Usage: mysql [OPTIONS] [database]
  -?, --help          Display this help and exit.
  -I, --help          Synonym for -?
  --auto-rehash       Enable automatic rehashing. One doesn't need to use
                      'rehash' to get table and field completion, but startup
                      and reconnecting may take a longer time. Disable with
                      --disable-auto-rehash.
  -A, --no-auto-rehash 
                      No automatic rehashing. One has to use 'rehash' to get
                      table and field completion. This gives a quicker start of
                      mysql and disables rehashing on reconnect. WARNING:
                      options deprecated; use --disable-auto-rehash instead.
  -B, --batch         Don't use history file. Disable interactive behavior.
                      (Enables --silent)
  --character-sets-dir=name 
                      Directory where character sets are.
  --default-character-set=name 
                      Set the default character set.
  -c, --comments      Preserve comments. Send comments to the server. The
                      default is --skip-comments (discard comments), enable
                      with --comments
  -C, --compress      Use compression in server/client protocol.
  -#, --debug[=#]     This is a non-debug version. Catch this and exit
  -D, --database=name Database to use.
  --delimiter=name    Delimiter to be used.
  -e, --execute=name  Execute command and quit. (Disables --force and history
                      file)
  -E, --vertical      Print the output of a query (rows) vertically.
  -f, --force         Continue even if we get an sql error.
  -G, --named-commands 
                      Enable named commands. Named commands mean this program's
                      internal commands; see mysql> help . When enabled, the
                      named commands can be used from any line of the query,
                      otherwise only from the first line, before an enter.
                      Disable with --disable-named-commands. This option is
                      disabled by default.
  -g, --no-named-commands 
                      Named commands are disabled. Use \* form only, or use
                      named commands only in the beginning of a line ending
                      with a semicolon (;) Since version 10.9 the client now
                      starts with this option ENABLED by default! Disable with
                      '-G'. Long format commands still work from the first
                      line. WARNING: option deprecated; use
                      --disable-named-commands instead.
  -i, --ignore-spaces Ignore space after function names.
  --local-infile      Enable/disable LOAD DATA LOCAL INFILE.
  -b, --no-beep       Turn off beep on error.
  -h, --host=name     Connect to host.
  -H, --html          Produce HTML output.
  -X, --xml           Produce XML output
  --line-numbers      Write line numbers for errors.
  -L, --skip-line-numbers 
                      Don't write line number for errors. WARNING: -L is
                      deprecated, use long version of this option instead.
  -n, --unbuffered    Flush buffer after each query.
  --column-names      Write column names in results.
  -N, --skip-column-names 
                      Don't write column names in results. WARNING: -N is
                      deprecated, use long version of this options instead.
  -O, --set-variable=name 
                      Change the value of a variable. Please note that this
                      option is deprecated; you can set variables directly with
                      --variable-name=value.
  --sigint-ignore     Ignore SIGINT (CTRL-C)
  -o, --one-database  Only update the default database. This is useful for
                      skipping updates to other database in the update log.
  --pager[=name]      Pager to use to display results. If you don't supply an
                      option the default pager is taken from your ENV variable
                      PAGER. Valid pagers are less, more, cat [> filename],
                      etc. See interactive help (\h) also. This option does not
                      work in batch mode. Disable with --disable-pager. This
                      option is disabled by default.
  --no-pager          Disable pager and print to stdout. See interactive help
                      (\h) also. WARNING: option deprecated; use
                      --disable-pager instead.
  -p, --password[=name] 
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty. WARNING: This is
                      insecure as the password is visible for anyone through
                      /proc for a short time.
  -P, --port=#        Port number to use for connection or 0 for default to, in
                      order of preference, my.cnf, $MYSQL_TCP_PORT,
                      /etc/services, built-in default (3306).
  --prompt=name       Set the mysql prompt to this value.
  --protocol=name     The protocol of connection (tcp,socket,pipe,memory).
  -q, --quick         Don't cache result, print it row by row. This may slow
                      down the server if the output is suspended. Doesn't use
                      history file.
  -r, --raw           Write fields without conversion. Used with --batch.
  --reconnect         Reconnect if the connection is lost. Disable with
                      --disable-reconnect. This option is enabled by default.
  -s, --silent        Be more silent. Print results with a tab as separator,
                      each row on new line.
  -S, --socket=name   Socket file to use for connection.
  --ssl               Enable SSL for connection (automatically enabled with
                      other flags). Disable with --skip-ssl.
  --ssl-ca=name       CA file in PEM format (check OpenSSL docs, implies
                      --ssl).
  --ssl-capath=name   CA directory (check OpenSSL docs, implies --ssl).
  --ssl-cert=name     X509 cert in PEM format (implies --ssl).
  --ssl-cipher=name   SSL cipher to use (implies --ssl).
  --ssl-key=name      X509 key in PEM format (implies --ssl).
  --ssl-verify-server-cert 
                      Verify server's "Common Name" in its cert against
                      hostname used when connecting. This option is disabled by
                      default.
  -t, --table         Output in table format.
  -T, --debug-info    Print some debug info at exit.
  --tee=name          Append everything into outfile. See interactive help (\h)
                      also. Does not work in batch mode. Disable with
                      --disable-tee. This option is disabled by default.
  --no-tee            Disable outfile. See interactive help (\h) also. WARNING:
                      option deprecated; use --disable-tee instead
  -u, --user=name     User for login if not current user.
  -U, --safe-updates  Only allow UPDATE and DELETE that uses keys.
  -U, --i-am-a-dummy  Synonym for option --safe-updates, -U.
  -v, --verbose       Write more. (-v -v -v gives the table output format).
  -V, --version       Output version information and exit.
  -w, --wait          Wait and retry if connection is down.
  --connect_timeout=# Number of seconds before connection timeout.
  --max_allowed_packet=# 
                      Max packet length to send to, or receive from server
  --net_buffer_length=# 
                      Buffer for TCP/IP and socket communication
  --select_limit=#    Automatic limit for SELECT when using --safe-updates
  --max_join_size=#   Automatic limit for rows in a join when using
                      --safe-updates
  --secure-auth       Refuse client connecting to server if it uses old
                      (pre-4.1.1) protocol
  --show-warnings     Show warnings after every statement.

Default options are read from the following files in the given order:
/etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf 
The following groups are read: mysql client
The following options may be given as the first argument:
--print-defaults	Print the program argument list and exit
--no-defaults		Don't read default options from any options file
--defaults-file=#	Only read default options from the given file #
--defaults-extra-file=# Read this file after the global files are read

Variables (--variable-name=value)
and boolean options {FALSE|TRUE}  Value (after reading options)
--------------------------------- -----------------------------
auto-rehash                       TRUE
character-sets-dir                (No default value)
default-character-set             latin1
comments                          FALSE
compress                          FALSE
database                          (No default value)
delimiter                         ;
vertical                          FALSE
force                             FALSE
named-commands                    FALSE
local-infile                      FALSE
no-beep                           FALSE
host                              (No default value)
html                              FALSE
xml                               FALSE
line-numbers                      TRUE
unbuffered                        FALSE
column-names                      TRUE
sigint-ignore                     FALSE
port                              3306
prompt                            mysql> 
quick                             FALSE
raw                               FALSE
reconnect                         FALSE
socket                            /var/run/mysqld/mysqld.sock
ssl                               FALSE
ssl-ca                            (No default value)
ssl-capath                        (No default value)
ssl-cert                          (No default value)
ssl-cipher                        (No default value)
ssl-key                           (No default value)
ssl-verify-server-cert            FALSE
table                             FALSE
debug-info                        FALSE
user                              mythtv
safe-updates                      FALSE
i-am-a-dummy                      FALSE
connect_timeout                   0
max_allowed_packet                16777216
net_buffer_length                 16384
select_limit                      1000
max_join_size                     1000000
secure-auth                       FALSE
show-warnings                     FALSE

```

This is clearly just the help information for the mysql command.  If I look in phpmyadmin, no tables have been created in the mythconverg database.  Attempting to have a better sense of humor with this problem, I have to admit, I like the i-am-a-dummy variable listed in the output.  I'm also glad to see that it's set to FALSE.

---

### Post by klc5555 on 2008-11-18
> **Meph1st0 said:**
> I get the following output when I use that command:

[CODE]jbrown@BrownDVR:/media/disk/mythtv$ mysql -u mythtv -p C1RFOKlE mythconverg < mythconverg-1214-20081114143424.sql
mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (i486) using readline 5.2
...


Looks like a syntax error: don't use a space between -p and the actual password.

Cheers! :)

---

### Post by dmfrey on 2008-11-18
I have been considering this so that I can switch to a larger harddrive.  Which directories did you also backup?  I am mostly concerned about the recordings, however, I am not sure if I am missing anything else besides that directory.  I would think i would also need some config files setup in my home and the mythtv home directories under .* directories (i.e. .mplayer, etc.).

---

### Post by Meph1st0 on 2008-11-20
Thank you, Thank you, Thank you.  I finally go it working.  [This]("http://www.uluga.ubuntuforums.org/showpost.php?p=2298778&postcount=4") post also helped considerably.

---

