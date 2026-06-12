---
title: "Commercial flag in 9.10 not working"
date: 2009-11-27
forum: Mythbuntu
---

### Post by dibuntux on 2009-11-27
I had commercial flagging enabled in 9.04 and it worked almost perfectly on most shows (on some it just could not tell the difference btw show and ads).
Upgraded to 9.10, now the shows are flagged, so mythcommflag runs, but it does not work - does not find any commercial to flag. This on the same show (CSI) as before.

I had standard settings on both 9.04 and 9.10. Any idea? TIA

---

### Post by SiHa on 2009-11-27
You've not checked "Strict Commercial Detection" have you? On my system, if I check this, I get almost no commercials flagged at all.

---

### Post by dibuntux on 2009-11-28
No. i did not - but it was CHECKED! It was not before the upgrade from 9.04, and then it was checked in 9.10 (new default?). 

Still, with the option unchecked, it is not able to find commercials anymore in CSI...Any ideas? TIA

---

### Post by SiHa on 2009-11-29
All I can suggest is try all the different flagging methods available.

---

### Post by dibuntux on 2009-11-30
Thanks, I will try... 
default is "all available methods":
it is just strange that in 9.04 was working and in 9.10 it is not on the same tv program

---

### Post by dibuntux on 2010-02-03
No, what used to work in 9.04 does not in 9.10.
Settings are the same:try all the different flagging, and "Strict Commercial Detection" is off.

Still some time it works, most of the time it does not - some times cuts what it believes is a commercial but is the tv show. very annoying. Any ideas? TIA

Mythbuntu 9.10 AMD64
Gigabyte GA-M720 2GB DDR2-800
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-t

---

### Post by ian dobson on 2010-02-03
Hi,

How long are the Commercials when it doesn't work? I think mythtv defaults to a maximum for only about 6 minutes (anything longer than this can't be a commercial).

There is a "hidden" setup option you can set in the database that allows you to increase this.

The key is called MaximumCommercialSkip or maybe CommDetectMaxCommBreakLength and you need to increment this.

I may be barking up the wrong tree, but increasing this value help me avoid the adverts on RTL which seam to run forever.

Edit: Just found this:- [http://mythtv.org/pipermail/mythtv-dev/2008-November/063594.html](http://mythtv.org/pipermail/mythtv-dev/2008-November/063594.html)

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-03
Thanks Ian! I think it maybe it! Commercials on the incriminated channels (Italia1, Rete 4) are pretty long, I think well above 6, something up to 9. 

I will try incrementing that parameter and report...

Thanks again,
Dave

---

### Post by SiHa on 2010-02-03
> Commercials on the incriminated channels (Italia1, Rete 4) are pretty long, I think well above 6, something up to 9Blimey, no wonder you want to skip them!

---

### Post by ian dobson on 2010-02-03
Hi,

Just be careful you can't change these options through the setup interface. You need to use phpmyadmin or direct from the terminal with mysqladmin.

Don't forget to set the hostname to the name of your backend.

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-04
Ian, my KB in sql is evidently not enough...
phpMyAdmin has to be installed server side - manually, no ubuntu package... (tried adding a PPA with no luck).
mysqladmin... no luck

I've installed EMMA, but could not connect to db from client.

Now I've installed on the client MySQL Admin & MySQL Query: they are very nice, I can connect to myth and they show a lot of info, but none regarding the CommDetectMaxCommBreakLength key...

So I get the idea, just do not know how to implement it... TIA

---

### Post by ian dobson on 2010-02-04
Hi,

If you go to the table settings, this table has 3 columns :-

Value - Thats the setting name (CommDetectMaxCommBreakLength  in this case)
Data  - The actual value you want to set this setting to (maybe 600 for 10 minutes)
Host  - the host name that should use this value (use your backend host name or whichever host does the commflagging if you have several backends)

This value might not exist in your database so you'll have to create it yourself. in sql:-

insert into settings(Value,Data,Host) VALUES('CommDetectMaxCommBreakLength','600','MythBackend_Name')

My SQL is abit rusty but that looks about right to me.

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-04
mmmmhhh...
using MySQL Administrator from the client I can see mythconverg and the table named settings. If I click on it I can Edit Table Data (beeing asked to connect to server with pwd) and then I can see all the Value,Data,Host keys in settings.
But I can not edit key values. 
The open window is called MySQL Query browser, and at the top there's a big field with the command: SELECT * FROM 'mythconverg'.'settings'  and next a big green button "execute".

As you suggested the key CommDetectMaxCommBreakLength is not present, and there's not option for creating a new keys.

I tried opening a "MySQL Text consolle" and executing the command at the mysql> prompt:

insert into settings(Value,Data,Host) VALUES('CommDetectMaxCommBreakLength','600','mitodue')

but nothing (apparently) happened...BUMP

---

### Post by ian dobson on 2010-02-04
Hi,

Woops, I made a small mistake in the SQL it should be:-

INSERT INTO settings( Value, DATA , HostName ) VALUES ('CommDetectMaxCommBreakLength','600','mitod ue') 

That should work now.

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-04
Again, in "MySQL Text consolle" and executed the command at the mysql> prompt:

INSERT INTO settings( Value, DATA , HostName ) VALUES ('CommDetectMaxCommBreakLength','600','mitodue') 

it accepted the line without a reply - I searched again the settings to see if the key was added, but the table was just the same... I'm missing something...

---

### Post by ian dobson on 2010-02-04
Hi,

I just tried exactly the same command on my myphpadmin system and it worked as expected so it's got to be something with your sql editor.

OK Try this:-

1) Go to the terminal and enter:-
**mysql -uUUUUUU -pXXXXX**

change UUUU to your user name (mythtv?) and change XXXX to the password.
Then enter and the mysql> prompt
**INSERT INTO mythconverg.settings( Value, DATA , HostName ) VALUES ('CommDetectMaxCommBreakLength','600','mitodue');**

Then enter **quit** at the mysql> prompt

Hope this helps
Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-04
OK, I did:

mysql> INSERT INTO mythconverg.settings( Value, DATA, HostName ) VALUES ('CommDetectMaxCommBreakLenght','800','mitodue');
Query OK, 1 row affected (0,00 sec)

mysql> quit
Bye

I tried to check with MySQL Administrator the table, but could not find it... maybe I'm using the wrong tool. Anyway the row was added - I'll try to flag again the commercials and see what happens... I will report.

Thank you so much for your precious help as usual!

Bye, Dave

---

### Post by ian dobson on 2010-02-04
Hi,

But the new setting MUST be in the DB now. If you look at the command, the text result was "Query OK, 1 row affected (0,00 sec)" so oe row has been changed.

if you go to the console again and start mysql again with the same user name and password then type:-

SELECT *  FROM mythconverg.settings WHERE `value` LIKE '%CommD%';

you'll see something like:-
```
+------------------------------+------+----------+
| value                        | data | hostname |
+------------------------------+------+----------+
| AggressiveCommDetect         | 1    | NULL     |
| CommDetectMaxCommBreakLength | 600  | alpha2   |
+------------------------------+------+----------+
2 rows in set (0.00 sec)
```
Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-04
Nope, I tried re-flagging C.S.I. Miami (BTW the ads are like 7-8 minutes) and nothing different...

Found your message so...

mysql> SELECT * FROM mythconverg.settings WHERE 'value' LIKE '%CommD%';
Empty set (0,00 sec)

So were did that line go?

---

### Post by ian dobson on 2010-02-04
Hi,

OK lets try it again:
Go to the terminal and type
**mysql -uUSER -pPASSWORD**

then at the mysql> prompt type:-
**INSERT INTO mythconverg.settings( Value, DATA, HostName ) VALUES ('CommDetectMaxCommBreakLenght','800','mitodue');**

it should respond:-
*Query OK, 1 row affected (0,00 sec)*

then type at the mysql> prompt
**SELECT * FROM mythconverg.settings WHERE `value` LIKE '%CommD%';**

it should respond with something like:-
```
[I]+------------------------------+------+----------+
| value                        | data | hostname |
+------------------------------+------+----------+
| AggressiveCommDetect         | 1    | NULL     |
| CommDetectMaxCommBreakLength | 600  | alpha2   |
+------------------------------+------+----------+
2 rows in set (0.00 sec)[/I]
```

then at the mysql prompt type
**quit**

note all values are Case sensitive (A is not the same as a).

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-05
Ian, I know linux is case sensitive... 
anyway, I copied your commands in gedit for EXACT confrontation, besides 800 instead of 600 they are the same.

So I tried again:
mysql> INSERT INTO mythconverg.settings( Value, DATA, HostName ) VALUES ('CommDetectMaxCommBreakLenght','800','mitodue');
Query OK, 1 row affected (0,00 sec)

mysql> SELECT * FROM mythconverg.settings WHERE 'value' LIKE '%CommD%';         Empty set (0,00 sec)

mysql> 

I believe is identical to yours - so what am I missing? TIA

---

### Post by ian dobson on 2010-02-05
Hi,

Sorry I have no idea whats wrong. Do you have phpmyadmin installed? I've got a feeling it's something really strange with your mysql configuration.

I think I'm going to try writing a small perl script that tries to read the info out of the DB and displays it. Give me 1-2hours to copy/paste something together.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-02-05
Hi,

OK I've banged something together. Just copy the text to a file, set it executable (chmod +x filename) then run it ./filename.

```

#!/usr/bin/perl -w
use DBI;
use strict;

my $XXX;
my ($user,$password,$SQLDBName,$SQLHost)=PrepSQLRead();

print "\n\n\n";
my @result=SQLQuery("SELECT * FROM `settings` WHERE `value` LIKE '%CommD%';");
for $XXX (@result){
   if (@$XXX[0] && @$XXX[1] && @$XXX[2] )  {
   print  " @$XXX[0]\t @$XXX[1]\t @$XXX[2] \n";
   }
}
exit;

#Perform  SQL query returns an array of arrays
sub SQLQuery {
   my  ($QUERY) = @_;
   my (@data,@row);
   my $dbh = DBI->connect_cached("DBI:mysql:$SQLHost:$SQLDBName", $user, $password)
     or die "Couldn't connect to database: " . DBI->errstr;
   my $table_data = $dbh->prepare_cached($QUERY) or die "Couldn't prepare statement: " . $dbh->errstr;
   $table_data->execute or die "Couldn't execute statement: " . $table_data->errstr;
   while ( @row = $table_data->fetchrow_array )  {
      push @data,[@row] ;
   }
   if ($data[0]) {
      return @data;
   } else {
      return 0;
   }
}

#Try and read MythTV configuration parameters from mysql.txt (This could be in several places)
sub PrepSQLRead {
   my $hostname = `hostname`;
   chomp($hostname);
   my ($SQLServer,$SQLUser,$SQLPassword);
# Read the mysql.txt file in use by MythTV. Could be in a couple places, so try the usual suspects
   my $found = 0;
   my @mysql = ('/usr/local/share/mythtv/mysql.txt',
      '/usr/share/mythtv/mysql.txt',
      '/etc/mythtv/mysql.txt',
      '/usr/local/etc/mythtv/mysql.txt',
      "$ENV{HOME}/.mythtv/mysql.txt",
      'mysql.txt'
     );
   foreach my $file (@mysql) {
      print ".Looking for Database information in $file\n";
      next unless (-e $file);
      print ".Found configuration file $file\n";
      $found = 1;
      open(CONF, $file) or die "Unable to open $file:  $!\n\n";
      while (my $line = <CONF>) {

         # Cleanup
         next if ($line =~ /^\s*#/);
         $line =~ s/^str //;
         chomp($line);

         # Split off the var=val pairs
         my ($var, $val) = split(/\=/, $line, 2);
         next unless ($var && $var =~ /\w/);
         if ($var eq 'DBHostName') {
            $SQLServer = $val;
         }
         elsif ($var eq 'DBUserName') {
            $SQLUser = $val;
         }
         elsif ($var eq 'DBName') {
            $SQLDBName = $val;
         }
         elsif ($var eq 'DBPassword') {
            $SQLPassword = $val;
         }

         # Hostname override
         elsif ($var eq 'LocalHostName') {
            $hostname = $val;
         }
      }
      close CONF;
   }
   die "Unable to locate mysql.txt:  $!\n\n" unless ($found && $SQLServer);
   return ($SQLUser, $SQLPassword, $hostname,$SQLDBName);
}

```

It should produce a printout something like:-
```

 ./Settings.pl
.Looking for Database information in /usr/local/share/mythtv/mysql.txt
.Looking for Database information in /usr/share/mythtv/mysql.txt
.Found configuration file /usr/share/mythtv/mysql.txt
.Looking for Database information in /etc/mythtv/mysql.txt
.Found configuration file /etc/mythtv/mysql.txt
.Looking for Database information in /usr/local/etc/mythtv/mysql.txt
.Looking for Database information in /root/.mythtv/mysql.txt
.Found configuration file /root/.mythtv/mysql.txt
.Looking for Database information in mysql.txt



 CommDetectMaxCommBreakLength    600     alpha2

```

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-08
Ian, I was out for the WE (went skiing) - Thanks a lot for the custom script!

I tried it out:

.Looking for Database information in /usr/local/share/mythtv/mysql.txt
.Looking for Database information in /usr/share/mythtv/mysql.txt
.Found configuration file /usr/share/mythtv/mysql.txt
.Looking for Database information in /etc/mythtv/mysql.txt
.Found configuration file /etc/mythtv/mysql.txt
.Looking for Database information in /usr/local/etc/mythtv/mysql.txt
.Looking for Database information in /home/davidino/.mythtv/mysql.txt
.Found configuration file /home/davidino/.mythtv/mysql.txt
.Looking for Database information in mysql.txt



 CommDetectMaxCommBreakLenght	 800	 mitodue 
 CommDetectMaxCommBreakLenght	 800	 mitodue 


So it seems the values were indeed changed - I need some testing now... I will let you know.
Thanks again

---

### Post by ian dobson on 2010-02-08
Hi,

Read the value name exactly please:-

CommDetectMaxCommBreakLenght is not the same as CommDetectMaxCommBreakLength.

I think thats your problem, your eyes are seeing what you want to see, not whats really there.

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-09
UNBELIEVABLE! Ahahahahaa, what a silly mistake... I kept reading that value over&over and writing it wrong again&again...

Ok back to work from the start - BTW now how do I get ridd of the wrong lines?

Thanks again Ian

---

### Post by dibuntux on 2010-02-09
Ok, I inserted the correct line:

mysql> INSERT INTO mythconverg.settings( Value, DATA, HostName ) VALUES ('CommDetectMaxCommBreakLength','800','mitodue');
Query OK, 1 row affected (0,00 sec)

then quit and re-entered mysql:

mysql> SELECT * FROM mythconverg.settings WHERE 'value' LIKE '%CommD%';
Empty set (0,00 sec)            <--- (still empty???)

then run your program:
davidino@mitodue:~$ ./commflagsettings
.Looking for Database information in /usr/local/share/mythtv/mysql.txt
.Looking for Database information in /usr/share/mythtv/mysql.txt
.Found configuration file /usr/share/mythtv/mysql.txt
.Looking for Database information in /etc/mythtv/mysql.txt
.Found configuration file /etc/mythtv/mysql.txt
.Looking for Database information in /usr/local/etc/mythtv/mysql.txt
.Looking for Database information in /home/davidino/.mythtv/mysql.txt
.Found configuration file /home/davidino/.mythtv/mysql.txt
.Looking for Database information in mysql.txt



 CommDetectMaxCommBreakLenght	 800	 mitodue 
 CommDetectMaxCommBreakLenght	 800	 mitodue 
 CommDetectMaxCommBreakLength	 800	 mitodue 

the third line is correct - what about eliminating the first 2?

---

### Post by ian dobson on 2010-02-09
Hi,

To delete the other 2 ht values just use this sql command

DELETE FROM mythconverg.settings WHERE 'value' LIKE '%CommDetectMaxCommBreakLenght%';

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-09
Nope, I tried but are still there:

mysql> DELETE FROM mythconverg.settings WHERE 'value' LIKE '%CommDetectMaxCommBreakLenght%';
Query OK, 0 rows affected (0,00 sec)

davidino@mitodue:~$ ./commflagsettings
.Looking for Database information in /usr/local/share/mythtv/mysql.txt
.Looking for Database information in /usr/share/mythtv/mysql.txt
.Found configuration file /usr/share/mythtv/mysql.txt
.Looking for Database information in /etc/mythtv/mysql.txt
.Found configuration file /etc/mythtv/mysql.txt
.Looking for Database information in /usr/local/etc/mythtv/mysql.txt
.Looking for Database information in /home/davidino/.mythtv/mysql.txt
.Found configuration file /home/davidino/.mythtv/mysql.txt
.Looking for Database information in mysql.txt



 CommDetectMaxCommBreakLenght	 800	 mitodue 
 CommDetectMaxCommBreakLenght	 800	 mitodue 
 CommDetectMaxCommBreakLength	 800	 mitodue 

mmmhh? TIA

---

### Post by ian dobson on 2010-02-09
Hi,

Maybe try:-
DELETE FROM mythconverg.settings WHERE value = 'CommDetectMaxCommBreakLenght' 

Have you added a space at the end of the value??


Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-10
I tried the command but it did not work - the lines are still there.

---

### Post by ian dobson on 2010-02-10
Hi,

Can you change the line:-
   print  " @$XXX[0]\t @$XXX[1]\t @$XXX[2] \n";

to read
   print  " >@$XXX[0]<\t >@$XXX[1]<\t >@$XXX[2]< \n";

and then rerun my script, you should see something like:-
 >CommDetectMaxCommBreakLength<  >600<   >alpha2<

Deleting the extra values won't make any difference, you can still try the commflagging to see if it works better.

Regards
Ian Dobson

---

### Post by dibuntux on 2010-02-12
Ian, I watched a movie yesterday, and ads cuts where perfect. Still, when I re-run commflag on the same CSI episode I keep for reference it does not work -it finds 4 comm breaks but does not jump - or does not jump right. 
I think I just have to accept that sometimes it works & sometimes not. 
Anyway 2 things seems to appear from this:
1) it was working better in Mythbuntu 9.04, mythtv 0.21
2) there should be an easier way to change that value in CommDetectMaxCommBreakLenght

Thank you so much for helping with this!
Dave

---

### Post by ian dobson on 2010-02-12
Hi,

I normally use phpmyadmin, it's abit of a pain to install. There's a apt package but it didn't work for me. So I had to manually install it.

I'm not sure why it's not jumping automatically, can you still manually jump to the end of the commercial?

Regards
Ian Dobson

---

